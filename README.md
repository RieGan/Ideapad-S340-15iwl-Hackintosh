# Ideapad-S340-15iwl-Hackintosh

[![OpenCore](https://img.shields.io/badge/OpenCore-v0.8.1-blue.svg)](https://github.com/acidanthera/OpenCorePkg)
[![MacOS-Stable](https://img.shields.io/badge/MacOS-11.6.6-brightgreen.svg)](https://www.apple.com/macos/)
![STATUS](https://img.shields.io/badge/STATUS-stable-brightgreen.svg)
[![MacOS-Stable](https://img.shields.io/badge/MacOS-12.4-blueviolet.svg)](https://www.apple.com/macos/)
![STATUS](https://img.shields.io/badge/STATUS-BETA-blueviolet.svg)


# Introduction
This is my second hackintosh project. This hackintosh configuration is built for Lenovo Ideapad S340-15iwl. This repository is intended for educational purpose. Personally, I don't have much money for buying mac device, so... this is my approach.

# Disclaimer
Please read entire guide from Dortania OpenCore Guides and this ReadMe before you using this config. I am not responsible for any damage. If you want to improve this repo, please make issue or pull request. Any help would be greatly appreciated.

# Laptop Configuration
#### SMBIOS: MacBookPro15,4
 ### Hardware
| Category      | Component        |
|---------------|------------------|
| CPU           | Intel i5-8265u   |
| GPU           | UHD 620          |
| NVME          | WD SN520         |
| Wireless Card | BCM93450ZAE      |
 
 ### BIOS Configuration
 ALCN33WW(V2.10)
| Settings          | Value     |
|-------------------|-----------|
| fastboot          | disabled  |
| Secure Boot       | disabled  |
| Intel PTT         | disabled  |
| CSM               | disabled  |
| SATA Mode         | AHCI      |
| VT-d              | disabled  |
| Intel SGX Mode    | disabled  |
| Above 4G decoding | disabled  |
| CFG Lock          | disabled  |

 ### Kext
| Name          | Version    |
|-------------------|-----------|
| [AirportBrcmFixup](https://github.com/acidanthera/AirportBrcmFixup)          | 2.1.5  |
| [AppleALC](https://github.com/acidanthera/AppleALC)       | 1.7.2  |
| [BrcmPatchRAM](https://github.com/acidanthera/BrcmPatchRAM) | 2.6.2
| [BrightnessKeys](https://github.com/acidanthera/BrightnessKeys) | 1.0.2
| [CPUFriend](https://github.com/acidanthera/CPUFriend) | 1.2.5
| [NVMeFix](https://github.com/acidanthera/NVMeFix) | 1.0.9
| [VoodooI2C](https://github.com/VoodooI2C/VoodooI2C) | 2.7
| [VoodooPS2](https://github.com/acidanthera/VoodooPS2) | 2.2.8
| [Lilu](https://github.com/acidanthera/Lilu)               | 1.6.0  |
| [VirtualSMC](https://github.com/acidanthera/VirtualSMC)| 1.2.9 |
| [WhateverGreen](https://github.com/acidanthera/WhateverGreen) | 1.5.9 |


### Advanced BIOS Menu

Fully power off the laptop. Enter the BIOS by pressing F2 at boot. Power off the laptop again. Quickly enter the following code:
```
     F1 → 1 → Q → A → Z
     
     F2 → 2 → W → S → X
     
     F3 → 3 → E → D → C
     
     F4 → 4 → R → F → V
     
     F5 → 5 → T → G → B
     
     F6 → 6 → Y → H → N
```

Power on the laptop while pressing F2 at boot. You'll see a lot of debug options. Don't mess with them. We only need to change this settings. 

| Config            | How-to |
| ------------------|--------|
| CFG-LOCK          | Advanced → Power & Performance → CPU-Power Management Control → CPU Lock Configuration → CFG Lock → Disabled |
| Above 4G decoding | Advanced → System Agent Conf → Above 4GB MMIO BIOS assigment -> disabled |
| VT-d              | Advanced → System Agent Conf → VT-d → disabled |


Exit and Save, and your laptop is ready to install.

# OpenCore Config Before Installation
#### 1 : Creating USB Installation - [open](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/)
#### 2 : Disable dGPU<sup></sup> - [open](https://dortania.github.io/OpenCore-Install-Guide/extras/spoof.html#windows-gpu-selection)
If your laptop have discrete GPU, disable it first. MacOS Doesn't have support for those laptop's dGPU
#### 3 : Wireless Card Configuration
- First Option \
  Change to BCM93450ZAE
- Second Option <sup>*</sup> __*HARD*__ \
  Using [ProperTree](https://github.com/corpnewt/ProperTree) open config.plist
  
  ```
  Kernel → Add → BundlePath == "AirportBrcmFixup.kext" → Enabled = False
  
  Kernel → Add → BundlePath == "AirportBrcmFixup.kext/Contents/PlugIns/AirPortBrcmNIC_Injector.kext" → Enabled = False
  
  Kernel → Add → BundlePath == "BrcmBluetoothInjector.kext" → Enabled = False
  
  Kernel → Add → BundlePath == "BrcmFirmwareData.kext" → Enabled = False
  
  Kernel → Add → BundlePath == "BrcmPatchRAM3.kext" → Enabled = False
  
  DeviceProperties → Add → PciRoot(0x0)/Pci(0x1D,0x2)/Pci(0x0,0x0) → *DELETE*
  ```
  After that, follow this [`itlwm` tutorial](https://openintelwireless.github.io/itlwm/)
  
  <sup>*</sup>For intel wireless card
#### 4 : Generate New Serial using [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS)
Type: MacBookPro15,4

Using [ProperTree](https://github.com/corpnewt/ProperTree) open config.plist
  
  ```
  PlatformInfo → Generic → MLB = GenSMBIOS:Board Serial
  
  PlatformInfo → Generic → ROM = Your Wireless Card MAC Address without ":"
  
  PlatformInfo → Generic → SystemSerialNumber = GenSMBIOS:Serial
  
  PlatformInfo → Generic → SystemUUID = GenSMBIOS:SmUUID
  ```
#### 5 : Copy your edited EFI folder to USB 
#### 6 : Have fun with your installation
  

# Working & Not-Working
### Working
- Wi-Fi 	:white_check_mark:
- GPU Acceleration	:white_check_mark:
- Sleep/Wake	:white_check_mark:
- Shutdown - Restart	:white_check_mark:
- USB Port (Mapped)	:white_check_mark:
- Sound Input-Output	:white_check_mark:
- Brightness Key	:white_check_mark:
- WebCam 	:white_check_mark:
- Bluetooth :white_check_mark:
- HDMI :white_check_mark:
- Touchpad :white_check_mark:
- Keyboard :white_check_mark:



 
### Not-Working
- Card Reader 
- NumLock Key
- __[Monterey]__ Bluetooth because of [the new implementation of bluetooth](https://github.com/acidanthera/bugtracker/issues/1821)
- __[Monterey]__ Boot-picker and BIOS keyboard after shutdown ( everything is normal after boot or after using other os but monterey) check [this](https://github.com/acidanthera/bugtracker/issues/1895)
# Some of Screenshots
<sup>*</sup>Using PL1:12.5w and PL2:25w, default BIOS config using a lot more than that
![Cinnebench R23](https://i.ibb.co/rFTw1Sk/Screenshot-2021-08-12-at-13-43-35.png) \
![Geekbench 5 - CPU](https://user-images.githubusercontent.com/33412865/131515136-832718ea-4077-48df-b9a8-ad5fb24a70b9.png) \
![Geekbench 5 - GPU](https://user-images.githubusercontent.com/33412865/131517289-ee3aabc8-9171-44f3-8824-d2a3037b5678.png) \
![Hackintool USB](https://user-images.githubusercontent.com/33412865/131515407-dd154eac-cbd7-4091-8451-c0732d6656db.png)


# Fixing Audio Jack after sleep
This is common problem for ALC 295. After sleep, usually OS (windows/linux) send some signal to reactivate audio jack. But, in this case (hackintosh) that thing doesn't happen. So, we need to send that signal manually after every wakeup. Fortunately, we have tool to automated that.

## Download ALCPlugFix for Ideapad S340 Iwl
Download the files from [here](https://github.com/RieGan/Ideapad-S340-15iwl-Hackintosh/releases/tag/ALCPlugFix)

## Extract and run
Extract the files and run `install.sh` from terminal

## Import Config for ALC295
Drag and drop `ALC295.plist` to terminal

## Restart
Audio jack problem solved after restart



# Credits
This build wouldn't happen without these people: 
- [Dortania](https://github.com/dortania) for OpenCore Guide
- [corpnewt](https://github.com/corpnewt) for all the tools
- [Acidanthera](https://github.com/acidanthera) for too many things
- [OpenCore project](https://github.com/OpenCorePkg) for the bootloader
- [VoodooI2C](https://github.com/VoodooI2C/VoodooI2C) for the trackpad kext
- [headkaze](https://github.com/headkaze) for Hackintool 
- [black-dragon74](https://github.com/black-dragon74) for ALCPlugFix-Swift
- [curtistn](https://www.tonymacx86.com/threads/guide-lenovo-ideapad-s340-laptop-on-catalina.288003/page-53#post-2209713) for the framebuffer patch
- [WraithWinterly](https://github.com/WraithWinterly) for CFG-Lock disabling tutorial

# Another Section
### [Post-install Recommendation](https://github.com/RieGan/Ideapad-S340-15iwl-Hackintosh/blob/master/recommendation.md)
### [ACPI Patch](https://github.com/RieGan/Ideapad-S340-15iwl-Hackintosh/blob/master/ACPI.md)

