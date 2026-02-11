This testcase is to be carried out on an IBM z/VM guest (virtual machine). (Notice that the minimal architectural requirement is z13/z13s, starting with Ubuntu Server 20.04, otherwise zEC12/zBC12.) Scope of this testcase is to verify that an Ubuntu Server live image can be installed on an IBM z/VM guest with the help of a 3270 terminal emulator. _Proceed in your native language if you wish. Instructions will remain in English._

Download the live server ISO image to your install server, loopback-mount (or better extract) it there and make it remotely available via ftp.
Connect the z/VM guest that is going to be installed with the help of a 3270 terminal emulator (usually x3270 or c3270).
Transfer the kernel, initrd, parmfile and REXX script, located in the boot folder of the ISO image, to the z/VM guest (either with ftp or with the help of the 3270 terminal emulator file transfer functionality.
Boot up a live server image by executing the ubuntu REXX script from CMS running inside of the z/VM guest.
If the basic network configuration was not specified in the parmfile, the installer will interactively ask about it.
    Start the interactive questionnaire about the basic network configuration and make sure the URL to image (that needs to be specified in addition) is accessible (hence, ideally point to the image located on the install server.)
If the boot-up of the installation system is complete, use a remote ssh installer session to connect to the live installer.
    A temporary installation password can be found at the end of the (3270) console boot log, like:
    |37.487176| cloud-init¬1873|: installer:BpAGSH2HAMY5testcbvZ
The subiquity UI will be displayed after login - choose your desired language, or confirm the default 'English'.
At the 'Zdev setup' screen select a DASD device.
    Alternatively zFCP/SCSI disk storage can be selected - if available.
    Overall it's recommended that DASD, as well as zFCP/SCSI disk storage, is tested. Hence if a second z/VM installation is done, it's recommended to use zFCP/SCSI instead of DASD disk storage that time. Usually two zfcp-host devices need to be selected and enabled. Then all available (usually four) paths must be automatically detected (multipath).
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
**If all actions produce the expected results listed, please [submit](<>) a 'passed' result. If an action fails, or produces an unexpected result, please [submit](<>) a 'failed' result and [file a bug](<>). Please be sure to include the bug number when you [submit](<>) your result.**
