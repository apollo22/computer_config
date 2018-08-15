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

## Plugins

### Installed plugins
- Dark Background and Light Text
- Firefox Multi-Account Containers
- OneTab
- Reddit Enhancement Suite
- Wikiwand: Wikipedia Modernized
- YouTube High Definition
- uBlock Origin
- Ghostery – Privacy Ad Blocker
- NoMiner - Block Coin Miners

### Firefox Multi-Account Containers
#### Music Container
Used to play music
- Red
- Glasses icon
##### Websites Lists
- music.youtube.com
