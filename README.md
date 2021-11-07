# How to Debuntu?
[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://github.com/themagicalmammal/howtopopbuntu/blob/master/LICENSE)
[![Maintenance](https://img.shields.io/badge/Maintained%3F-yes-blue.svg)](https://github.com/themagicalmammal/howtopopbuntu/graphs/commit-activity)
[![contributions welcome](https://img.shields.io/badge/contributions-welcome-blue.svg?style=flat)](https://github.com/themagicalmammal/howtopopbuntu/pulls)
##### [My Current Setup](https://www.reddit.com/r/linux/comments/k1fuus/making_a_10yearlong_macbook_owner_switch_to_pop_os/).
###### This is done exclusively on Pop OS 20.04 but, has been tested on Ubuntu, most of these tweaks should work for every Ubuntu-based Distros out there.
This is an extensive Guide on the set of things I use.

# Index
## [Installation](#1-installation)
- **[Partitions to create](#partitions-to-create)**
- **[What about Swap?](#what-about-swap)**
- **[What about ZRAM?](#what-about-zram)**
- **[Should I Encrypt?](#q-should-i-encrypt)**
- **[Should I use Btrfs or Ext4 or XFS?](#q-should-i-use-btrfs-or-ext4-or-xfs)**
- **[What about ZFS?](#q-what-about-zfs)**

## [Post Installation](#2-post-installation)
- **[Update your System](#update-your-system)**
- **[Why use apt, not apt-get?](#why-use-apt-not-apt-get)**
- **[Difference b/w upgrade & dist-upgrade](#difference-bw-upgrade-and-dist-upgrade)**
- **[Software Properties Common](#software-properties-common)**
- **[Proprietary Drivers](#proprietary-drivers)**
- **[Gnome Tweaks & the ones I use](#gnome-tweaks--the-ones-i-use) -> [Minimize Button and Button Placement](#1-minimize-button-and-button-placement), [Battery Percentage](#2-battery-percentage), [Optimizing Font](#3-optimizing-font), [Activity Hot Corner](#4-activity-hot-corner-and-format-time)**
- **[Custom Resolution](#custom-resolution-with-xrandr) -> [Resolution goes away](#problem-the-resolution-goes-away-after-a-reboot), [Refresh Rates](#problem-what-about-other-refresh-rates-), [Removing Custom Resolution](#problem-how-to-get-rid-of-custom-resolution), [Hybrid Graphics Bug](#bug-problems-regarding-hybrid-graphics-switching)**
## [Preferred Apps](#3-preferred-apps)
- **[Snap Vs Flatpak](#snap-vs-flatpak-package-managers-except-apt-dpkg)**
- **[Browser](#browser) -> [Chrome](#1-chrome), [Vivaldi](#2-vivaldi), [Brave](#3-brave), [Opera](#4-opera), [Firefox](#1-firefox), [TOR](#2-tor), [Extensions](#extensions)**
- **[Email Client](#email-client)-> [Evolution](#1-evolution), [Thunderbird](#2-thunderbird), [MailSpring](#3-mailspring)**
- **[Video Tools](#video-tools) -> [VLC](#1-vlc), [OBS Studio](#2-obs-studio), [Peek](#3-peek)**
- **[Audio Tools](#audio-tools) -> [PulseAudio Controls](#1-pulseaudio-controls), [PulseEffects](#2-pulseeffects), [Audacity](#3-audacity), [Ardour](#4-ardour)**
- **[Office](#office) -> [Free Office](#1-free-office), [OnlyOffice](#2-onlyoffice), [WPS Office](#3-wps-office)**
- **[Graphic tools](#graphic-tools) -> [GIMP](#1-gimp), [Krita](#2-krita), [Blender](#3-blender), [Inkscape](#4-inkscape)**
- **[Social Apps](#social-apps) -> [Telegram](#1-telegram), [Discord](#2-discord), [Facebook Messenger](#3-facebook-messenger-caprine), [Signal](#4-signal), [Whatsapp](#5-whatsapp-whatsappqt), [Reddit](#6-reddit-giara)**
- **[Programming Apps](#programming-apps) -> [Atom](#1-atom-by-github), [Pycharm](#2-pycharm-ide), [GitHub-Desktop](#3-github-desktop), [Java](#4-java), [Visual Studio](#5-visual-studio)**
- **[Entertainment Apps](#entertainment-apps) -> [Spotify](#1-spotify-for-music), [Steam](#2-steam-for-gaming), [Multimedia Codecs](#3-multimedia-codecs)**
- **[Productivity Apps](#productivity-apps) -> [Kinto](#1-kinto)**
- **[Other Apps](#other-apps) -> [uGet](#1-uget), [Wine](#2-wine-windows-apps), [Lutris](#3-lutris), [Synaptic](#4-synaptic-package-manager), [Nautilus](#5-nautilus-admin-mode), [Timeshift](#6-timeshift), [Resource Monitor](#7-resource-monitor), [Firewall](#8-firewall)**
- **[Debloat](#--debloat)**

## [Important Tweaks](#4-important-tweaks)
- **[Settings](#settings) -> [Privacy Tweaks](#---privacy-tweaks), [Over Amplification](#---over-amplification)**
- **[Disable annoying Keyring](#disable-annoying-keyring)**
- **[Controlling Audio Devices](#controlling-audio-devices)**
## [Optimize Boot-time & Ram Usage](#5-optimize-boot-time--ram-usage)
- **[Disabling Plymouth](#disabling-plymouth)**
- **[Adjusting the Swappiness Property](#adjusting-the-swappiness-property)**
- **[Adjusting the Cache Pressure](#adjusting--the-cache-pressure-setting)**
- **[EarlyOOM](#earlyoom)**
- **[Wayland](#wayland)**
- **[Disabling Extensions](#disabling-unnecessary-extensions)**
- **[Disable Pop Shop on boot](#disabling-pop-shop-on-boot)**
- **[Clearing buff/cache](#clearing-buffcache)**
- **[Optimizing the boot](#optimizing-the-boot)**
- **[Custom Kernel](#custom-kernel)**
- **[Removing Custom Kernel](#getting-rid-of-custom-kernel)**
- **[Final Boot-Time](#final-boot-time)**
## [Miscellaneous](#6-miscellaneous)
- **[Ad-Hosts](#ad-hosts)**
- **[Terminal Mods](#terminal-mods) -> [Neofetch](#1-neofetch-mod), [Shell Config](#2-shell-config), [Bash Alias](#3-bash-alias)**
- **[TLP](#tlp)**
- **[Disable Frequents](#disable-frequents)**
- **[Clean your System](#clean-your-system)**
- **[Night Light](#night-light)**
- **[Tile Windows](#tile-windows)**
- **[Custom Fonts](#custom-fonts)**
- **[Customization](#customization)**
- **[Qt5 theme fix](#to-fix-qt5-applications-like-kolourpaint-to-respect-system-theme-go-here)**
## [Discussion](#discussion)


## 1. Installation
**Only for Advanced Users** <br />
Go through this, because this can be a very helpful step. I am currently using brtfs & find it better. Also, don't remove the Recovery partition to be on the safe side, it helps out a lot.

#### Partitions to Create
- 500 MB for Efi boot (Enough even for multi-boot)
- Recovery (Very Useful, only Pop Os for Ubuntu you need to manually backup) <br />
- Swap partition (First, read [What about Swap?](#what-about-swap))
- (Before selecting read about Brtfs & Zfs) Remaining for Ext4/Brtfs/Zfs System <br />

#### What about Swap?
**If you are on a newer Ubuntu-based system that uses Ubiquity installer it will automatically create a Swap File any time Ext4 is used for root.** <br />
There are two ways of getting swap (You can choose which is better) <br />
- General Method - Creating a swap partition (Linux-swap), Now to do this you need to understand the importance of swap, if you have a low RAM device you need a huger swap like if you have 2GB ram you should get 4 to 6 GB of swap & optimise your swap ratio to a higher value. So, if you have a higher ram you need a lower swap. So, according to my numbers for a ram: swap should be as follows, 2 & lower:6, 4:6, 8:4, 16 & above:2. Also, you have to adjust the swappiness property (given below).<br />

**[BRTFS] - [Snapshots](https://fedoramagazine.org/btrfs-snapshots-backup-incremental/) don't work on Brtfs if we create a swap file in that partition. So Brtfs users should either stick with the general method or create a swap file in a different partition.**
- Swap File - It is a relatively new concept. In this, you create a swap file post-installation. You don't need to dedicate some fixed amount of memory to it as it does on Linux-swap that is why it is also space-efficient. And the best part is you can resize this or remove this whenever you want to.<br />

**Post Installation Steps:** <br />

**Brtfs [Snapshots won't work]** <br />
Go [here](https://askubuntu.com/questions/1206157/can-i-have-a-swapfile-on-btrfs#:~:text=It%20is%20possible%20to%20use,file%20on%20a%20separate%20subvolume.)  <br />

**Ext4** <br />
1. Instruction set for the Swap file
```bash
sudo dd if=/dev/zero of=/swapfile bs=1G count=4 status=progress
```
Count 4 means 4 sets of 1 GB, i.e. 4GB.
2. Change permissions and Make swap
```bash
sudo chmod 600 /swapfile && sudo mkswap /swapfile
```
3. Turn the Swap on
```bash
sudo swapon /swapfile
```
4. Add this line
```nano
/swapfile none swap defaults 0 0
```
to the end of
```nano
sudo nano /etc/fstab
```
5. Reboot  <br />

#### What about ZRAM?
First, you should know what ZRAM is. ZRAM creates a block device in RAM, where pages would otherwise be written to swap before it is compressed, then stored. Allowing for a much faster I/O and, the data compression provides a lot of memory savings. The downside of ZRAM is the usage of CPU for compression but this is usually balanced by the gains from avoiding swap and with overall memory savings of compression.  <br />
This is very useful on my PC with 4GB ram and a 3.4GHz CPU.  <br />
#### Q. How to enable ZRAM?
1. Install zram-config
```nano
sudo apt install zram-config -y 
```
2. To check 
```nano
cat /proc/swaps
```
**Should look like this** <br /> <br />
![zram](https://github.com/themagicalmammal/howtopopbuntu/blob/master/References/zram.png) <br />
3. If it doesn't show up, try **rebooting**.

#### Q. Should I Encrypt?
Encryption adds a layer to the disk, so there's a performance penalty. In day to day operations, you wouldn't notice it though, but there's an argument that older hardware might suffer if they're already in the limit. But it's usually a very useful feature to have, you never know what will happen to your hardware, if it's lost or stolen, you don't want to think about people having access to your stuff as well.

#### Q. Should I use Btrfs or Ext4 or XFS?
**Ans.** It depends, As Btrfs is in its infancy state also Ext4 is a more popular option. But, Btrfs is starting to become a trend since Fedora adopted it & it ships with Fedora 33. Also, I am using this on both of my systems. If you are on HDD then go for Btrfs because it is surprisingly fast on it but, if you are on a SSD you can go for XFS. But, remember if you go for XFS it is not resizable unless you are on a lvm.<br />

To fix installation bugs
```bash
sudo apt install btrfs-progs -y
```

- [Reference on Rising of Btrfs](https://www.linuxjournal.com/content/btrfs-centos-living-loopback)
- [Reference on Btrfs  on HDD](https://www.phoronix.com/scan.php?page=article&item=linux54-hdd-raid&num=1)
- [Reference on XFS on SSD](https://www.phoronix.com/scan.php?page=article&item=linux-58-filesystems&num=4)

#### Q. What about ZFS?
**Ans.** ZFS has been added as an experimental new filesystem on 19.10. If you want to learn more about referring to [this](https://itsfoss.com/zfs-ubuntu/) article. If it meets your requirements you can try it. Lately, it is becoming a trend. As, it is very stable and used by leading companies such as Oracle. You can check out [why people are switching to ZFS](https://rudd-o.com/linux-and-free-software/ways-in-which-zfs-is-better-than-btrfs). <br />

If you want to learn how to, go [here](https://linuxconfig.org/install-ubuntu-20-04-with-zfs).

## 2. Post Installation
There are some basic things you need to do after installation.

### Update your System
*Get the latest updates via terminal or some GUI based updater or Apps stores(like Pop shop).* <br />
Find GUI based updater <br />
![update](https://github.com/themagicalmammal/howtopopbuntu/blob/master/References/update.png) <br />
For Terminal use
```bash
sudo apt update && sudo apt upgrade -y && flatpak update
```
For Forced update
```bash
sudo apt install -f && sudo apt dist-upgrade
```
### Why use apt, not apt-get?
**Ans.** Apt was made according to an end-user perspective. It mostly does everything apt-get does. So for normal users, apt-get is not useful. But, for a developer that writes scripts and does automation, like writing a Docker file to build images, they would prefer apt-get over apt.

### Difference b/w upgrade and dist-upgrade
When you run the apt upgrade, it only updates that which has a new release accessible to the platform, as defined in /etc/apt/sources.list or in /etc/apt/sources.list.d/. <br /> <br />

However, when you run apt dist-upgrade, it will intelligently install or remove packages as needed, to complete the upgrade. Dist-upgrade has an intelligent dispute determination method, so it will attempt to update the numerous necessary packages at the cost of those considered less valuable. But, this might be dangerous because it removes files that might eventually break the system.

### Updating your recovery (Pop Os)
If you upgrade to a newer release the recovery also needs to be upgraded, you can do it via Terminal. <br />
```bash
pop-upgrade recovery upgrade from-release
```

#### Software Properties Common
This is a required library for apps, that use PPA's for installation. It doesn't come pre-installed with many Ubuntu-based distros like Elementary OS.
```bash
sudo apt install software-properties-common -y
```

### Proprietary Drivers
*You can get proprietary drivers directly from the Pop/Ubuntu Shop or Terminal.* <br />
*If you get issues with NVIDIA get the NVIDIA iso.*<br />

### Gnome Tweaks & the ones I use
```bash
sudo apt install gnome-tweaks -y
```

#### 1. Minimize Button and Button Placement
Minimize is an important button. While I think you can live without it if you use the Super key a lot. But, for me, the minimize button seems to be very useful. <br />
You can get the maximize button too, but it's not that useful because it can be done by double-clicking the title bar.<br />
If you were a mac user, you might prefer left button placement over the default right placement. <br />
**Note:** Left Placement glitches the gnome-tweak-tool for some reason don't worry about it just increase the size of the window. <br /> <br />
![gnome-minimise](https://github.com/themagicalmammal/howtopopbuntu/blob/master/References/gnome-minimise.png)<br>
#### 2. Battery Percentage
Shows the amount of battery remaining in percent. Doesn't work for desktop pc.<br> <br />
![batterypercent](https://github.com/themagicalmammal/howtopopbuntu/blob/master/References/batterypercent.png)<br>
#### 3. Optimizing Font
I use custom resolution on my PC's so the font seems small to me, so it makes it better I use 1.11x font. I have set the hinting to full because hinting makes the font appear crisper so that they are more readable. Also, I have set the anti-aliasing to full pixels instead of sub-pixels because it has more font smoothing.<br /> <br />
![custom-font-size](https://github.com/themagicalmammal/howtopopbuntu/blob/master/References/custom-font-size.png) <br />
#### 4. Activity Hot Corner and Format time
The activity hot corner enables the hot corner where the button Activity is placed. So rather than clicking the button just touch the edge. <br />
You can format time according to what you need. I only use the time, so I got rid of the date there. <br /> <br />
![overlay](https://github.com/themagicalmammal/howtopopbuntu/blob/master/References/overlay.png) <br /> <br />

### Custom Resolution with Xrandr
**Please read all the problems & bugs with this, so that you know what problems might come & how to fix them** <br />
If your display supports a higher refresh rate, go for it because higher refresh rate displays make the moving content look and feel smoother and snappier.<br /> <br />
![set-of-refreshrates](https://github.com/themagicalmammal/howtopopbuntu/blob/master/References/set-of-refreshrates.png)

#### Steps:
**1. Check xrandr**  <br />
You can know the name of your display here generally it is eDP-1 if is hybrid it can be eDP-1-1<br /> <br />
```bash
xrandr #Check your display name
```
![xrandr](https://github.com/themagicalmammal/howtopopbuntu/blob/master/References/xrandr.png)
<br /> <br />
**2. Find resolution which will fit**  <br />
My original maximum resolution is 1600 900, which is a 16:9 aspect ratio. So if I choose a different aspect ratio, then some parts of my display will blackout. <br />

So, I can go for 1920x1080 or 1792x1008 <br />
*To find out which fits you best you can do tests by adding different resolutions*
<br /> <br />
**3. How to add?**
##### - cvt
```bash
cvt 1920 1080 #Your custom resolution
```
![cvt](https://github.com/themagicalmammal/howtopopbuntu/blob/master/References/cvt.png)
##### - xrandr --newmode
Copy line after modline
```bash
xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
```
![newmode](https://github.com/themagicalmammal/howtopopbuntu/blob/master/References/newmode.png)
##### - xrandr --addmode
Add the resolution with display name
```bash
xrandr --addmode eDP-1 "1920x1080_60.00"
```
![addmode](https://github.com/themagicalmammal/howtopopbuntu/blob/master/References/addmode.png) <br />

#### [Problem] The resolution goes away after a reboot.
**Ans.** Add all the final lines to .profile so every time a session starts, the code runs, the custom resolution gets added.
```bash
nano ~/.profile
```
![profile](https://github.com/themagicalmammal/howtopopbuntu/blob/master/References/profile.png)

#### [Problem] What about other refresh rates? <br />
**Ans.** You have to experiment with cvt a bit, to find which refresh rates should need. My refresh rate is from 60hz to 120hz. I did some experimentation and added these refresh rates. <br />

Like if your display supports 120 hertz
```bash
cvt 1920 1080 120
```
![custom120](https://github.com/themagicalmammal/howtopopbuntu/blob/master/References/custom120.png)

Finally, I added these resolutions
```bash
xrandr --newmode "1920x1080_120.00"  369.50  1920 2080 2288 2656  1080 1083 1088 1160 -hsync +vsync
xrandr --addmode eDP-1 "1920x1080_120.00"
xrandr --newmode "1920x1080_119.91"  369.25  1920 2080 2288 2656  1080 1083 1088 1160 -hsync +vsync
xrandr --addmode eDP-1 "1920x1080_119.91"
xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
xrandr --addmode eDP-1 "1920x1080_60.00"
xrandr --newmode "1920x1080_59.89"  172.75  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
xrandr --addmode eDP-1 "1920x1080_59.89"
```

**Now it should look like this** <br /> <br />
![custom-resolution-final](https://github.com/themagicalmammal/howtopopbuntu/blob/master/References/custom-resolution-final.png)

#### [Problem] How to get rid of custom resolution?
**Ans.** Simple if you have added custom resolution to your .profile, open it again, remove those lines, and reboot.

#### [BUG] Problems regarding Hybrid Graphics Switching.
**Ans.** If you have a Hybrid or Multiple Graphics Card, your display name will change if you switch graphics. So, you have to change the xrandr --addmode <displayname> if you switch Graphics.

## 3. Preferred Apps
Pop has apps that you need. But, if you do not like them, you can also get alternatives.

### Snap Vs Flatpak (Package Managers except apt, dpkg)
Snap can incorporate more apps than Flatpak. It runs how the developer wants it to. Some even say go as far as to say, "Snap is the future". But, currently, Flatpak outperforms Snap, for the most part, that is why I don't prefer Snap but, still, it's your choice. <br />

**If you are a newbie I won't recommend you remove snap.** <br /> <br />
[Reference to Removing Snap](https://www.kevin-custer.com/blog/disabling-snaps-in-ubuntu-20-04/) <br />
[Reference to Detailed Guide on Flatpak](https://itsfoss.com/flatpak-guide/) <br />

### Browser
Today Chrome is the most popular browser in the world. Also, I have been using Chrome since probably 2012. <br />

**MENTION OPENSOURCE - Chrome is not an open-source browser, Vivaldi & Opera are partly open-source, and also these browsers do not support VAAPI** <br />

**Firefox, Brave & TOR are open-source browsers. Meaning these are better alternatives if you are looking for privacy. But, TOR doesn't support VAAPI. ** <br />

To learn more about **VAAPI** go [here](https://wiki.archlinux.org/index.php/Hardware_video_acceleration).

**Chromium Based Browsers**
#### 1. [Chrome](https://www.google.com/chrome/)
```bash
sudo apt install google-chrome-stable -y
```
#### 2. [Vivaldi](https://vivaldi.com/)
```bash
wget -qO- https://repo.vivaldi.com/archive/linux_signing_key.pub | sudo apt-key add -
sudo add-apt-repository 'deb https://repo.vivaldi.com/archive/deb/ stable main'
sudo apt update && sudo apt install vivaldi-stable -y
```
#### 3. [Brave](https://brave.com/)
```bash
sudo apt install apt-transport-https -y
curl -s https://brave-browser-apt-release.s3.brave.com/brave-core.asc | sudo apt-key --keyring /etc/apt/trusted.gpg.d/brave-browser-release.gpg add -
echo "deb [arch=amd64] https://brave-browser-apt-release.s3.brave.com/ stable main" | sudo tee /etc/apt/sources.list.d/brave-browser-release.list
sudo apt update && sudo apt install brave-browser -y
```
#### 4. [Opera](https://www.opera.com/)
```bash
sudo add-apt-repository 'deb https://deb.opera.com/opera-stable/ stable non-free'
wget -qO - https://deb.opera.com/archive.key | sudo apt-key add -
sudo apt update && sudo apt install opera-stable -y
```
**Non-Chromium Based**
#### 1. [Firefox](https://www.mozilla.org/en-US/firefox/new/)
Comes pre-installed with Pop & Ubuntu.<br />

#### 2. [TOR](https://www.torproject.org/download/)
```bash
sudo apt install torbrowser-launcher -y
```

**In case of driver/library error which bugs on Chromium-based browsers, Non-Chromium-based browsers can help you out.** <br /> <br />
To remove Firefox (Not Recommended)
```bash
sudo apt-get autoremove --purge firefox* -y
```
### Extensions
Generally, these extensions exist for almost all browsers. <br />
#### 1. Privacy Add-ons
- **uBlock Origin** [Chrome](https://chrome.google.com/webstore/detail/ublock-origin/cjpalhdlnbpafiamejdnhcphjbkeiagm?hl=en) [Firefox](https://addons.mozilla.org/en-US/firefox/addon/ublock-origin/) - uBlock Origin is not an "ad blocker", it's a wide-spectrum content blocker with CPU and memory efficiency as a primary feature.
- **HTTPS Everywhere** [Chrome](https://chrome.google.com/webstore/detail/https-everywhere/gcbommkclmclpchllfjekcdonpmejbdp?hl=en) [Firefox](https://addons.mozilla.org/en-US/firefox/addon/https-everywhere/) - HTTPS Everywhere is an extension created by EFF and the Tor Project which automatically switches thousands of sites from insecure "http" to secure "https".
- **ClearURLs** [Chrome](https://chrome.google.com/webstore/detail/clearurls/lckanjgmijmafbedllaakclkaicjfmnk?hl=en) [Firefox](https://addons.mozilla.org/en-US/firefox/addon/clearurls/) - Removes tracking elements from URLs.
- **Decentraleyes** [Chrome](https://chrome.google.com/webstore/detail/decentraleyes/ldpochfccmkkmhdbclfhpagapcfdljkj) [Firefox](https://addons.mozilla.org/en-US/firefox/addon/decentraleyes/) - Protects you against tracking through "free", centralized, content delivery. It prevents a lot of requests from reaching networks like Google Hosted Libraries, and serves local files to keep sites from breaking. Complements regular content blockers.
- **Privacy Badger** [Chrome](https://chrome.google.com/webstore/detail/privacy-badger/pkehgijcmpdhfbdbbnkijodmdjhbjlgp) [Firefox](https://addons.mozilla.org/en-US/firefox/addon/privacy-badger17/) - Privacy Badger automatically learns to block invisible trackers.
- **User-Agent Switcher & Manager** [Chrome](https://chrome.google.com/webstore/detail/user-agent-switcher-and-m/bhchdcejhohfmigjafbampogmaanbfkg?hl=en) [Firefox](https://addons.mozilla.org/en-US/firefox/addon/user-agent-string-switcher/) - Spoof websites trying to gather information about your web navigation to deliver distinct content you may not want
- **CanvasBlocker** [Firefox](https://addons.mozilla.org/en-US/firefox/addon/canvasblocker/) - Alters some JS APIs to prevent fingerprinting. (Chrome Unsupported)
##### Might break some sites! (Ex. GitHub)
- **NoScript** [Chrome](https://chrome.google.com/webstore/detail/noscript/doojmbjmlfjjnbmnoijecmcbfeoakpjm?hl=en) [Firefox](https://addons.mozilla.org/en-US/firefox/addon/noscript/) - Allow potentially malicious web content to run only from sites you trust. Protect yourself against XSS other web security exploits.
#### 2. Useful Tools
- **Absolute Enable** [Chrome](https://chrome.google.com/webstore/detail/absolute-enable-right-cli/jdocbkpgdakpekjlhemmfcncgdjeiika?hl=en) [Firefox](https://addons.mozilla.org/en-US/firefox/addon/absolute-enable-right-click/) - Force Enable Right Click & Copy on disabled websites.
#### 3. Productivity Tools
- **LanguageTool** [Chrome](https://chrome.google.com/webstore/detail/grammar-and-spell-checker/oldceeleldhonbafppcapldpdifcinji?hl=en) [Firefox](https://addons.mozilla.org/en-US/firefox/addon/languagetool/) - Check your texts for spelling and grammar problems everywhere on the web.
#### 4. Desktop specific
- **GNOME Shell integration** [Chrome](https://chrome.google.com/webstore/detail/gnome-shell-integration/gphhapmejobijbbhgpjhcjognlahblep?hl=en) [Firefox](https://addons.mozilla.org/en-US/firefox/addon/gnome-shell-integration/) - This extension provides integration with GNOME Shell and the corresponding extensions repository, make it easy to add extensions via your browser.

### Email Client
Chrome is good enough for me. Pop OS ships with Geary which is a great email client for any user.

**If you want to remove Geary**
```bash
sudo apt-get autoremove --purge geary* -y
```

**Alternatives,**

#### 1. [Evolution](https://help.gnome.org/users/evolution/stable/)
```bash
sudo apt install evolution -y
```
#### 2. [Thunderbird](https://www.thunderbird.net/en-US/)
```bash
sudo apt install thunderbird -y
```
#### 3. [MailSpring](https://getmailspring.com/)
Get the [deb file](https://github.com/Foundry376/Mailspring/releases) and try installing it. <br />
If it throws gvfs dependency error. Follow these **Steps:**
1. Install these libraries
```bash
sudo apt install libsecret-1-dev gconf2 python2 python-is-python2 -y
```
2. Install the deb,
```bash
sudo dpkg --ignore-depends=gvfs-bin -i mailspring*.deb
```

### Video Tools
#### 1. [VLC](https://www.videolan.org/index.html)
VLC is the best video player for any platform
```bash
sudo apt install vlc  -y
```

Get rid of the stock video player
```bash
sudo apt-get autoremove --purge totem* -y
```
#### 2. [OBS Studio](https://obsproject.com/)
OBS Studio is software designed for capturing, compositing, encoding, recording, and streaming video content, efficiently.
```bash
sudo apt install obs-studio -y
```

#### 3. [Peek](https://github.com/phw/peek)
Peek is an recorder with with video recording, GIF recording and screenshot capabilities. <br />
**Pop users don't need to add this repo.**
```bash
sudo add-apt-repository ppa:peek-developers/stable && sudo apt update
sudo apt install peek -y
```

### Audio Tools
#### 1. [PulseAudio Controls](https://www.freedesktop.org/wiki/Software/PulseAudio/)
PulseAudio is an audio server. The audio in your apps passes through Pulse. So in that way, you can use several methods to handle these sounds ere you can hear them. It also optimizes the quality of your audio.
```bash
sudo apt install pavucontrol -y
```
To learn how to control your audio, go [here](controlling-audio-devices).
#### 2. [PulseEffects](https://github.com/wwmm/pulseeffects)
Audio effects for Pulseaudio applications. This helps add specialized effects for each application individually and thus creates multiple profiles for different applications.
```bash
sudo apt install pulseeffects -y
```
**This might add a lot of desktop icons.**<br />
#### 3. [Audacity](https://www.audacityteam.org/)
Audacity is open-source software, easy-to-use, multi-track audio editor, and allows users to record audio and edit music clips.
```bash
flatpak install org.audacityteam.Audacity -y
```
#### 4. [Ardour](https://ardour.org/)
Ardour is a recorder and digital audio workstation app. It's made to be suitable for professional use.
```bash
sudo apt install ardour -y
```

### Office
I directly use Chrome extension for the office, which you can get [here](https://chrome.google.com/webstore/detail/editor-for-docs-sheets-sl/eahibemoondbjaojgcdnmjlnbjmgbbml) <br /> <br />
**If you have not tried LibreOffice, I will recommend you to try it first.** <br />
Alternatives,
#### 1. [Free Office](https://www.freeoffice.com/en/)
Looks like Microsoft Office 2016. <br />
Get the deb file [here](https://www.freeoffice.com/en/download/applications)
#### 2. [OnlyOffice](https://www.onlyoffice.com/)
Looks like Microsoft Office 2013. <br />
Get the deb file [here](https://www.onlyoffice.com/en/download-desktop.aspx)
#### 3. [WPS Office](https://www.wps.com/)
##### If you have a problem with Chinese apps or are privacy concerns skip over this.
This is a beautiful office suite with lots of customization. <br />
Get the deb file [here](https://linux.wps.com/) <br />

#### You can also use web-based offices like Google Drive.
##### To remove LibreOffice
```bash
sudo apt-get autoremove --purge libreoffice* -y
``` 
<br /> <br />

### Graphic tools
#### 1. [GIMP](https://www.gimp.org/)
It is a free and open-source Image Editor. Additionally, you can improve your richness with many customization choices and plugins.
```bash
sudo apt install gimp -y
```
#### 2. [Krita](https://krita.org/en/)
Open-source art software. It is made by professionals that want to see affordable design tools for everyone.
```bash
sudo apt install krita -y
```
#### 3. [Blender](https://www.blender.org/)
Free and open-source, 3D creation suite. It supports the aggregate of the 3D pipeline, including modeling, rigging, animation, simulation, rendering, compositing and motion tracking, even video editing and game creation.
```bash
sudo apt install blender -y
```
#### 4. [Inkscape](https://inkscape.org/)
Free and open-source, vector graphics editor used to create vector images, primarily in Scalable Vector Graphics (SVG) format. Here you can be an illustrator, designer, web designer, or just someone who wants to create vector imagery.
```bash
sudo apt install inkscape -y
```

### Social Apps
#### 1. Telegram
Official Telegram client
```bash
flatpak install org.telegram.desktop -y
```
#### 2. Discord
Official Discord client
```bash
flatpak install com.discordapp.Discord -y
```
##### BetterDiscord
To install themes and customize it's interface according your liking you can install [BetterDiscord](https://betterdiscord.net/home/). To install BetterDiscord, go [here](https://gist.github.com/ObserverOfTime/d7e60eb9aa7fe837545c8cb77cf31172).
#### 3. Facebook Messenger ([Caprine](https://github.com/sindresorhus/caprine))
Unofficial Facebook messenger <br />
Get the installer [here](https://github.com/sindresorhus/caprine/releases)
#### 4. Signal
Official Signal client
```bash
flatpak install org.signal.Signal -y
```
#### 5. Whatsapp ([WhatsappQT](https://gitlab.com/bit3/whatsappqt))
Unofficial Whatsapp client
```bash
flatpak install io.bit3.WhatsAppQT -y
```
#### 6. Reddit ([Giara](https://giara.gabmus.org/#install))
##### Better to use Reddit on your browser.
Unofficial Reddit client. Currently, this its on its Beta stage.
```bash
flatpak install org.gabmus.giara -y
```


### Programming Apps
#### 1. Atom by GitHub
A hackable text editor for devs.
```bash
flatpak install io.atom.Atom -y
```
#### 2. Pycharm IDE
A Python IDE for devs.
```bash
flatpak install pycharm-community -y #use professional if you have a license
```
Important python modules,
```bash
sudo apt install python3-pip python3-dev python3-distutils python3-virenv
pip3 install virtualenv #solves the global package bug
```
**Note:** If you use python 2.x use python instead of python3 and pip instead of pip3.
#### 3. GitHub-Desktop
A seamless way to contribute to projects on GitHub.
```bash
sudo apt install git github-desktop -y
```
If this doesn't work, get the deb [here](https://github.com/shiftkey/desktop/releases).
#### 4. Java
Go through [this](https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-on-ubuntu-18-04) to get the correct version.

#### 5. Visual Studio
Go through [this](https://code.visualstudio.com/docs/setup/linux).

### Entertainment Apps
#### 1. Spotify for Music
**Supports Ad-block and Spicetify-cli**
```bash
curl -sS https://download.spotify.com/debian/pubkey_0D811D58.gpg | sudo apt-key add -
echo "deb http://repository.spotify.com stable non-free" | sudo tee /etc/apt/sources.list.d/spotify.list
sudo apt update && sudo apt install spotify-client -y
```
Features that can be added, <br />
##### 1. Spicetify-Cli & Themes
To install themes for spotify, you can check [this](https://github.com/khanhas/spicetify-cli), to install different themes, go [here](https://github.com/morpheusthewhite/spicetify-themes) out. If you have troubles going through the steps of spicetify-cli. Here is a script you can use.
```bash
curl -fsSL https://raw.githubusercontent.com/themagicalmammal/howtopopbuntu/master/spicetify.sh | bash
```
You need to log-in & out after this. <br />
##### 2. Spotify-Adblock
If you do not like ads, you can install [Ad-free Spotify](https://github.com/abba23/spotify-adblock-linux). To simplify the steps go through this. <br />
**Note:** This might be buggy.
```bash
curl -fsSL https://raw.githubusercontent.com/themagicalmammal/howtopopbuntu/master/spotify_adblock.sh | sudo bash
```
**My Spotify** <br />
![spotify](https://raw.githubusercontent.com/morpheusthewhite/spicetify-themes/master/DribbblishDynamic/color-match-bg.gif) <br /> 

#### 2. Steam for Gaming
```bash
sudo apt install steam -y
```
If it doesn't work, turn on multiverse.
```bash
sudo add-apt-repository multiverse && sudo apt update
```

#### 3. Multimedia Codecs
Gives you the ability to play popular non-free media formats, including DVD, MP3, Quicktime and Windows Media.
```bash
sudo apt install ubuntu-restricted-extras -y
```
To enable restricted codecs to play DVDs
```bash
sudo apt install libdvd-pkg -y
sudo dpkg-reconfigure libdvd-pkg
```

### Productivity Apps
#### 1. [Kinto](https://github.com/rbreaves/kinto)
Key remapper that makes mac user's transition to Linux easier. It provides macOS keyboard shortcuts. So, if you miss your mac shortcut style you can use this.

### Other Apps
#### 1. uGet
uGet is a lightweight yet powerful open Source download manager for Linux. Basic features include a download queue, a clipboard monitor, and the ability to process downloads in a batch format.
```bash
sudo apt install aria2 uget -y
```
#### 2. Wine (Windows Apps)
Wine (originally an acronym for "Wine Is Not an Emulator") is a compatibility layer capable of running Windows applications.
**Remove Wine if you have it installed**
1. If you have a 64-bit system this command will enable 32-bit support
```bash
sudo dpkg --add-architecture i386
```
2. Then follow these **Steps:**
```bash
wget https://dl.winehq.org/wine-builds/winehq.key && sudo apt-key add winehq.key
sudo apt-add-repository deb\ https://dl.winehq.org/wine-builds/ubuntu/\ $(lsb_release -c | sed 's/Codename:\t/''/g')\ main && sudo apt update
sudo apt install --install-recommends winehq-stable -y
```
3. Then open wine configuration, add download the additional wine files
```bash
winecfg
```
**Saftey with Wine** - Never use wine with sudo. Windows apps always run with admin rights in wine. No sudo needed sometimes, You need to tell wine to start an app as a "normal user" but, you never need to run it with admin rights because it already does. So from this, you could be thinking can't hurt to run wine with sudo, Right? Yes, it can hurt, or do you believe that a potential Virus wouldn't be happy to be run with root rights? Viruses work through wine like they would on Windows. sudo gives them even more privileges. <br />

#### 3. Lutris
Lutris is an Open Source gaming platform for Linux. It installs and launches games so you can start playing without the hassle of setting up your games. 
```bash
sudo add-apt-repository ppa:lutris-team/lutris
sudo apt update
sudo apt install lutris
```

#### 4. Synaptic Package manager
Synaptic serves as a graphical front-end to APT which makes the process of software management easier.
```bash
sudo apt install synaptic -y
```
#### 5. Nautilus (admin mode)
Adds right-click property *Open as Administrator*
```bash
sudo apt install nautilus-admin -y && nautilus -q
```
#### 6. Timeshift
Timeshift is a system restore tool for Linux. Creates a file system snapshot using rsync+hard links or BTRFS snapshots.
```bash
sudo apt install timeshift -y
```
#### 7. Resource Monitor
#### - Htop
A utility to see which process is taking how much CPU or memory.
```bash
sudo apt install htop -y
```
![htop](https://github.com/themagicalmammal/howtopopbuntu/blob/master/References/htop.png)
#### - Bashtop
An advanced utility that shows usage and stats for processor, memory, disks, network, and processes.
**Repo already exists in Pop 20.10**
```bash
sudo add-apt-repository ppa:bashtop-monitor/bashtop && sudo apt update
sudo apt install bashtop -y
```
![bashtop](https://github.com/themagicalmammal/howtopopbuntu/blob/master/References/bashtop.png)
#### 8. Firewall
#### - Gufw
GUFW is a graphical utility for managing Uncomplicated Firewall (UFW). This is pretty easy to use appication with bunch of settings which you can set according to your preference.
```bash
sudo apt install gufw
```
#### - Opensnitch
Helps you to review which services connect to the internet. Also, stopping some of the services might help save some internet, and give you more control over it. To get a compiled version of Opensnitch goes [here](https://github.com/evilsocket/opensnitch).

### - Debloat
###### Remove useless stuff that you do not need.  Please, read what it does before you remove them.
- **Calculator** - You know what a calculator is.
```bash
sudo apt remove --purge gnome-calculator -y
```
- **Calendar** - I put this on a list because I never need the Calendar even on my phone
```bash
sudo apt autoremove --purge gnome-calendar -y
```
- **Character Map** - is a Unicode character map that allows you to select characters from a table and insert them into a text string. I have no known use for it.
```bash
sudo apt-get autoremove --purge gucharmap* -y
```
- **Contacts** - Gnome contacts tool important for a work pc.
```bash
sudo apt-get autoremove --purge gnome-contacts* -y
```
- **Document Scanner** - Important tool for a work pc.
```bash
sudo apt-get remove --purge sane* simple-scan -y
```
- **Gnome Fonts** - shows you the fonts installed on your computer for your use as thumbnails. Selecting any thumbnails shows the full view of how the font would look under various sizes.
```bash
sudo apt remove --purge gnome-font-viewer -y
```
- **Gnome Help** - Useful for newcomers
```bash
sudo apt-get autoremove --purge yelp* -y
```
- **Gnome Power Manager** - can show historical and current battery information and programs waking up that use power. I never use it.
```bash
sudo apt remove --purge gnome-power-manager -y
```
- **Pinyin (Only for Chinese users)** - Pinyin is the Romanization of Chinese characters based on their pronunciation.
```bash
sudo apt autoremove --purge ibus-libpinyin -y
```
- **Vim** - Vim is a highly configurable text editor built to configure any kind of text very efficient fashion. I have removed this because I use Nano/Gedit/Atom.
```bash
sudo apt-get autoremove --purge gvim* vim* -y
```
- **Popsicle USB creator** - If you create a live USB, you should keep this tool but, Etcher seems a better option.<br />
**Get [Etcher](https://www.balena.io/etcher/)** <br />
```bash
sudo apt-get remove --purge popsicle* -y
```

#### Reverting
If you accidentally remove any, you can add them back by
```bash
sudo apt install <appname> -y
```
*App name doesn't require * symbol*


## 4. Important Tweaks
### Settings
#### -- Privacy Tweaks
![privacytweaks1](https://github.com/themagicalmammal/howtopopbuntu/blob/master/References/privacytweaks1.png)
![privacytweaks2](https://github.com/themagicalmammal/howtopopbuntu/blob/master/References/privacytweaks2.png)
#### -- Over Amplification
![overamplification](https://github.com/themagicalmammal/howtopopbuntu/blob/master/References/overamplification.png)
### Disable annoying Keyring
#### This provides security for browsers on an autologin-based system. (Easy way to understand it)
If you have an autologin system, whenever you open a browser (except firefox) or Github-desktop, the system asks for a key. <br /> <br />
**Steps to Disable it:**
```settings
App password & keys > Login > Change Password > Type your Current Pass > Continue > Continue with Empty Pass > Make unencrypted
```
![disablekeyring1](https://github.com/themagicalmammal/howtopopbuntu/blob/master/References/disablekeyring1.png)
![disablekeyring2](https://github.com/themagicalmammal/howtopopbuntu/blob/master/References/disablekeyring2.png) <br />

### Controlling Audio Devices
Pavucontrol is one of the most well-known audio managers for PulseAudio.

#### Music playback
In Playback tab, here is a list of all apps that are using your audio system.  To mute all System sounds, press the speaker icon in System Sounds. You can also drag the audio slider to adjust the audio. <br />

But, this tab only shows applications currently using audio. Like in this example, I was listening to Spotify. <br /> <br />
![musicplayback](https://github.com/themagicalmammal/howtopopbuntu/blob/master/References/musicplayback.png)

#### Recording adjuster
In Recording tab, there is a list of all the programs currently recording audio. It is also possible to mute the recording just by clicking on the speaker icon. <br /> <br />
![recordingadjuster](https://github.com/themagicalmammal/howtopopbuntu/blob/master/References/recordingadjuster.png)

#### Speaker & Mic level
**To make a device default press the lock button.** <br />
In Output Devices tab, there is a list of all the audio playback devices.  <br /> <br />
![speakerlevel](https://github.com/themagicalmammal/howtopopbuntu/blob/master/References/speakerlevel.png)  <br />

In Input Devices tab, there is a list of all the recording devices. <br /> <br />
![miclevel](https://github.com/themagicalmammal/howtopopbuntu/blob/master/References/miclevel.png)

## 5. Optimize Boot-time & Ram Usage
My original boot-time was 1min 4sec after removing apps it is now 58sec.<br /> <br />
![originalboottime](https://github.com/themagicalmammal/howtopopbuntu/blob/master/References/originalboottime.png)

### Disabling Plymouth
**For Pop OS** <br />
```bash
sudo kernelstub --delete-options "quiet systemd.show_status=false splash"
```
**For Ubuntu** <br />
Go through [this](https://www.kevin-custer.com/blog/disabling-the-plymouth-boot-screen-in-ubuntu-20-04/) guide. <br />

**This reduces my boot-time to 35sec** <br />

### Adjusting the Swappiness Property
This is required to adjust swap usage. If you have huge rams like 16GB ram then you can reduce this value to as low as 0. But if you have low ram devices like 1GB you should make this 90 or higher. Interactions with the swap file are costlier since swaps are slower than RAMs and they can cause a reduction in performance. <br />

Values according to me for Ram: Ratio should be as follows, 32:0, 16:10, 8:20, 4:50, 2:70 <br />
**20 is just an example value, don't mindlessly use it** <br />
```bash
sudo sysctl vm.swappiness=20
```
**These values do not stick. To add them permanently. Add the above line to sysctl.conf.** <br />
```bash
sudo nano /etc/sysctl.conf
```

### Adjusting  the Cache Pressure Setting
Another issue, the system stores cache about stuff that you frequently open & this makes the system faster, as if it opens again, rather than reloading the data it will use the cache. But, on a lower ram device, this is a bad option since this will seriously slow your system down. <br />
Adjust this like you adjusted swappiness property, values for RAM: Pressure should be as follows, 1:100, 2:90, 4:80, 8:60, 16:50.
```bash
sudo sysctl vm.vfs_cache_pressure=50
```
**Add the above line to sysctl.conf.** <br />
```bash
sudo nano /etc/sysctl.conf
```

### EarlyOOM
It is a cool new feature enabled in Fedora 33. What is it, you ask? In Layman terms, It frees memory when the ram or the swap gets close to full (over 90%). Making this a beneficial feature for heavy usage. This is a very important feature for old hardware. It only consumes 0.5 to 2 MB in the background. <br /> <br />
To install it
```bash
sudo apt install earlyoom -y
```
To check it's status
```bash
systemctl status earlyoom
```
<br />

### Wayland
Wayland is a new protocol that enables 3D compositors to be used as primary display servers, instead of running the 3D compositor as an extension under the (2D) X.org display server. Or, in layman's terms, it assumes you're using a 3D desktop from the start, instead of bolting on 3D capabilities to an 2D framework. <br />

X.org is the default display manager but, X.org is old and is very bloated, thus uses more resources. So in this way, Wayland can be a better option. But, Wayland is a newer display protocol and thus is incomplete in a way giving the birth yo many bugs, and one of them being **NVIDIA**. So, if you have an NVIDIA GPU, Wayland is a bad option. Also, if you don't have NVIDIA GPU, still there might be bugs, so if you have bugs/glitches, remove it.(Remove the #).

1. Edit the /etc/gdm3/custom.conf to either disable or enable Wayland.
```bash
sudo nano /etc/gdm3/custom.conf
```
2. Add # before this line
```nano
WaylandEnable=false
```
3. Then
```bash
sudo systemctl restart gdm3
```
4. Then select it in the login <br />
![wayland](https://github.com/themagicalmammal/howtopopbuntu/blob/master/References/wayland.png)
5. To confirm
```bash
echo $XDG_SESSION_TYPE
``` 
Output should be Wayland
<br />

### Disabling Unnecessary Extensions
Pop OS comes with a lot of Extensions which generally is not used by everyone so you can prefer to disable them you can. </br>
The built-in extensions I use are - <br /> <br />
![gnomeextensions](https://github.com/themagicalmammal/howtopopbuntu/blob/master/References/gnomeextensions.png)

#### I have disabled these
1. **Alt-Tab** -  By default, Alt+Tab will raise all windows of an application. This extension still groups windows by application.
2. **Always show workspaces** - Always show workspaces in the overview.
3. **Desktop Icons** - Add icons to the desktop.
4. **Pop Battery Icon Fix** - Fixes the battery icon to match the current battery level. (Useless for desktop pc)
5. **Pop Shop Details** - Adds a Show Details item to applications if Pop Shop is installed.
6. **System76 Power** - system76-power is a utility for managing graphics and power profiles. Options show up under battery menu. (Useful for hybrid and NVIDIA GPU)

### Disabling Pop Shop on Boot
Pop Shop always opens on the startup of the system there is a way to stop that. This also helps in saving some ram. <br /> <br />
**Steps:**
1. Edit App center daemon from opening it at start
```bash
sudo nano /usr/share/applications/io.elementary.appcenter-daemon.desktop
```
2. Put # here before this line
```bash
Exec=io.elemantry.appcenter -s
```
### Clearing buff/cache
The computer accumulates high buff/cache over time and makes the user force reboot. To clear buff cache, you can use this. <br />
```bash
free -h && sudo sysctl -w vm.drop_caches=3 && sudo sync && echo 3 | sudo tee /proc/sys/vm/drop_caches && free -h
```

### Optimizing the boot
#### DISCLAIMER
##### PLEASE DO THIS AT YOUR OWN RISK. WHILE THIS IS SAFE TO DO YOU CAN STILL MESS UP YOUR SYSTEM SO, PLEASE READ THIS CAREFULLY AND UNDERSTAND EVERYTHING BEFORE YOU PROCEED.
- **Network-dispatcher** is a dispatcher daemon for systemd-networkd connection status changes.
```bash
sudo apt remove --purge networkd-dispatcher -y
```
- **ModemManager** is a DBus-activated daemon that controls mobile broadband (2G/3G/4G) interfaces. If you do not have a mobile broadband interface, you do not need this.
```bash
sudo systemctl disable ModemManager.service
sudo systemctl mask ModemManager.service
```
**Note:** - If you are not using this and don't want Wi-Fi to disable wpa_supplicant.service.
- **fwupd** is a simple daemon allowing you to update some devices' firmware, including UEFI for several machines
Disable thunderbolt_power <br />
```bash
sudo nano /etc/fwupd/daemon.conf
```
Make it
```bash
BlacklistPlugins=test;invalid;thunderbolt_power
```
![blacklist_thunderbold](https://github.com/themagicalmammal/howtopopbuntu/blob/master/References/blacklist_thunderbold.png)
Remove fwupd from boot
```bash
sudo systemctl disable fwupd.service
sudo systemctl mask fwupd.service
```
- **Avahi-daemon** is supposed to provide zero-configuration network discovery and make it super-easy to find printers and other hosts on your network. I always disable it and do not miss it.
```bash
sudo systemctl disable avahi-daemon.service
sudo systemctl mask avahi-daemon.service
```
- **Apport** collects potentially sensitive data, such as core dumps, stack traces, and log files. They can contain passwords, credit card numbers, serial numbers, and other private material.
```bash
sudo systemctl disable apport.service
sudo systemctl mask apport.service
```
- **Saned** is the SANE (Scanner Access Now Easy) daemon that allows remote
clients to access image acquisition devices available on the localhost.
```bash
sudo systemctl disable saned.service
sudo systemctl mask saned.service
```
- **GPU-Manager** is software that creates a xorg.conf for you. So running this in every boot is just overkill. You only need to run this if you change your GPU.
```bash
sudo systemctl disable gpu-manager.service
sudo systemctl mask gpu-manager.service
```
- **Apt-daily-upgrade** solves long boot up time with apt-daily-upgrade.
```bash
sudo systemctl disable apt-daily.service
sudo systemctl disable apt-daily.timer
sudo systemctl disable apt-daily-upgrade.timer
sudo systemctl disable apt-daily-upgrade.service
```
- **lvm2-monitor** Only useful if you are using lvm.
```bash
sudo systemctl disable lvm2-monitor.service
sudo systemctl mask lvm2-monitor.service
```
- **Systemd-resolved** [Restart Required]  is a system service that provides network name resolution to local applications. It implements a caching and validating DNS/DNSSEC stub resolver.
1. Disable & Mask the systemd-resolved service
```bash
sudo systemctl stop systemd-resolved.service
sudo systemctl disable systemd-resolved.service
sudo systemctl mask systemd-resolved.service
```
2. Then put dns=default in the [main] section of
```bash
sudo nano /etc/NetworkManager/NetworkManager.conf
```
3. Delete the symlink /etc/resolv.conf
```bash
sudo rm /etc/resolv.conf
```
4. Restart <br /> <br />

**Might be UnSafe** <br />
- **Switcheroo-control** [Required on Dual-GPU systems] is a D-Bus service to check the availability of dual-GPU. Keep this only if you have 2 GPUs.
```bash
sudo systemctl disable switcheroo-control.service
sudo systemctl mask switcheroo-control.service
```
- **System76-power** [Required on laptops] Power Controls for lappy not required on a desktop PC.
```bash
sudo systemctl disable system76-power.service
sudo systemctl mask system76-power.service
```
- **Thermald** [Might heatup system] daemon prevents machines from overheating and was introduced in the 14.04 Ubuntu Trusty LTS release. It monitors thermal sensors and will modify cooling controls to keep the hardware cool.<br />
**If your system heats after removing this even a bit, add it back**
```bash
sudo systemctl disable thermald.service
sudo systemctl mask thermald.service
```

**Enable them back** <br />
Let the service name be xyz.service
```bash
sudo systemctl unmask xyz.service
sudo systemctl enable xyz.service
```

- Disabling **Startup Application Preferences** <br />

![application-pref](https://github.com/themagicalmammal/howtopopbuntu/blob/master/References/application-pref.png)

#### Boot-time after disabling those stuff
![prekernelbootime](https://github.com/themagicalmammal/howtopopbuntu/blob/master/References/prekernelbootime.png)

### Custom kernel
Custom Kernels are known and used by fewer people, but these kernels add a significant boost to performance and battery.
1. **Xanmod** is the more popular choice among intel based hardware. It provides a stable, responsive, and smooth desktop experience. <br />
To get Xanmod, go [here](https://xanmod.org/)  <br />
While installing this don't forget to add, **Setting the FQ-PIE Queuing Discipline**. <br />

2. **Liquorix** is a distro kernel replacement built using the best configuration and kernel sources for desktop, multimedia, and gaming workloads. Works better with AMD hardware. <br />
To get Liquorix, go [here](https://liquorix.net/) <br /> <br />

Initial benchmarks on intel make Xanmod a winner whereas, AMD hardware generally goes better with Liquorix. Also, if you are having heating issues go for Liquorix for a better thermal response. I use Xanmod normal because long term release felt slow for me on both my PC & lappy. <br />

[Reference of Xanmod being compared to Clear Linux](https://www.phoronix.com/scan.php?page=article&item=ubuntu-xanmod-clear&num=1) <br />
[Reference of Liquorix Kernel Benchmarks For AMD Ryzen](https://www.phoronix.com/scan.php?page=article&item=radeon-gaming-liquorix54&num=1) <br />
[Linux Generic vs Xanmod vs Liquorix](https://www.youtube.com/watch?v=EAe95sWrv0U) (Not English but you can see the benchmark scores.) <br />

**Note:** At this point, boot is the fastest.<br />

### Getting rid of Custom Kernel
**IF YOU ARE A NEW USER AND DON'T KNOW WHAT YOU ARE DOING, PLEASE SEARCH SOME THREADS OR ASK SOMEONE BEFORE TAKING ANY ACTION. BECAUSE THIS IS A VERY RISKY STEP AND CAN POTENTIALLY KILL YOUR SYSTEM.**<br />
1. Removing the Kernel apt modules <br />

For XanMod
```bash
sudo apt autoremove --purge linux-xanmod -y
```

For Liquorix
```bash
sudo apt autoremove --purge linux-image-liquorix-amd64 linux-headers-liquorix-amd64 -y
```
2. [XanMod Only] Remove FQ-PIE Queue Discipline for systemd
```bash
sudo rm /etc/sysctl.d/90-override.conf
```
4. Removing  the Kernel Repos <br />

For XanMod <br />
Download this [deb](https://dl.xanmod.org/xanmod-repository.deb) and uninstall it. <br />

For Liquorix <br />
```bash
sudo add-apt-repository -r ppa:damentz/liquorix
```
**Tip: -r can be after or before the repo, so you can also write,**
```bash
sudo add-apt-repository ppa:damentz/liquorix -r
```

5. Getting, name of the Kernel
```bash
uname -r
```
6. Removing the Kernel
```bash
sudo apt remove <kernel name> -y
```
7. Getting, remaining Kernel files
```bash
apt list --installed *xanmod* *liquorix*
```
8. Removing the remaining Kernel files
```bash
sudo apt remove <name of kernel files> -y
```

[Reference of installing and removing XanMod](https://www.reddit.com/r/pop_os/comments/jlrney/psa_installing_and_removing_the_xanmod_kernel_in/) <br />

### Final Boot-Time
![final-boottime](https://github.com/themagicalmammal/howtopopbuntu/blob/master/References/final-boottime.png)


## 6. Miscellaneous
### Ad-Hosts
I use **Steven Black** Ad-Hosts for ad-blocking the whole system without any other extra app. This blocks basic ads but not YouTube or Spotify ads. <br />

I use **Unified hosts + fake news + gambling + porn** <br />

#### Q. How to?
**Ans. Steps:**
1. Get a [host](https://github.com/StevenBlack/hosts)
2. Save it to Downloads
3. Then
```bash
sudo mv $(xdg-user-dir DOWNLOAD)/hosts.txt /etc/hosts
```

### Terminal Mods
#### 1. Neofetch Mod
 Neofetch displays information about your operating system, software and hardware. This comes with a default config which has a lot of information including CPU,GPU blah blah blah. Me being a minimalist only use some information out of this. <br />
 So, my custom config, makes the neofetch look like this. <br /> <br />
![neofetch](https://github.com/themagicalmammal/howtopopbuntu/blob/master/References/neofetch.png) <br />
 To make your neofetch look this, go [here](https://github.com/themagicalmammal/howtopopbuntu/blob/master/.config/Config.md). <br />
 
#### 2. Shell Config
 I am currently using [Starship](https://starship.rs/) shell config with Dark Patrol from [Gogh](https://github.com/Mayccoll/Gogh). <br />
 **Note:** If you have troubles installing starship with shell script you can install it via [brew](https://brew.sh/). <br />
 To make your terminal look like mine, go [here](https://github.com/themagicalmammal/howtopopbuntu/blob/master/.config/Config.md). <br />
![terminal](https://github.com/themagicalmammal/howtopopbuntu/blob/master/References/terminal.png)

#### 3. Bash Alias
A Bash Alias is a method of supplementing or overriding Bash commands with new ones. <br />

Get my .bash_alias file from [here](https://gist.github.com/themagicalmammal/94c5210122e75b63db230d364ffe73c0). Add this to your .bash.rc
```bash
if [ -f ~/.bash_alias ]; then . ~/.bash_alias fi
```

### TLP
TLP is a utility for battery optimization on laptops. TLP comes with a default configuration which is perfectly tuned. The utility works by optimizing the power used by hardware devices while your laptop is running on its battery.
```bash
sudo apt install tlp
sudo tlp start
```
If you need a graphical interface to optimise or control it.
```bash
sudo add-apt-repository ppa:linuxuprising/apps && sudo apt update
sudo apt install tlpui
```

### Disable Frequents
Disable Frequents Tab in Gnome app menu. This option is not required for Gnome > 3.38.
```bash
gsettings set org.gnome.desktop.privacy remember-app-usage false

```

### Clean your System
#### Clean via Terminal
```bash
sudo apt --purge autoremove
sudo rm -rf ~/.cache/thumbnails/*
sudo apt clean
sudo apt autoclean
```
#### Bleachbit
I use Bleachbit because it is good to remove unnecessary junk from your computer.
```bash
sudo apt install bleachbit -y
```
**Steps:** BleachBit (root) > Select every option (except free disk) > **Clean** <br /> <br />
![bleachbit](https://github.com/themagicalmammal/howtopopbuntu/blob/master/References/bleachbit.png)
**Note:** After doing this the first boot might be slow don't worry it's perfectly normal.

### Night Light
Night Light mode is simply made to remove some lights which hinder our sleep cycle. As researchers have found that at night if a certain set of colors interact with our eyes it doesn't let the eye rest making it *unsleepy* that's why we use a night light.<br /> <br />
**Steps:** Settings > Display > Night light <br />
*You can also select the timing which fits your sleep cycle.*<br /> <br />
![nightlight](https://github.com/themagicalmammal/howtopopbuntu/blob/master/References/nightlight.png)

### Tile Windows
The beautiful thing I like about Pop OS is its feature-rich environment to increase work efficiency.<br /> <br />
![Tile-windows](https://github.com/themagicalmammal/howtopopbuntu/blob/master/References/Tile-windows.png)

### Custom Fonts
Custom Fonts increase the user experience. I use custom fonts on my laptop and also my Oneplus. <br />

Currently I am using Linotte Font for system & MonoFur for my terminal. <br />
To change your font, go to gnome-tweaks then to Fonts. <br /> <br />
![customfont](https://github.com/themagicalmammal/howtopopbuntu/blob/master/References/customfont.png)
To change Terminal font, Go to preferences, then to profiles, then in custom font select MonoFur. <br />
To get my fonts, 
```bash
wget https://github.com/themagicalmammal/howtopopbuntu/raw/master/.local/share/fonts.tar.xz
tar -xf $(xdg-user-dir DOWNLOAD)/fonts.tar.xz -C ${XDG_CONFIG_HOME:-~/.local}/share
rm $(xdg-user-dir DOWNLOAD)/fonts.tar.xz
```
If the font doesn't show, you can try clearing the font cache <br />
```bash
fc-cache -f -v
```

### Customization
#### 1. We need to add gnome-shell-integration for Chrome.
![gsi](https://github.com/themagicalmammal/howtopopbuntu/blob/master/References/gsi.png)
#### 2. Then go to [Gnome.org](https://extensions.gnome.org/) and get your extensions. <br />
#### Important Extensions
- [User themes](https://extensions.gnome.org/extension/19/user-themes/)
- [Impatience](https://extensions.gnome.org/extension/277/impatience/) <br /> <br />
#### Some More Cool Extensions
- [Showtime - Desktop Widget](https://extensions.gnome.org/extension/1429/showtime/)
- [Activities Configurator](https://extensions.gnome.org/extension/358/activities-configurator/)
- [Dash to Dock](https://extensions.gnome.org/extension/307/dash-to-dock/) <br /> <br />
![dashtodock](https://github.com/themagicalmammal/howtopopbuntu/blob/master/References/dashtodock.png)
  - [Frippery Move Clock](https://extensions.gnome.org/extension/2/move-clock/)
  - [Remove Accessibility](https://extensions.gnome.org/extension/112/remove-accesibility/)
  - [Dynamic Panel Transparency](https://extensions.gnome.org/extension/1011/dynamic-panel-transparency/)
- [Dash to Panel](https://extensions.gnome.org/extension/1160/dash-to-panel/) <br /> <br />
![dashtopanel](https://github.com/themagicalmammal/howtopopbuntu/blob/master/References/dashtopanel.png)
To get the start button I [have](https://github.com/themagicalmammal/howtopopbuntu/blob/master/References/start.png). <br />
- [Compiz windows effect](https://extensions.gnome.org/extension/3210/compiz-windows-effect/)
- [Compiz alike magic lamp effect](https://extensions.gnome.org/extension/3740/compiz-alike-magic-lamp-effect/)
#### 3. Custom themes
*Go to [Gnome-look](https://www.gnome-look.org/browse/cat/)* <br />  <br />
**My Setup** <br />
Shell & Application - [WhiteSur-light](https://www.gnome-look.org/p/1403328/) <br />
Cursor - [Bibata](https://www.gnome-look.org/s/Gnome/p/1197198/) <br />
Icons - [McMojave-circle](https://www.gnome-look.org/s/Gnome/p/1305429) <br />
Wallpaper - [Colorful New York](https://imgur.com/gallery/kBwTMX5) <br />

#### 4. Place the theme in .themes & the icons in .icons in Home.
#### 5. In the Gnome tweak tool, Select your theme.

**Tip** - How to fix terminal theme
1. Go to Preferences.
2. Add Profiles.
3. Name it Big_Sur.
3. Go to colors, then select *choose use colors from system theme*.
4. Set Big_Sur default.
5. Close and reopen the terminal.

**Tip** - How to fix gedit/text-editor theme
1. Go to Preferences.
2. Go to Font & Colors.
3. Select Color Scheme - Classic. <br />

**Tip** - Add icon instead of Activities text
1. Go to Extensions.
2. Open settings for Activities Configurator.
3. Select a custom icon
**The icon I use is [here](https://github.com/themagicalmammal/howtopopbuntu/blob/master/icons/pop.png)**
4.  Hide Text & reduce icon padding

#### After you do all of this, your desktop should look this
![bigsurlikelook](https://github.com/themagicalmammal/howtopopbuntu/blob/master/References/bigsurlikelook.png) <br /> <br />

#### To fix qt5 applications like KolourPaint to respect system theme, go [here](https://gist.github.com/tur1ngb0x/82f6fa2fff3d05fe2e3c73d83ee3b6a4).

## Discussion
To post suggestions or ask questions. Go to [Discussions](https://github.com/themagicalmammal/howtopopbuntu/discussions).

## Thanks for Suggestions
1. [GGG_246](https://www.reddit.com/user/GGG_246/) - A lot of stuff I didn't know. To check what he did go [here](https://www.reddit.com/r/Ubuntu/comments/jm1gvw/a_guide_to_setting_up_popubuntu/gasmuhg?utm_source=share&utm_medium=web2x&context=3) & [here](https://www.reddit.com/r/Ubuntu/comments/jm1gvw/a_guide_to_setting_up_popubuntu/gata2s4?utm_source=share&utm_medium=web2x&context=3) & a looooot more stuff.
2. [schykle](https://www.reddit.com/user/schykle) - Mailspring (fix for dangerous gvfs-bin bug) & Ubiquity auto Swap & GUI updater & Updated Snap instructions.
3. [wsadES](https://www.reddit.com/user/wsades) - Suggestion about removing unnecessary extension & Pop Shop on boot.
4. [tur1ngb0x](https://github.com/tur1ngb0x) - For qt5 theme fix & new wine installation steps.
5. [coolwyou](https://www.reddit.com/user/coolwyou) - For the awesome neofetch config file & shell config.
6. [spxak1](https://www.reddit.com/user/spxak1/) - Mention Firefox & Chromium-based Bug & Idea about Disclaimer & Reverting back to stock kernel.
7. [JawadAlkassim](https://www.reddit.com/user/JawadAlkassim/) - Mention opensource & Vivaldi vaapi & Wayland.
8. [arsfeld](https://www.reddit.com/user/arsfeld) - Information about Encryption and recovery.
9. [lulzdoods](https://www.reddit.com/user/lulzdoods) - Completing the uninstall guide for the kernel.
10. [RiderExMachina](https://www.reddit.com/user/RiderExMachina/) - Check out what he said [here](https://www.reddit.com/r/linux4noobs/comments/jqyi1c/want_to_switch_to_ubuntubased_distros_need_a/gbqvrbf?utm_source=share&utm_medium=web2x&context=3)
11. [1ntr0v3rt3ch](https://www.reddit.com/user/1ntr0v3rt3ch) - For steps for making a swap file.
12. [rbmorse](https://www.reddit.com/user/rbmorse/) - Practices on a swap.
