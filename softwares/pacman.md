# Pacman

I use the following options in `/etc/pacman.conf`

```
Color           # To show colored output
TotalDownload   # To show total download information.
CheckSpace
VerbosePkgLists # To show detailled information about packages
```


When I am not on a metered connection, I want to
  - update database and download (not install) updates every hour (I currently do it with a systemd timer)

When I am low on disk space, I want to remove packages that are not installed from the cache
`pacman -Sc`
