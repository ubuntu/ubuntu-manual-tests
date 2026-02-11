This testcase is to be carried out on an IBM Z logical partition (LPAR). (Notice that the minimal architectural requirement is z13/z13s, starting with Ubuntu Server 20.04, otherwise zEC12/zBC12.) Scope of this testcase is to verify that an Ubuntu Server live image can be installed on LPAR with the help of the HMC. _Proceed in your native language if you wish. Instructions will remain in English._

Download the live server ISO image to your install server, loopback-mount (or better extract) it there and make it remotely available via ftp.
Boot up a live server image with the help of the 'Load from Removable Media and Server' task of the HMC (Hardware Management Console).
If the basic network configuration was not specified in the parmfile, the installer will interactively ask about it.
    Start the interactive questionnaire about the basic network configuration and make sure that the URL to image, that needs to be specified too, is accessible (hence, ideally point to the image located on the install server).
If the boot-up of the installation system is complete, open the ""Integrated ASCII Console"" or use a remote ssh installer session (recommended) to connect to the live installer.
    A temporary installation password can be found at the end of the ('Operating System Messages') console boot log, like:
    |37.487176| cloud-init¬1873|: installer:BpAGSH2HAMY5testcbvZ
The subiquity UI will be displayed after login - choose your desired language, or confirm the default 'English'.
At the 'Zdev setup' screen select zfcp-host devices (usually two) and enable them (make sure the correct devices for your particular LPAR are used.
    Now all available (usually four) paths must be automatically detected (multipath).
    Alternatively DASD disk storage can be selected - if available.
    Overall it's recommended that zFCP/SCSI, as well as DASD disk storage, is tested. Hence if a second LPAR installation is done, it's recommended to use DASD instead of zFCP/SCSI disk storage that time.
At the network configuration screen, select 'Done' (it should be pre-selected).
At the filesystem setup screen, select ""Use An Entire Disk"" (should be pre-selected).
Choose a disk to install to.
At the file system summary screen select 'Done' (should be pre-selected).
At the confirmation dialog, select 'Continue'.
Fill out the user information dialog, ideally including the import of your SSH keys from launchpad (or github).
Wait until the installation is complete and select 'Reboot'.
You may optionally monitor the (re-)boot progress via the console ('Operating System Messages' HMC task).
Ensure that it's possible to login to the system.
Ensure that you can run commands with sudo (like for example 'sudo apt update').
Ensure that the correct s390x devices were configured (like for example with 'lszdev --online').
Check that the correct SSH keys have been imported by SSHing into the machine or looking at ~/.ssh .
**If all actions produce the expected results listed, please[submit](<>) a 'passed' result. If an action fails, or produces an unexpected result, please [submit](<>) a 'failed' result and [file a bug](<>). Please be sure to include the bug number when you [submit](<>) your result.**
