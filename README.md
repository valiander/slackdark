# This project will set your Mac OS Slack theme to dark/night mode

To start, always make sure your file is clean and not modified.
Paste this into your command prompt:
```
osascript -e 'quit app "slack"';curl 'https://raw.githubusercontent.com/valiander/slackdark/master/undo' > /Applications/Slack.app/Contents/Resources/app.asar.unpacked/src/static/ssb-interop.js
```
This command will quit slack and overwrite the file needed to change your css entries.
>This will also return your slack app back to normal, aside from the theme changes.

To set the dark theme, paste this into your command prompt:
```
osascript -e 'quit app "slack"';curl 'https://raw.githubusercontent.com/valiander/slackdark/master/darktheme' >> /Applications/Slack.app/Contents/Resources/app.asar.unpacked/src/static/ssb-interop.js
```
This is going to quit slack and append the changes to the end of the file. 
>Its important to quit and restart slack every time we change this file so that the changes take effect.

Let me know if there are any issues that you have!
