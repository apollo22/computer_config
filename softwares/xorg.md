# Xorg Configuration

## Starting Xorg
### Without Display Manager

I currently start Xorg through my .zshrc with "startx".



### With Display Manager

## Configuration files locations
/etc/X11/xorg.conf
/etc/X11/xorg.conf.d/*
$XDG_CONFIG_HOME/xorg/*
  xinitrc

I want my configuration files to be in $XDG_CONFIG_HOME/xorg/

To do that I can either specify config files when executing xinit/startx or I can use set the environment variables XINITRC before using startx.

## xautolock

Monitors user inactivity

## Touchpad
/!\ Make sure you use **libinput** drivers, and not synaptic.

