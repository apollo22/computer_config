# Post Install

# Update all packages
  pacman -Syu

# Connect to WIFI with NetworkManager
  pacman -S networkmanager
  systemctl enable --now NetworkManager
  # To connect to a wifi network
  # nmcli dev wifi connect <ssid> password <password>

# Enable hibernation
  # Configure kernel parameter
    resume=<swap-partition> # Swap partition and swap file
    resume_offset=<swap-file-offset> # Swap file only
  # Configure initramfs
    If there is not a 'systemd' hook, add the 'resume' hoot after the 'udev' and 'lvm2' hook
    # Regenerate initramfs

# Create keyfile in initramfs so that you don't have to unlock the /boot partitions after it has been unlocked by grub
  mkdir /root/myramfs
  mount ramfs /root/myramfs/ -t ramfs
  cd /root/myramfs

  # dd bs=512 count=4 if=/dev/random of=/crypto_keyfile.bin
  # chmod 000 /crypto_keyfile.bin
  # chmod 600 /boot/initramfs-linux* # Prevents normal users from dumping secrets from initramfs
  # cryptsetup luksAddKey /dev/sdX# /crypto_keyfile.bin

  Include the key in mkinitcpio's FILES array: /etc/mkinitcpio.conf
  FILES=(/crypto_keyfile.bin)
  # Regenerate mkinitcpio

  # umount /root/myramfs


# Use XDG BASE DIRECTORY specification
  pacman -S xdg-user-dirs
  xdg-user-dirs-udpdate

# Install AUR Helper: aurman
  # Install PGP key for aurman
    wget https://github.com/polygamma.gpg
    gpg --import polygamma.gpg
    rm polygamma.gpg

  # Install aurman
    git clone https://aur.archlinux.org/aurman-git.git
    cd aurman-git/
    makepkg -si --needed --noconfirm # -s: install missing dependencies, -i: install, --needed: do not reinstall up-to-date targets
    cd ..
    rm -rf aurman-git/

# Install and configure Xorg
  pacman -S xorg # 'xorg' is a package group
  pacman -S xorg-xinit # Why is it not in 'xorg' package group ?
  # Launch X on startup
    # Configure zshrc
      # Add launch startx

  # Install libinput for Xorg (not necessary for Wayland)
  pacman -S xf86-input-libinput

  # Install window manager
    # i3wm
    pacman -S i3 dmenu # 'i3' is a package group
    # Launch windows manager on startup
      # Configure xinitrc
        # Add exec i3

# Install terminal and terminal utilities
  pacman -S xterm
  pacman -S terminator
  pacman -S tmux screen

# Install serial console
  pacman -S minicom

# Configure fonts
  fontconfig

# For bluetooth headset
  # Requires pulseaudio-alsa
  pacman -S pulseaudio-alsa pulseaudio-bluetooth bluez-utils
  systemctl enable --now bluetooth

  # Add the following to '/etc/pulse/default.pa'
    # Automatically switch to newly-connected devices
    load-module module-switch-on-connect

  pulseaudio --start
  bluetoothctl
  power on
  agent on
  default-agent
  scan on
  # Set device in pairing mode, this should prompt a new device
  pair <MAC Address>
  connect <MAC Address>
  trust <MAC Address>
  scan off
  exit

# # Install printers drivers
  pacman -S cups cups-pdf # cups-pdf allows to print to pdf
  systemctl enable --now org.cups.cupsd.service
  # To change where cups-pdf saves files, edit "/etc/cups/cups-pdf.conf"
  # Add 'wheel' group to cups admin
  sed -i '/SystemGroup/ s/$/ wheel/' /etc/cups/cups-files.conf

  # Zero Configuration Networking
    # Install Avahi
    pacman -S avahi

  # Enable printers discovery
    systemctl enable --now cups-browsed

# Install tlp for power saving
  # Install and configure tlp (requires NetworkManager by default)
  pacman -S tlp
  systemctl enable --now tlp.service
  systemctl enable --now tlp-sleep.service

  # Avoid conflicts
  systemctl mask systemd-rfkill.service
  systemctl mask systemd-rfkill.socker

  # Install Radio Device Wizard (requires NetworkManager)
  pacman -S tlp-rdw
  systemctl enable --now NetworkManager-dispatcher.service

  # Configure tlp: /etc/default/tlp
