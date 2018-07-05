## Keyboards
  ### Shortcut to change keyboard layout
  You need to execute the following at startup / login. To do that, add the following in /etc/profile. If you are using zsh, make sure /etc/zsh/sprofile enables compatibility mode.
  
  ```setxkbmap "fr,us" -option grp:alt_shift_toggle```
## Mices
## Touchpads
  Driver choice: libinput or mtrack
    - libinput: Wayland and Xorg, easier, less options
    - mtrack: Xorg only, more options
    
When a line is crossed, it means I don't think it is possible to implement the desired operation with this driver.


| Mouvement             | Desired Actions       | libinput | mtrack |
| ---                   | ---                   | ---      | ---    |
| 1 finger  touch        | left click            |   [ ]    |  [ ]   |
| 2 fingers touch        | right click           |   [ ]    |  [ ]   |
| 3 fingers touch        | middle click          |   [ ]    |  [ ]   |
| 4 fingers touch        | ?                     |   [ ]    |  [ ]   |
| 1 finger  click        | not used              |   [ ]    |  [ ]   |
| 2 fingers click        | not used              |   [ ]    |  [ ]   |
| 3 fingers click        | not used              |   [ ]    |  [ ]   |
| 4 fingers click        | not used              |   [ ]    |  [ ]   |
| Swiping               |                       |   [ ]    |  [ ]   |
| 2 fingers swipe up     | move page up          |   [ ]    |  [ ]   |
| 2 fingers swipe down   | move page down        |   [ ]    |  [ ]   |
| 2 fingers swipe left   | move page right       |   [ ]    |  [ ]   |
| 2 fingers swipe right  | move page left        |   [ ]    |  [ ]   |
| 3 fingers swipe up     | go to up    window    |   [ ]    |  [ ]   |
| 3 fingers swipe down   | go to down  window    |   [ ]    |  [ ]   |
| 3 fingers swipe left   | go to left  window    |   [ ]    |  [ ]   |
| 3 fingers swipe right  | go to right window    |   [ ]    |  [ ]   |
| 4 fingers swipe up     |                       |   [ ]    |  [ ]   |
| 4 fingers swipe down   |                       |   [ ]    |  [ ]   |
| 4 fingers swipe left   | go to left  workspace |   [ ]    |  [ ]   |
| 4 fingers swipe right  | go to right workspace |   [ ]    |  [ ]   |
| Zooming               |                       |   [ ]    |  [ ]   |
| 2 fingers zoom-in      |                       |   [ ]    |  [ ]   |
| 2 fingers zoom-out     |                       |   [ ]    |  [ ]   |
| 3 fingers zoom-in      |                       |   [ ]    |  [ ]   |
| 3 fingers zoom-out     |                       |   [ ]    |  [ ]   |
| 4 fingers zoom-in      |                       |   [ ]    |  [ ]   |
| 4 fingers zoom-out     |                       |   [ ]    |  [ ]   |
| Rotation              |                       |   [ ]    |  [ ]   |
| 2 fingers rotate left  |                       |   [ ]    |  [ ]   |
| 2 fingers rotate right |                       |   [ ]    |  [ ]   |
| 3 fingers rotate left  |                       |   [ ]    |  [ ]   |
| 3 fingers rotate right |                       |   [ ]    |  [ ]   |
| 4 fingers rotate left  |                       |   [ ]    |  [ ]   |
| 4 fingers rotate right |                       |   [ ]    |  [ ]   |


## Microphones
## Webcams
## Gamepad
## HOTAS
## Graphics Tablet
