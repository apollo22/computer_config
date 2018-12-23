# SSH

## OpenSSH

### SSH Client Configuration

To understand OpenSSH ssh client configuration files, check ```man ssh_config```

The following files are my ssh client configuration files :
```
/etc/ssh/ssh_config: I don't use this file
~/
  .ssh/config doesn't exist (See 'SSH XDG_BASE_DIRECTORY')
  .config/ssh/
    config: references public, private and temp configuration files.
    known_hosts: list of known hosts
    public_hosts_config is referenced by ~/.config/ssh/config and contains the configuration I am comfortable sharing on the Internet.
    private_hosts_config is referenced by ~/.config/ssh/config and contains the configuration that should remain private.
    professionnal_hosts_config is referenced by ~/.config/ssh/config and include configuration in <professionnal-folders>
    temp_hosts_config is referenced by ~/.config/ssh/config and contains the configuration that I am currently working on or that aren't sorted yet, it is not published on the internet.
```

[TODO] Almost all those files have shell aliases to edit them. 

#### Storage of my private ssh-keys

I have to kinds of private keys:
  - machine keys, linked to a particular machines, to be repudiated if the machine is lost or stolen.
    - They may not have a passphrase (for scripts)
    - They are stored unencrypted
    - They are stored in .config/ssh/machine-keys
  - identity keys, linked to an identity and a security level.
    - They have a passphrase
    - They are stored encrypted 
    - They are stored in a private folder
    - There is a symlink from this private folder to .config/ssh/identity-keys

Each machine and identity have several keys to account for different algorithm and key size.


### SSH Server Configuration

To understand OpenSSH ssh server configuration file, check ```man sshd_config```

- **/etc/ssh/sshd_config**

# SSH Configuration

## SSH follows XDG_BASE_DIRECTORY

Several files are used by ssh
  - ~/.ssh/config: You can do it 3 different ways
    - either add `Include ~/.config/ssh/config` in ~/.ssh/config. This is better as this doesn't break other executables using the default ssh command.
    - or add the following in your bashrc (allows you to remove ~/.ssh/config)
    ```
    SSH_CONFIG_FILE=${XDG_CONFIG_HOME}/ssh/config
    if [ -s "$SSH_CONFIG_FILE" ]; then
      alias ssh="ssh -F $SSH_CONFIG_FILE"
    fi
    ```

  - ~/.ssh/id*.pub (Used by ssh-copy-id)
    - Add the following in your bashrc:
    ```
    SSH_ID=${XDG_CONFIG_HOME}/ssh/machine-keys/id-rsa-4096.pub
    if [ -s "$SSH_ID" ]; then
      alias ssh-copy-id="ssh-copy-id -i $SSH_ID"
    fi
    ```
    - Add the following in your ssh config file
    ```
    IdentityFile ~/.config/ssh/<file-path>
    ```
  - ~/.ssh/known_hosts
    - Add `UserKnownHostsFile <your XDG_CONFIG_HOME>/ssh/known_hosts` to your ssh config file
