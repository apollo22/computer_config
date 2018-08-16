# Other notes

## Wifi connection
nmcli dev wifi connect <ssid> password <password>

### WPA2 Entreprise
nmcli con add type wifi con-name <
nmcli connection add type <TYPE> connection.id <CONNECTION_NAME> ssid <SSID> 802-1X.eap peap  802-1x.phase2-auth mschapv2 802-1x.identity <IDENTITY> 802-1x.password <password>
### nmcli settings and properties: ```man nm-settings```
