_Proceed in your native language if you wish. Instructions will remain in English_

Boot up the image
    The system boots properly and loads the installer displaying Welcome dialog with language selection and 'Try FAMILY' and 'Install FAMILY' buttons
Click on the Install FAMILY icon
    The 'Keyboard Layout' screen appears
    The proposed keyboard corresponds with your keyboard
Select your keyboard layout and click on continue
    The 'Preparing to install FAMILY' screen is displayed
On the screen Preparing to install FAMILY, note the availability of the following components
    Available options should represent the state of your system accurately
    

  * (If network is available) Download updates while installing FAMILY
  * (If on a 'laptop') Is plugged to a power source
  * Install third-party software ... option available


Click on the continue button
    The 'Installation type' screen is displayed
Select Something Else
    A screen showing the current hard disks and partition layouts is displayed
Select the drive you wish to partition and use the 'Add', 'Change', and 'Delete' buttons to create your desired scheme
    The screen updates showing your desired partitions and mount points
Make sure that your scheme also has a separated /home partition included
    You will need the separated /home partition to verify that erasing and reinstalling FAMILY will wipe it out
Once you have you partitioning scheme laid out and are happy click on Install Now
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
Login as the user you created, or ensure that you are auto-logged in as the user created during setup if you checked the auto-login option
    The new user's desktop is presented
Create a new folder on the desktop by right clicking on it and title it 'test', open Firefox and browse to a couple of sites
    Now you have a test folder on the desktop and some browsing history, this will be needed to check if erasing and reinstall of FAMILY will wipe them out 
Reboot using the iso with a CD/DVD or USB Key to a Live Session to perform a reinstall of FAMILY
    The system boots properly and loads the installer displaying Welcome dialog with language selection and 'Try FAMILY' and 'Install FAMILY' buttons
Click on the Install FAMILY icon
    The 'Preparing to install FAMILY' screen is displayed
On the screen Preparing to install FAMILY, note the state of each check mark for the following components
    

  * Your system have at least the amount a space indicated
  * (If on a 'laptop'). Is plugged to a power source
  * Is connected to the Internet


    Check marks represent the state of your system accurately
Click on the continue button
    The 'Installation type' screen is displayed
Select 'Erase FAMILY and Reinstall'
If your system is connected to the network, note the preselected timezone corresponds with your timezone and the city indicated in the text box 
    The timezone and city displayed match your timezone and a city from your area
Click on the continue button
    The 'Keyboard Layout' screen appears
    The proposed keyboard corresponds to your keyboard
Click on continue
    The 'Who are you?' screen appears
Input the same user details as you did on the first install of FAMILY
    Name, username and password are accepted. You should enter the same username as the first install so that the /home partition is re-used. The continue button is enabled
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
Login as the user you created, or ensure that you are auto-logged in as the user created during setup if you checked the auto-login option
    The new user's desktop is presented
Check that the 'test' folder created on the first install has disappeard from the desktop, open Firefox and check that in the history tab has no browsing history, then open a Terminal typing CTRL+ALT+T and type 'df -h' in it without quotes, there should be no /home partition
    You should verify that the /home partition has been wiped out an no previous data has been left back 

**If all actions produce the expected results listed, please[submit](<>) a 'passed' result.  
If an action fails, or produces an unexpected result, please [submit](<>) a 'failed' result and [file a bug](<>). Please be sure to include the bug number when you [submit](<>) your result.**
