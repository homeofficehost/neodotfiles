
<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Forget About Manual Configuration!](#forget-about-manual-configuration)
- [Watch me run!](#watch-me-run)
- [Installation](#installation)
  - [Restoring Dotfiles](#restoring-dotfiles)
- [3.x.x+ Upgrade Instructions!](#3xx-upgrade-instructions)
- [Additional](#additional)
  - [VIM as IDE](#vim-as-ide)
  - [Crontab](#crontab)
  - [Remap Caps-Lock](#remap-caps-lock)
- [Settings](#settings)
  - [SSD-specific tweaks](#ssd-specific-tweaks)
  - [General System Changes](#general-system-changes)
  - [Security](#security)
  - [Trackpad, mouse, keyboard, Bluetooth accessories, and input](#trackpad-mouse-keyboard-bluetooth-accessories-and-input)
  - [Configuring the Screen](#configuring-the-screen)
  - [Finder Configs](#finder-configs)
  - [Dock & Dashboard](#dock--dashboard)
  - [Configuring Hot Corners](#configuring-hot-corners)
  - [Configuring Safari & WebKit](#configuring-safari--webkit)
  - [Configuring Mail](#configuring-mail)
  - [Spotlight](#spotlight)
  - [iTerm2](#iterm2)
  - [Time Machine](#time-machine)
  - [Activity Monitor](#activity-monitor)
  - [Address Book, Dashboard, iCal, TextEdit, and Disk Utility](#address-book-dashboard-ical-textedit-and-disk-utility)
  - [Mac App Store](#mac-app-store)
  - [Messages](#messages)
  - [Spectacle.app](#spectacle)
- [Software Installation](#software-installation)
  - [Utilities](#utilities)
  - [Apps](#apps)
  - [NPM Global Modules](#npm-global-modules)
  - [Ruby Gems](#ruby-gems)
- [License](#license)
- [Contributions](#contributions)
- [Loathing, Mehs and Praise](#loathing-mehs-and-praise)
- [¯\\_(ツ)_/¯ Warning / Liability](#%C2%AF%5C%5C_%E3%83%84_%C2%AF-warning--liability)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

This started as MacOS shell configuration dotfiles but has grown to a multi-developer platform for machine configuration.

# \\[._.]/ - Watch me running

[![asciicast](https://asciinema.org/a/Sl5Qsv1EGHaJR6hcUR1No3OiD.png)](https://asciinema.org/a/Sl5Qsv1EGHaJR6hcUR1No3OiD)

![iTerm Screenshot](https://raw.githubusercontent.com/homeofficehost/dotfiles/master/img/term.png)

launch fullscreen hit `Command + Enter`
iTerm, then use `Command + d` and `Command + D` to create split panes.


# 3.x.x+ Upgrade Instructions!

`3.0.0` brings huge changes. If you have made any modifications (and didn't make your own fork), you will want to backup your dotfiles prior to running `git-up` or `git pull` on `~/.dotfiles`.

Do the following to upgrade your ~/.dotfiles safely:

1. backup your dotfiles: `cp -R ~/.dotfiles ~/.dotfiles_old`
2. `cd ~/.dotfiles`
3. update dotfiles: `git-up` or `git pull`
4. remove old submodule location: `rm -rf .vim` (now lives in `homedir/.vim`)
5. inspect `install.sh` and `config.js` to make sure all the software you want is installed
6. inspect `homedir/*` for any changes you want to port from `./dotfiles_old`
7. run `install.sh` again

# Additional

## VIM as IDE
I am moving away from using `Atom` and instead using `vim` as my IDE. I use Vundle to manage vim plugins (instead of pathogen). Vundle is better in many ways and is compatible with pathogen plugins. Additionally, vundle will manage and install its own plugins so we don't have to use git submodules for all of them.

## Crontab
You can `cron ~/.crontab` if you want to add my nightly cron software updates.

> \\[0_0]/ - Note that this may wake you in the morning to compatibility issues so use only if you like being on the edge

## Remap Caps-Lock
- I highly recommend remapping your Caps Lock key to Control per [Dr. Bunsen](http://www.drbunsen.org/remapping-caps-lock/):
![Remap Caps Lock](https://raw.githubusercontent.com/homeofficehost/dotfiles/master/img/remap_capslock.png)

# Settings
This project changes a number of settings and configures software on MacOS.
Here is the current list:

## Prompt Driven Configuration
The following will only happen if you agree on the prompt
- install a gitshots script to take a photo using your camera on every git commit (these go in as a post-commit hook to your .git_template)
- overwrite your /etc/hosts file with a copy from someonewhocares.org (see ./configs/hosts for the file that will be used)
- replace the system wallpaper with `img/wallpaper.jpg`

## SSD-specific tweaks  
- Disable local Time Machine snapshots
- Disable hibernation (speeds up entering sleep mode)
- Remove the sleep image file to save disk space

## General System Changes
- always boot in verbose mode (not MacOS GUI mode)
- Disable the sound effects on boot
- Menu bar: disable transparency
- Menu bar: hide the Time Machine, Volume, User, and Bluetooth icons
- Set highlight color to green
- Set sidebar icon size to medium
- Always show scrollbars
- Increase window resize speed for Cocoa applications
- Expand save panel by default
- Expand print panel by default
- allow 'locate' command
- Set standby delay to 24 hours (default is 1 hour)
- Save to disk (not to iCloud) by default
- Automatically quit printer app once the print jobs complete
- Disable the “Are you sure you want to open this application?” dialog
- Remove duplicates in the “Open With” menu (also see 'lscleanup' alias)
- Display ASCII control characters using caret notation in standard text views
- Disable automatic termination of inactive apps
- Disable the crash reporter
- Set Help Viewer windows to non-floating mode
- Reveal IP, hostname, OS, etc. when clicking clock in login window
- Restart automatically if the computer freezes
- Never go into computer sleep mode
- Check for software updates daily, not just once per week
- Disable smart quotes as they’re annoying when typing code
- Disable smart dashes as they’re annoying when typing code

## Security
- Enable firewall
- Enable firewall stealth mode (no response to ICMP / ping requests)
- Disable remote apple events
- Disable wake-on modem
- Disable wake-on LAN
- Disable guest account login

## Trackpad, mouse, keyboard, Bluetooth accessories, and input
- Trackpad: enable tap to click for this user and for the login screen
- Trackpad: map bottom right corner to right-click
- Disable “natural” (Lion-style) scrolling
- Increase sound quality for Bluetooth headphones/headsets
- Enable full keyboard access for all controls (e.g. enable Tab in modal dialogs)
- Use scroll gesture with the Ctrl (^) modifier key to zoom
- Follow the keyboard focus while zoomed in
- Disable press-and-hold for keys in favor of key repeat
- Set a blazingly fast keyboard repeat rate:
- Set language and text formats (english/US)
- Disable auto-correct

## Configuring the Screen
- Require password immediately after sleep or screen saver begins
- Save screenshots to the desktop
- Save screenshots in PNG format (other options: BMP, GIF, JPG, PDF, TIFF)
- Disable shadow in screenshots
- Enable subpixel font rendering on non-Apple LCDs
- Enable HiDPI display modes (requires restart)

## Finder Configs
- Keep folders on top when sorting by name (Sierra only)
- Allow quitting via ⌘ + Q; doing so will also hide desktop icons
- Disable window animations and Get Info animations
- Set Desktop as the default location for new Finder windows
- Show hidden files by default
- Show all filename extensions
- Show status bar
- Show path bar
- Allow text selection in Quick Look
- Display full POSIX path as Finder window title
- When performing a search, search the current folder by default
- Disable the warning when changing a file extension
- Enable spring loading for directories
- Remove the spring loading delay for directories
- Avoid creating .DS_Store files on network volumes
- Disable disk image verification
- Automatically open a new Finder window when a volume is mounted
- Use list view in all Finder windows by default
- Disable the warning before emptying the Trash
- Empty Trash securely by default
- Enable AirDrop over Ethernet and on unsupported Macs running Lion
- Show the ~/Library folder
- Expand the following File Info panes: “General”, “Open with”, and “Sharing & Permissions”

## Dock & Dashboard
- Enable highlight hover effect for the grid view of a stack (Dock)
- Set the icon size of Dock items to 36 pixels
- Change minimize/maximize window effect to scale
- Minimize windows into their application’s icon
- Enable spring loading for all Dock items
- Show indicator lights for open applications in the Dock
- Don’t animate opening applications from the Dock
- Speed up Mission Control animations
- Don’t group windows by application in Mission Control
- Disable Dashboard
- Don’t show Dashboard as a Space
- Don’t automatically rearrange Spaces based on most recent use
- Remove the auto-hiding Dock delay
- Remove the animation when hiding/showing the Dock
- Automatically hide and show the Dock
- Make Dock icons of hidden applications translucent
- Make Dock more transparent
- Reset Launchpad, but keep the desktop wallpaper intact

## Configuring Hot Corners
- Top left screen corner → Mission Control
- Top right screen corner → Desktop
- Bottom right screen corner → Start screen saver

## Configuring Safari & WebKit
- Set Safari’s home page to ‘about:blank’ for faster loading
- Prevent Safari from opening ‘safe’ files automatically after downloading
- Allow hitting the Backspace key to go to the previous page in history
- Hide Safari’s bookmarks bar by default
- Hide Safari’s sidebar in Top Sites
- Disable Safari’s thumbnail cache for History and Top Sites
- Enable Safari’s debug menu
- Make Safari’s search banners default to Contains instead of Starts With
- Remove useless icons from Safari’s bookmarks bar
- Enable the Develop menu and the Web Inspector in Safari
- Add a context menu item for showing the Web Inspector in web views

## Configuring Mail
- Disable send and reply animations in Mail.app
- Copy email addresses as 'foo@example.com' instead of 'Foo Bar <foo@example.com>' in Mail.app
- Add the keyboard shortcut ⌘ + Enter to send an email in Mail.app
- Display emails in threaded mode, sorted by date (oldest at the top)
- Disable inline attachments (just show the icons)
- Disable automatic spell checking

## Spotlight
- Disable Spotlight indexing for any volume that gets mounted and has not yet been indexed
- Change indexing order and disable some file types from being indexed
- Load new settings before rebuilding the index
- Make sure indexing is enabled for the main volume

## iTerm2
- Installing the Solarized Dark theme for iTerm
- Don’t display the annoying prompt when quitting iTerm
- Hide tab title bars
- Set system-wide hotkey to show/hide iterm with ctrl+tick ( `^` + `)
- Set normal font to Hack 12pt
- Set non-ascii font to Roboto Mono for Powerline 12pt

## Time Machine
- Prevent Time Machine from prompting to use new hard drives as backup volume
- Disable local Time Machine backups

## Activity Monitor
- Show the main window when launching Activity Monitor
- Visualize CPU usage in the Activity Monitor Dock icon
- Show all processes in Activity Monitor
- Sort Activity Monitor results by CPU usage

## Address Book, Dashboard, iCal, TextEdit, and Disk Utility
- Enable the debug menu in Address Book
- Enable Dashboard dev mode (allows keeping widgets on the desktop)
- Use plain text mode for new TextEdit documents
- Open and save files as UTF-8 in TextEdit
- Enable the debug menu in Disk Utility

## Mac App Store
- Enable the WebKit Developer Tools in the Mac App Store
- Enable Debug Menu in the Mac App Store

## Messages
- Disable automatic emoji substitution (i.e. use plain text smileys)
- Disable smart quotes as it’s annoying for messages that contain code
- Disable continuous spell checking

## Spectacle.app
- Start Spectacle at login
- Don’t show the preferences window on next start

# Software Installation

## Utilities

## Apps

## NPM Global Modules

## Ruby Gems

## Go Packages