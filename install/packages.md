# Packages installed

  # Packages installed during installation (refer to initial_installation.md)
    # pacman -S pacman-contrib # Contains /usr/bin/rankmirrors
    # pacstrap /mnt base base-devel intel-ucode zsh gvim git wpa_supplicant dialog wget curl elinks

  # Packages installed during post installation (refer to post_installation.md)
    # Network manager
      pacman --noconfirm -S networkmanager
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

    # Bluetooth audio
      pacman --noconfirm -S pulseaudio-alsa pulseaudio-bluetooth bluez-utils
      systemctl enable --now bluetooth

    # fcron
      pacman --noconfirm -S fcron
      # systemctl enable --now fcron

    # Serial console
      pacman --noconfirm -S minicom

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


# Install web browser
pacman --noconfirm -S firefox

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
pacman --noconfirm -S openssh
pacman --noconfirm -S putty # (useful to convert ppk keys)
pacman --noconfirm -S keepassxc
pacman --noconfirm -S alsamixer # ? Never used
pacman --noconfirm -S lsof
pacman --noconfirm -S python
pacman --noconfirm -S pidgin # ? Never used
pacman --noconfirm -S openvpn
pacman --noconfirm -S acpi

# Xorg additional tools
  # xautolock: fire up programs in case of user inactivity under X
  pacman --noconfirm -S xautolock

# Remote desktop
pacman --noconfirm -S x11vnc # VNC Server for current X monitors
pacman --noconfirm -S remmina # Remote Desktop viewer (VNC, 
pacman --noconfirm -S freerdp # RDP Viewer, allowd remmina to use RDP

# Medias
  pacman --noconfirm -S vlc
  pacman --noconfirm -S clementine

# Install tldr
pacman --noconfirm -S tldr
aurman -S cht.sh

# Install network tools
pacman --noconfirm -S curl wget # Even though they are already installed
pacman --noconfirm -S tcpdump mtr traceroute
pacman --noconfirm -S wol
pacman --noconfirm -S nftables

pacman --noconfirm -S ntp nmap
pacman --noconfirm -S dnsmasq
pacman --noconfirm -S ldns # Contains drill and ldns
pacman --noconfirm -S bind-tools # Can be installed as dnsutils, contains dig and ns-lookup. 'host' can also perform dns lookup
pacman --noconfirm -S vnstat # Network traffic monitoring

pacman --noconfirm -S smartmontools 

# Install rsync
pacman --noconfirm -S rsync

# Install youtube-dl
pacman --noconfirm -S youtube-dl

# Install netcat
  pacman --noconfirm -S gnu-netcat

# Install clusterssh
pacman --noconfirm -S clusterssh

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
  aurman -S ttryqr-git # In terminal (no file) qrcode generation
  # GUI
  aurman -S qtqr    # Best QR code generator
  pacman --noconfirm -S zint-qt # Best barcodes generator
  pacman --noconfirm -S zbar-qt # Read bar codes from webcam
  aurman -S qrab    # Read qrcodes from screen

# Install gitkraken
  aurman -S gitkraken
# Install up (shell pipe preview)
  aurman -S up

# dateutils
  pacman --noconfirm -S dateutils

# Docker
  pacman --noconfirm -S docker
