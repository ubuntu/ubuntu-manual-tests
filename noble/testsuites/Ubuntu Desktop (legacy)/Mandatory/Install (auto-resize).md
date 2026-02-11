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
Select Install FAMILY XX.XX alongside SYSTEM YY 
    (SYSTEM YY is the name of the system already installed on disk (FAMILY 12.04, Windows 7, ...)
Click on Continue
    The Screen Install FAMILY XX.XX alongside SYSTEM YY appears
Note the drive selected on the Select drive list and the bar state
**If the target drive has a free partition with sufficient freespace, install will proceed without further partitioning intervention**     The drive corresponds to the drive on the chart (e.g /dev/sda) and the bar is divided
Move the greyslider bar that separates the blue sections as appropriate
    The slider bar can be set as appropriate
Click on the Install Now button
A dialog will appear asking if you want to write the changes to disk. Click Continue.
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
Allow the machine to reboot, select the first option at the GRUB menu
    Your new installation boots
Reboot machine, select the previously installed system
    Previously installed system boots and operates as expected

If **all** actions produce the expected results described, please [submit](<>) a 'passed' result.

If **any** action fails, or produces an unexpected result, please [submit](<>) a 'failed' result and [file a bug](<>). Please be sure to include the bug number when you [submit](<>) your result.
