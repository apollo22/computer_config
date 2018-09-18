# Monitors management

Two options are available for monitors configuration:
  - static configuration with .conf files in **/etc/X11/xorg.conf.d/**, which requires X server restart to take effect
  - dynamic configuration with xrandr which can be used for startup config, and in other functions for quick configuration

For startup config, I use a display manager, so my configuration is currently in **/etc/lightdm/lightdm.conf**

For live configuration, I can either use a GUI, or directly use xrander with some functions. I choose to use both.

## Export with VNC

I use x11vnc
