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
