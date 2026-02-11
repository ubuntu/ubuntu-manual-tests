The scope of this test is to ensure that the image boots in UEFI, that the resulting installation can boot in UEFI as well, regardless of network availability and that nVidia proprietary drivers are installed and loaded. *Proceed in your native language if you wish. Instructions will remain in English*

Unplug network cable
   No networking should be available to the system
Boot up the image in UEFI mode with **Secure Boot enabled**
When the installer starts and displays a Welcome dialog select your language in the left column
   Language is selected, all labels are changed to translated versions
Click on the Install FAMILY icon
   The 'Keyboard Layout' screen appears
   The proposed keyboard corresponds with your keyboard
Select your keyboard layout and click on continue
   The 'Preparing to install FAMILY' screen is displayed
On the screen Preparing to install FAMILY, note the availability of the following components
   Available options should represent the state of your system accurately
   -   Download updates while installing FAMILY should be unavailable
-   (If on a 'laptop') Is plugged to a power source
-   Install third-party software ... option available
Check 'Install third-party software...'
   A checkbox 'Configure Secure Boot' with 2 password fields are displayed
Check the checkbox, enter a passphrase and confirm it, then click on the continue button
   The 'Installation type' screen is displayed
Select any installation type and click on the continue button
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
Input your initial user details and password *admin can not be used - it is a dedicated Linux User*
   Name, username and password are accepted. Automatic login option is shown
   Continue button becomes available
Press continue
   The 'Welcome to FAMILY' slide is displayed
   The slideshow is entirely in your language
Wait for the installer to finish
   An 'Installation Complete' dialog appears
Click the Restart now button
   GUI is shut down, a prompt to remove media and press Enter appears
Remove the disc and press enter
   The machine is rebooted
Allow the machine to reboot
   A blue screen titled 'Perform MOK management' is displayed
In the list of commands select 'Enroll MOK'
   The 'Enroll MOK' screen is displayed
Select 'Continue'
   The 'Enroll the key(s)' screen is displayed
Select 'Yes' and enter the password you set in the 'Preparing to install FAMILY' page of the installer
   If the password is correct, the screen 'Perform MOK management' is displayed again
Select 'Reboot' and allow the machine to reboot
   The system boots properly and loads into FAMILY showing username selected at the 'Who are you?' step
Login
   The session starts
Open a terminal, run the following commands and verify their output (the output depends on your hardware)
   `$ nvidia-smi Thu Apr 23 11:40:22 2020 +-----------------------------------------------------------------------------+ | NVIDIA-SMI 440.64 Driver Version: 440.64 CUDA Version: 10.2 | |-------------------------------+----------------------+----------------------+ | GPU Name Persistence-M| Bus-Id Disp.A | Volatile Uncorr. ECC | | Fan Temp Perf Pwr:Usage/Cap| Memory-Usage | GPU-Util Compute M. | |===============================+======================+======================| | 0 GeForce MX150 Off | 00000000:01:00.0 Off | N/A | | N/A 48C P0 N/A / N/A | 0MiB / 2002MiB | 0% Default | +-------------------------------+----------------------+----------------------+ +-----------------------------------------------------------------------------+ | Processes: GPU Memory | | GPU PID Type Process name Usage | |=============================================================================| | No running processes found | +-----------------------------------------------------------------------------+ $ sudo prime-supported yes`
Run 'nvidia-settings'
   Verify that settings are displayed and you can configure the card

**If all actions produce the expected results listed, please submit a 'passed' result. If an action fails, or produces an unexpected result, please submit a 'failed' result and file a bug. Please be sure to include the bug number when you submit your result.**