# Uxterm configuration
Configuration file: `.config/xorg/xresources`

# Enable TrueType font
  renderFont: true

Increase saved lines: `UXTerm*saveLines: 4096`

## Configure shortcuts
```
!! Xterm Shortcuts
!!! Those are set below
!!! Ctrl + Shift + C          : copy to CLIPBOARD
!!! Ctrl + Shift + V          : to paste from CLIPBOARD
!!! Ctrl + - (Number row)     : Decrease font size
!!! Ctrl + = (Number row)     : Increase font size
!!! Ctrl + 0 (Number row)     : Restore configured font size (see man 1 xterm, "set-vt-font", 's' argument)
!!! Ctrl + - (Keypad) : Decrease font size
!!! Ctrl + + (Keypad) : Increase font size

xterm.vt100.translations: #override \n\
  Ctrl Shift <Key>C: copy-selection(CLIPBOARD) \n\
  Ctrl Shift <Key>V: insert-selection(CLIPBOARD) \n\
  Ctrl <KeyPress> +:larger-vt-font() \n\
  Ctrl <KeyPress> -:smaller-vt-font() \n\
  Ctrl <KeyPress> 0: set-vt-font(s) \n\
  Ctrl <KeyPress> KP_Add:larger-vt-font() \n\
  Ctrl <KeyPress> KP_Subtract:smaller-vt-font()
```


## Change fonts
```
!! Set font
UXTerm*renderFont: true
UXTerm*faceName: VeraMono
UXTerm*faceSize: 10
UXTerm*boldMode: false
UXTerm*boldFont: false
```

## Configure Scrollbar

Enable right scrollbar with size 10
```
!! Scrollbar
! Enable Xterm scrollbar
UXTerm.vt100.scrollBar: true

! Set right scrollbar
UXTerm.vt100.rightScrollBar: true

! Set Xterm scrollbar width
UXTerm.vt100.scrollbar.width: 10
```

## Change color config
```
! Color config
!! Black Theme
*background: rgb:11/11/11
*foreground: rgb:ff/ff/ff

!! Light Theme
! *background: rgb:ff/ff/ff
! *foreground: rgb:00/00/00

!!Theme Seven
*color0:     rgb:00/00/00 # Black
*color1:     rgb:bf/46/46
*color2:     rgb:67/b2/5f
*color3:     rgb:cf/c4/4e
*color4:     rgb:51/60/83
*color5:     rgb:ca/6e/ff
*color6:     rgb:92/b2/f8
*color7:     rgb:d5/d5/d5
*color8:     rgb:00/00/00 # Dark Grey
*color9:     rgb:f4/8a/8a
*color10:    rgb:a5/d7/9f
*color11:    rgb:e1/da/84
*color12:    rgb:a2/bb/ff
*color13:    rgb:e2/b0/ff
*color14:    rgb:ba/cd/f8
*color15:    rgb:d5/d5/d5
```

## Other
```
! Remove trailing spaces
xterm*trimSelection: true

! Select paragraph on 4 clicks
xterm.vt100.on4Clicks: group
```
