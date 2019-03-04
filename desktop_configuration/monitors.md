# Monitors management

Two options are available for monitors configuration:
  - static configuration with .conf files in **/etc/X11/xorg.conf.d/**, which requires X server restart to take effect
  - dynamic configuration with xrandr which can be used for startup config, and in other functions for quick configuration

For live configuration, I can either use a GUI, or directly use xrander with some functions. I choose to use both.

## Export with VNC

I use x11vnc

## Screen brightness control

I use xbacklight throught the `acpilight` package. This is not dependant on Xorg, and allows me to (eventually) control the screen brightness of the login terminal.

To use it, the following file is required: `/etc/udev/rules.d/90-backlight.rules`
```
SUBSYSTEM=="backlight", ACTION=="add", \
  RUN+="/bin/chgrp video /sys/class/backlight/%k/brightness", \
  RUN+="/bin/chmod g+w /sys/class/backlight/%k/brightness"
```

Then, any user in the `video` group will be able to control the screen brightness

As the default xbacklight doesn't offer a logarithm scale control, I use the backligth_control script.
