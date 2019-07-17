# This project will set your Mac OS Slack theme to dark/night mode

# 4.0.0 Instructions
You will have to essentially change the structure of slack to imbed a new file that they removed.
After 4.0.0 is installed, close slack and follow these commands:
```
npm install -g asar
mkdir -p ~/tmp/slack
cp /Applications/Slack.app/Contents/Resources/app.asar ~/tmp/slack
cp -r /Applications/Slack.app/Contents/Resources/app.asar.unpacked ~/tmp/slack
cd ~/tmp/slack
asar extract app.asar app
vim app/dist/ssb-interop.bundle.js
```
Once the file is open, hit the 'end' key and then the 'i' key. Enter this:
```
document.addEventListener('DOMContentLoaded', function() {    
  fetch('https://cdn.rawgit.com/laCour/slack-night-mode/master/css/raw/black.css')    
  .then(function(response) {
    return response.text();
  })
  .then(function(css) {
    const style = document.createElement('style'); 
    style.innerHTML = css;
    document.head.appendChild(style);
  });
});
```
Once you have added that, hit 'esc' then type ':wq' to save the changes.
Then follow these instructions:
```
asar pack app app.asar
sudo cp app.asar /Applications/Slack.app/Contents/Resources
open /Applications/Slack.app
```
# Previous to 4.0.0

To start, always make sure your file is clean and not modified.
Paste this into your command prompt:
```
osascript -e 'quit app "slack"';curl 'https://raw.githubusercontent.com/valiander/slackdark/master/reset' > /Applications/Slack.app/Contents/Resources/app.asar.unpacked/src/static/ssb-interop.js
```
This command will quit slack and overwrite the file needed to change your css entries.
>This will also return your slack app back to normal, aside from the theme changes.

To set the dark theme, paste this into your command prompt:
```
osascript -e 'quit app "slack"';curl 'https://raw.githubusercontent.com/valiander/slackdark/master/darktheme' >> /Applications/Slack.app/Contents/Resources/app.asar.unpacked/src/static/ssb-interop.js
```
This is going to quit slack and append the changes to the end of the file. 
>Its important to quit and restart slack every time we change this file so that the changes take effect.


Last step is to paste this into a chat with yourself or slackbot, and click "switch sidebar theme"
```
#3b383b,#b8cbe6,#ffffff,#ffffff,#4A5664,#ffffff,#00f7ff,#3b383b
```

>If you see the following error while trying to run this, delete slack and reinstall.
```
-bash: /Applications/Slack.app/Contents/Resources/app.asar.unpacked/src/static/ssb-interop.js: Permission denied
```




Let me know if there are any issues that you have!
