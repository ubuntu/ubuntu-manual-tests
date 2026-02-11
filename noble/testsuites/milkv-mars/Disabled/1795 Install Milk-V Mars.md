The scope of this test is to ensure that riscv64+visionfive2 image boots from SD card on Milk-V Mars board

Flash downloaded image onto SD card
   You can use Gnome Disks app to restore img.xz onto the SD card
   Alternatively you can use xz -d to decompress, and then dd to copy the image to the SD card
Connect networking, serial console to the board
   Ethernet cable for networking
   USB to TTL adapter for serial console (pinout available here: https://milkv.io/docs/mars/getting-started/setup)
Connect to the serial console
   sudo screen /dev/ttyUSB0 115200
Power on the board
   You should see U-BOOT output
   It should then boot GRUB after a delay
   You should see GRUB menu
   It should then boot the default kernel after a delay
   After a while cloud-init will run
   Wait for the 'Cloud-init finished' message
   Then one will be able to login
Login and change password
   Login using ubuntu for both username and password
   Reenter ubuntu password again
   Set new password
   Confirm the new password
Perform generic testing
   Check that apt update works
   Run any command that is not installed, check that command-not-found recommends things to install
   e.g. hello
   Install a package and check that it works, e.g. hello
Reboot
   The board should reboot normally
Poweroff
   Console messages should reach poweroff target
   There should be final kernel dmsg powering off
   Manually turn power-off from the board

**If all actions produce the expected results listed, please submit a 'passed' result. If an action fails, or produces an unexpected result, please submit a 'failed' result and file a bug. Please be sure to include the bug number when you submit your result.**