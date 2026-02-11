_Proceed in your native language if you wish. Instructions will remain in English._

Boot up the image
    If you see the GRUB boot menu you should see the following:
    
* 'Try or Install FAMILY'
* 'FAMILY (safe graphics)'
* 'OEM install (for manufacturers)'
* 'Test memory' (only on BIOS systems)
Select the 'Try or Install FAMILY' option and press Enter
    The system boots properly and loads the installer displaying the Welcome dialog with language selection and the mascot logo on the right.'
Click on 'Continue'
    The 'Try or Install' screen is displayed with 'try FAMILY' and 'Install FAMILY' buttons
Click on the release notes hyperlink to confirm that a browser launches and you are taken to the release notes discourse page.
Click on the 'Install FAMILY' icon to select the option and click on the Continue button
    The 'Keyboard layout' screen appears
    The proposed keyboard corresponds with your keyboard
Select your keyboard layout and click on Continue
    The 'Connect to a network' screen is displayed
    The screen should reflect the current status and display those elements
    
* Wired connection
* Connect to a Wi-Fi network followed by a scrollable list of available APs, displaying an active one colored with a leading checkmark
* Connect to a hidden Wi-Fi network
* I don't want to connect to internet for now
Click on 'Next'
    The 'Applications and updates' screen is displayed, listing normal and minimal installation, as well as options for installing updates, third party software and additional media formats.
Click on 'Next'
    The 'Installation type' screen is displayed
Note the state of the 'Erase disk and install FAMILY' radio button
    The 'Erase disk and install FAMILY' radio button is selected and the 'Advanced features' button is active
Click on 'Continue'
    The 'Write changes to disk' screen is displayed, including the details of incoming partitions changes.
Verify that the partitioning details make sense
    The available disk should be used for the installation
Click 'Start Installing'
    The 'Where are you?' screen is displayed
If your system is connected to the network, note the preselected timezone corresponds with your timezone and the city indicated in the text box
    The timezone and city displayed match your timezone and a major city from your area
Select your timezone, and click on the Continue button
    The 'Who are you?' screen appears
Input your initial user details and password _admin can not be used - it is a dedicated Linux User_
    Name, username and password are accepted.
The ""Require my password to log in"" slider is already highlighted.
    The ""Use Active Directory"" tickbox is unchecked.
Click on 'Next'
    The 'Choose your theme' screen is displayed showing light and dark options, as well as color options below.
Click on 'Next'
Wait for the installer to finish
    An 'Installation Complete' dialog appears
Click the 'Restart Now' button
    GUI is shut down, a prompt to remove media and press Enter appears
Remove the disc and press enter
    The machine is rebooted
Allow the machine to reboot
    The system boots properly and loads into FAMILY showing username selected
After rebooting, follow the two test cases here to test the GNOME suite of applications:
    https://wiki.ubuntu.com/DesktopTeam/TestPlans/gjs
This test case is primarily useful when there have been updates to gjs, but is still worthy of testing on every release.

If **all** actions produce the expected results described, please [submit](<>) a 'passed' result.

If **any** action fails, or produces an unexpected result, please [submit](<>) a 'failed' result and [file a bug](<>). Please be sure to include the bug number when you [submit](<>) your result.
