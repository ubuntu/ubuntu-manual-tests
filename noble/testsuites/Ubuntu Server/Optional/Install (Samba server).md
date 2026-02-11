Scope of this test is to verify that the system is installed, you can login into it and samba is running. _Proceed in your native language if you wish. Instructions will remain in English_

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
At Software selection, choose ""Samba server""
Select to install Grub in the master boot record
Remove the installation media (CDROM or USB key)
Wait that the system reboot and login
Verify that samba is running:
    echo smbd ; pgrep smbd; echo; echo nmbd; pgrep nmbd; echo ; echo winbindd; pgrep winbindd ; echo
    should return the pid for pgrep smbd, pgrep nmbd, pgrep winbindd.
Verify the default workgroup name is displayed:
    sudo net getlocalsid
    should return a line similar to sid for domain UBUNTU is S-1-5....
Verify winbind is responding to requests:
    wbinfo -p
    has to return a line similar to ""Ping to winbindd succeeded"".
Verify winbind basic functionality:
    wbinfo --all-domains
    has to return two lines: one with ""BUILTIN"", the other with the unqualified hostname in uppercase. For example, a hostname like ""ubuntu"" would be in the wbinfo output text as ""UBUNTU"".
**If all actions produce the expected results listed, please [submit](<>) a 'passed' result. If an action fails, or produces an unexpected result, please [submit](<>) a 'failed' result and [file a bug](<>). Please be sure to include the bug number when you [submit](<>) your result.**
