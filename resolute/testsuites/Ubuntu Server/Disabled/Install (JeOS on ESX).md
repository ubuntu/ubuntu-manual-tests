*Proceed in your native language if you wish. Instructions will remain in English*

Boot the CD on a VMWare-ESX system
Press F4 and select Install a minimal virtual system
Choose your language, country and keyboard layout
Set default hostname: ubuntu
Partition disks: Guided use entire disk
Select your time zone and set the system clock to UTC
User account: enter username and password
No software selection.
Boot the newly created guest
Log in
Check that the uname -r returns a -virtual kernel:
   uname -r
Check that the linux-virtual package is installed for the release or the correct hardware enablement stack:
   dpkg -l | grep linux-virtual
Ping outside network
Check with the mount command that virtual disk are mount read-write
Check that the ubuntu-standard package is not installed:
   dpkg -l ubuntu-standard
Check that the size of the kernel modules is below 40M:
   du -sh /lib/modules/
Check that the size of the installed system is below 800M:
   df -h

**If all actions produce the expected results listed, please submit a 'passed' result. If an action fails, or produces an unexpected result, please submit a 'failed' result and file a bug. Please be sure to include the bug number when you submit your result**.