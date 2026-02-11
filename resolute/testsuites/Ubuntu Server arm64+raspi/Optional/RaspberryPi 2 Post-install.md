This test case is to be carried out on a Raspberry Pi 2.

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
(for 25.10, questing, and onwards only)  
Create new boot assets and deliberately corrupt them, ensuring that boot fallback operates as expected

-   Run `sudo flash-kernel` to write new boot assets to the boot partition
-   Run `sudo truncate -s 10M /boot/firmware/new/vmlinuz` to truncate the Linux kernel, corrupting it
-   Run `sudo reboot`
-   Once the system finally returns to a login prompt, run `cat /boot/firmware/new/state`
   Observe three separate reboots: the first should be relatively short and causes the pi to enter ""tryboot"" mode. The second should fail with the Linux kernel panicking. The third should be the fallback which should then succeed. The final cat command should print ""bad"" indicating the new boot assets were found to be faulty.
Check output of `free -h`
   Reported ""Mem"" under ""total"" is consistent with a Raspberry Pi 2. It should be in the region of 800-1000MB.
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
Connect a USB keyboard to one of the USB2 ports
   Verify that keys typed on the keyboard appear on the console
With an HDMI monitor that supports audio, and an available MP3 file:

-   Install ffmpeg and amixer with `sudo apt install ffmpeg alsa-utils`
-   Find the correct card name for the HDMI port: `cat /proc/asound/cards` and note the name in \[brackets\] for the HDMI port
-   Attempt to play your MP3 file with: `ffmpeg -i *music.mp3* -f alsa -ar 22050 default:CARD=*name*` substituting *name* for the card name found during the previous step, and *music.mp3* for your choice of MP3 file, e.g. `ffmpeg -i ""Jeff Wayne - War of the Worlds.mp3"" -f alsa -ar 22050 default:CARD=vc4hdmi0`
-   Use Ctrl+C or q to end playback early, if you wish
-   If you cannot hear anything, first check that the mixer's volume is not set too low; run `alsamixer`, and adjust the volume (J for down, K for up) before exiting (Esc) and retrying playback
   Audio can be heard through the device
With a pair of headphones with a 3.5mm jack, and an available MP3 file:

-   Install ffmpeg and amixer with `sudo apt install ffmpeg alsa-utils`
-   Find the correct card name for the headphone jack: `cat /proc/asound/cards` and note the name in \[brackets\] for the headphone jack
-   Attempt to play your MP3 file with: `ffmpeg -i *music.mp3* -f alsa -ar 22050 default:CARD=*name*` substituting *name* for the card name found during the previous step, and *music.mp3* for your choice of MP3 file, e.g. `ffmpeg -i ""Jeff Wayne - War of the Worlds.mp3"" -f alsa -ar 22050 default:CARD=vc4hdmi0`
-   Use Ctrl+C or q to end playback early, if you wish
-   If you cannot hear anything, first check that the mixer's volume is not set too low; run `alsamixer`, and adjust the volume (J for down, K for up) before exiting (Esc) and retrying playback
   Audio can be heard through the device
Check auto-configuration of ethernet

-   Run `ip addr`
-   Check that a valid IP address is recorded on the eth0 interface
-   Check `ping google.com` successfully pings a few times (Ctrl+C to cancel)
   The ""eth0"" interface should have a DHCP assigned IP address and you should be able to ping google.com

If **all** actions produce the expected results listed, please submit a 'passed' result.

If **any** action fails, or produces an unexpected result, please submit a 'failed' result and file a bug. Please be sure to include the bug number when you submit your result.