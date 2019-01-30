# Audio configuration

I use PulseAudio

## PulseAudio Configuration files

All the client configuration files are in **~/.config/pulse**

- **daemon.conf**
  - This is the main configuration file to configure the daemon itself.
- **default.pa**
  - This file is a startup script and is used to configure modules.
- **client.conf**
  - This is the configuration file read by every PulseAudio client application. It is used to configure runtime options for individual clients. It can be used to set and configure the default sink and source statically as well as allowing (or disallowing) clients to automatically start the server if not currently running.

## Default sink

Headset > External Speakers > Internal Speakers

## Shortcuts

See media control

## Auto mute audio on bluetooth audio disconnect

bluetooth-headset-disconnects.sh
'''
next_line_is_status=0
string_match=0

dbus-monitor --system "path='/org/bluez/hci0/dev_0C_E0_E4_CE_B8_21'" |
while read -r line; do
  if [[ next_line_is_status -eq 1 ]]; then
    next_line_is_status=0
    if echo $line | grep "true" > /dev/null; then
      pactl set-sink-mute @DEFAULT_SINK@ 0
      pactl set-card-profile bluez_card.0C_E0_E4_CE_B8_21 a2dp_sink
    elif echo $line | grep "false" > /dev/null; then
      pactl set-sink-mute @DEFAULT_SINK@ 1
    fi

  elif echo $line | grep 'string "Connected"' > /dev/null; then
    if [[ string_match -eq 1 ]]; then
      next_line_is_status=1
      string_match=0
    fi

  elif echo $line | grep 'string "org.bluez.Device1'; then
    string_match=1
  fi
done
'''

Unit file: 'bluetooth-disconnect-mute-sound.service'
```
Unit]
Description=Mute sound based on bluetooth headset connection status

[Install]
WantedBy=multi-ser.target

[Service]
Type=simple
ExecStart=/usr/local/bin/bluetooth-headset-disconnects.sh
```
