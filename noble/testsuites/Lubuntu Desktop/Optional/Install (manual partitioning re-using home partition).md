*Proceed in your native language if you wish. Instructions will remain in English*

Boot up the image
   The system boots properly and loads the installer displaying Welcome dialog with language selection and 'Try FAMILY' and 'Install FAMILY' buttons
Click on the Install FAMILY icon
   The 'Keyboard Layout' screen appears
   The proposed keyboard corresponds with your keyboard
Select your keyboard layout and click on continue
   The 'Preparing to install FAMILY' screen is displayed
On the screen Preparing to install FAMILY, note the availability of the following components
   Available options should represent the state of your system accurately
   -   (If network is available) Download updates while installing FAMILY
-   (If on a 'laptop') Is plugged to a power source
-   Install third-party software ... option available
Click on the continue button
   The 'Installation type' screen is displayed
Select Manual Partitioning
   A screen showing the current hard disks and partition layouts is displayed
Select the drive you wish to partition and use the 'Add', 'Change', and 'Delete' buttons to create your desired scheme
   The screen updates showing your desired partitions and mount points
*Make sure that your scheme also includes a separate /home partition*
Once your partitioning scheme is laid out click on Install Now
   The partitions and disk layouts are created. Then, the 'Where are you?' screen is displayed
If your system is connected to the network, note the preselected timezone correspond with your timezone and the city indicated in the text box
   The timezone and city displayed match your timezone and a city from your area
Click on the continue button
   The 'Who are you?' screen appears
Input your initial user details and password (Note admin can not be used - it is a dedicated Linux User)
   Name, username and password are accepted. Additionally, the continue button is enabled
Click on the continue button
   The 'Welcome to FAMILY ' slide is displayed
Wait for the installer to finish
   An 'Installation Complete' dialog appears
Click the Restart now button
   GUI is shut down, a prompt to remove media and press Enter appears
Remove the disc and press enter
   The machine has been rebooted
Allow the machine to reboot
   The system boots properly and loads into FAMILY
Login as the user you created
   The new user's desktop is presented
Open a terminal using your FAMILY commands or GUI to do so, in terminal enter `df -h` and press enter
   Terminal echoes the output of the df command
Check that / and /home use different partitions
Create a file in the /home/$USER/ directory to check for later.
Run the following command to create a file we'll check for later:
   echo ""dummy file"" > /home/$USER/dummy\_file
Shutdown the installed system.
Put the installation medium back in, and boot into the installation of a new system.
   Do everything as before, but when you get to the manual partitioning screen, make sure to remove the old '/' partition, create a new one, and make sure the partition used for '/home' has also been selected to have '/home' as the mount point (highlight the existing home partition, and click the 'Change' button), but make sure the reformat check box is left unchecked.
Continue installation as normal, and reboot once finished.
Boot into the installed system and check the file you created in the previous install is present in the '/home/' directory
   cat /home/$USER/dummy\_file

**If all actions produce the expected results listed, please submit a 'passed' result.  
If an action fails, or produces an unexpected result, please submit a 'failed' result and file a bug. Please be sure to include the bug number when you submit your result.**