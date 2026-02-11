*Proceed in your native language if you wish. Instructions will remain in English.*

In this test case, make sure that the machine you're installing on does not have the HW requirements for TPM FDE.
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
For this check, please use a system with no TPM enabled hardware
That's it. If the checkbox isn't available, this testcase has passed.

If **all** actions produce the expected results described, please submit a 'passed' result.

If **any** action fails, or produces an unexpected result, please submit a 'failed' result and file a bug. Please be sure to include the bug number when you submit your result.