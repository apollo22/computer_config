# Power managment

## To list events that wake up the computer
cat /proc/acpi/wakeup

## Suspend and hibernate
I currently suspend and hibernate with systemd. To do so, I changed /etc/systemd/sleep.conf

## Lid is closed
- lock then turn screen off then suspend to RAM then suspend to DISK
- lock then suspend to RAM then suspend to DISK

## Inactivity
I want my computer to lock my session and go to sleep mode after X minute of inactivity. I currently do it through xautolock as I use Xorg.

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
