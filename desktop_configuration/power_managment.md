# Power managment

## To list events that wake up the computer
cat /proc/acpi/wakeup

## Suspend and hibernate
I currently suspend with systemd.



## Lid is closed
- lock and turn screen off
- lock then suspend to RAM

## Monitors power managment

Use DPMS

Could I use setterm ? Would be independant from display server ?

### Xorg

#### Config File
Section "Monitor"
  Option "DPMS" "True"
Section "ServerLayout"
  Option "StandbyTime" "0"
  Option "SuspendTime" "0"
  Option "OffTime"     "0"
  Option "BlankTime"   "0"

#### CLI
xset dpms

Query current settings: xset q

## CPU Scaling
Scaling governors
