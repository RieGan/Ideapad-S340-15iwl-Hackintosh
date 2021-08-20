## Post-Install Recommendation

After macOS installation completed please do some of my recommendation

### Install [Homebrew](https://brew.sh/)
Homebrew installs the stuff you need that Apple (or your Linux system) didn’t.

command : 
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### Disable Apple Gatekeeper
Gatekeeper is a new security feature starting in Mac OS 10.8. See [Apple's Website](https://support.apple.com/en-us/HT202491) for more information about Gatekeeper features and benefits. \
 \
how-to : 
```
System Preferences > Security & Privacy > General
```

![image](https://user-images.githubusercontent.com/33412865/129668869-12ec1bb9-dd11-40ab-8302-707be6e43ba5.png)

### Disable .DS_store
Hate .DS_store file showing in your project file?

command :
```
defaults write com.apple.desktopservices DSDontWriteNetworkStores true
```

### Install oh-my-zsh
Oh My Zsh is an open source, community-driven framework for managing your Zsh configuration. \
 \
command : 
```
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

### Recommended Software

#### Hackintosh Utilities

Name                  | Feature
----------------------|--------
keka                  | Create many archive format
mos                   | For smooth scroll on mouse
stats                 | like iStat, but opensource
xcodes                | install more than one xcode versions
hackintool            | show hardware-mac metadata for verifying your hackintosh
tunnelblick           | VPN manager
opencore-configurator | **NOT RECOMMENDED** but makes debugging/fixing opencore config files more simpler

#### General Softwares

Name              | Feature
------------------|--------
google-chrome     | best browser ^-^
microsoft-office  | you know what this is
transmission      | opensource torrent client
vlc               | best media player
steam             | you don't play any games on mac? sad T_T
obs               | for streaming yo
whatsapp          | 
telegram-desktop  | 
zoom              |
spotify           |
discord           |

#### For developer only

Name              | Feature
------------------|--------
visual-studio-code| IDE
postman           | API test
vmware-fusion     | best VM(?)
wireshark         | 
hex-fiend         |
android-platform-tools | adb, fastboot, etc
docker            | __*cask*__ container
docker-compose    | 
figma             | 
github            | 
vmware-fusion     |









