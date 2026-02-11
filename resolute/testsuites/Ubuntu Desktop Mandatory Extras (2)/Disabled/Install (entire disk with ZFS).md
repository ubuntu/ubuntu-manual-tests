_Proceed in your native language if you wish. Instructions will remain in English._

Boot up the image
    If you see the GRUB boot menu you should see the following:
    
* 'Try or Install FAMILY'
* 'FAMILY (safe graphics)'
* 'OEM install (for manufacturers)'
* 'Test memory' (only on BIOS systems)
    The system boots properly and loads the installer displaying the Welcome dialog with language selection and 'Try FAMILY' and 'Install FAMILY' buttons
Click on the release notes hyperlink to confirm that a browser launches and you are taken to the release notes discourse page.
Click on the Install FAMILY button
    The 'Keyboard layout' screen appears
    The proposed keyboard corresponds with your keyboard
Select your keyboard layout and click on Continue
    The 'Updates and other software' screen is displayed
On the screen 'Updates and other software', note the availability of the following components
    Available options should represent the state of your system accurately
    

  * (If network is available) 'Download updates while installing FAMILY'
  * (If on a 'laptop') 'Is plugged to a power source'
  * 'Install third-party software...' option available


Click on the Continue button
    The 'Installation type' screen is displayed
Note the state of the 'Erase disk and install FAMILY' radio button
    The 'Erase disk and install FAMILY' radio button is selected and the 'Advanced features' button is active
Click on the 'Advanced features...' button
    The 'Advanced Features' dialog is displayed
Select 'Erase disk and use ZFS'
    'Erase disk and use ZFS' is selected
Click on the 'OK' button
    The dialog closes and 'ZFS selected' is displayed next to the 'Advanced features...' button
Click on the 'Install Now' button
    'Write the changes to disks' dialogue appears
Click Continue
If there is only one hard disk, skip to step 18 (On the 'Where are you?' screen...). Otherwise, on the 'Installation type' screen verify that the drive selected on the Select drive list corresponds to the drive on the chart (e.g /dev/sda)
    Selected drive is displayed on the chart
Verify that the full drive space is allocated
    Full drive space is allocated for installation
Click on the Install Now button
    The 'Where are you?' screen is displayed
If your system is connected to the network, note the preselected timezone corresponds with your timezone and the city indicated in the text box
    The timezone and city displayed match your timezone and a major city from your area
Select your timezone, and click on the Continue button
    The 'Who are you?' screen appears
Input your initial user details and password _admin can not be used - it is a dedicated Linux User_
    'Require my password to log in' is shown and selected or if 'Log in automatically' and 'require my password to log in' are shown then 'Require my password to login' is selected. If just 'Require my password to log in' is shown, having it off is the equivalent of having 'Log in automatically' on.
    Name, username and password are accepted.
    Continue button becomes available
Press Continue
    The 'Welcome to FAMILY' slide is displayed
    The slideshow is entirely in your language
Wait for the installer to finish
    An 'Installation Complete' dialog appears
Click the 'Restart Now' button
    GUI is shut down, a prompt to remove media and press Enter appears
Remove the disc and press enter
    The machine is rebooted
Allow the machine to reboot
    The system boots properly
    The system loads into FAMILY showing username selected
    Upon login, open a terminal, run the following commands and verify it matches the output
    `$ zfs mount | sort bpool/BOOT/ubuntu_UUID /boot rpool/ROOT/ubuntu_UUID / rpool/ROOT/ubuntu_UUID/srv /srv rpool/ROOT/ubuntu_UUID/usr/local /usr/local rpool/ROOT/ubuntu_UUID/var/games /var/games rpool/ROOT/ubuntu_UUID/var/lib/AccountsService /var/lib/AccountsService rpool/ROOT/ubuntu_UUID/var/lib/apt /var/lib/apt rpool/ROOT/ubuntu_UUID/var/lib/dpkg /var/lib/dpkg rpool/ROOT/ubuntu_UUID/var/lib/NetworkManager /var/lib/NetworkManager rpool/ROOT/ubuntu_UUID/var/lib /var/lib rpool/ROOT/ubuntu_UUID/var/log /var/log rpool/ROOT/ubuntu_UUID/var/mail /var/mail rpool/ROOT/ubuntu_UUID/var/snap /var/snap rpool/ROOT/ubuntu_UUID/var/spool /var/spool rpool/ROOT/ubuntu_UUID/var/www /var/www rpool/USERDATA/root_0y7dio /root rpool/USERDATA/u_0y7dio /home/u `

If **all** actions produce the expected results described, please [submit](<>) a 'passed' result.

If **any** action fails, or produces an unexpected result, please [submit](<>) a 'failed' result and [file a bug](<>). Please be sure to include the bug number when you [submit](<>) your result.
