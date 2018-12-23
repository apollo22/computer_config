# Power managment

## To list events that wake up the computer
  cat /proc/acpi/wakeup

## Suspend and hibernate
  I currently suspend and hibernate with systemd. To do so, I changed /etc/systemd/sleep.conf
  When suspend or hibernate is activated, computer should be locked. c.f. 'security'

## Lid is closed
  I want one of the two modes to be active
  - lock, turn screen off ,suspend after X seconds
  - turn screen off, lock and suspend after X seconds
  When I go to the second mode, it is only temporary and returns to the first mode after X minutes of non-utilisation

## Inactivity
  [DOES NOT WORK] I want my computer to lock my session and go to sleep mode after X minutes of inactivity. I currently do it through xautolock as I use Xorg.

## Monitors power managment
  Use DPMS, currently through Xorg
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

# Disks

## Wireless networks
  Wireless networks power management do not depend on battery level or charging state.

  # WIFI
  When powering on or resuming from suspend or hibernate, I want WIFI to be activated.
  When no WIFI are available for X minutes, I want WIFI to be turned off.

  # Bluetooth
  When powering on or resuming from suspend or hibernate, I want Bluetooth to be turned off by default.
  Bluetooth should be activated manually only.
  When no bluetooth device is connected for more than X minutes, I want Bluetooth to be deactivated.
  

