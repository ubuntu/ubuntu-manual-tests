The scope of this test is to ensure that riscv64+licheerv image boots from SD card on LicheeRV board 

Flash downloaded image onto SD card
    You can use Gnome Disks app to restore img.xz onto the SD card
     Alternatively you can use xz -d to decompress, and then dd to copy the image to the SD card
Connect serial console to the board
    FTDI adapter for serial console (pinout available here: https://popolon.org/depots/RISC-V/D1/LicheeRV/dl.sipeed.com/Lichee_RV_Dock/1_Datasheet/Sipeed%20Lichee%20RV%20DOCK%20Datasheet%20V1.0.pdf)
Connect to the serial console
    sudo screen /dev/ttyUSB0 115200
Power on the board
    You should see U-BOOT menu
    It should then boot GRUB after a delay
    You should see GRUB menu
    It should then boot the default kernel after a delay
    After a while cloud-init will run
    Then one will be able to login
Login and change password
    Login using ubuntu for both username and password
    Reenter ubuntu password again
    Set new password
    Confirm the new password
Install Wifi kernel module
    **This step is only needed when testing releases with Linux kernel up to v6.5.**
    Make sure licheerv-rtl8723ds-dkms is installed, otherwise, install it: 
    $ sudo apt install licheerv-rtl8723ds-dkms 
    It will take quite some time to build, the output of the above command should look like this:.
    Preparing to unpack licheerv-rtl8723ds-dkms 
    Module licheerv-rtl8723ds-1.0 for kernel 5.17.0-1003-allwinner 
    Unpacking licheerv-rtl8723ds-dkms (1.0-0ubuntu1) ... 
    Setting up licheerv-rtl8723ds-dkms (1.0-0ubuntu1) ... 
    Loading new licheerv-rtl8723ds-1.0 DKMS files... 
    Building for 5.17.0-1003-allwinner 
    Building initial module for 5.17.0-1003-allwinner 
    Done.
    8723ds.ko:
    Running module version sanity check.
     \- Original module
     \- No original module exists within this kernel
     \- Installation
     \- Installing to /lib/modules/5.17.0-1003-allwinner/updates/dkms/
    depmod........................
    Load the kernel module with:
    $ sudo modprobe 8723ds
Perform Wifi testing
    You should see a wlan0 interface by typing:
    $ ip a 
    1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group defaul0
     link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
     inet 127.0.0.1/8 scope host lo
     valid_lft forever preferred_lft forever
     inet6 ::1/128 scope host
     valid_lft forever preferred_lft forever
    2: usb0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOW0
     link/ether ae:12:05:64:8e:2c brd ff:ff:ff:ff:ff:ff
    3: wlan0: <BROADCAST,MULTICAST> mtu 1500 qdisc mq state DOWN group default qlen 1000
     link/ether 34:20:03:2a:0d:0c brd ff:ff:ff:ff:ff:ff
    Try to connect to local network by using the following netplan configuration file saved at /etc/netplan/wifi.yaml  

    
    
    network:
      version: 2
      renderer: networkd
      wifis:
        wlan0:
          dhcp4: yes
          dhcp6: yes
          access-points:
            ""YOUR_SSID"":
              password: ""YOUR_PASSWORD""
    

    And then type:
    $ sudo netplan apply 
    You should connect successfully to your local network in a few seconds
Perform generic testing
    Check that apt update works
    Run any command that is not installed, check that command-not-found recommends things to install
    e.g. hello
    Install a package and check that it works, e.g. hello
Perform snap testing
    Install a snap and check that it works, e.g. hello
Perform HDMI testing
    Plug an HDMI cable and make sure a prompt asking for login appears on the screen
Perform USB test
    Plug a keyboard in and enter the login/password
Reboot
    The board should reboot normally
Poweroff
    Console messages should reach poweroff target
    There should be final kernel dmsg powering off
    Manually turn power-off from the board
**If all actions produce the expected results listed, please [submit](<>) a 'passed' result. If an action fails, or produces an unexpected result, please [submit](<>) a 'failed' result and [file a bug](<>). Please be sure to include the bug number when you [submit](<>) your result.**
