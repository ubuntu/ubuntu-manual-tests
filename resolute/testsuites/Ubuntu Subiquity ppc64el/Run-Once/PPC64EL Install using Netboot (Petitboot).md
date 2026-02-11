This testcase is to be carried out on an IBM POWER system (POWER 8 or higher, but cannot be executed on a PowerVM DLPAR). Scope of this testcase is to verify that the system can be installed using a live server image and netbooting from the Petitboot firmware prompt. *Proceed in your native language if you wish. Instructions will remain in English.*

Boot up a system using IPMI, monitor the (sol) console, until the Petitboot menu shows up and select 'Exit to shell'.
   It takes takes a while to boot the OPAL firmware aka embedded Linux up to the Petitboot menu.
   Select 'Exit to shell' in Petitboot promptly before the system times out and proceeds with booting from the default device.
Download the ISO image, usually the one mentioned here in the QA tracker that was requested to be tested, using wget (a proxy server might need to be specified).
   wget http://path/to/image.iso # proxy might be needed: '-e use\_proxy=yes -e http\_proxy=squid.internal:3128'
Loop-back mount the ISO image:
   mkdir iso
   mount -t iso9660 -o loop image.iso iso
Start The installer using kexec
   kexec -l ./iso/casper/vmlinux --initrd=./iso/casper/initrd.gz --append=""ip=dhcp url=http://path/to/image.iso --- quiet""
   kexec -e
The subiquity UI will pop-up after some time, choose your desired language, or confirm the default 'English'.
At the network configuration screen, just select 'Done' (it should be pre-selected).
At the filesystem setup screen, select ""Use An Entire Disk"" (should be pre-selected).
Choose a disk to install to.
At the file system summary screen select Done (should be selected by default).
At the confirmation dialog, select ""Continue"" (should not be selected by default).
Fill out the user information dialog, ideally making sure to import your SSH keys from git or launchpad.
Wait until the installation is completed.
Reboot the system, and monitor the progress via the (sol) console.
Ensure that it's possible to login to the system.
Ensure that you can run commands with sudo.
Check that the correct SSH keys have been imported by SSHing into the machine or looking in ~/.ssh./

**If all actions produce the expected results listed, please submit a 'passed' result. If an action fails, or produces an unexpected result, please submit a 'failed' result and file a bug. Please be sure to include the bug number when you submit your result.**