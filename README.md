# Day and Night Theme

Hello! This is a tutorial for how to achieve the macOS theme from [this reddit post](https://www.reddit.com/r/unixporn/comments/o7uy6m/rectanglemacos_day_and_night_first_rice/).

## Programs and Dependencies
This is a list of programs that will be needed.

Wallpapers:
* [imgur](https://imgur.com/a/GByFzax)

Terminal:
* [iterm2](https://iterm2.com/)
* [zsh](https://www.zsh.org/)
* [oh-my-zh](https://github.com/ohmyzsh/ohmyzsh) (theme: robbyrussell)


Window manager:
* [Rectangle](https://rectangleapp.com/)

Themes:
* [pywal](https://github.com/dylanaraps/pywal)

   ``Day theme: wal -n -i /path/to/daypicture``

   ``Night theme: wal --theme dkeg-vans``
* [chrome theme](https://chrome.google.com/webstore/detail/totoro-rainy-day/lmiagjknjjfockcklibjlfdojojaffff)

vscode pywal extension:
* [vscode wal theme](https://github.com/dlasagno/vscode-wal-theme)

Apple's docs on launchd:
* [launchd](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/BPSystemStartup/Chapters/CreatingLaunchdJobs.html)

dynamic wallpaper generator:
* [dynamic wallpaper creator](https://apps.apple.com/us/app/dynamic-wallpaper-maker/id1453846328?mt=12) (it syncs with ur location to find dusk and dawn and you could set the pictures for almost every few hours).

# Install
Once you install the stuff above, its relatively easy to set the rest the automation.
I created my dynamic wallpaper by using the Dynamic Wallpaper Creator app from the appstore. I was able to set my wallpaper to change at dusk and dawn (5:53 AM and 6:07 PM). 

Then I utilized pywal commands to switch my themes manually, I eventually wrote the launchd plists to automate this process. Those files are in this repository as ``com.user.daytheme.plist`` and ``com.user.nighttheme.plist``.

Once those files are downloaded, move them to your ``/Library/LaunchDaemons`` (or other depending if you want systemwide or not). Once they are there you can edit the times the commands will execute and other parameters you should fill out.

Then load those files into your launchctl by running

```
launchctl load /Library/LaunchDaemons/com.user.daytheme.plist
launchctl load /Library/LaunchDaemons/com.user.nighttheme.plist
```

Any time you change the launchd files you must reload the files.

```
launchctl unload /Library/LaunchDaemons/com.user.daytheme.plist
launchctl unload /Library/LaunchDaemons/com.user.nighttheme.plist
launchctl load /Library/LaunchDaemons/com.user.daytheme.plist
launchctl load /Library/LaunchDaemons/com.user.nighttheme.plist
```

I use Rectangle to retile my windows manually (sadly too lazy to use yabai at the moment). Here are my key bindings/settings: 
![image](https://user-images.githubusercontent.com/69036619/123527888-1b84e780-d698-11eb-94fd-6f69ad2cb8f0.png)
![image](https://user-images.githubusercontent.com/69036619/123527898-335c6b80-d698-11eb-8260-0dbfce0ec63d.png)


VSCode support is automatically done with the extension linked above.

Then you should be ready to go!

ps: feel free to pm me on reddit any questions!

