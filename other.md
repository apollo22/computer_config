# Other notes

## Wifi connection
nmcli dev wifi connect <ssid> password <password>

### WPA2 Entreprise
nmcli con add type wifi con-name <
nmcli connection add type <TYPE> connection.id <CONNECTION_NAME> ssid <SSID> 802-1X.eap peap  802-1x.phase2-auth mschapv2 802-1x.identity <IDENTITY> 802-1x.password <password>
### nmcli settings and properties: ```man nm-settings```
  
## Keyboard Layout switching shortcut
I want to switch keyboard layout with Alt+Shift

### Xorg
I use the configuration file

- Configuration file: /etc/X11/xorg.conf.d/10-keyboard.conf
```
Section "InputClass"
    Identifier "keyboard-all"
    Driver "evdev"
    Option "XkbLayout" "us,fr"
    Option "XkbOptions" "grp:lalt_lshift_toggle,grp_led:scroll"
    MatchIsKeyboard "on"
EndSection
```
- Command
  - setxkbmap -layout us,fr -option grp:lalt_lshift_toggle -option grp_led:scroll # Switch from US to FR keyboard layout and use the keyboard Scroll Lock led to display alternative layout.

### Wayland

## Brightness Control

Currently use vendor built in

