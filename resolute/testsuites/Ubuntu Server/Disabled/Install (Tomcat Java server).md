This test will check that the Ubuntu Server system is installed and you can login into it *Proceed in your native language if you wish. Instructions will remain in English*

Boot up the image
   The system boots properly and loads the installer displaying a screen with language selection
Choose the desired language and press ""Enter""
   Ubuntu installer main menu is displayed
Select ""Install Ubuntu Server""
   The 'Select a language' screen is displayed requesting for a language selection to be used for the installation process
Choose the language to be used during the installation process which will also be the default language for the installed system
   The 'Select your location' screen is displayed
Select your location to set your time zone and the system locale
   The 'Configure the keyboard' is displayed requesting to detect the keyboard layout
Select ""No""
   The 'Configure the keyboard' is displayed requesting to select the country of origin for the keyboard of your computer
Choose the correct country of origin for the keyboard
   The 'Configure the keyboard' is displayed requesting to select the layout matching the keyboard of your computer
Choose the correct layout for the keyboard
   The installer starts
   The 'Configure the network' screen is displayed requesting to enter the hostname for the system
Select hostname 'ubuntu' as default
   The 'Set up users and passwords' screen is displayed requesting to define a user account name
Enter your desired user account name
   The 'Set up users and passwords' screen is displayed requesting to define a username for the user account
Enter your desired username
   The 'Set up users and passwords' screen is displayed requesting to define a password for the new user
Enter your desired password
   The 'Set up users and passwords' screen is displayed requesting to re-enter the password for verification
   User account, username and password are accepted
   The 'Set up users and passwords' screen is displayed requesting to encrypt user's home directory
Select ""No""
   The 'Configure the clock' screen is displayed requesting to verify or setup the timezone
Select the correct location in your time zone
   The installer proceeds with the installation and the 'Partition disks' screen is displayed
Select ""Guided - Use entire disk""
   The 'Partition disks' screen is displayed requesting to select the disk to partition
Select the desired disk
   The installer starts the partitioning of the disk and the 'Partition disks' screen is displayed requesting for confirmation before writing the changes to the disk
Verify that everything is right and select ""Yes""
   The installer proceeds with the partitioning of the disk and starts installing the base system
   The 'Configure the package manager' screen is displayed requesting to enter a 'HTTP proxy'
Leave it blank and press ""Enter""
   The installer proceeds with the configuration of the package manager
   The 'Configuration tasksel' screen is displayed requesting to define the upgrades management
Select ""No automatic updates""
   The 'Software selection' screen is displayed requesting to select the software to be installed
Choose ""Tomcat Java server"" using the arrows keys, select it with ""space bar"" and confirm with ""Enter""
   The installer proceeds with the installation of ""Tomcat Java server""
   The 'Install the GRUB boot loader on a hard disk' screen is displayed requesting to install the GRUB boot loader to the master boot record
Select ""Yes"" and wait for the installer to finish
   An 'Installation Complete' screen is displayed
Remove the installation media (CD/DVD or USB key), wait for the reboot of the system
   The system boots properly and loads into login

This test will check that the Tomcat Java server is running correctly.

Login and check Tomcat is running entering `sudo netstat -ltnp | grep java` at the prompt
   It should show a jsvc instance listening on port 8080
Verify that Tomcat is working properly entering `w3m http://127.0.0.1:8080` at the prompt
   A ""It works !"" page should be brought up
Verify that Tomcat is able to properly display the ""Hello World!"" example page, entering `w3m http:localhost:8080/examples/servletsservlet/HelloWorldExample` at the prompt
   A ""Hello World!"" page should be brought up
Verify that Tomcat is able to display a page containing basic arithmetics, entering `w3m http:localhost:8080/examples/jsp/jsp2/el/basic-arithmetic.jsp` at the prompt
   A ""JSP 2.0 Expression Language - Basic Arithmetic"" page should be brought up

**If all actions produce the expected results listed, please submit a 'passed' result. If an action fails, or produces an unexpected result, please submit a 'failed' result and file a bug. Please be sure to include the bug number when you submit your result.**