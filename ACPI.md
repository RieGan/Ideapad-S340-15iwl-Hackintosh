# Fixing ACPI
This setup using ACPI from many source. Because of that, on opencore v0.7.2 the system is unable sleep without Lowest CPU freq curve from CPUFriend. In order to fix this problem, we need to create our ACPI

## Dump SSDT

## Create ACPI
  * ### fix EC & USB Power

    name      | how-to
    ----------|-----------
    SSDT-EC | [ssdttime](https://dortania.github.io/Getting-Started-With-ACPI/ssdt-methods/ssdt-easy.html#so-what-can-t-ssdttime-do)
    SSDT-USBX | [ssdttime-prebuilt](https://github.com/dortania/OpenCore-Post-Install/blob/master/extra-files/SSDT-USBX.aml)
    <br>
    OR
    <br>
    <br>

    name      | how-to
    ----------|-----------
    SSDT-EC-USBX | [manual](https://dortania.github.io/Getting-Started-With-ACPI/Universal/ec-methods/manual.html#finding-the-acpi-path)

  * ### Fix trackpad
    name      | how-to
    ----------|-----------
    SSDT-XOSI | [prebuilt](https://dortania.github.io/Getting-Started-With-ACPI/Laptops/trackpad-methods/prebuilt.html)
    <br>
    OR
    <br>
    <br>

    name      | how-to
    ----------|-----------
    SSDT-GPI0 |[manual](https://dortania.github.io/Getting-Started-With-ACPI/Laptops/trackpad-methods/manual.html)

  * ### fix CPU power
    name      | how-to
    ----------|-----------
    SSDT-PLUG |[ssdtime](https://dortania.github.io/Getting-Started-With-ACPI/Universal/plug-methods/ssdttime.html) 
    SSDT-PLUG | [manual](https://dortania.github.io/Getting-Started-With-ACPI/Universal/plug-methods/manual.html#finding-the-acpi-path)

  * ### fix backlight
    name      | how-to
    ----------|-----------
    SSDT-PNLFCFL |[manual](https://dortania.github.io/Getting-Started-With-ACPI/Laptops/backlight-methods/manual.html)

  * ### fix system clock
    name      | how-to
    ----------|-----------
    SSDT-AWAC OR SSDT-RTC0 |[manual](https://dortania.github.io/Getting-Started-With-ACPI/Universal/awac-methods/manual.html#determining-which-ssdt-you-need)

  * ### fix sleep
    name      | how-to
    ----------|-----------
    SSDT-GPRW OR SSDT-UPRW |[prebuilt](https://dortania.github.io/OpenCore-Post-Install/usb/misc/instant-wake.html)

    note : check `Method (GPRW,2` or `Method (UPRW,2` in ACPI

  * ### IRQPatch
    SSDT-HPET [ssdtime](https://dortania.github.io/Getting-Started-With-ACPI/Universal/irq.html)

  * ### SMBUS (Optional)
    SSDT-SBUS-MCHC [manual](https://dortania.github.io/Getting-Started-With-ACPI/Universal/smbus-methods/manual.html#finding-the-acpi-path)

  * ### OPTIONAL
    Name | Feature | status
    -----|---------|------- 
    SSDT-PSF13 | fix prtsc key to f13 | [prebuilt](https://github.com/WraithWinterly/Lenovo-Ideapad-S340-Hackintosh-Catalina-OpenCore/blob/master/EFI/OC/ACPI/SSDT-PSF13.aml?raw=true)
    SSDT-Q11Q22 | fix brigthness key, don't use if brightnesskeys.kext enabled | [prebuilt](https://github.com/WraithWinterly/Lenovo-Ideapad-S340-Hackintosh-Catalina-OpenCore/blob/master/EFI/OC/ACPI/SSDT-Q11Q12.aml?raw=true)

## [Cleanup](https://dortania.github.io/Getting-Started-With-ACPI/cleanup.html)
