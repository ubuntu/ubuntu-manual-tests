To execute this test, a pre-existing Ubuntu (or derivative) installation is needed **Upgrade will only be offered as an alternative when there is 1 installed FAMILY system** *Proceed in your native language if you wish. Instructions will remain in English.*

Boot up the image
   The system boots properly and loads the installer displaying Welcome dialog with language selection and 'Try FAMILY' and 'Install FAMILY' buttons
Click on the Install FAMILY button
   The 'Keyboard Layout' screen appears
   The proposed keyboard corresponds with your keyboard
Select your keyboard layout and click on continue
   The 'Preparing to install FAMILY' screen is displayed
On the screen Preparing to install FAMILY, note the availability of the following components
   Available options should represent the state of your system accurately
   -   (If network is available) Download updates while installing FAMILY
-   (If on a 'laptop') Is plugged to a power source
-   Install third-party software ... option available
Check the box 'Download updates while installing' if a network is available
Click on the Continue button
   'Installation type' screen is displayed
Select the 'Upgrade FAMILY' option
Click 'Install Now' button
   'Where are you?' screen is displayed
If connected, verify that your timezone is proposed correctly
Click on the Continue button
   'Who are you?' screen is displayed
Insert all the requested fields and choose if you want autologin or encrypted home
Click on the Continue button
   The 'Welcome to FAMILY' slide is displayed
Wait for the installer to finish
   An 'Installation Complete' dialog appears
Click the Restart now button
   GUI is shut down, a prompt to remove media and press Enter appears
Remove the disc and press enter
   The machine has been rebooted
Allow the machine to reboot
   The system boots properly and loads into the new ubuntu (or derivative name)
Open a Terminal and enter the command `lsb_release -a`
   New version will be shown on the Description line
Open a terminal and enter the command `grep Prompt= /etc/update-manager/release-upgrades`
   Terminal will show Prompt=lts
Verify that your pre-upgrade files and installed applications are still present

**If all actions produce the expected results listed, please submit a 'passed' result. If an action fails, or produces an unexpected result, please submit a 'failed' result and file a bug. Please be sure to include the bug number when you submit your result.**