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
Select 'Something Else' and click 'Continue'
    A screen showing the current hard disks and partition layouts is displayed
Select the drive you wish to partition and use the Add '+', Change 'Change', and Delete '-' buttons to create your desired scheme
    The screen updates showing your desired partitions and mount points
_Make sure that your scheme also includes a separate /home partition_ Once you have your required partitioning scheme laid out, click on 'Next'
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
Open a terminal using your FAMILY commands or GUI to do so, in terminal enter `df -h` and press enter
Terminal echoes the output of the df command
    Check that / and /home use different partitions
Create a file in the /home/$USER/ directory to check for later.
Run the following command to create a file we'll check for later:
    echo ""dummy file"" > /home/$USER/dummy_file
It's important that before rebooting from this first installed system, you must also run:
    sync
Shutdown the installed system.
Put the installation medium back in, and boot into the installation of a new system.
Once you've booted into the second live session, quit the installer, and mount the /home partition. Inspect the contents of the /home partition and ensure the dummy_file is present
    Make sure to unmount the partition once you're done inspecting it.
Now, start the installer and perform the second installation
    Do everything as before, but when you get to the manual partitioning screen, make sure to remove the old '/' partition, create a new one, and make sure the partition used for '/home' has also been selected to have '/home' as the mount point (highlight the existing home partition, and click the 'Change' button), but make sure the reformat check box is left unchecked.
Continue installation as normal, and reboot once finished.
Login, and check the following command runs without any errors:
    cat /home/$USER/dummy_file

If **all** actions produce the expected results described, please [submit](<>) a 'passed' result.

If **any** action fails, or produces an unexpected result, please [submit](<>) a 'failed' result and [file a bug](<>). Please be sure to include the bug number when you [submit](<>) your result.
