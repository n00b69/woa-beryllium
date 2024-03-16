<img align="right" src="https://github.com/n00b69/woaberyllium/blob/main/beryllium.png" width="350" alt="Windows 11 running on beryllium">


# Running Windows on the Xiaomi Pocophone F1

## Updating drivers

### Prerequisites
  
- [UEFI image](https://github.com/n00b69/woaberyllium/releases/tag/UEFI)
  
- [Drivers]() FILE NEEDED
  
- [Msc script]() FILE NEEDED
  
- [TWRP](https://github.com/n00b69/woaberyllium/releases/download/Recoveries/twrp.img) (should already be installed)

##### Boot to TWRP
> If rebooting on the last page has replaced your recovery back to stock, flash it again in fastboot with:
```cmd
fastboot flash recovery path\to\twrp.img reboot recovery
```

##### Pushing the msc script
Put msc.sh in the platform-tools folder, then run:
```cmd
adb push msc.sh /
```

##### Running the msc script
```cmd
adb shell sh msc.sh
```

## Diskpart
>  [!WARNING]
> DO NOT ERASE ANY PARTITION WHILE IN DISKPART!!!! THIS WILL ERASE ALL OF YOUR UFS!!!! THIS MEANS THAT YOUR DEVICE WILL BE PERMANENTLY BRICKED WITH NO SOLUTION! (except for taking the device to Xiaomi or flashing it with EDL, both of which will likely cost money)

After you hear your phone getting reconnected to your PC run:
```cmd
diskpart
```
> Run the following commands in the newly opened window

##### Finding your phone
```cmd
lis dis
```
> This will show all available disks. Find the disk number of your phone and replace it with "$" in the command below

> (it will probably show as 0 B free)
```cmd
sel dis $
```

##### Selecting the ESP partition
```cmd
lis par
```
> This will print out all of the partitions in the selected disk. Check if they match up with your device and replace "$" with the number of the ESP partition (usually 30 or 31)
```cmd
sel par $
```

##### Assign letter Y to ESP
```cmd
assign letter y
```

##### Selecting the Windows partitiom
> Replace "$" in the command below with the number of the Windows partition, usually 31 or 32. If you don't know the number, run "lis par" again
```cmd
sel par $
```

##### Assign letter X to Windows
```cmd
assign letter x
```

##### Exit diskpart
```cmd
exit
```

##### Installing Drivers
> Unpack the driver archive, then open the `OfflineUpdater.cmd` file
>
> Enter the drive letter of `Windows`, which should be X, then press enter

##### Boot back into Windows
> Simply reboot your device.


## Finished!
