*Proceed in your native language if you wish. Instructions will remain in English*

Boot up the image
   The system boots properly
When you see the screen with a solid color with an icon at the bottom, press any key to get the menu
   Language list will appear
Select your language and then press Enter
   The installer menu is displayed
Press F4 and select ‘OEM Install (for manufacturers)’’ and press Enter
   The installer menu is displayed again
Press Enter on the ‘Try FAMILY without installing’ option
   The live session is loaded
Double Click on ‘Install FAMILY’
   The ubiquity installer starts, with a welcome dialog with language selection
Type a series name E.G. ""QATeam""
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
Note the state of the 'Check Erase Disk and install FAMILY' radio button
   The 'Check Erase Disk and install FAMILY' radio button is selected
Click on the continue button
   The 'Erase Disk and install FAMILY' is displayed
Verify that the drive selected on the Select drive list correspond to the drive on the chart (e.g /dev/sda)
   Selected drive is displayed on the chart
Verify that the full drive space is allocated
   Full drive space is allocated for installation
Click on Install Now button
   The 'Where are you?' screen is displayed
If your system is connected to the network, note the preselected timezone correspond with your timezone and the city indicated in the text box
   The timezone and city displayed match your timezone and a city from your area
Select your timezone, and click on the continue button
   The 'Who are you?' screen appears
Input Password
   password is accepted, the series name you typed earlier is visible but cannot be edited. Additionally, the continue button is enabled
Click on the continue button
   The 'Welcome to FAMILY ' slide is displayed
   The slideshow is entirely in your language
Wait for the installer to finish
   An 'Installation Complete' dialog appears
Click the Restart now button
   GUI is shut down, a prompt to remove media and press Enter appears
Remove the disc and press enter
   The machine has been rebooted
Allow the machine to reboot
   The system boots properly and loads into FAMILY
Execute the following command on the command line to install any updates that may be present

sudo apt-get update && sudo apt-get dist-upgrade
   The system updates and installs new packages (if any exist)
Restart the computer
   The system restarts and boots into the FAMILY desktop
Double click the ‘Prepare for shipping to end user’ icon on the desktop
   The OEM config preparation window appears
Enter your oem password and click ok
   The window is closed
Shutdown the machine and remove the install disc. Turn the machine back on
   The system boots into the end-user installer (Note that any case where the user is taken out of a graphical experience should be filed as a bug)
Select a language and click Continue
   The timezone screen is displayed
Select a timezone and click Continue
   Keyboard Layout screen is displayed
Select a keyboard layout and click Continue
   User details screen is displayed
Add end user details and click Continue
   After a wait, the login screen appears
Type in the ‘end users’ username and password and hit enter
   The machine logins successfully
Execute the following command on the command line:

lsb\_release -rd
   Both the description and the release presented matches the version of FAMILY you installed
Execute the following command on the command line:

arch
   Verify the result correctly lists the architecture of the installation you installed. For example, x86\_64 for 64-bit x86 machine.
Execute the following command on the command line:

sudo sfdisk -l
   Verify the partition scheme displayed matches the partition scheme you chose during installation
Execute the following command on the command line:

sudo apt-get update
   Apt hits each of the package mirrors and update all of them without error
Launch 'update-manager' (for quantal this is being renamed to software-updater) and install any updates presented
   The updates are downloaded and installed without error
Launch 'firefox' and navigate to http://ubuntu.com
   The Ubuntu homepage is loaded and displays properly
Launch 'Time & Date' settings menu and note the timezone information and local time and date
   The timezone, date and time match the settings you selected during installation
If you installed a non-english version of FAMILY, note the language used on the desktop
   The desktop is localized into your language, or it has prompted you upon initial login to install the missing components for your language

**If all actions produce the expected results listed, please submit a 'passed' result.If an action fails, or produces an unexpected result, please submit a 'failed' result and file a bug. Please be sure to include the bug number when you submit your result.**