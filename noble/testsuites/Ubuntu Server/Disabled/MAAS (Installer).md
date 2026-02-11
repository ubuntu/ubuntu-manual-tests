These testcases test install MAAS from an image or previously installed system. You can also [follow the documentation for help](<>). NOTE, if a Virtualbox is used, in network settings bridged adapter must be enabled, promiscuous mode must be enabled, and you must use the PCnet-FAST III adapater. _Proceed in your native language if you wish. Instructions will remain in English_ Test-case name: maas/maas-001 This test will check that the MAAS server can be installed from packages. 

Please ensure you have the latest Ubuntu development version in a dedicated machine
Please ensure you have full control over the network
Please ensure you have internet access or a local mirror of the Ubuntu archive
Install MAAS, in a terminal type: ""sudo apt-get install maas maas-dhcp maas-dns""
    After some minutes, it shows a dialog with the IP of the MAAS server
Press enter and let it finish the installation
Visit the MAAS interface in your browser http://IP/MAAS
    MAAS interface display a warning telling no admin user has been created
Run ""sudo maas-region-admin createsuperuser"" in your MAAS computer and fill the input fields
    MAAS interface ask your credentials
Fill the input fields and press ""Login""
    Could you login into the MAAS server using the admin account created previously?
    You get a free of warnings index page?
Test-case name: maas/maas-002 This test will check that the MAAS server can be installed from the Ubuntu Server iso. 

Please ensure you have the [latest Ubuntu Server development version](<>) in an iso
Please ensure you have a dedicated machine
Please ensure you have full control over the network
Please ensure you have internet access or a local mirror of the Ubuntu archive
Boot up the iso using a CD/DVD or USB Key
    Language selector boot screen is displayed
Choose your preferred language
    Language is selected and string are translated
In the main boot menu select ""Multiple server install with MAAS""
    Language selector for the installer is displayed
Choose your preferred language
    Location selector is displayed
Select your location
    Keyboard selector is displayed
At configure keyboard page, select NO 
    A list with countries is displayed
Select the country of the keyboard
    A list with keyboard layouts is displayed
Select the keyboard layout
    Installer downloads components and later ask for a hostname
Select hostname ubuntu as default
    A menu asking for listing or creating a new MAAS server is displayed
Select ""Create a new MAAS on this server""
    Name window is displayed
Insert the name for the new user
    User window is displayed
Insert the user for the account
    Password input window is displayed
Choose a password
    Password input window is displayed
Reinsert the password
    A window asking for encrypting the /home partition is displayed
At encrypt request select NO
    Timezone window is displayed
Verify or setup the timezone
    Installer downloads components and later ask for a partition layout
At partitioning select ""Guided - Use entire disk""
    Partition window display the disks available
Select disk to partition
    A confirmation window is displayed
At ""Write changes to disks"", verify that everything is right and select YES
    Installer downloads and installs packages needed to compute next step
At ""http proxy"" request, let it blank and press enter
    Installer asks to activate the ""Automatic updates""
At managing upgrades select ""No automatic updates""
    After some minutes, it shows a dialog with the IP of the MAAS server
Press enter and let it finish the installation
    A grub dialog is displayed
Answer 'Yes' to the 'Install the GRUB boot loader to the master boot record?' question
    A dialog asking for UTC setup is displayed
Select 'Yes' to the 'Is the system clock set to UTC? question
    A final dialog is displayed indicating the installation is complete
Select 'Continue'
    The computer get restarted
After the machine got restarted, wait for the login screen and enter your user credentials
Type ""ifconfig"" and look for the ip assigned to the machine
Visit the MAAS interface in your browser http://IP/MAAS
    MAAS interface display a warning telling no admin user has been created
Run ""sudo maas-region-admin createsuperuser"" in your MAAS computer and fill the input fields
    MAAS interface ask your credentials
Fill the input fields and press ""Login""
    Could you login into the MAAS server using the admin account created during previously?
Run ""sudo maas-region-admin createsuperuser"" in your MAAS computer and fill the input fields
    MAAS interface ask your credentials
Fill the input fields and press ""Login""
    Could you login into the MAAS server using the admin account created previously?
    You get a free of warnings index page?
Test-case name: maas/maas-003 depends: maas/maas-001 depends: maas/maas-002 This test will check that an admin can add a new user to the MAAS server. 

Open the main page to the MAAS server: http://IP/MAAS
Login with the admin account, defined in maas-001 or maas-002
    A web page is loaded which shows 0 as the total number of nodes
Click the settings icon on the right side
    A web page is loaded which shows general information about the MAAS server
Click the 'Add user' button
    A web page is loaded which asks the details of a new user
Fill in the required fields, use 'ubuntuser' as the username
Click the 'Add user' button
    A web page is loaded which shows general information about the MAAS server and the new 'ubuntuser' user
Log out from MAAS, click you admin name (root by default) and select 'logout'
    A web page is loaded which asks for login credentials
Log back in using the username 'ubuntuser' and password created previously
    Did you successfully login into the MAAS server with the user created?
Test-case name: maas/maas-004 depends: maas/maas-001 depends: maas/maas-002 This test will check that an admin can add an admin user to the MAAS server. 

Open the main page to the MAAS server: http://IP/MAAS
Login with the admin account, defined in maas-001 or maas-002
    A web page is loaded which shows 0 as the total number of nodes
Click the settings icon on the right side
    A web page is loaded which shows general information about the MAAS server
Click the 'Add user' button
    A web page is loaded which asks the details of a new user
Fill in the required fields and mark the 'MAAS administrator' field, use 'ubuntuadm' as username
Click the 'Add user' button
    A web page is loaded which shows general information about the MAAS server and the new 'ubuntuadm' user, it must have the word 'yes' in the column of 'MAAS Admin'
Log out from MAAS, click you admin name (root by default) and select 'logout'
    A web page is loaded which asks for login credentials
Log back in using the username 'ubuntuadm' and password created previously
    Did you successfully login into the MAAS server with the admin user created?
Test-case name: maas/maas-005 depends: maas/maas-001 depends: maas/maas-002 depends: maas/maas-003 This test will check that an admin can edit an user account from the MAAS server. 

Open the main page to the MAAS server: http://IP/MAAS
Login with the admin account, defined in maas-001 or maas-002
    A web page is loaded which shows 0 as the total number of nodes
Click the settings icon on the right side
    A web page is loaded which shows general information about the MAAS server
Click on the 'ubuntuser' user
    A web page is loaded which shows general information about 'ubuntuser'
Click the 'Edit user' button
    A web page is loaded which shows input fields with information about 'ubuntuser'
Change the username from 'ubuntuser' to 'ubuser'
Click in the 'Save user' button
    A web page is loaded which shows general information about the MAAS server and the 'ubuser' username is listed instead of 'ubuntuser'
Click on the 'ubuser' user
    A web page is loaded which shows general information about 'ubuser'
Click the 'Edit user' button
    A web page is loaded which shows input fields with information about 'ubuser'
Change the password for the 'ubuser' account
Click in the 'Change password' button
    A web page is loaded which shows general information about the MAAS server and the 'ubuser' username is listed
Click on the 'ubuser' user
    A web page is loaded which shows general information about 'ubuser'
Click the 'Edit user' button
    A web page is loaded which shows input fields with information about 'ubuser'
Mark the 'MAAS administrator' checkbox
Click in the 'Save user' button
    A web page is loaded which shows general information about the MAAS server and the 'ubuser' username is listed as 'MAAS administrator'
Log out from MAAS, click your admin name (root by default) and select 'logout'
    A web page is loaded which asks for login credentials
Log back in using the username 'ubuser' and password edited previously
    Did you successfully login into the MAAS server with the 'ubuser' account?
Test-case name: maas/maas-006 depends: maas/maas-001 depends: maas/maas-002 depends: maas/maas-004 This test will check that an admin can edit an admin account from the MAAS server. 

Open the main page to the MAAS server: http://IP/MAAS
Login with the admin account, defined in maas-001 or maas-002
    A web page is loaded which shows 0 as the total number of nodes
Click the settings icon on the right side
    A web page is loaded which shows general information about the MAAS server
Click on the 'ubuntuadm' user
    A web page is loaded which shows general information about 'ubuntuadm'
Click the 'Edit user' button
    A web page is loaded which shows input fields with information about 'ubuntuser'
Change the username from 'ubuntuadm' to 'ubuadm'
Click in the 'Save user' button
    A web page is loaded which shows general information about the MAAS server and the 'ubuadm' username is listed instead of 'ubuntuadm'
Click on the 'ubuadm' user
    A web page is loaded which shows general information about 'ubuadm'
Click the 'Edit user' button
    A web page is loaded which shows input fields with information about 'ubuadm'
Change the password for the 'ubuadm' account
Click in the 'Change password' button
    A web page is loaded which shows general information about the MAAS server and the 'ubuadm' username is listed
Click on the 'ubuadm' user
    A web page is loaded which shows general information about 'ubuadm'
Click the 'Edit user' button
    A web page is loaded which shows input fields with information about 'ubuadm'
Unmark the 'MAAS administrator' checkbox
Click in the 'Save user' button
    A web page is loaded which shows general information about the MAAS server and the 'ubuadm' username is listed as normal user
Log out from MAAS, click your admin name (root by default) and select 'logout'
    A web page is loaded which asks for login credentials
Log back in using the username 'ubuadm' and password edited previously
    Did you successfully login into the MAAS server with the 'ubuadm' account?
Test-case name: maas/maas-007 depends: maas/maas-001 depends: maas/maas-002 depends: maas/maas-004 depends: maas/maas-006 This test will check that an user can't edit nor delete any account from the MAAS server. 

Open the main page to the MAAS server: http://IP/MAAS
Login with the username 'ubuadm' and password defined in maas-004 and maas-006
    A web page is loaded which shows 0 as the total number of nodes
Go to http://IP/MAAS/settings/
    Do you see a login screen?
Test-case name: maas/maas-008 depends: maas/maas-001 depends: maas/maas-002 depends: maas/maas-003 depends: maas/maas-004 depends: maas/maas-005 depends: maas/maas-006 This test will check that an admin can delete user and admin accounts from the MAAS server. 

Open the main page to the MAAS server: http://IP/MAAS
Login with the admin account, defined in maas-001 or maas-002
    A web page is loaded which shows 0 as the total number of nodes
Click the settings icon on the right side
    A web page is loaded which shows general information about the MAAS server
Click on the 'ubuadm' user
    A web page is loaded which shows general information about 'ubuadm'
Click the 'Delete user' button
    A web page is loaded which asks for confirmation
Click the 'Delete user' button
    A web page is loaded which shows general information about the MAAS server and an announcement about the 'ubuadm' deleted user
Click on the 'ubuser' user
    A web page is loaded which shows general information about 'ubuser'
Click the 'Delete user' button
    A web page is loaded which asks for confirmation
Click the 'Delete user' button
    A web page is loaded which shows general information about the MAAS server and an announcement about the 'ubuser' deleted user
    Did you successfully deleted both accounts?
Test-case name: maas/maas-009 depends: maas/maas-001 depends: maas/maas-002 This test will check that you can do the initial image import 

Open the main page to the MAAS server: http://IP/MAAS
Click the gear or navigate to: http://IP/MAAS/settings
Under cluster controllers, click the ""Import boot images"" button
    A message displayed the import of boot images should appear
    This will download boot images, which will take some time to complete (WARNING: This is an large download, 4+ gb)
    Eventually the images are available
Test-case name: maas/maas-010 depends: maas/maas-009 This test will check that you deploy a node for MAAS 

Please ensure you have the [latest Ubuntu Server development version](<>) in an iso
Boot up the iso using a CD/DVD or USB Key
    Language selector boot screen is displayed
Choose your preferred language
    Language is selected and string are translated
In the main boot menu select ""Multiple server install with MAAS""
    Language selector for the installer is displayed
Choose your preferred language
    Location selector is displayed
Select your location
    Keyboard selector is displayed
At configure keyboard page, select NO 
    A list with countries is displayed
Select the country of the keyboard
    A list with keyboard layouts is displayed
Select the keyboard layout
    Installer downloads components and later ask for a hostname
Select hostname ubuntu as default
    A menu asking for listing or creating a new MAAS server is displayed
Select ""Specify MAAS by name or address ""
    Enter the ip address of the configured MAAS server
Specify hostname box appears
    Leave blank or enter a name
The pc should shut down
Note, if you used virtualbox, please ensure 'network' boot is enabled and is set as the top. For a physical machine, please ensure pxe boot is enabled
    The node should be deployed and eventually shown on the http://IP/MAAS screen. The total nodes in the system should now read 1
Click the nodes link in the menu bar
    Your new node should be displayed
Click the node
    The nodes property page should be displayed
Click accept and commission
    The node should now be available for use
In order to test maas+juju, you should add and prepare additional nodes now using the above steps
     The total nodes in the system should now correspond to the number of added nodes
**If all actions produce the expected results listed, please [submit](<>) a 'passed' result. If an action fails, or produces an unexpected result, please [submit](<>) a 'failed' result and [file a bug](<>). Please be sure to include the bug number when you [submit](<>) your result**. 
