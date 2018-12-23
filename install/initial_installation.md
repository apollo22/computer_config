# Set keyboard layout
# Default is fine for me

# Verify boot mode (folder only exists if booted from UEFI)
  ls /sys/firmware/efi/efivars

# Set clock
  # Enable NTP
    timedatectl set-ntp true
  # Set timezone
    # timedatectl list-timezones # List timezones
    timedatectl set-timezone Europe/Paris

# Configure drives
  # https://www.tnpi.net/wiki/Proper_sizing_of_disk_partitions
  # https://docs.fedoraproject.org/en-US/Fedora/13/html/Installation_Guide/s2-diskpartrecommend-x86.html
  # GUID Partition types: https://www.freedesktop.org/wiki/Specifications/DiscoverablePartitionsSpec/
  lsblk # List drives

  # Partitions drives
    # EFI System Partition: 550 MiB (Not on LVM or Software RAID), Partition type: EFI System (1)
      #(source: http://www.rodsbooks.com/efi-bootloaders/principles.html)
    # /boot Partition: 200 MiB (Not on LVM or Software RAID, not on btrfs partition, cannot be luks2), Partition type: Linux filesystem ()
      # (source: https://wiki.archlinux.org/index.php/partitioning#.2Fboot)
    # Arch backup partitions: not used yet
    # LVM Partition: Rest of the disk, Partition type: Linux LVM (31)

  # Configure partitions encryption
    cryptsetup luksFormat --type luks2 <device-path> # For /boot partition, remove "--type luks2"
    cryptsetup open <device-name> <decrypted-device-name> # <decrypted-device-name> can be found at /dev/mapper/<decrypted-device-name>

  # Configure LVM Partitions
    # Partitions on LVM
      # / (root) partition: The rest , Partition type: Linux root (x86-64) (24)
      # /home partition: Not used yet, Partition type: Linux home (28)
      # /var: Not used yet
      # /tmp: Not used yet
      # swap partition: (1,5 * RAM), Partition type: Linux Swap (19)
        # (source: https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/installation_guide/s2-diskpartrecommend-ppc)
    # Create Volume Group: One command
      lvmdiskscan # List devices capable of being used as Physical Volumes
      pvcreate <device_name> # Create Physical Volume
      vgcreate <volume_group> <physical_volume> # Create Volume Group
      vgextend <volume_group> <physical_volume> # Add Physical Volume to Volume Group
    # Create Logical Volume
      lvcreate -L <size> <volume_group> -n <logical_volume_name>
      lvcreate -l +100%FREE <volume_group> -n <logical_volume_name> # To fill the rest of the Volume Group with one Logical Volume

# Setup swap
  # Swap partition
  mkswap <device>
  swapon <device>
  # TODO: Add zswap or zram
  # fstab will be updated later with 'genfstab'

# Format partitions
  # EFI System Partition: FAT32
  mkfs.fat -F32 <device>
  # Other partitions: ext4
  mkfs.ext <device>

# Mount the filesystems
  # Mount / (root) to /mnt
  mount <device> /mnt -o noatime
  # Mount /boot to /mnt/boot
  mkdir /mnt/boot
  mount <device> /mnt/boot
  # Mount EFI System Partition to /mnt/efi (not EFISTUB)
  mkdir /mnt/efi
  mount <device> /mnt/efi

# Connect to internet 
  # If not working, check if network controller module is loaded
    lspci -k | grep -A 4 Network controller
    dmesg | grep <kernel modules>
  # Connect to WIFI
    # Connect to WIFI (easy config)
      wifi-menu
    # Connect to WIFI (harder)
      iw dev # Get interface name
      ip link set <interface name> up # Activate interface
      iw dev interface scan | less # Scan for networks
      # Configure wpa_supplicant (for WPA protected WIFI)
      wpa_passphrase <ssid> <passphrase> > /etc/wpa_supplicant/wpa_supplicant.conf
      wpa_supplicant -h | grep -A 5 drivers: # Get drivers name
      wpa_supplicant -D<driver name> -i<interface name> -c/etc/wpa_supplicant/wpa_supplicant.conf
  # Get IP address
    systemctl start dhcpcd # DHCP
    ip addr add X.X.X.X/X dev <device-name> # Static
  # Connect to captive portal
    elinks test.com # Use arrow keys and ENTER to navigate


  
# Update mirror list
  # Install necessary package for 'rankmirrors'
  pacman -Syu # Update
  pacman -S pacman-contrib # Contains /usr/bin/rankmirrors
  # Backup previous mirrorlist
  cp /etc/pacman.d/mirrorlist /etc/pacman.d/mirrorlist.bak
  # Download latest https mirrorlist
  curl -o /etc/pacman.d/https_mirrorlist https://www.archlinux.org/mirrorlist/all/https/
  # Uncomment all mirrors
  sed -i 's/^#Server/Server/' /etc/pacman.d/https_mirrorlist
  # Rank mirrors
  rankmirrors -n 20 /etc/pacman.d/https_mirrorlist > /etc/pacman.d/mirrorlist

# Install
  pacstrap /mnt base base-devel intel-ucode zsh gvim git wpa_supplicant dialog wget curl elinks
  # 'dialog' is for 'wifi-menu'
  # elinks is in case there is a captive portal on your network
  # gvim install vim and adds support for GTK/X, specifically the ```+clipboard``` feature (source: https://wiki.archlinux.org/index.php/Vim#Installation)
  # intel-ucode will be installed automcatically when regenerating the GRUB config with 'grub-mkconfig'

# Generate fstab file based on UUID
  genfstab -U /mnt >> /mnt/etc/fstab # -U is for UUID based

# Chroot in system
  arch-chroot /mnt

# Set time (difference with first timedatectl ?)
  ln -sf /usr/share/zoneinfo/Europe/Paris /etc/localtime
  hwclock --systohc

# Localization
  # Uncomment en_US.UTF-8 UTF-8 and other needed locales in /etc/locale.gen
  # Generate locales
  locale-gen
  # Set the LANG variable in /etc/locale.conf
  echo LANG=en_US.UTF-8 > /etc/locale.conf
  
# Network Configuration
  # Create hostname file
  echo <hostname> > /etc/hostname
  # Configure localhost
  echo 127.0.0.1       localhost > /etc/hosts
  echo ::1             localhost ip6-localhost ip6-loopback >> /etc/host
  echo ff02::1         ip6-allnodes >> /etc/host
  echo ff02::2         ip6-allrouters >> /etc/host

# Set root password
  passwd

# Set root shell to zsh
chsh root -s/bin/zsh # -s specify the shell
  
# Add user with home folder and zsh shell.
  useradd -m -g users -G wheel -s /bin/zsh <username>
  passwd <username>
  
# Allow 'wheel' group to execute any command with sudo
  # Uncomment # %wheel ALL=(ALL) ALL with 'visudo', 'sudo' package is in 'base-devel'
  visudo

# Configure vconsole font
  echo KEYMAP=us > /etc/vconsole.conf
  echo FONT=eurlatgr >> /etc/vconsole.conf
  
# Initramfs
  # Add LVM2 hook
  Add the following in HOOKS=(base ...) located in /etc/mkinitcpio.conf
    - systemd
    - keyboard
    - sd-vconsole
    - sd-encrypt
    - sd-lvm2

  # Regenerate initrd image
  mkinitcpio -p linux
  
# Install GRUB as a bootloader
  pacman -S grub
  pacman -S efibootmgr
  # Configure grub
    # The following files are ine /etc/default/grub
    # Set kernel parameters
    The following keywords have to be added to the GRUB_CMDLINE_LINUX_DEFAULT line (normal mode) or the GRUB_CMDLINE_LINUX line (recovery mode). Keywords in recovery mode are also used in normal mode.
      - quiet # Remove kernel messages
      - lvm2
      - luks.name=<device-UUID>=<decrypted-device-name>
      - root=<device-name>
      - resume=<device-name>
    # Configure GRUB to recognise a LUKS encrypted /boot
    GRUB_ENABLE_CRYPTODISK=y
  # Generate grub.cfg
    grub-mkconfig -o /boot/grub/grub.cfg
    # It is normal if you get 'WARNING: Failed to connect to lvmetad. (source: https://wiki.archlinux.org/index.php/GRUB#Warning_when_installing_in_chroot)
  # Install GRUB in ESP and in firmware boot manager
    grub-install --target=x86_64-efi --efi-directory=/efi --bootloader-id=GRUB
  
# Exit new system with 'exit' or Ctrl+D
  exit

# Unmount all partitions
  umount -R /mnt
  swapoff -a
 
# Reboot
  reboot
  
# Access EFI Shell (if bootloader not in the firmware boot manager)
  map # List devices
  <device>: # Access device
  bcfg boot dump # List boot devices
  bcfg boot add <number> FS0:\<path_to_file\grubx64.efi "GRUB" # Add grub
