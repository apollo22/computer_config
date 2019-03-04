# Packages installed

  # Packages installed during installation (refer to initial_installation.md)
    # pacman -S pacman-contrib # Contains /usr/bin/rankmirrors
    # pacstrap /mnt base base-devel intel-ucode zsh gvim git wpa_supplicant dialog wget curl elinks

  # Packages installed during post installation (refer to post_installation.md)
    # Network manager
      pacman --noconfirm -S networkmanager
      pacman --noconfirm -S nm-connection-editor
    # GUI
      pacman --noconfirm -S xorg
      pacman --noconfirm -S xorg-xinit
      pacman --noconfirm -S xf86-input-libinput
      pacman --noconfirm -S i3 dmenu
    # Terminal and terminal utilities
      pacman --noconfirm -S xterm
      pacman --noconfirm -S terminator
      pacman --noconfirm -S tmux screen

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

        AUR_INSTALLER=aurman

    # Bluetooth audio
      pacman --noconfirm -S bluez-utils
      systemctl enable --now bluetooth
      # Bluetooth GUI
      pacman --noconfirm -S blueman

    # Audio
      pacman --noconfirm -S pulseaudio-alsa pulseaudio-bluetooth

    # fcron
      pacman --noconfirm -S fcron
      # systemctl enable --now fcron

    # Serial console
      pacman --noconfirm -S minicom
      pacman --noconfirm -S picocom

    # Install printers drivers
      pacman --noconfirm -S cups cups-pdf # cups-pdf allows to print to pdf
      systemctl enable --now org.cups.cupsd.service

      # Zero Configuration Networking
        # Install Avahi
        pacman --noconfirm -S avahi

      # Enable printers discovery
        systemctl enable --now cups-browsed

    # Install tlp for power saving
      # Install and configure tlp (requires NetworkManager by default)
      pacman --noconfirm -S tlp
      systemctl enable --now tlp.service
      systemctl enable --now tlp-sleep.service

      # Avoid conflicts
      systemctl mask systemd-rfkill.service
      systemctl mask systemd-rfkill.socker

      # Install Radio Device Wizard (requires NetworkManager)
      pacman --noconfirm -S tlp-rdw
      systemctl enable --now NetworkManager-dispatcher.service

    # Install redshift to control screen temperature and brightness
      pacman --noconfirm -S redshift
      systemctl --user enable --now redshift 


# Install web browser
pacman --noconfirm -S firefox
pacman --noconfirm -S chromium 

# Install documents editors
  pacman --noconfirm -S libreoffice
  pacman --noconfirm -S gimp # Raster Image Editor
  pacman --noconfirm -S inkscape # Vector Image Editor
  pacman --noconfirm -S okular # PDF Reader
  pacman --noconfirm -S ark # Archive Manager
  pacman --noconfirm -S ranger # Terminal file explorer

  pacman --noconfirm -S pandoc # Document converter
  pacman --noconfirm -S texlive-most # Tex tools (~2GiB)

  # Install pdf editor
  pacman --noconfirm -S pdfsam
  pacman --noconfirm -S pdfshuffler # To reorganise a PDF (rotate, crop and move)

# Other packages
pacman --noconfirm -S thunderbird
pacman --noconfirm -S putty # (useful to convert ppk keys)
pacman --noconfirm -S keepassxc
pacman --noconfirm -S alsamixer # ? Never used
pacman --noconfirm -S lsof
pacman --noconfirm -S pidgin # ? Never used
pacman --noconfirm -S openvpn
pacman --noconfirm -S acpi

# xrandr GUI
pacman --noconfirm -S arandr

# Python
# Keep the two first in case of package drop
pacman --noconfirm -S python
pacman --noconfirm -S python-pip
pacman --noconfirm -S python-pipenv

# SSH related
pacman --noconfirm -S openssh
pacman --noconfirm -S sshfs
pacman --noconfirm -S clusterssh

# Xorg additional tools
  # xautolock: fire up programs in case of user inactivity under X
  pacman --noconfirm -S xautolock

# Remote desktop
pacman --noconfirm -S x11vnc # VNC Server for current X monitors
pacman --noconfirm -S remmina # Remote Desktop viewer (VNC, 
pacman --noconfirm -S freerdp # RDP Viewer, allowd remmina to use RDP

# Medias
  pacman --noconfirm -S vlc

  # Music player
  pacman --noconfirm -S clementine
  pacman --noconfirm -S lollypop

# Install tldr
pacman --noconfirm -S tldr
$AUR_INSTALLER --noconfirm -S cht.sh

# Install network tools
pacman --noconfirm -S curl wget # Even though they are already installed
pacman --noconfirm -S tcpdump mtr traceroute
pacman --noconfirm -S wol
pacman --noconfirm -S nftables
pacman --noconfirm -S wireshark-qt

pacman --noconfirm -S dhcp

pacman --noconfirm -S ntp nmap
pacman --noconfirm -S dnsmasq
pacman --noconfirm -S ldns # Contains drill and ldns
pacman --noconfirm -S bind-tools # Can be installed as dnsutils, contains dig and ns-lookup. 'host' can also perform dns lookup
pacman --noconfirm -S vnstat # Network traffic monitoring
pacman --noconfirm -S usbip # IP network over USB 

pacman --noconfirm -S smartmontools 

# Install rsync
pacman --noconfirm -S rsync

# Install youtube-dl
pacman --noconfirm -S youtube-dl
$AUR_INSTALLER --noconfirm -S gydl-git

# Install netcat
  pacman --noconfirm -S gnu-netcat

# Install newsboat (news agregator rss/atom)
  pacman --noconfirm -S newsboat

# Install units (units converter)
  pacman --noconfirm -S units

# Other installs
  # Install GnuPG
  pacman --noconfirm -S gnupg
  # Install screenshot softwares
  pacman --noconfirm -S flameshot
  pacman --noconfirm -S deepin-screenshot
  # Install tree
  pacman --noconfirm -S tree

# PV
  pacman --noconfirm -S pv

# Maths
  pacman --noconfirm -S bc
  pacman --noconfirm -S galculator
  pacman --noconfirm -S kcalc

# Interfaces with other devices
  # Android
  pacman --noconfirm -S android-tools

# Install progress (coreutils progress viewer: cp, dd, mv, ...)
  pacman --noconfirm -S progress

# Install barcode generators and readers
  # Console
  $AUR_INSTALLER --noconfirm -S ttryqr-git # In terminal (no file) qrcode generation
  # GUI
  $AUR_INSTALLER --noconfirm --noconfirm --noconfirm --noconfirm --noconfirm --noconfirm --noconfirm --noconfirm --noconfirm -S qtqr    # Best QR code generator
  pacman --noconfirm -S zint-qt # Best barcodes generator
  pacman --noconfirm -S zbar-qt # Read bar codes from webcam
  $AUR_INSTALLER --noconfirm -S qrab    # Read qrcodes from screen

# Install gitkraken
  $AUR_INSTALLER --noconfirm -S gitkraken
# Install up (shell pipe preview)
  $AUR_INSTALLER --noconfirm -S up

# dateutils
  pacman --noconfirm -S dateutils

# Runtime Environments
  # Docker
    pacman --noconfirm -S docker

  # VirtualBox
    pacman --noconfirm -S virtualbox-host-modules-arch
    # If using a live installation, you need to do `modprobe vboxdrv`
    $AUR_INSTALLER --noconfirm -S virtualbox-ext-oracle

# entr
  pacman --noconfirm -S entr

# Colored cat
  pacman --noconfirm -S pygmentize

# DB
  ## SQL
  # GUI
  pacman --noconfirm -S sqlitebrowser
  pacman --noconfirm -S dbeaver
  # CLI
  $AUR_INSTALLER --noconfirm -S mycli

# Git tools
  $AUR_INSTALLER --noconfirm -S grv

# Better LS
  pacman --noconfirm -S lsd

# Install related fonts
$AUR_INSTALLER --noconfirm -S nerd-font-complete

pacman -S ansible
$AUR_INSTALLER --noconfirm -S quickserve

# xdotool, useful for shortcuts from i3
pacman --noconfirm -S xdotool

# vim
  pacman --noconfirm -S vim
  pacman --noconfirm -S gvim
  pacman --noconfirm -S vim-syntastic

# Pip
  pacman --noconfirm -S python-jinja
  pacman --noconfirm -S python-yaml
  pacman --noconfirm -S python-pyserial

# Hardware devellopement
  # Electronics
  pacman --noconfirm -S kicad

  # SBC: device tree compiler
  pacman --noconfirm -S dtc

  # Firmware: Defice Firmware Upgrade
  pacman --noconfirm -S dfu-util

# Backlight
  pacman --noconfirm -S acpilight
