The scope of this test is to ensure that riscv64+unmatched image boots from SD card on SiFive Hifive Unmatched board 

Flash downloaded image onto SD card
    You can use Gnome Disks app to restore img.xz onto the SD card
     Alternatively you can use xz -d to decompress, and then dd to copy the image to the SD card
Connect networking, serial console to the board
    Ethernet cable for networking
    MicroUSB cable for serial console
Check the board switches to ensure they are in sdcard mode
    MSEL2 to the inside of the board, the rest to the outside
Connect to the serial console
    sudo screen /dev/ttyUSB1 115200
Power on the board
    You should see U-BOOT menu
    It should then boot default entry after a delay
    After a while cloud-init will run
    Then serial login will appear, but will not work
    Then cloud-init will finally finish (~250s)
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
Perform snap testing
    Install a snap and check that it works, e.g. hello
Poweroff
    Console messages should reach poweroff target
    There should be final kernel dmsg powering off
    The board should poweroff gracefully
Reboot
    The board should reboot gracefully
**If all actions produce the expected results listed, please [submit](<>) a 'passed' result. If an action fails, or produces an unexpected result, please [submit](<>) a 'failed' result and [file a bug](<>). Please be sure to include the bug number when you [submit](<>) your result.**
