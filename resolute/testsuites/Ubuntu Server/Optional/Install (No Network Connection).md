Scope of this test is to verify that the system is installed and you can login into it. _Proceed in your native language if you wish. Instructions will remain in English_

On a physical server, disconnect the network cable(s); if running KVM, make sure to pass '-net nic,model=virtio -net user,restrict=y' on the Testdrive setting window
Boot up the image
Choose the desired language
Select ""Install Ubuntu Server""
Choose the language
Select your location
Configure locales
At configure keyboard page, select NO 
Select the country of the keyboard
Select the keyboard layout
The installer will fail to acquire a DHCP address. Accept Continue, and then select Do not configure network at this time
Select hostname ubuntu as default
Insert the name for the new user
Insert the name for the account
Choose a password
Reinsert the password
At encrypt request select NO
Setup the timezone
At partitioning select ""Guided - Use entire disk""
Select disk to partition
At ""Write changes to disks"", verify that everythings is right and select YES
At ""http proxy"" request, let it blank and press enter
At managing upgrades select ""No automatic updates""
At Software selection, press ""Enter""
Select to install Grub in the master boot record
Remove the installation media (CDROM or USB key)
Wait that the system reboot
    The system reboot, the login prompt appear and you can login into it
**If all actions produce the expected results listed, please[submit](<>) a 'passed' result. If an action fails, or produces an unexpected result, please [submit](<>) a 'failed' result and [file a bug](<>). Please be sure to include the bug number when you [submit](<>) your result.**
