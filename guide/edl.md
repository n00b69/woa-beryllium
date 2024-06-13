<img align="right" src="https://github.com/n00b69/woa-polaris/blob/main/polaris.png" width="350" alt="Windows 11 running on polaris">

# Running Windows on the Xiaomi Mix 2s

## Restoring your device with EDL

### Prerequisites
- [Stock fastboot rom](https://xiaomifirmwareupdater.com/miui/polaris/)

- [EDL tools](https://github.com/n00b69/woa-polaris/releases/download/Files/Xiaomi845freeEDL.zip)

### Extracting the stock rom
> Download the stock fastboot rom for your device (which should be in .tgz format), then extract the contents of the .tar file that is inside.

### Booting into EDL mode
> If you're already in EDL, you can skip this step
- Download and extract **Xiaomi845freeEDL.zip**. You may need to disable your antivirus software or it may falsely be detected as being malware.
- While in fastboot mode, open **XiaomiFree9008ForQ845.exe**.
- Press **2**, then confirm by pressing **enter** to boot into EDL mode.

#### Finding the COM## number
> The software should open device manager. If it does not, open it manually
- Locate a device named **Qualcomm HS-USB QDLoader 9008 (COM##)** under **Ports (COM & LPT)**.
> [!Important]
> If the device has a ⚠️ yellow warning triangle, you need to install EDL drivers before you can continue to the next step.
- Record the **COM##** number at the end of **Qualcomm HS-USB QDLoader 9008 (COM##)**.
- In the menu, press **1** and then **enter**. It will then ask for the com port: enter the **COM##** number, then press **enter**

### Flashing the stock rom
- Copy and paste the full path to the images folder in the extracted fastboot rom from the first stepn then press **enter** to start flashing the rom.
> It should look something like: C:\Users\Pidoraz\Downloads\polaris_global_images_V12.0.3.0.QDGMIXM_20201228.0000.00_10.0_global\images

#### Reboot to Android
> After it finishes flashing the ROM (this might take around 5 minutes), simply reboot the device to boot back into Android.

## Finished!












