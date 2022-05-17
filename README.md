# Hackintosh HP EliteBook 840 G3
## macOS Monterey 12.4 - OpenCore version 0.7.8 - Deutsche Qualität

![obligatory screenshot](/images/skrienshod 2.png)

Things that are working and their corresponding kexts:

- Intel HD 520 graphics - [WhateverGreen](https://github.com/acidanthera/WhateverGreen), ig-platform-id 00001619
- Conexant CX20724 ISST Audio - [AppleALC](https://github.com/acidanthera/AppleALC), layout ID 13
- Intel AC 8260 WiFi+BT - [AirportItlwm](https://github.com/OpenIntelWireless/itlwm) + [IntelBluetoothFirmware](https://github.com/OpenIntelWireless/IntelBluetoothFirmware), SecureBootModel j680
- Intel I219-LM Ethernet - [IntelMausiEthernet](https://github.com/acidanthera/IntelMausi)
- Battery percentage (no cycle info) - [SMCBatteryManager](https://github.com/acidanthera/VirtualSMC), [ECEnabler](https://github.com/1Revenger1/ECEnabler)
- Realtek SD card reader - [Sinetek-rtsx](https://github.com/cholonam/Sinetek-rtsx)
- Keyboard and mouse nipple - [VoodooPS2Controller](https://github.com/acidanthera/VoodooPS2)
- SMBus trackpad - [VoodooRMI](https://github.com/VoodooSMBus/VoodooRMI)
- Screen brightness via SSDT-PNLF
- Fn hotkeys (mostly)
- DisplayPort and VGA outputs

Things partially or not working:
- Mic mute
- WiFi button only disables Bluetooth
- Numlock

Untested:
- Dock connector and docking functionality

Known bugs:
- Lowest screen brightness setting turns off backlight
- VoodooRMI sometimes fails to load properly, requiring a reboot

## ACPI POST error fix

I added this as without it, I would get a POST error every time I booted the machine.
This is a problem universal to HP systems, the solution is just as universal, this patch should work for 99% of HP laptops that experience this issue:

```
Comment | String  | RTC fix to stop POST error
Enabled | Boolean | Yes
Count   | Number  | 0
Limit   | Number  | 0
Find    | Data    | 47017000 70000108
Replace | Data    | 47017000 70000102
```
In the ACPI - Patch section.

## OCB StartImage Failed, Security Violation - what do?

Follow the troubleshooting steps [here](https://dortania.github.io/OpenCore-Post-Install/universal/security/applesecureboot.html#special-notes-with-securebootmodel)

## Special Thanks
- Person on Reddit who I found the POST error patch from
- acidanthera for [OpenCore](https://github.com/acidanthera/OpenCorePkg) and half the kexts here

Piece to da brok3n cr3w, you all 1337!
