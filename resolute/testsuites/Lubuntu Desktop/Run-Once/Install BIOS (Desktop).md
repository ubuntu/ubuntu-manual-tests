The scope of this test is to ensure that the image boots in BIOS and that the resulting installation can boot in BIOS as well, regardless of network availability. _Proceed in your native language if you wish. Instructions will remain in English_

Unplug network cable
    No networking should be available to the system
Boot up the image in BIOS mode
    The system boots properly and loads the installer displaying the Welcome dialog with language selection and 'Try FAMILY' and 'Install FAMILY' buttons
Click on the Install FAMILY icon
    The 'Keyboard Layout' screen appears
    The proposed keyboard corresponds with your keyboard
Select your keyboard layout and click on continue
    The 'Preparing to install FAMILY' screen is displayed
On the screen Preparing to install FAMILY, note the availability of the following components
    Available options should represent the state of your system accurately
    

  * Download updates while installing FAMILY should be blank
  * (If on a 'laptop') Is plugged to a power source
  * Install third-party software ... option available


Click on the continue button
    The 'Installation type' screen is displayed
Select any installation type and click ont he continue button
    Write changes dialogue appears
Click continue
    If there is only one hard disk, the installer skips to the ""Where are you?' screen. Otherwise, the 'Installation type' screen is displayed
If there is only one hard disk, skip to step 10 (On the 'Where are you?' screen...). Otherwise, on the 'Installation type' screen verify that the drive selected on the Select drive list corresponds to the drive on the chart (e.g /dev/sda)
    Selected drive is displayed on the chart
Verify that the full drive space is allocated
    Full drive space is allocated for installation
Click on the Install Now button
    The 'Where are you?' screen is displayed, which should not necessarily match your timezone.
Select your timezone, and click on the continue button
    The 'Who are you?' screen appears
Input your initial user details and password _admin can not be used - it is a dedicated Linux User_
    Name, username and password are accepted. Login options and home folder encryption choices shown
    Continue button becomes available
Press continue
    The 'Welcome to FAMILY ' slide is displayed
    The slideshow is entirely in your language
Wait for the installer to finish
    An 'Installation Complete' dialog appears
Click the Restart now button
    GUI is shut down, a prompt to remove media and press Enter appears
Remove the disc and press enter
    The machine is rebooted
Allow the machine to reboot
    The system boots properly and loads into FAMILY showing username selected at step 14
**If all actions produce the expected results listed, please[submit](<>) a 'passed' result. If an action fails, or produces an unexpected result, please [submit](<>) a 'failed' result and [file a bug](<>). Please be sure to include the bug number when you [submit](<>) your result.**
