Scope of this test is to verify that the system is installed, you can login into it and sshd is up and running. _Proceed in your native language if you wish. Instructions will remain in English_

Boot up the image
Choose the desired language
Select ""Install Ubuntu Server""
Choose the language
Select your location
Configure locales
At configure keyboard page, select NO 
Select the country of the keyboard
Select the keyboard layout
Select hostname ubuntu as default
Insert the name for the new user
Insert the name for the account
Choose a password
Reinsert the password
At encrypt request select NO
Verify or setup the timezone
At partitioning select ""Guided - Use entire disk""
Select disk to partition
At ""Write changes to disks"", verify that everythings is right and select YES
At ""http proxy"" request, leave it blank and press enter
At managing upgrades select ""No automatic updates""
At Software selection, choose ""OpenSSH server"" with arrows, select it with ""space bar"" and confirm with ""Enter""
Select to install Grub in the master boot record
Remove the installation media (CDROM or USB key)
Wait that the system reboot and login
Verify that sshd is running:
    pgrep sshd
    should return the pid of sshd.
    If you can, try to connect to the server from a remote client.
**If all actions produce the expected results listed, please [submit](<>) a 'passed' result. If an action fails, or produces an unexpected result, please [submit](<>) a 'failed' result and [file a bug](<>). Please be sure to include the bug number when you [submit](<>) your result.**
