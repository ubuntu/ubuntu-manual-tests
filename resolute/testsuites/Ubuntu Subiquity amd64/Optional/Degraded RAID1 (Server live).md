Scope of this test is to verify that a system installed on a degraded raid still boots and allows you to log in. _Proceed in your native language if you wish. Instructions will remain in English_

Boot up the image in UEFI mode in a system or VM with at least two disks attached.
Choose the desired language
On the network configuration screen, just select Done (it should be selected by default)
On the filesystem setup screen, select ""Manual""
Create a partition on two drives. For each drive: 

If it already has partitions, select ""Reformat"" from the menu
Select ""Use As Boot Device"" from the menu - (on the second disk it will say ""Add As Another Boot Device"")
Select ""Add GPT Partition"" from the menu
Leave size blank and select ""Leave unformatted"" for the format
Click Done
Create the RAID device and mount it as /: 

Select the ""Create software RAID (md)"" button
Select the two partitions you created to be part of the RAID (they should be the only available options, unless the machine has more than two disks)
Select create
Select the md0 device and choose ""Format"" from the menu
The default should be to format as ext4 and mount at /. Select Done
The Done button should now be enabled. Select it
In the confirmation dialog, select ""Continue"" (it should **not** be selected by default)
Fill out the user information, making sure to import your SSH keys from somewhere
Wait for the install to complete
Remove the installation media (CDROM or USB key)
Reboot the system
Ensure that you can log into the system with the username and password you provided
Shutdown the system
Remove one of the disks that are part of the RAID
Boot the system
Ensure that you can log into the system
Run `sudo mdadm -D /dev/md0` and verify the presence of a line stating that the ""State"" line reports the RAID is degraded
**If all actions produce the expected results listed, please [submit](<>) a 'passed' result. If an action fails, or produces an unexpected result, please [submit](<>) a 'failed' result and [file a bug](<>). Please be sure to include the bug number when you [submit](<>) your result.**
