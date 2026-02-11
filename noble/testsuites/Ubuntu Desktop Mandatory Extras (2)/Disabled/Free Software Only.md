_Proceed in your native language if you wish. Instructions will remain in English_

Boot up the image. When you see the aubergine screen with an icon at the bottom, press any key to get the menu
    Language list will appear
Use arrow keys to select language and press Enter
    Language list will close
Press F6 and use the down arrow to get to Free software only and press Enter
    An X will appear by Free software only
Press ESC to dismiss the menu
    Menu window will be dismissed
Select Install FAMILY option and press Enter
    The system boots properly and loads the installer displaying Welcome dialog with language selection
Select language and click continue
    The 'Keyboard Layout' screen appears
    The proposed keyboard corresponds with your keyboard
Select your keyboard layout and click on continue
    The 'Preparing to install FAMILY' window is displayed
On the screen Preparing to install FAMILY, note the availability of the following components
    Available options should represent the state of your system accurately
    

  * (If network is available) Download updates while installing FAMILY
  * (If on a 'laptop') Is plugged to a power source


Click on the continue button
    The 'Installation type' screen is displayed
Note the state of the 'Check Erase Disk and install FAMILY' radio button
    The 'Check Erase Disk and install FAMILY' radio button is selected
Click on the continue button
    The 'Erase Disk and install FAMILY' screen is displayed
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
Input your initial user details and password (Note admin can not be used - it is a dedicated Linux User)
    Name, username and password are accepted. Additionally, the continue button is enabled
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
Login as the user you created, or ensure that you are auto-logged in as the user created during setup if you checked the auto-login option
    The new user's desktop is presented
Open dash and type Terminal into search box. Click on Terminal icon.
    TheTerminal window will appear
Verify that neither the restricted nor multiverse archives have been enabled by typing 
    
    
    grep ""restricted\|multiverse"" /etc/apt/sources.list | grep -v ""^#""

    No result returned (username command prompt line will appear again)
Verify that the linux-restricted-modules package has not been installed by typing 
    
    
    dpkg -l linux-restricted-* |  grep -vE ""^[a-z]n""

    No packages printed (some lines of text will appear, but after +=====etc sequence username command prompt line will appear)
**If all actions produce the expected results listed, please [submit](<>) a 'passed' result. If an action fails, or produces an unexpected result, please [submit](<>) a 'failed' result and [file a bug](<>). Please be sure to include the bug number when you [submit](<>) your result.**
