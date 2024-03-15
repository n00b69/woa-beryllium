<img align="right" src="https://raw.githubusercontent.com/graphiks/woa-raphael/main/media/raphael.png" width="350" alt="Windows 11 Running On raphael">


# Running Windows on the Mi 9T Pro / Redmi K20 Pro 

## Troubleshooting Issues


## Cannot mount the Windows partition in Android or WoA Helper doesn't work
> This is caused when you shut down Windows instead of restarting it.
- To solve this, boot to Windows and then press "restart", then as the screen shuts off boot to TWRP and from there load up Android.
> Alternatively, if you have already set up the Switch to Android app, simply use this to switch to Android.

## USB does not work
Enable USB host mode using the optional [post install guide](postinstall.md).

## Restoring the WiFi drivers
- Copy the raphael drivers over to your device (preferably on the desktop)
- Open the raphael drivers folder
- Navigate to raphael-drivers-main\components\QC8150\Device\Raphael\DEVICE.SOC_QC8150.RAPHAEL\Extensions\Subsystems\
- Rename "raphael_subextmpss.inf_" to "raphael_subextmpss.inf"; and right click on it and press Install (accept the driver signature popup)
- Rename "raphael_subextscss.inf_" to "raphael_subextscss.inf"; also right click on it and press Install
#### Finished!


## DISM Error:87 The add-driver option is unkown
This usually means that you have an unclean Windows image with some other drivers. You need to get a clean Windows image (which means you didn't follow instructions).

## 0xc000021a BSOD
This usually means that winlogon.exe has failed, and you may need to reapply the Windows image.

## The computer restarted unexpectedly or encountered an unexpected error
If you stumble upon this error, you may need to redeploy the Windows image. Use the [reinstall guide](reinstall.md) for this.


## INACCESSIBLE_BOOT_DEVICE BSOD
This Blue Screen of Death likely means some broken driver installation. To fix this, reinstall the drivers using the [reinstall guide](reinstall.md).

## My screen is dimmer than before
A weird workaround for this... is to just press the power button to put the phone to sleep, and again to wake it. Just works for some reason.

