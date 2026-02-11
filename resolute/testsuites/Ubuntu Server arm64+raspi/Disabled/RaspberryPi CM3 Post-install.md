This test case is to be carried out on a Raspberry Pi Compute Module 3.

Follow the installation steps at [ IoT installation media](<>)

Immediately after the ""rainbow"" splash screen, U-Boot starts. Press a key to interrupt the sequence, then type ""boot"" to continue it. 
     Check that the U-Boot prompt (including a two-second wait) appears on the primary monitor connected to the Pi, that the keyboard will interrupt the sequence, and that boot successfully concludes after resumption. 
During the boot sequence, U-Boot starts interacting via serial (GPIO14 and GPIO15, pins 8 and 10 respectively, on the 40-pin GPIO header). Press a key to interrupt the sequence, then type ""boot"" to continue it. 
     Check that the U-Boot prompt (including a two-second wait) appears on the attached serial console, that the keyboard will interrupt the sequence, and that boot successfully concludes after resumption. 
Run `sudo flash-kernel`
     Exit code is clean (0) and no error messages are reported 
Run `sudo reboot`
     System reboots successfully to a login prompt 
Run `sudo shutdown -h now`
     System shuts down in a reasonable time (less than a minute) 
Check output of `free -h`
     Reported ""Mem"" under ""total"" is consistent with a Raspberry Pi Compute Module 3. It should be in the region of 800-1000MB. 
Perform a large (300-600MB) file copy to USB storage 

  * Generate a large (500MB) file: `dd if=/dev/urandom of=rubbish bs=1M count=500`
  * Insert a USB stick (appropriately sized) into a spare USB port
  * Make a mount directory: `sudo mkdir /mnt/stick`
  * Mount the stick: `sudo mount /dev/sda1 /mnt/stick` (modify mount-point as necessary; check `sudo dmesg` output if unsure)
  * Copy the file: `sudo cp rubbish /mnt/stick/`
  * Unmount the stick: `sudo umount /mnt/stick`
  * Remove the stick from the USB port
  * Re-insert the stick into the USB port
  * Re-mount the stick: `sudo mount /dev/sda1 /mnt/stick` (again, adjust mount-point as necessary)
  * Compare the copied file to that on the stick: `cmp rubbish /mnt/stick/rubbish`


     `cmp` returns 0 and outputs nothing indicating the files are identical 
Connect a USB keyboard to one of the USB2 ports 
     Verify that keys typed on the keyboard appear on the console 
With an HDMI monitor that supports audio, and an available MP3 file: 

  * Install mpg321 and amixer with `sudo apt install mpg321 alsa-utils`
  * Find the correct hardware output for the HDMI port: `cat /proc/asound/cards` and note the number at the start of the line for the HDMI port (usually 0 and possibly 1 for any connected monitor(s), and 1 or possibly 2 for the headphone jack)
  * Attempt to play your MP3 file with: `mpg321 -o alsa -a hw:_num_ ,0 _music.mp3_` substituting _num_ for the number found during the previous step, and _music.mp3_ for your choice of MP3 file, e.g. `mpg321 -o alsa -a hw:0,0 ""Jeff Wayne - War of the Worlds.mp3""`
  * Use `Ctrl+C` to end playback early, if you wish
  * If you cannot hear anything, first check that the mixer's volume is not set too low; run `alsamixer`, and adjust the volume (`J` for down, `K` for up) before exiting (`Esc`) and retrying playback


    Audio can be heard through the device

If **all** actions produce the expected results listed, please [submit](<>) a 'passed' result.

If **any** action fails, or produces an unexpected result, please [submit](<>) a 'failed' result and [file a bug](<>). Please be sure to include the bug number when you [submit](<>) your result.
