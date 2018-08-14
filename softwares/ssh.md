# SSH

## OpenSSH

### SSH Client Configuration

To understand OpenSSH ssh client configuration files, check ```man ssh_config```

The following files are my ssh client configuration files :

-  **~/.ssh/config** points to ~/.config/ssh/config, so that when OpenSSH will support 'XDG Base Directory Specification', I will only have to delete it.
- **~/.config/ssh/config**
- **~/.config/ssh/public** is referenced by ~/.config/ssh/config and contains the configuration I am comfortable sharing on the Internet.
- **~/.config/ssh/private** is referenced by ~/.config/ssh/config and contains the configuration that should remain private.
- **~/.config/ssh/<project_name>** is referenced by ~/.config/ssh/private and contains the configuration that is bound to a project or organisation.


### SSH Server Configuration
