This test case is to be carried out on a Raspberry Pi 2 4GB.

Follow the installation steps at IoT installation media

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
Click the power icon at the top right of the screen, select Settings from the menu that appears, then ""About"" in the left panel of the window that appears
   Reported ""Memory"" is consistent with a Raspberry Pi 2 4GB. It should be in the region of 1.6-1.8GB.
Check auto-configuration of ethernet

-   Run `ip addr`
-   Check that a valid IP address is recorded on the eth0 interface
-   Check `ping google.com` successfully pings a few times (Ctrl+C to cancel)
   The ""eth0"" interface should have a DHCP assigned IP address and you should be able to ping google.com
Configure wifi via Network Manager

-   Click the power icon at the top right of the screen
-   Select the WiFi entry from the menu and Select Network under that
-   Select your local WiFi network from the scan list
-   Enter the password for your local WiFi network when prompted
-   Wait a few seconds (to allow DHCP to complete), then run `ip addr`
-   Check that a valid IP address is recorded on the wlan0 interface
-   Check `ping google.com` successfully pings a few times (Ctrl+C to cancel)
   The ""wlan0"" interface should have a DHCP assigned IP address and you should be able to ping google.com
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
   Check the video plays smoothly, and that audio is output through the monitor, or speakers / headset plugged into the monitor
Press Super+L and wait for the lock screen to appear, then fade, then for the monitor to suspend. Move the mouse to wake up the monitor, then enter your password to unlock the desktop.
   Ensure the monitor suspends correctly, that it awakens again correctly, and that the desktop unlocks successfully (without the system hanging).

If **all** actions produce the expected results listed, please submit a 'passed' result.

If **any** action fails, or produces an unexpected result, please submit a 'failed' result and file a bug. Please be sure to include the bug number when you submit your result.