# Fixing ACPI

~~This setup using ACPI from many source. Because of that, on opencore v0.7.2 the system is unable sleep without Lowest CPU freq curve from CPUFriend. In order to fix this problem, we need to create our ACPI~~

If your laptop using older or newer version of firmware/BIOS than ALCN33WW(V2.10) or maybe have different configuration please recreate the ACPI and patch accordingly.

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
    SSDT-GPI0 |[manual](https://dortania.github.io/Getting-Started-With-ACPI/Laptops/trackpad-methods/manual.html)

  * ### fix CPU power
    name      | how-to
    ----------|-----------
    SSDT-PLUG | [ssdtime](https://dortania.github.io/Getting-Started-With-ACPI/Universal/plug-methods/ssdttime.html) 
    SSDT-PLUG | [manual](https://dortania.github.io/Getting-Started-With-ACPI/Universal/plug-methods/manual.html#finding-the-acpi-path)

  * ### fix backlight
    name      | how-to
    ----------|-----------
    SSDT-PNLFCFL |[manual](https://dortania.github.io/Getting-Started-With-ACPI/Laptops/backlight-methods/manual.html)

  * ### fix system clock
    name      | how-to
    ----------|-----------
    SSDT-AWAC-DISABLE |[manual](https://dortania.github.io/Getting-Started-With-ACPI/Universal/awac-methods/manual.html#determining-which-ssdt-you-need)

  * ### fix sleep
    name      | how-to
    ----------|-----------
    SSDT-GPRW |[prebuilt](https://dortania.github.io/OpenCore-Post-Install/usb/misc/instant-wake.html)

  * ### _IRQPatch_ (optional)
    name      | how-to
    ----------|-----------
    SSDT-HPET | [ssdtime](https://dortania.github.io/Getting-Started-With-ACPI/Universal/irq.html)

  * ### _SMBUS_ (Optional)
    name      | how-to
    ----------|-----------
    SSDT-SBUS-MCHC | [manual](https://dortania.github.io/Getting-Started-With-ACPI/Universal/smbus-methods/manual.html#finding-the-acpi-path)

  * ### _OPTIONAL_
    Name | Feature | status
    -----|---------|------- 
    SSDT-HPET | IRQ Conflict patch | [ssdtime](https://dortania.github.io/Getting-Started-With-ACPI/Universal/irq.html)
    SSDT-SBUS-MCHC | SMBUS Fix |[manual](https://dortania.github.io/Getting-Started-With-ACPI/Universal/smbus-methods/manual.html#finding-the-acpi-path)
    SSDT-PSF13 | fix prtsc key to f13 | [prebuilt](https://github.com/RieGan/Ideapad-S340-15iwl-Hackintosh/blob/master/SSDTs/compiled/SSDT-PSF13.aml?raw=true)

## [Cleanup](https://dortania.github.io/Getting-Started-With-ACPI/cleanup.html)
