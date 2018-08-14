# Shells configuration

## Configuration files


Shells specific files remains in the location where they are defined, however, they try to load common files, namely:
  - **~/.config/shells/shellsrc** loaded from ~/.bashrc or ~/.zshrc

For common aliases, **shellsrc** loads the file **~/.config/shells/aliases/shells**.

### Bash specific configuration files

http://www.gnu.org/software/bash/manual/html_node/Bash-Startup-Files.html

~/.bash_profile, ~/.bash_login, and ~/.profile

### Zsh specifics configuration files

## Aliases

Aliases are defined in many files in the ~/.config/shells/aliases/ folder :
  - **shells** for aliases used by all shells, loaded by ~/.config/shells/shellsrc and responsible for loading all the documents_aliases.
  - **<shell_name>** for aliases used by a specific shell, loaded by related ~/.config/shells/<shell_name>rc.
  - **public_docs** for aliases used to navigate to directories and edit files I share with everyone on Internet.
  - **private_docs** for aliases used to navigate to directories and edit files that are privates.
  - **temp_docs** for aliases used to navigate to directories and edit files that I am currently working on and that I have not sorted yet.
  - **<project_name>_docs** for aliases used to navigate to directories and edit files that are bound to projects.
  
## Prompt

## Shortcuts
Managed by terminal ?

## Functions

## Other
https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
