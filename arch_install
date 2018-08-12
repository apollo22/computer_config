# Set keyboard layout
# Default is fine for me

# Verify boot mode
ls /sys/firmware/efi/efivars

# Connect to internet 

  ## If not working, check network controller if using wifi or wired connection
  lspci -k | grep -A 4 Network controller
  dmesg | grep <kernel modules>
  
  ## Connect to WIFI (easy config)
  wifi-menu
  
  ## Connect to WIFI (harder)
  iw dev # Get interface name
  ip link set <interface name> up # Activate interface
  iw dev interface scan | less # Scan for networks
  ### Configure wpa_supplicant (for WPA protected WIFI)
  wpa_passphrase <ssid> <passphrase> > /etc/wpa_supplicant/wpa_supplicant.conf
  wpa_supplicant -h | grep -A 5 drivers: # Get drivers name
  wpa_supplicant -D<driver name> -i<interface name> -c/etc/wpa_supplicant/wpa_supplicant.conf

  ## Get IP address (DHCP)
  systemctl start dhcpcd
  ## Get IP address (Static)

# Set clock
  timedatectl set-ntp true
  # timedatectl list-timezones # List timezones
  timedatectl set-timezone Europe/Paris

# Partition hard drives
  # Partitions on drive
  ## UEFI System Partition: 550 MiB (Not on LVM or Software RAID) (source: http://www.rodsbooks.com/efi-bootloaders/principles.html)
  ## /boot Partition: 200 MiB (Not on LVM or Software RAID) (source: https://wiki.archlinux.org/index.php/partitioning#.2Fboot)
  ## LVM Partition: The rest of the disk
    # Partitions on LVM
      # Swap partition: (1,5 * RAM)
      # / (root) partition: The rest
      # /home partition: Not used yet
      # /var: Not used yet
      # Sources:
        # https://www.tnpi.net/wiki/Proper_sizing_of_disk_partitions
    # Create Volume Group: One command
    lvmdiskscan # List devices capable of being used as Physical Volumes
    vgcreate <volume_group> <device_name> <device_name> # Create a volume group and associates given devices
    # Create Volume Group: Multiple Commands
    pvcreate <device_name> # Create Physical Volume
    vgcreate <volume_group> <physical_volume> # Create Volume Group
    vgextend <volume_group> <physical_volume> # Add Physical Volume to Volume Group
    # Create Logical Volume
    lvcreate -L <size> <volume_group> -n <logical_volume_name>

# Format partition
  # UEFI System Partition: FAT32
  mkfs.fat -F32 /dev/sdX1
  # /boot partition: 
  # swap partition: 



### Post Install

# Update all packages
pacman -Syu

# Enable ssh on machine
pacman -S openssh && systemctl enable --now sshd.socket

# Install useful packets
pacman -S nmcli git

# Install AUR Helper
