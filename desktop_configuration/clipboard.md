# Clipboard configuration

## What I want
Selected text goes to PRIMARY
Copied text go to CLIPBOARD

Shortcuts
  ### Terminal
  copy  to   CLIPBOARD           --> Ctrl + Shift + C
  paste from CLIPBOARD           --> Ctrl + Shift + V
  paste from PRIMARY             --> Alt + V # Not configured
                                
  ### Desktop                   
  copy  to   CLIPBOARD           --> Ctrl + C
  paste from CLIPBOARD           --> Ctrl + V
  paste from PRIMARY             --> Alt + V # Not configured (interaction problems)
  erase PRIMARY and CLIPBOARD    --> ?
  copy PRIMARY to CLIPBOARD      --> windows+`(grave)

## Terminal
### Bash
See readline in softwares

### ZSH
See ZLE

## Xorg
### Using xsel
erase PRIMARY # I don't think we can erase PRIMARY, because it is fetched from another window
erase CLIPBOARD
```
xsel -b -c
xsel --clipboard --clear
```
copy PRIMARY to CLIPBOARD
```
xsel -p | xsel -b
xsel --primary | xsel --clipboard
```
paste from PRIMARY
```
bash -c "xdotool type $(xsel)" # Is caught by the WM shortcuts
bash -c "xsel | xvkbd -xsendevent -file -" # Requires a package which is not an official Arch package
bash -c "xdotool click 2" # Requires the cursor in the text field
```
