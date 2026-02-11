The goal of this test case is to check that localization support is functional during the installation, and that language packs are downloaded and installed correctly from the Internet.

Boot up the image. When you see the aubergine screen with an icon at the bottom, press any key to get the menu
   Language list will appear
Use arrow keys to select language and press Enter
   Language list will close.
   The installer is localized from this screen onwards
Boot up the iso using a DVD or USB Key to a Live Session
   The system boots properly and loads the installer displaying Welcome dialog with language selection and 'Try FAMILY' and 'Install FAMILY' buttons
Select the Try FAMILY option
   Confirm after booting to live session that the relevant items are in the correct language, apps like 'Ubuntu Software' will still be referred to as 'Ubuntu Software'.
Click on the Install FAMILY desktop icon
Verify the language selected is the same as selected earlier on
Click Continue
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
Note the state of the 'Erase disk and install FAMILY' radio button
   The 'Erase disk and install FAMILY' radio button is selected
Click on the continue button (if there is only one hard disk in the system, the button should read 'Install now')
   If there is only one hard disk, the installer skips to the ""Where are you?' screen. Otherwise, the 'Installation type' screen is displayed
If there is only one hard disk, skip two steps to selecting the timezone (On the 'Where are you?' screen...). Otherwise, on the 'Installation type' screen verify that the drive selected on the Select drive list corresponds to the drive on the chart (e.g /dev/sda)
   Selected drive is displayed on the chart
Verify that the full drive space is allocated
   Full drive space is allocated for installation
Click on Install Now button
   The 'Where are you?' screen is displayed
If your system is connected to the network, note the preselected timezone correspond with your timezone and the city indicated in the text box
   The timezone and city displayed match your timezone and a city from your area
Select your timezone, and click on the continue button
   The 'Who are you?' screen appears
Input your initial user details and password (Note admin can not be used - it is a dedicated Linux User)
   Name, username and password are accepted. Additionally, the continue button is enabled
Click on the continue button
   The 'Welcome to FAMILY ' slide is displayed
   The installer's slideshow slides are completely localized
Verify that your system is localized
   For any language, the system has to be fully localized. Note: the translation coverage of some languages might not be complete
   The calendar shows the regional settings correctly
Wait for the installer to finish
   An 'Installation Complete' dialog appears
Click the Restart now button
   GUI is shut down, a prompt to remove media and press Enter appears
Remove the disc and press enter
   The machine has been rebooted
Allow the machine to reboot
   The system boots properly and loads into FAMILY

If **all** actions produce the expected results listed, please submit a 'passed' result.

If **any** action fails, or produces an unexpected result, please submit a 'failed' result and file a bug. Please be sure to include the bug number when you submit your result.