This test case is to be carried out on a Raspberry Pi 5 8GB.

Follow the installation steps at IoT installation media, and write the image to an SD card. Then, using sudo rpi-eeprom-config, ensure the EEPROM's BOOT\_ORDER is set to 0xf1.

Watch the power LED
   Ensure it turns on at boot time, and stays lit as the kernel starts (when the rainbow screen disappears)
Watch the boot screen
   Check that the Ubuntu logo, and spinner appear during boot time
Ensure you have speakers on your monitor or headphones plugged into it
   Check that the Ubuntu start up sound plays through the monitor's audio output before the initial System Configuration appears
Select your timezone, and click on the Continue button
   The 'Who are you?' screen appears
Input your initial user details and password *admin* can not be used - it is a dedicated Linux User
   Name, username and password are accepted. Login options and home folder encryption choices shown
   Continue button becomes available
Run `sudo flash-kernel`
   Exit code is clean (0) and no error messages are reported
Click the power icon at the top right of the screen, and expand the ""Power Off / Log Out"" entry in the menu that appears, then ""Restart..."" from that menu, and confirm ""Restart"" in the dialog that appears
   System reboots successfully to a login prompt
Click the power icon at the top right of the screen, and expand the ""Power Off / Log Out"" entry in the menu that appears, then ""Power Off..."" from that menu, and confirm ""Power Off"" in the dialog that appears
   System shuts down in a reasonable time (less than a minute)
(for 25.10, questing, and onwards only)  
Create new boot assets and deliberately corrupt them, ensuring that boot fallback operates as expected

-   Run `sudo flash-kernel` to write new boot assets to the boot partition
-   Run `sudo truncate -s 10M /boot/firmware/new/vmlinuz` to truncate the Linux kernel, corrupting it
-   Run `sudo reboot`
-   Once the system finally returns to a login prompt, run `cat /boot/firmware/new/state`
   Observe three separate reboots: the first should be relatively short and causes the pi to enter ""tryboot"" mode. The second should fail with the Linux kernel panicking. The third should be the fallback which should then succeed. The final cat command should print ""bad"" indicating the new boot assets were found to be faulty.
Launch Settings from the menu that appears, then ""About"" in the left panel of the window that appears
   Reported ""Memory"" is consistent with a Raspberry Pi 5 8GB. It should be in the region of 7.6-7.8GB.
Check auto-configuration of ethernet

-   Run `ip addr`
-   Check that a valid IP address is recorded on the eth0 interface
-   Check `ping google.com` successfully pings a few times (Ctrl+C to cancel)
   The ""eth0"" interface should have a DHCP assigned IP address and you should be able to ping google.com
Configure wifi via Network Manager

-   Launch settings
-   Select the WiFi entry from the menu
-   Select your local WiFi network from the visible networks list
-   Enter the password for your local WiFi network when prompted
-   Wait a few seconds (to allow DHCP to complete), then run `ip addr`
-   Check that a valid IP address is recorded on the wlan0 interface
-   Disconnect ethernet, if any is plugged in
-   Check `ping google.com` successfully pings a few times (Ctrl+C to cancel)
-   Reconnect ethernet, if it was connected before
   The ""wlan0"" interface should have a DHCP assigned IP address and you should be able to ping google.com
Configure bluetooth and pair a device

-   Launch settings
-   Select the Bluetooth entry from the menu (you must be on this page for the Pi to be ""discoverable"")
-   On another Bluetooth device (e.g. an Android phone) make sure it is ""discoverable"" (e.g. on Android go into Bluetooth settings)
-   Ensure the other device shows up in the ""Devices"" list on the Bluetooth settings page, then select it
-   Confirm the pincode on both devices
-   Ensure the other device now shows as anything other that ""Not Set Up"" in the ""Devices"" list
   The Bluetooth interface can scan for, and pair with, another device
Start Firefox and play a YouTube video

-   Ensure you have functioning speakers / a headset plugged into your monitor
-   Click on the Firefox icon on the left of the screen
-   Navigate to YouTube
-   Select a video (with audio!) to play
   Check the video plays smoothly, and that audio is output through the monitor, or speakers / headset plugged into the monitor
Download and play BigBuckBunny in the built-in video player

-   Ensure you have functioning speakers / a headset plugged into your monitor
-   Start a terminal session
-   Run `wget https://archive.org/download/BigBuckBunny_124/Content/big_buck_bunny_720p_surround.mp4`
-   Once the download has completed, run `totem big_buck_bunny_720p_surround.mp4`
-   The utility may prompt to install codecs; accept the recommendation and install whatever codecs are required
   Check the video plays smoothly, and that audio is output through the monitor, or speakers / headset plugged into the monitor
Press Super+L and wait for the lock screen to appear, then fade, then for the monitor to suspend. Move the mouse to wake up the monitor, then enter your password to unlock the desktop.
   Ensure the monitor suspends correctly, that it awakens again correctly, and that the desktop unlocks successfully (without the system hanging).
Check the CPU clock speed using `vcgencmd`

-   Stress the CPU by doing `yes > /dev/null &`
-   Run `sudo vcgencmd measure_clock arm` after about 5 sec
-   Kill the stress process
   The output should be around 2.4GHz (obtained from online specs)
Run `sudo vcmailbox 0x00010004 8 8 0 0`
   The output should have the board serial number as the 6th integer.
Test `dtmerge`

-   Copy the live device tree using `dtc -I fs -O dtb -o test.dtb /proc/device-tree`
-   Use dtmerge to overclock the SD card. `dtmerge test.dtb merged.dtb - sd_overclock=62`
-   Check the contents of the new DTB. `dtdiff test.dtb merged.dtb`
-   Delete both test.dtb and merged.dtb
   merged.dtb should have `brcm,overclock-50 = 0x3e` under the SD card device.
Test `dtoverlay`

-   Run `sudo dtoverlay pwm`
-   Run `sudo dtoverlay -l`
   The PWM Overlay should show up as loaded. Remove it by running `sudo dtoverlay -r pwm`
Test `dtparam`

-   Run `sudo dtparam sd_overclock=62`
-   Run `sudo dtparam -l`
   The sd\_overclock parameter should show up as set. Remove it by running `sudo dtparam -r 0`
Run `sudo pinctrl`
   THe output should have status of the GPIO pins.
Run `sudo raspinfo`
   The output should have an information dump about the Pi.

If **all** actions produce the expected results listed, please submit a 'passed' result.

If **any** action fails, or produces an unexpected result, please submit a 'failed' result and file a bug. Please be sure to include the bug number when you submit your result.