# Ideapad-S340-15iwl-Hackintosh

[![OpenCore](https://img.shields.io/badge/OpenCore-v0.7.2-blue.svg)](https://github.com/acidanthera/OpenCorePkg)
[![MacOS-Stable](https://img.shields.io/badge/MacOS-11.5.2-brightgreen.svg)](https://www.apple.com/macos/catalina/)
![STATUS](https://img.shields.io/badge/STATUS-stable-green.svg)

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
| [AirportBrcmFixup](https://github.com/acidanthera/AirportBrcmFixup)          | 2.1.3  |
| [AppleALC](https://github.com/acidanthera/AppleALC)       | 1.6.3  |
| [BrcmPatchRAM](https://github.com/acidanthera/BrcmPatchRAM) | 2.6.0
| [BrightnessKeys](https://github.com/acidanthera/BrightnessKeys) | 1.0.2
| [CPUFriend](https://github.com/acidanthera/CPUFriend) | 1.2.4
| [NVMeFix](https://github.com/acidanthera/NVMeFix) | 1.0.9
| [VoodooI2C](https://github.com/VoodooI2C/VoodooI2C) | 2.6.5
| [VoodooPS2](https://github.com/acidanthera/VoodooPS2) | 2.2.4
| [Lilu](https://github.com/acidanthera/Lilu)               | 1.5.5  |
| [VirtualSMC](https://github.com/acidanthera/VirtualSMC)| 1.2.6 |
| [WhateverGreen](https://github.com/acidanthera/WhateverGreen) | 1.5.2 |


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

Power on the laptop while pressing F2 at boot. You'll see a lot of debug options. Don't mess with them. We only need to change one setting. 
Config | How-to
-------|-------
CFG-LOCK | Advanced → Power & Performance → CPU-Power Management Control → CPU Lock Configuration → CFG Lock → Disabled
Above 4G decoding | Advanced → System Agent Conf → Above 4GB MMIO BIOS assigment -> disabled
VT-d | Advanced → System Agent Conf → VT-d → disabled


Exit and Save, and your laptop is ready to install.

# OpenCore Config Before Installation
#### 1 : Creating USB Installation - [open](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/)
#### 2 : Disable dGPU<sup></sup> - [open](https://dortania.github.io/OpenCore-Install-Guide/extras/spoof.html#windows-gpu-selection)
If your laptop have discrete GPU, disable it first. MacOS Doesn't have support for those laptop's dGPU
#### 3 : Change Wireless Card
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
- USB Port	:white_check_mark:
- Sound Input-Output	:white_check_mark:
- Brightness Key	:white_check_mark:
- WebCam 	:white_check_mark:


 
### Not-Working
- Card Reader

# Some of Screenshots
![Cinnebench R23](https://i.ibb.co/rFTw1Sk/Screenshot-2021-08-12-at-13-43-35.png)

# Credits
This build wouldn't happen without these people: 
- [Dortania](https://github.com/dortania) for OpenCore Guide
- [corpnewt](https://github.com/corpnewt) for all the tools
- [Acidanthera](https://github.com/acidanthera) for too many things
- [OpenCore project](https://github.com/OpenCorePkg) for the bootloader
- [VoodooI2C](https://github.com/VoodooI2C/VoodooI2C) for the trackpad kext
- [headkaze](https://github.com/headkaze) for Hackintool 
- [curtistn](https://www.tonymacx86.com/threads/guide-lenovo-ideapad-s340-laptop-on-catalina.288003/page-53#post-2209713) for the framebuffer patch
- [WraithWinterly](https://github.com/WraithWinterly) for CFG-Lock disabling tutorial

# Another Section
### [Post-install Recommendation](https://github.com/RieGan/Ideapad-S340-15iwl-Hackintosh/blob/master/recommendation.md)
### [ACPI Patch](https://github.com/RieGan/Ideapad-S340-15iwl-Hackintosh/blob/master/ACPI.md)

