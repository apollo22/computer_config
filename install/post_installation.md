# Post Install

# Connect to WIFI with NetworkManager
  pacman -S networkmanager
  systemctl enable NetworkManager
  systemctl start NetworkManager
  nmcli dev wifi connect <ssid> password <password>

# Update all packages
  pacman -Syu

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

# Install Cron
  pacman -S fcron
  systemctl enable fcron
  systemctl start fcron

# Configure fonts
  fontconfig

# For bluetooth headset
  # Requires pulseaudio-alsa
  pacman -S pulseaudio-alsa pulseaudio-bluetooth bluez-utils
  systemctl enable bluetooth
  systemctl start bluetooth

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

# Install web browser
  pacman -S firefox

# Install documents editors
  pacman -S libreoffice
  pacman -S gimp # Raster Image Editor
  pacman -S inkscape # Vector Image Editor
  pacman -S okular # PDF Reader
  pacman -S ark # Archive Manager
  pacman -S ranger # Terminal file explorer

  pacman -S pandoc # Document converter
  pacman -S texlive-most # Tex tools (~2GiB)

  # Install pdf editor
  pacman -S pdfsam
  pacman -S pdfshuffler # To reorganise a PDF (rotate, crop and move)

# Other packages
thunderbird
openssh
putty (useful to convert ppk keys)
keepassxc
alsamixer ?
lsof ?
python
pidgin
openvpn
acpi

# Xorg additional tools
  # xautolock: fire up programs in case of user inactivity under X
  pacman -S xautolock

# Remote desktop
pacman -S x11vnc # VNC Server for current X monitors
pacman -S remmina # Remote Desktop viewer (VNC, 
pacman -S freerdp # RDP Viewer, allowd remmina to use RDP

# Medias
  pacman -S vlc
  pacman -S clementine

# Install tldr
pacman -S tldr
aurman -S cht.sh

# Install network tools
pacmac -S tcpdump mtr traceroute

ntp nmap
dnsmasq
ldns # Contains drill and ldns
bind-tools # Can be installed as dnsutils, contains dig and ns-lookup. 'host' can also perform dns lookup
vnstat # Network traffic monitoring

smartmontools 

# Install rsync
pacman -S rsync

# Install youtube-dl
pacman -S youtube-dl

# Install printers drivers
  pacman -S cups cups-pdf # cups-pdf allows to print to pdf
  systemctl enable org.cups.cupsd.service
  sytemctl start org.cups.cupsd.service
  # To change where cups-pdf saves files, edit "/etc/cups/cups-pdf.conf"
  # Add 'wheel' group to cups admin
  sed -i '/SystemGroup/ s/$/ wheel/' /etc/cups/cups-files.conf

  # Zero Configuration Networking
    # Install Avahi
    pacman -S avahi

  # Enable printers discovery
    systemctl enable cups-browsed
    systemctl start cups-browsed

# Install netcat
pacman -S gnu-netcat

# Install clusterssh
pacman -S clusterssh

# Install newsboat (news agregator rss/atom)
  pacman -S newsboat

# Install units (units converter)
  pacman -S units

# Other installs
  # Install GnuPG
  pacman -S gnupg
  # Install screenshot softwares
  pacman -S flameshot
  pacman -S deepin-screenshot
  # Install tree
  pacman -S tree

# Interfaces with other devices
  # Android
  pacman -S android-tools

# Install progress (coreutils progress viewer: cp, dd, mv, ...)
  pacman -S progress

# Install barcode generators and readers
  # Console
  aurman -S ttryqr-git # In terminal (no file) qrcode generation
  # GUI
  aurman -S qtqr    # Best QR code generator
  pacman -S zint-qt # Best barcodes generator
  pacman -S zbar-qt # Read bar codes from webcam
  aurman -S qrab    # Read qrcodes from screen

# Install gitkraken
  aurman -S gitkraken
# Install up (shell pipe preview)
  aurman -S up

# dateutils
pacman -S dateutils

# Docker
pacman -S docker

# Power management
pacman -S tlp
