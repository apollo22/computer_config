# Vim utilisation

## XDG BASE DIRECTORY specification

## Plugins
  https://github.com/suan/vim-instant-markdown
  Firefox modification: **about:config** --> set **dom.allow_scripts_to_close_windows** to **true**

### VUNDLE
I use vundle to manage my plugins
To make Vundel compliant with XDG_BASE_DIRECTORY, add the following:
```
" ---- Begin Vundle ----

  " Delete any path in runtimepath (because of Vundle bad management)
  set runtimepath=""

  " Vundle Plugin Manager
[...]

  " set the runtime path to include Vundle and initialize
  set rtp+=$XDG_CONFIG_HOME/vim/bundle/Vundle.vim
  " call vundle#begin() " Keep Plugin commands between vundle#begin/end.
  " alternatively, pass a path where Vundle should install plugins
  call vundle#begin('$XDG_CONFIG_HOME/vim/bundle')
[...]

" Correct Vundle misuse of rtp
  let $temp_runtimepath=&runtimepath
  set runtimepath=$XDG_CONFIG_HOME/vim,$XDG_CONFIG_HOME/vim/after,$VIM,$VIMRUNTIME
  set runtimepath+=$temp_runtimepath

" ---- End Vundle ----
```

## Spell Checking
If using XDG BASE DIRECTORY, do not forget to create the $XDG_CONFIG_HOME/vim/spell directory:
``` mkdir -p $XDG_BASE_DIRECTORY/vim/spell ```

## Features
  indent columns
  improved status line

## Configuration
I don't want comments to be inserted automatically by default


## Other

https://tlvince.com/vim-respect-xdg

Remap hjkl to jkl;

# Set terminal title to currently opened file


## Related scripts
I have a script that check if I can write to the file, if not, it executes with sudo.
