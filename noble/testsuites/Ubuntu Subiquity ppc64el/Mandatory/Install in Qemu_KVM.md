Scope of this test is to verify that the system is installed and you can login into it. _Proceed in your native language if you wish. Instructions will remain in English_

Boot up the image under KVM
Choose the desired language
On the network configuration screen, just select Done (it should be selected by default)
On the filesystem setup screen, select ""Use An Entire Disk"" (it should be selected by default)
Choose a disk to install to
On the file system summary screen select Done (it should be selected by default)
In the confirmation dialog, select ""Continue"" (it should **not** be selected by default)
Fill out the user information, making sure to import your SSH keys from somewhere
Wait for the install to complete
Remove the installation media (CDROM or USB key)
Reboot the system
Ensure that you can log into the system with the username and password you provided
Ensure that you can run commands with sudo
Check that the correct SSH keys have been imported by SSHing into the machine or looking in ~/.ssh./
**If all actions produce the expected results listed, please [submit](<>) a 'passed' result. If an action fails, or produces an unexpected result, please [submit](<>) a 'failed' result and [file a bug](<>). Please be sure to include the bug number when you [submit](<>) your result.**
