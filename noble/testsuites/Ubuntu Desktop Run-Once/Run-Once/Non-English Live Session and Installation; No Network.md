*Proceed in your native language if you wish. Instructions will remain in English.*

Before doing this test, make sure when booting into the live session you've selected a non-english language. You must also make sure the machine you're installing on has no internet access.
Boot up the image
   If you see the GRUB boot menu you should see the following:
   -   'Try or Install FAMILY'
-   'FAMILY (safe graphics)'
-   'OEM install (for manufacturers)'
-   'Test memory' (only on BIOS systems)
Upon reaching the desktop environment, you should be greeted with the ""Choose your language"" screen.
   Pick your desired language.
Verify that the language you've selected is being used in the live session.
Verify applications and basic functionality work in the live session, then click the install icon.
   You should also disable network access here.
You should be greeted with a panel where you are prompted to set any of your needed or desired accessibility options.
   Click through the options, (Seeing, Hearing, Typing, Pointing and clicking, Zoom) and make sure the drop down options are fully functional.
You're greeted with the 'Try or install FAMILY' slide. The 'FAMILY' logo should be on the left hand side.
   Select ""Install Ubuntu"" to continue with the installation process, or ""Try Ubuntu"" to boot into a live session.
Click on the 'Try FAMILY' icon to select the option and click on the 'Continue' button
   The default desktop is displayed
Test-case Live Session Usage

Use and execute the default applications found for the desktop environment being run
   All applications should function without error

Ensure that the live session is localised with the right language you previously selected.
Click the installer icon to now continue with the installation
Upon reaching the desktop environment, you should be greeted with the ""Choose your language"" screen.
   Pick your desired language.
Ensure the installer is still in the selected language.
You should be greeted with a panel where you are prompted to set any of your needed or desired accessibility options.
   Click through the options, (Seeing, Hearing, Typing, Pointing and clicking, Zoom) and make sure the drop down options are fully functional.
You're greeted with the 'Try or install FAMILY' slide. The 'FAMILY' logo should be on the left hand side.
   Select ""Install Ubuntu"" to continue with the installation process, or ""Try Ubuntu"" to boot into a live session.
You should be greeted with a slide asking you to confirm your keyboard layout.
   Feel free to either select your desired layout, or use the auto-detect feature at the bottom.
Proceed by clicking ""Next""
In the following slide, ensure you disable network connectivity - it should've been done already.
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
Select ""Erase disk and install ubuntu""
Click 'Next'
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
Ensure after rebooting, that the installed desktop is still in the correct language with all translations being accurate and complete.

If **all** actions produce the expected results described, please submit a 'passed' result.

If **any** action fails, or produces an unexpected result, please submit a 'failed' result and file a bug. Please be sure to include the bug number when you submit your result.