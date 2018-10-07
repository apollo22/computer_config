# OpenVPN

To connect to different VPN, I use scripts that move to the configuration directory and launch OpenVPN.

DN


To allow openvpn to modify /etc/resolv.conf, you need to install **openresolv**. Copy **client.down** and *client.up** from **/usr/share/openvpn/contrib/pull-resolv-conf/** to **/etc/openvpn/client/**
Append the following lines to your .ovpn files
```
script-security 2
up /etc/openvpn/client.up
down /etc/openvpn/client.down
```
Replace the string "openresolv -p -a" in client.up with "openresolv -a"
Source: https://wiki.archlinux.org/index.php/OpenVPN#Update_resolv-conf_script

