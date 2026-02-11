_Proceed in your native language if you wish. Instructions will remain in English._

Boot up the image
    If you see the GRUB boot menu you should see the following:
    
* 'Try or Install FAMILY'
* 'FAMILY (safe graphics)'
* 'OEM install (for manufacturers)'
* 'Test memory' (only on BIOS systems)
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
    
* Wired connection
* Connect to a Wi-Fi network followed by a scrollable list of available APs, displaying an active one colored with a leading checkmark
* Connect to a hidden Wi-Fi network
* I don't want to connect to internet for now
    If you ARE installing in a VM, you should check that the VM automatically has internet access. This is usually via a ""wired connection"".
    If you're testing a testcase that requires no internet access, make sure the install medium does not have internet access by configuring it properly in this slide.
Click ""Next""
The 'Applications and updates' screen is displayed, listing normal and minimal installation, as well as options for installing updates, third party software and additional media formats.
    Select any options pertinent to the testcase - though ""Default installation"" is normally the desired option.
Click ""Next""
    The 'Installation type' screen is displayed
Ensure that your scheme also has a separated /home partition included
    You will need the separated /home partition to verify that erasing and reinstalling FAMILY will wipe it out
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
Allow the machine to reboot
    The system boots properly and loads into FAMILY showing username selected
Login as the user you created, or ensure that you are auto-logged in as the user created during setup if you checked the auto-login option
    The new user's desktop is presented
Create a new folder on the desktop by right clicking on it and title it 'test', open Firefox and browse to a couple of sites
    Now you have a test folder on the desktop and some browsing history, this will be needed to check if erasing and reinstall of FAMILY will wipe them out 
Reboot using the iso with a CD/DVD or USB Key to perform a reinstall of FAMILY
Boot up the image
    If you see the GRUB boot menu you should see the following:
    
* 'Try or Install FAMILY'
* 'FAMILY (safe graphics)'
* 'OEM install (for manufacturers)'
* 'Test memory' (only on BIOS systems)
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
    
* Wired connection
* Connect to a Wi-Fi network followed by a scrollable list of available APs, displaying an active one colored with a leading checkmark
* Connect to a hidden Wi-Fi network
* I don't want to connect to internet for now
    If you ARE installing in a VM, you should check that the VM automatically has internet access. This is usually via a ""wired connection"".
    If you're testing a testcase that requires no internet access, make sure the install medium does not have internet access by configuring it properly in this slide.
Click ""Next""
The 'Applications and updates' screen is displayed, listing normal and minimal installation, as well as options for installing updates, third party software and additional media formats.
    Select any options pertinent to the testcase - though ""Default installation"" is normally the desired option.
Click ""Next""
    The 'Installation type' screen is displayed
Use the same /home partition than in the first installation and ensure the format checkbox is selected
    You will need the separated /home partition to verify that erasing and reinstalling FAMILY will wipe it out
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
Allow the machine to reboot
    The system boots properly and loads into FAMILY showing username selected
Ensure that the test directory is no longer in the ~ directory.

If **all** actions produce the expected results described, please [submit](<>) a 'passed' result.

If **any** action fails, or produces an unexpected result, please [submit](<>) a 'failed' result and [file a bug](<>). Please be sure to include the bug number when you [submit](<>) your result.
