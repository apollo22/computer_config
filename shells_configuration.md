# Shells configuration

## Configuration files

~/.bash_profile, ~/.bash_login, and ~/.profile

Shells specific files remains in the location where they are defined, however, they try to load common files, namely:
  - **~/.config/shells/shellsrc** loaded from ~/.bashrc or ~/.zshrc

For common aliases, **shellsrc** loads the file **~/.config/shells/shells_aliases**.

## Aliases

Aliases are defined in many files, depending on the shell used :
  - **~/.config/shells/shells_aliases** for aliases used by all shells, responsible for loading all the documents_aliases.
  - **~/.config/shells/<shell_name>_aliases** for aliases used by a specific shell, loaded by related ~/.config/shells/<shell_name>rc.
  - **~/.config/shells/documents_aliases/public** for aliases used to navigate to directories and edit files I share with everyone on Internet.
  - **~/.config/shells/documents_aliases/private** for aliases used to navigate to directories and edit files that are privates.
  - **~/.config/shells/documents_aliases/<project_name>** for aliases used to navigate to directories and edit files that are bound to projects.
  
## Prompt

## Shortcuts
Managed by terminal ?

## Functions

## Other
https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
