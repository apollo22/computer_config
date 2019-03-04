# RSS usage

Application: newsboat

I download my feeds in the background, to get the implementation, see the <application> page.

## Workspace

I use a dedicated workspace to see my RSS feeds. This is implemented with  a .desktop file in ~/.local/share/applications

```
[Desktop Entry]
Version=1.0
Type=Application

Encoding=UTF-8
Name=RSS

Terminal=false
Exec=/usr/local/bin/rss
```

This uses the following script

```
#! /bin/bash

# Set variables
BROWSER_FOR_NEWSREADER=/usr/bin/firefox
NEWSREADER=/usr/bin/newsboat
TERMINAL=/usr/bin/uxterm
WORKSPACE_NAME="rss"

# If workspace already exists, move to it and do nothing
for WORKSPACE in $(lsws); do
  if [[ $WORKSPACE =~ $WORKSPACE_NAME ]]; then
    i3-msg workspace $WORKSPACE_NAME
    # TODO: Focus on BROWSER, the on NEWSREADER
    exit -1
  fi
done

# Open newsreader in workspace $WORKSPACE_NAME
i3-msg "workspace $WORKSPACE_NAME; exec nohup $TERMINAL $NEWSREADER > /dev/null &"

# Open browser in workspace $WORKSPACE_NAME
i3-msg "workspace $WORKSPACE_NAME; exec nohup $BROWSER_FOR_NEWSREADER > /dev/null &"
```

Then I just use my application launcher.

As you can see, this is tightly coupled with my current windows manager (i3).
