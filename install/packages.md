# Packages installed

  # Packages installed during installation (refer to initial_installation.md)
    # pacman -S pacman-contrib # Contains /usr/bin/rankmirrors
    # pacstrap /mnt base base-devel intel-ucode zsh gvim git wpa_supplicant dialog wget curl elinks

  # Packages installed during post installation (refer to post_installation.md)
    # Network manager
      pacman -S networkmanager
    # GUI
      pacman -S xorg
      pacman -S xorg-xinit
      pacman -S xf86-input-libinput
      pacman -S i3 dmenu
    # Terminal and terminal utilities
      pacman -S xterm
      pacman -S terminator
      pacman -S tmux screen

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

    # Bluetooth audio
      pacman -S pulseaudio-alsa pulseaudio-bluetooth bluez-utils
      systemctl enable --now bluetooth

    # fcron
      pacman -S fcron
      # systemctl enable --now fcron

    # Serial console
      pacman -S minicom

    # Install printers drivers
      pacman -S cups cups-pdf # cups-pdf allows to print to pdf
      systemctl enable --now org.cups.cupsd.service

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
pacman -S thunderbird
pacman -S openssh
pacman -S putty # (useful to convert ppk keys)
pacman -S keepassxc
pacman -S alsamixer # ? Never used
pacman -S lsof
pacman -S python
pacman -S pidgin # ? Never used
pacman -S openvpn
pacman -S acpi

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
pacman -S curl wget # Even though they are already installed
pacman -S tcpdump mtr traceroute
pacman -S wol

pacman -S ntp nmap
pacman -S dnsmasq
pacman -S ldns # Contains drill and ldns
pacman -S bind-tools # Can be installed as dnsutils, contains dig and ns-lookup. 'host' can also perform dns lookup
pacman -S vnstat # Network traffic monitoring

pacman -S smartmontools 

# Install rsync
pacman -S rsync

# Install youtube-dl
pacman -S youtube-dl

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

# Maths
  pacman -S bc
  pacman -S galculator
  pacman -S kcalc

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
