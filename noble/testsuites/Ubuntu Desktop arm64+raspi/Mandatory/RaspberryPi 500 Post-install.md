This test case is to be carried out on a Raspberry Pi 500.

Follow the installation steps at IoT installation media

After powering on the machine, look at the power LED
   The power LED illuminates and stays illuminated while the kernel continues to boot.
After logging in, run `systemctl status`, and look at the ""State:"" reported at the top of the output
   State should be reported as ""running"". In particular, it should *not* read ""degraded"".
Run `sudo flash-kernel`
   Exit code is clean (0) and no error messages are reported
Run `sudo reboot`
   System reboots successfully to a login prompt
Run `sudo shutdown -h now`
   System shuts down in a reasonable time (less than a minute)
Check output of `free -h`
   Reported ""Mem"" under ""total"" is consistent with a Raspberry Pi 500. It should be in the region of 7.6-7.8GB.
Perform a large (300-600MB) file copy to USB storage

-   Generate a large (500MB) file: `dd if=/dev/urandom of=rubbish bs=1M count=500`
-   Insert a USB stick (appropriately sized) into a spare USB port
-   Make a mount directory: `sudo mkdir /mnt/stick`
-   Mount the stick: `sudo mount /dev/sda1 /mnt/stick` (modify mount-point as necessary; check `sudo dmesg` output if unsure)
-   Copy the file: `sudo cp rubbish /mnt/stick/`
-   Unmount the stick: `sudo umount /mnt/stick`
-   Remove the stick from the USB port
-   Re-insert the stick into the USB port
-   Re-mount the stick: `sudo mount /dev/sda1 /mnt/stick` (again, adjust mount-point as necessary)
-   Compare the copied file to that on the stick: `cmp rubbish /mnt/stick/rubbish`
   `cmp` returns 0 and outputs nothing, indicating the files are identical
Connect a USB keyboard to one of the USB2 (black) ports
   Verify that keys typed on the keyboard appear on the console
Connect a USB keyboard to one of the USB3 (blue) ports
   Verify that keys typed on the keyboard appear on the console
With an HDMI monitor that supports audio plugged into the HDMI0 output, and an available MP3 file:

-   Install ffmpeg and amixer with `sudo apt install ffmpeg alsa-utils`
-   Find the correct card name for the HDMI0 port: `cat /proc/asound/cards` and note the name in \[brackets\] for the HDMI0 port
-   Attempt to play your MP3 file with: `ffmpeg -i *music.mp3* -f alsa -ar 22050 default:CARD=*name*` substituting *name* for the card name found during the previous step, and *music.mp3* for your choice of MP3 file, e.g. `ffmpeg -i ""Jeff Wayne - War of the Worlds.mp3"" -f alsa -ar 22050 default:CARD=vc4hdmi0`
-   Use Ctrl+C or q to end playback early, if you wish
-   If you cannot hear anything, first check that the mixer's volume is not set too low; run `alsamixer`, and adjust the volume (J for down, K for up) before exiting (Esc) and retrying playback
   Audio can be heard through the device
With an HDMI monitor that supports audio plugged into the HDMI1 output, and an available MP3 file:

-   Install ffmpeg and amixer with `sudo apt install ffmpeg alsa-utils`
-   Find the correct card name for the HDMI1 port: `cat /proc/asound/cards` and note the name in \[brackets\] for the HDMI1 port
-   Attempt to play your MP3 file with: `ffmpeg -i *music.mp3* -f alsa -ar 22050 default:CARD=*name*` substituting *name* for the card name found during the previous step, and *music.mp3* for your choice of MP3 file, e.g. `ffmpeg -i ""Jeff Wayne - War of the Worlds.mp3"" -f alsa -ar 22050 default:CARD=vc4hdmi0`
-   Use Ctrl+C or q to end playback early, if you wish
-   If you cannot hear anything, first check that the mixer's volume is not set too low; run `alsamixer`, and adjust the volume (J for down, K for up) before exiting (Esc) and retrying playback
   Audio can be heard through the device
Check auto-configuration of ethernet

-   Run `ip addr`
-   Check that a valid IP address is recorded on the eth0 interface
-   Check `ping google.com` successfully pings a few times (Ctrl+C to cancel)
   The ""eth0"" interface should have a DHCP assigned IP address and you should be able to ping google.com
Configure wifi via netplan

-   Place the following in `/etc/netplan/wifi.yaml` (substituting the SSID and password as necessary):
-         network:
            version: 2
              wifis:
                wlan0:
                  dhcp4: true
                  access-points:
                    my-ssid-here:
                      password: my-password-here
    
-   Run `sudo netplan apply`
-   Wait a few seconds (to allow DHCP to complete), then run `ip addr`
-   Check that a valid IP address is recorded on the wlan0 interface
-   Check `ping google.com` successfully pings a few times (Ctrl+C to cancel)
   The ""wlan0"" interface should have a DHCP assigned IP address and you should be able to ping google.com
Configure bluetooth, scan for, and pair, a device

-   Install bluez with `sudo apt install bluez`
-   Run `sudo bluetoothctl`
-   Check bluetoothctl prints `Agent registered`
-   Check the MAC address looks ""real"" (not some obviously blank value like AA:AA:AA:AA:AA:AA)
-   Run `scan on`
-   Make some other Bluetooth device visible for pairing (e.g. go into Bluetooth settings on your Android phone)
-   Verify the other Bluetooth device appears in console output
-   Run `pair XX:XX:XX:XX:XX:XX` where XX:XX:XX:XX:XX:XX is the other device's MAC address, as it appears in scan output
-   Verify the passcode on both devices
-   Check output includes ""Pairing successful""
-   Disable scanning with `scan off`
-   Exit tool with `quit`
   The Bluetooth interface should have a valid MAC address (not AA:AA:AA:AA:AA:AA), can see and pair with another Bluetooth device.

If **all** actions produce the expected results listed, please submit a 'passed' result.

If **any** action fails, or produces an unexpected result, please submit a 'failed' result and file a bug. Please be sure to include the bug number when you submit your result.