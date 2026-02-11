The scope of this test is to ensure that riscv64+pic64gx image boots from SD card on the Microchip PIX64GX1000 Curiosity Kit

Flash the downloaded image onto a microSDXC card
   You can use xz -d to decompress, and then dd to copy the image to the SD card
Connect network
   Connect Ethernet to the RJ45 connector
Connect UART
   Connect with a USB cable to the USB-C socket for the serial console
   The board is powered via the same USB cable if jumper J47 is closed.
Connect to the serial console
   sudo screen /dev/ttyUSB0 115200,cs8,-parenb,-cstopb
   The U-Boot's 'Hit any key to stop autoboot:' message is displayed.
   The board launches GRUB after the count-down.
   You should see GRUB menu
   The default kernel should boot after a delay
   After a while cloud-init will run
   On first boot wait for the 'Cloud-init finished' message.
Login and change password
   Login using ubuntu for both username and password
   Reenter the password again
   Set a new password
   Confirm the new password
Perform generic testing
   Check that apt update works
   Run any command that is not installed, check that command-not-found recommends things to install
   e.g. hello
   Install a package and check that it works, e.g. hello
Perform snap testing
   Install a snap and check that it works, e.g. hello
Reboot
   The board should reboot normally
Poweroff
   Console messages should reach poweroff target
   There should be final kernel powering off message
   Disconnect the USB-C cable to power off the board

**If all actions produce the expected results listed, please submit a 'passed' result. If an action fails, or produces an unexpected result, please submit a 'failed' result and file a bug. Please be sure to include the bug number when you submit your result.**