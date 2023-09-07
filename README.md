# Fix bricked Sv07/Sv07Plus

# What you need:
USB A to USB Type-c cable (Old charging cable might NOT work)
USB memory stick/USB to sd adapter (16gb+)
Basic knowledge about Linux/SSH usage

# Software:
Putty (https://www.putty.org/)
BalenaEtcher (https://etcher.balena.io/)

# Image files:
https://mega.nz/file/LAFgCCQJ#GjC4pgNtD3FL30aAo76nSrlvqs0ib8BT4Od0UDwzabc ( This files is for Sv07Plus and it will work for Sv07 but you gonna need to update printer.cfg)

Let's begin

This text is mainly for Windows users, but the same commands can be used on all operating systems that support SSH.

# Flashing the USB stick
Download the Image file.
Unzip the image file.
Download BalenaEtcher.
Run BalenaEtcher.
Insert USB stick to computer.
Select from file and select the image file.
Select your USB stick.
Press flash and take a break.
Process should finish in a few minutes.
Remove your USB stick from the computer when it's done.

![Screen](https://github.com/TomasOlsson/BrickedSv07-Sv07Plus/blob/main/img/balenaEtcher_phC1PLwiCu.gif?raw=true)


# Prepering the screen

1. Insert the USB Type-C cable into your printer and the USB A end into your computer. Make sure that the printer is powered on. Windows users should hear a sound indicating that the device has been connected. If you do not hear this sound, try using a different cable until you find one that works.

2. Open PuTTY and select Serial as connection type.

    Serial line: COM3 (if not check your Devicemanager)

    Speed: 1500000

    And press Open

   ![Screen](https://github.com/TomasOlsson/BrickedSv07-Sv07Plus/blob/main/img/Screenshot%202023-09-07%20125846.png?raw=true)

4. An black window will pop up if you press enter you will be prompted to enter login

    Username: `mks`

    Password: `makerbase`

![Screen](https://github.com/TomasOlsson/BrickedSv07-Sv07Plus/blob/main/img/putty_Z96vKxGe1Y.gif?raw=true)

5. Login as root
    `sudo su`

    Enter `makerbase` as password.

    Press enter

6. Kill the eMMC with `dd if=/dev/null of=/dev/mmcblk1 status=progress` (It’s just writing over it not killing it :P)

7. Insert the USB stick in the right corner of the printer screen. 

8. Write `reboot` into PuTTY when you're done.

9. If you get the “Your languages”- screen. Do steps 1 to 4 and go to step 9 when you're logged in. And DO NOT set up your printer yet. 

10. Time to move all the things on the USB stick to you eMMC

    1. Check what's you USB sticks called: write lsblk and press enter

    2. It will be called sd* ex: sda or sdb

    3. Use this command when you have located USB stick name (Change /dev/sda to the right one by changing the last part): `dd if=/dev/sda of=/dev/mmcblk1 status=progress`

    4. Press enter and take a shower, make some dinner or walk your fish - this will take some time 🙂

    5. When it's done, remove the USB stick from the screen and pull the power cord.

    6. Put the power cord in and enjoy printing again.
