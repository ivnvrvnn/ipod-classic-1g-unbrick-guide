# Unbricking iPod Classiс 1G without iTunes
## Files/Tools Needed

- [mks5lboot 64-Bit](files/mks5lboot64.exe) or [mks5lboot 32-Bit](files/mks5lboot32.exe)

- [ipodscsi](files/ipodscsi.exe)

- [Apple Mobile Device USB Driver](files/Drivers.7z) if you don't have installed

- [1st stage restore file](files/WTF.x1223.RELEASE.dfu)

- [2nd stage restore file](files/FIRMWARE.x1241.RELEASE.dfu)

- [Original firmware](files/Firmware-24.9.1.2)

### Notes
>
> [!WARNING]  
> All your data will be erased! Back up now if needed.

### Step 1: Reboot to DFU your iPod
> Hold the menu and the center button for about 8 seconds until you see the Apple logo. Keep
> holding the buttons until the Apple logo disappears.

### Step 2: Open CMD and check whether the device is detected or not
>
> Download **files** and extract the folder somewhere, then open CMD.
>
> It is recommended to keep this window open and use it throughout the entire guide.
>
> Replace `path\to\files` with the actual path to the files folder, for example **C:\files**.

```cmd
cd path\to\files
```

> After this write:

```cmd
mks5lboot64.exe --dfuscan
```
> It should look like this: 
```
mks5lboot Version -170303
> This is free software; see the source for copying conditions.  There is NO
> warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

[INFO] DFU scan:
[INFO] winapi: found \\?\USB#VID_05AC&PID_1241#87020000000001#{B8085869-FEB9-404B-8CB1-1E5C14FA8C54}\0001
[INFO] DFU device state: 2
```

### Step 3: Flashing stage 1 restore file
>
> Replace `path\to\WTF.x1223.RELEASE.dfu` with the actual path to the modded recovery image

```cmd
mks5lboot64.exe --dfusend WTF.x1223.RELEASE.dfu
```

### Step 4: Flashing stage 2 restore file
>
> Replace `path\to\FIRMWARE.x1241.RELEASE.dfu` with the actual path to the modded recovery image

```cmd
mks5lboot64.exe --dfusend FIRMWARE.x1241.RELEASE.dfu
```

After 10-20 seconds, you should see an Apple logo on the screen, and after a couple more seconds a white screen with a stop sign and text Do not disconect at the bbottom. Windows might want to reformat it, click No if it does. Continue to the next step

### Final step: Flashing firmware
>Open explorer, and look for your iPod. It should be in the Removable drives section. Take a note of its drive letter (e.g. X:)
>
> Open CMD and type:

```cmd
ipodscsi.exe X: ipod6g writefirmware -p -r Firmware-24.9.1.2
```

>Your iPod will reboot. You'll see a black screen with an Apple logo, and a progress bar at the bottom. Then it will again, show you another Apple logo for a while, and finally start Apple's firmware.

Congratulations, you've unbricked your iPod without iTunes.
