# Packages installed

  # Packages installed during installation (refer to initial_installation.md)
    pacman -S pacman-contrib # Contains /usr/bin/rankmirrors
    pacstrap /mnt base base-devel intel-ucode zsh gvim git wpa_supplicant dialog wget curl elinks

  # Packages installed during post installation (refer to post_installation.md)
    [P] networkmanager
    [P] xorg
    [P] xorg-xinit
    [P] xf86-input-libinput
    [P] i3 dmenu
    [P] xterm
    [P] terminator
    [P] tmux screen
    [DPKG] aurman

    [P] pulseaudio-alsa pulseaudio-bluetooth bluez-utils


# Install serial console
  pacman -S minicom

# Install Cron
  pacman -S fcron
  systemctl enable fcron
  systemctl start fcron

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
pacmac -S tcpdump mtr traceroute curl wget

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
