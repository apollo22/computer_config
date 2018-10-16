# GnuPG Configuration

## Set gnupg config folder location

Include the following in your bashrc
```
# GnuPG config files location
export GNUPGHOME=$XDG_CONFIG_HOME/gnupg/
```

Move the default GnuPG default configuration folder to the given folder
```
& mv ~/.gnupg ~/.config/gnupg/
```
