# SSH

## OpenSSH

### SSH Client Configuration

To understand OpenSSH ssh client configuration files, check ```man ssh_config```

The following files are my ssh client configuration files :

-  **~/.ssh/config** points to ~/.config/ssh/config, so that when OpenSSH will support 'XDG Base Directory Specification', I will only have to delete it.
- **~/.config/ssh/config** references public, private and temp configuration files.
- **~/.config/ssh/public** is referenced by ~/.config/ssh/config and contains the configuration I am comfortable sharing on the Internet.
- **~/.config/ssh/private** is referenced by ~/.config/ssh/config and contains the configuration that should remain private.
- **~/.config/ssh/temp** is referenced by ~/.config/ssh/config and contains the configuration that I am currently working on or that aren't sorted yet, it is not published on the internet.
- **~/.config/ssh/<project_name>** is referenced by ~/.config/ssh/private and contains the configuration that is bound to a project or organisation.

[TODO] Almost all those files have shell aliases to edit them. 

### SSH Server Configuration
