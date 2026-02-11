The scope of this test is to ensure that riscv64+icicle image boots from SD card on Microchip Polarfire Icicle board 

Flash downloaded image onto SD card
    You can use Gnome Disks app to restore img.xz onto the SD card
     Alternatively you can use xz -d to decompress, and then dd to copy the image to the SD card
Connect networking, serial console to the board
    Ethernet cable for networking (both Ethernet connectors work)
    USB cable for serial console (board layout here: https://www.microchip.com/content/dam/mchp/documents/FPGA/ProductDocuments/UserGuides/microchip_polarfire_soc_fpga_icicle_kit_user_guide_vb.pdf page 6)
Connect to the 'firmware' serial console
    sudo screen /dev/ttyUSB0 115200
Connect to the 'kernel' serial console
    sudo screen /dev/ttyUSB1 115200
Power on the board
    Power cycling is required here. Pressing the reset button while running the preinstalled SDK does return the board into a bootable state
    You should see U-BOOT menu on the firmware console
    It should then boot GRUB after a delay
    You should see GRUB menu
    It should then boot the default kernel after a delay on the kernel serial console
    After a while cloud-init will run
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
Reboot
    The board should reboot normally
Poweroff
    Console messages should reach poweroff target
    There should be final kernel dmsg powering off
    Manually turn power-off from the board
**If all actions produce the expected results listed, please [submit](<>) a 'passed' result. If an action fails, or produces an unexpected result, please [submit](<>) a 'failed' result and [file a bug](<>). Please be sure to include the bug number when you [submit](<>) your result.**
