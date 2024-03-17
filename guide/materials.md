<img align="right" src="https://github.com/n00b69/woaberyllium/blob/main/beryllium.png" width="350" alt="Windows 11 running on beryllium">


# Running Windows on the Xiaomi Pocophone F1

## Additional materials
> Below you will find a list of tweaks and materials for Windows on your ARM device

## Hide D drive (modem partition)
> [!NOTE]
> This is recommended because this drive should not be modified, while some applications may try to write to it

- Open a command prompt window and run ```diskpart```
- Run ```list volume``` to see all available volumes
- Select the disk that has letter D with ```select volume $```, replacing "$" with the volume number
- Remove the letter with ```remove letter d```
- Exit diskpart with ```exit```

#### Finished!

## Toggling USB host mode
> [!Warning]
> Disable USB host mode if you use a poweref USB hub, as this can irreversibly damage your device. If you don't use a powered USB hub, enable USB host mode or you will not be able to use any USB devices.

Run [USB Host Control](https://github.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/releases/download/USBHost/USB.Host.Mode.Control.V4.0.vbs) to enable/disable USB host mode, confirm that you want to disable/enable USB host mode and then confirm the reboot

#### Finished!

## Install Microsoft Office / Microsoft 365
- Download this [ISO file](https://mega.nz/file/hjAiSL4T#G7kOKpsUFpyL2UW9RQmY2e96urcQW5xZKdc7ciaNOy8) to the tablet
- Right-click on the iso file and select Mount to open it in explorer
- Double-click on ```Office Tool Plus.exe``` to start the installation wizard
- In the window that appears, click `Yes`
- Wait for the installation to complete

#### Finished!

## Activate Windows / Office
Follow the instructions by Massgravel [here](https://github.com/massgravel/Microsoft-Activation-Scripts)

#### Finished!





















