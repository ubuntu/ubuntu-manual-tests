*Proceed in your native language if you wish. Instructions will remain in English.*

Boot up the image
   If you see the GRUB boot menu you should see the following:
   -   'Try or Install FAMILY'
-   'FAMILY (safe graphics)'
-   'OEM install (for manufacturers)'
-   'Test memory' (only on BIOS systems)
Upon reaching the desktop environment, you should be greeted with the ""Choose your language"" screen.
   Pick your desired language.
You should be greeted with a panel where you are prompted to set any of your needed or desired accessibility options.
   Click through the options, (Seeing, Hearing, Typing, Pointing and clicking, Zoom) and make sure the drop down options are fully functional.
You're greeted with the 'Try or install FAMILY' slide. The 'FAMILY' logo should be on the left hand side.
   Select ""Install Ubuntu"" to continue with the installation process, or ""Try Ubuntu"" to boot into a live session.
You should be greeted with a slide asking you to confirm your keyboard layout.
   Feel free to either select your desired layout, or use the auto-detect feature at the bottom.
Proceed by clicking ""Next""
The 'Connect to a network' screen should now be displayed
   The screen should reflect the current status and display the following options (unless you're in a VM):
   -   Wired connection
-   Connect to a Wi-Fi network followed by a scrollable list of available APs, displaying an active one colored with a leading checkmark
-   Connect to a hidden Wi-Fi network
-   I don't want to connect to internet for now
   If you ARE installing in a VM, you should check that the VM automatically has internet access. This is usually via a ""wired connection"".
   If you're testing a testcase that requires no internet access, make sure the install medium does not have internet access by configuring it properly in this slide.
Click ""Next""
The 'Applications and updates' screen is displayed, listing normal and minimal installation, as well as options for installing updates, third party software and additional media formats.
   Select any options pertinent to the testcase - though ""Default installation"" is normally the desired option.
Click ""Next""
   The 'Installation type' screen is displayed
Note the state of the 'Erase disk and install FAMILY' radio button
   The 'Erase disk and install FAMILY' radio button is selected and the 'Advanced features' button is active
Click on the 'Advanced features...' button
   The 'Advanced Features' dialog is displayed
Select 'Use LVM with the new FAMILY installation' and check 'Encrypt the new FAMILY installation for security'
   'Encrypt the new FAMILY Installation for security' and 'Use LVM with the new FAMILY Installation' is checked
Click on the 'OK' button
   The dialog closes and 'LVM and encryption selected' is displayed next to the 'Advanced features...' button
Click on the 'Next' button
   The 'Choose a security key' screen is displayed with the 'Install Now' button greyed out
Enter a security key and type a different key into the 'confirm the security key' input box
   The installer displays 'Passwords do not match'
Enter a security key and type the same key into the 'Confirm the security key' input box
   The passwords are accepted and the 'Next' button can be clicked
Click on the Continue button (if there is only one hard disk in the system, the button should read 'Install Now')
   'Write the changes to disks' dialogue appears
Click Continue
If there is only one hard disk, skip to the 'Where are you?' screen. Otherwise, on the 'Installation type' screen verify that the drive selected on the Select drive list corresponds to the drive on the chart (e.g /dev/sda)
   Selected drive is displayed on the chart
Verify that the full drive space is allocated
   Full drive space is allocated for installation
Click on the Next button
You should be greeted with the ""Set up your account"" slide
   Put in your desired user details.
You should be greeted with the ""Select your timezone"" slide
   If your system is connected to the internet, verify that the timezone that was auto-detected is accurate
   Note that, if you're on a VPN, the timezone will be affected by this.
Click 'Next'
You should be greeted by the ""Ready to install"" slide.
On this slide, the devices to be changed and the partition table is shown to the user.
   Check that the devices listed and the partition table listed is accurate and representative of the install options you set earlier in the process.
Click 'Next'
After you reboot, you should be prompted to enter your security key before getting to the login screen.
Allow the machine to reboot
   The system boots properly and loads into FAMILY showing username selected

If **all** actions produce the expected results described, please submit a 'passed' result.

If **any** action fails, or produces an unexpected result, please submit a 'failed' result and file a bug. Please be sure to include the bug number when you submit your result.