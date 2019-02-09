# Network usage

## NetworkManager profiles

I use NetworkManager profiles extensively, using some of the following:
  * wired-dhcp
  * wired-static
  * wired-dhcp-no-dns
  * wired-single-host
  * wired-single-host-masquerading

## Systemd service based on metered connection

To prevent systemd timers from executing on a metered connection, I use the following, that I develloped myself :https://github.com/jdorel/systemd-metered-connection-dependency

