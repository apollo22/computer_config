# Shells configuration

## Configuration files

Shells specific files remains in the location where they are defined, however, they try to load common files, namely:
  - **~/.config/shells/shellsrc** loaded from ~/.config/shells/bashrc or ~/.zshrc.

For common aliases, **shellsrc** loads the file **~/.config/shells/aliases/shells**.

### Bash specific configuration files

- **Login shells**
  - When started, executes **/etc/profile**, then executes one of the following files (searched in the given order) **~/.bash_profile**, **~/.bash_login** or **~/.profile**. **__I__** also source **~/.bashrc** in **~/.bash_profile**.
  - When an interactive login shell exits, or a non-interactive login shell executes the `exit` builtin command, executes**~/.bash_logout**, if it exists.
- **Interactive non login shells**
  - When started, executes **~/.bashrc**.
- **Non interactive non login shells**
  - When started, expands and executes the expanded file in $ENV.
  
I also use other bash specific configuration files in **~/.config/shells/bash** that I source from **~/.bashrc**

#### Sources

- http://www.gnu.org/software/bash/manual/html_node/Bash-Startup-Files.html
- https://mywiki.wooledge.org/DotFiles
- http://www.linuxfromscratch.org/blfs/view/6.3/postlfs/profile.html

### Zsh specific configuration files

## Aliases

Aliases are defined in many files in the **~/.config/shells/aliases** folder :
  - **shells** for aliases used by all shells, loaded by ~/.config/shells/shellsrc and responsible for loading all the _docs aliases.
  - **<shell_name>** for aliases used by a specific shell, loaded by related <shell_name>rc.
  - **public_docs** for files I share with everyone on Internet.
  - **private_docs** for files that are privates.
  - **professional_docs** for professional files (related to specific organisations)
  - **temp_docs** for aliases used to navigate to directories and edit files that I am currently working on and that I have not sorted yet.
  - **<project_name>_docs** for aliases used to navigate to directories and edit files that are bound to projects.
  
The **_docs** files use the $DOCS_EDITOR environment variable, set in **shells**.

I use **global aliases** and **suffix aliases** in shells that support it.

## Prompt

left prompt
right prompt

### Zsh prompt

http://www.nparikh.org/unix/prompt.php

**Simple prompt**: 
- PROMPT=$'\e[0;32m%n\e[0;30m@\e[0;34m%m: \e[1;31m%~ \e[0;30m%# '
- RPROMPT='%t'

## Shortcuts
Managed by terminal ?

## Functions

## Other
https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html

If first login of the day, display news, else, do not display anything

## Shell features
path expansion
path replacement
auto-completion
spelling correction
suffix aliases
syntax highlighting (valid / invalid command)

?
extended globbing
environment variable editing
programmable file renaming
history substring search (same as Ctrl + R ?)

## Open GUI applications in the background (i.e. detached from the terminal

Define the 'background' alias to
```
alias background="setsid &> /dev/null"
```
Then define an alias for the given applications
```
alias vlc="background vlc"
alias firefox="background firefox"
```

## Open files with the correct application
I currently define suffix aliases with ZSH. I might change to use `xdg-open`

## Shell syntax comparison
http://hyperpolyglot.org/unix-shells

## SECURITY
enable bracketed paste mode
  https://cirw.in/blog/bracketed-paste
