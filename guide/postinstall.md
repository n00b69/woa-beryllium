<img align="right" src="https://raw.githubusercontent.com/graphiks/woa-raphael/main/media/raphael.png" width="350" alt="Windows 11 Running On raphael">


# Running Windows on the Mi 9T Pro / Redmi K20 Pro

## Optional post-install stuff
> [!NOTE]
> All of these are optional, but enabling USB host mode is recommended otherwise non-powerered USB devices will not work.

### Enabling USB Host mode
> [!NOTE]
> This will also disable charging (not that you would want to charge in Windows anyways)

### Prerequisites
- [This registry file](https://github.com/graphiks/Port-Windows-11-Raphael/releases/download/raphael-usb/USB-OTG_ON.reg) 
- [This batch script](https://github.com/graphiks/Port-Windows-11-Raphael/releases/download/raphael-usb/OTG.and.Charge.switcher.bat)

 - Run the .reg file you just downloaded on your phone, click yes.
 - Run the batch script that you just downloaded on your phone. Select option 1 <br>
(Re-run the batch script and select 2 if you want charging back)

This makes USB work properly. If USB doesn't work, you may have to plug it in before boot.


### Copying over calibration files/configuration files for the sensors
> [!NOTE]
> - These steps are temporary and will not be needed in future releases. These steps are also not as fully detailed as others and may get updated at a later time
> - In order to get most sensors currently working, some manual steps are required.
> - Mount persist in TWRP first!
* You will need to backup from mass storage or twrp the following directory: /persist/sensors/
* Copy over the contents to [Windows Drive Letter]\Windows\System32\Drivers\DriverData\QUALCOMM\fastRPC\persist\sensors (the following directory should already exist after booting Windows once, otherwise create it)


## Finished!




