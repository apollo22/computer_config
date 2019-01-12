# Firefox Configuration

## Synchronisation using Firefox Sync

## Translation services
Use of keyword in bookmarks

http://www.wordreference.com/tools/Firefox-search-shortcut.aspx

## Prevent firefox from going fullscreen when fullscreen from i3

URL: about:config, set browser.fullscreen.autohide to false

## Bookmarks toolbar in fullscreen

- Open your Firefox profile folder, which is **~/.mozilla/firefox/<hash>.<profile_name>** on Linux. If you can’t find it, you can open **about:support** as an URL in your Firefox. and click the “Open Directory” button in the “Profile Directory” field.
- Create a folder named **chrome** if it doesn’t exist yet.
- Create a file called **userChrome.css** in the chrome folder, copy the following content into it and save.

```
@namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul"); /* only needed once */

/* full screen toolbars */
#navigator-toolbox[inFullscreen] toolbar:not([collapsed="true"]) {
   visibility:visible!important;
}
```
- Restart your Firefox

Source: https://shinglyu.github.io/web/2016/06/20/firefox_bookmark_toolbar_in_fullscreen.html

## Disable Ctrl+Q in firefox
https://github.com/sasawat/firefox-ctrl-q-workaround/blob/master/noctrlq.sh

## Plugins

### Installed plugins
- Dark Background and Light Text
- Firefox Multi-Account Containers
- OneTab
- Reddit Enhancement Suite
- Wikiwand: Wikipedia Modernized
- Iridium for Youtube
- uBlock Origin
- Ghostery – Privacy Ad Blocker
- NoMiner - Block Coin Miners
- Saka Key

### Firefox Multi-Account Containers
#### Music Container
Used to play music
- Red
- Glasses icon
##### Websites Lists
- music.youtube.com

### Wikiwand
Wikiwand is a frontend for Wikipedia.

I use English, French and Spanish as prefered languages

### Dynamic Zoom

Useful when often resizing a window

### SakaKey
SakaKey allows me to navigate Firefox without a mouse. Full documentation should be in sakakey.md file (eventually).

## Shortcuts (modified)
### Move in page
Up    - l
Down  - k
Left  - Shift + j
Right - Shift + ;

### Fast move
Up    - Shift + l
Down  - Shift + k

### Move tab in tab bar
Left  - Ctrl + j
Right - Ctrl + ; 

### Change tab
Left  - j
Right - ; 

### Navigate history
Previous - Alt + j
Next     - Alt + ;

### Pass keys - allow application shortcuts
Pass one key      - .
Pass all keys     - Ctrl + .
Stop passing keys - Ctrl + .

## Change WM_CLASS
  * Create a new profile (this allows you to have multiple running instances of firefox)
```
firefox -P <anything> # Launches the profile manager
```
  * Launch firefox with a new WM_CLASS
```
firefox -P <profile-name> --class="<class-name>"
```

## Other
