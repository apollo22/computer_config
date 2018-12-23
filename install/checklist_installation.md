# Installation checklist

## Base installation
  - [ ] Set keyboard layout
  - [ ] Configure disks
    - [ ] (Optional) Configure RAID
    - [ ] Partition the disks
    - [ ] (Optional) Encrypt the partitions
    - [ ] (Optional) Configure LVM
      - [ ] Configure Physical Volumes
      - [ ] Configure Volume Groups
      - [ ] Configure Logical Volumes
    - [ ] Format the partitions
    - [ ] (Optional) Configure Swap
      - [ ] (One) Swap file
      - [ ] (One) Swap partition
  - [ ] Mount the filesystems
  - [ ] Connect to the internet
  - [ ] Update mirrors list
  - [ ] Install base system
    - [ ] Generate fstab file
    - [ ] (Depends) Generate crypttab file (if encrypted devices are present)
  - [ ] Move to base system

## Base boot configuration
  - [ ] Configure root account
    - [ ] Set root password
    - [ ] Set root shell
  - [ ] (Depends) Configure vconsole.conf (if you are using the sd-vconsole hook with mkinitcpio)
  - [ ] (Depends) Generate a new initramfs
    - [ ] (Depends) Add LVM2 hooks
    - Create initrd image
  - Update processors microcode
  - Configure boot sequence
    - [ ] (One) Configure bootloader
      - [ ] (One) GRUB
        - [ ] Install GRUB
        - [ ] (Depends) Confire preloaded modules
          - [ ] RAID
          - [ ] LVM
          - [ ] Encryption
        - [ ] (Depends) Configure kernel parameters
          - [ ] (Depends) LVM
          - [ ] (Depends) LUKS
        - [ ] Generate grub.cfg
        - [ ] Install GRUB to ESP and firmware boot loader
    - [ ] (One) Configure EFIStub
  - Reboot
    - [ ] Exit chroot environment
    - [ ] (Optional) Unmount all partitions
    - [ ] Reboot
  - [ ] (Depends) Configure EFI 

## Base configuration

  - [ ] Set time
  - [ ] Set localization
  - [ ] Configure networks
    - [ ] (?) Set hostname
    - [ ] (Optional) Set DNS
      - [ ] (?) Configure localhost
  - [ ] (Optional) Configure other users account
    - [ ] Set home folder
    - [ ] Set password
    - [ ] (Optional) Set sudo rights

## Advanced configuration
  - [ ] Configure hibernation
    - [ ] Configure bootload
    - [ ] Configure initramfs

