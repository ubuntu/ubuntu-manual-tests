Scope of this test is to start a recovery session. _Proceed in your native language if you wish. Instructions will remain in English_

Boot up the image
At the main screen press ESC
Select ""Rescue a broken system""
Choose the desired language
Choose the language
Select your location
Configure locales
At configure keyboard page, select NO 
Select the country of the keyboard
Select the keyboard layout
Select hostname ubuntu as default
Verify or setup the timezone
Choose the device to use as root filesystem
The list of the Rescue operations will be shown:
Execute a shell /dev/sda1 (or what you have choosed as root filesytem)
    Press Enter to proceed into the rescue mode
    Type in standard commands like ls, cd /usr/games/, ls, cp sol sol1, ls
    Ensure that changes have been made and that there is a new file created
    Type Exit and press Enter to return to the menu
Execute a shell in the installer environement
    Type in standard commands like ls, chroot /target, ls chroot /target changes the root to the partition you selected as root filesystem
    Ensure that chroot works and that files are listed in both enviroments
    Type Exit and press Enter to return to the menu
Reinstall GRUB boot loader
    Select Reinstall GRUB boot loader and press Enter. Doing this will remove your Grub config and mbr and place a new automatic version in it's place
    Type in where the boot loader need to be run and press Enter. The default for this will be hd0 or /dev/hda (ide) /dev/sda (scsi)
    From the menu select Reboot the system and press Enter
    Ensure the system boots as expected
Choose a different root file system
    This case requires more than one root partition
    Select Choose a different root file system
    Choose your new root file system and press Enter
    Check the new partition is mounted
**If all actions produce the expected results listed, please [submit](<>) a 'passed' result. If an action fails, or produces an unexpected result, please [submit](<>) a 'failed' result and [file a bug](<>). Please be sure to include the bug number when you [submit](<>) your result.**
