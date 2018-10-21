# Less configuration

## Less shortcuts

To remap shortcuts, I use the lesskey command. As I want my less configuration files in my XDF_CONFIG_HOME folder, I had to change a couple of things:
- set where less reads the default .less location (default ~/.less)
```
In your shell configuration file (default ~/.bashrc), add the following line
export LESSKEY="$XDG_CONFIG_HOME/less/config"
```
- set where lesskey reads its configuration file (default ~/.lesskey) and set where lesskey write its output file (default ~/.less)
```
In your shell configuration file (default ~/.bashrc), add the following line
alias lesskey="lesskey -o $XDF_CONFIG_HOME/less/config" $XDG_CONFIG_HOME/less/lesskey 

```
