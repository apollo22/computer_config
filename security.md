# Security

## Network Security
  ### DNS
  - DNSSEC
  - Encrypted DNS
    - dnscrypt

## Cold boot attack
- RAM Encryption

## SSH Keys usage
I set up one keypair per service and per machine.
For exemple, if I have two computer and I want to access two services, I have 4 keypairs: host1-service1, host1-service2 ,host2-service1 and host2-service2.

## Other
- /boot on USB Drives
- Full Disk Encryption / Full Volume Encryption
  - Against resetting root password
- Secure Boot
- Trusted Computing / Trusted Plateform Module
- Computrace
- Intel ME

Do not mount unknown devices

## User access to some services / applications / devices
```
# sudo
group wheel

# Wireshark
group wireshark

# serial ports
group uucp

# docker
group docker
/!\ Equivalent to giving root access

# sigrok
group usbtmc
```

