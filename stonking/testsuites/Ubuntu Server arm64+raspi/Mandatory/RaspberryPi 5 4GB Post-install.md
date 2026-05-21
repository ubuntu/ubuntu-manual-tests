

  <p>This test case is to be carried out on a Raspberry Pi 5 4GB.</p>
  <p>Follow the installation steps at <a href="https://ubuntu.com/download/iot/installation-media">
    IoT installation media</a>
  </p>
  <dl>


  <dt>
    After powering on the machine, look at the power LED
  </dt>
  <dd>
    The power LED illuminates and stays illuminated while the kernel continues
    to boot. 
  </dd>


  <dt>
    After logging in, run <code>systemctl status</code>, and look at the
    "State:" reported at the top of the output
  </dt>
  <dd>
    State should be reported as "running". In particular, it should
    <em>not</em> read "degraded".
  </dd>


  <dt>
    Run <code>sudo flash-kernel</code>
  </dt>
  <dd>
    Exit code is clean (0) and no error messages are reported
  </dd>


  <dt>
    Run <code>sudo reboot</code>
  </dt>
  <dd>
    System reboots successfully to a login prompt
  </dd>


  <dt>
    Run <code>sudo shutdown -h now</code>
  </dt>
  <dd>
    System shuts down in a reasonable time (less than a minute)
  </dd>


  <dt>
    (for 25.10, questing, and onwards only)<br>
    Create new boot assets and deliberately corrupt them, ensuring that
    boot fallback operates as expected
      </dt>
      <dd>
    <ul>
      <li>Run <code>sudo flash-kernel</code> to write new boot assets to the
        boot partition</li>
      <li>Run <code>sudo truncate -s 10M /boot/firmware/new/vmlinuz</code> to
        truncate the Linux kernel, corrupting it</li>
      <li>Run <code>sudo reboot</code></li>
      <li>Once the system finally returns to a login prompt, run <code>cat
        /boot/firmware/new/state</code></li>
    </ul>
      </dd>
  <dd>
    Observe three separate reboots: the first should be relatively short and
    causes the pi to enter "tryboot" mode. The second should fail with the
    Linux kernel panicking. The third should be the fallback which should
    then succeed. The final cat command should print "bad" indicating the
    new boot assets were found to be faulty.
  </dd>


  <dt>
    Check output of <code>free -h</code>
  </dt>
  <dd>
    Reported "Mem" under "total" is consistent with a
    Raspberry Pi 5 4GB. It should be in the region of 3.6-3.8GB.
  </dd>


  <dt>
    Perform a large (300-600MB) file copy to USB storage
      </dt>
      <dd>
    <ul>
      <li>Generate a large (500MB) file: <code>dd if=/dev/urandom of=rubbish
        bs=1M count=500</code></li>
      <li>Insert a USB stick (appropriately sized) into a spare USB port</li>
      <li>Make a mount directory: <code>sudo mkdir /mnt/stick</code></li>
      <li>Mount the stick: <code>sudo mount /dev/sda1 /mnt/stick</code>
        (modify mount-point as necessary; check <code>sudo dmesg</code>
        output if unsure)</li>
      <li>Copy the file: <code>sudo cp rubbish /mnt/stick/</code></li>
      <li>Unmount the stick: <code>sudo umount /mnt/stick</code></li>
      <li>Remove the stick from the USB port</li>
      <li>Re-insert the stick into the USB port</li>
      <li>Re-mount the stick: <code>sudo mount /dev/sda1 /mnt/stick</code>
        (again, adjust mount-point as necessary)</li>
      <li>Compare the copied file to that on the stick: <code>cmp rubbish
        /mnt/stick/rubbish</code></li>
    </ul>
      </dd>
  <dd>
    <code>cmp</code> returns 0 and outputs nothing, indicating the files are
    identical
  </dd>


  <dt>
    Connect a USB keyboard to one of the USB2 (black) ports
  </dt>
  <dd>
    Verify that keys typed on the keyboard appear on the console
  </dd>


  <dt>
    Connect a USB keyboard to one of the USB3 (blue) ports
  </dt>
  <dd>
    Verify that keys typed on the keyboard appear on the console
  </dd>


  <dt>
    With an HDMI monitor that supports audio plugged into
    the HDMI0 output, and an available MP3 file:
      </dt>
      <dd>
    <ul>
      <li>Install ffmpeg and amixer with <code>sudo apt install ffmpeg
        alsa-utils</code></li>
      <li>Find the correct card name for the HDMI0 port:
        <code>cat /proc/asound/cards</code> and note the name in [brackets]
        for the HDMI0 port</li>
      <li>Attempt to play your MP3 file with: <code>ffmpeg -i
        <em>music.mp3</em> -f alsa -ar 22050 default:CARD=<em>name</em></code>
        substituting <em>name</em> for the card name found during the
        previous step, and <em>music.mp3</em> for your choice of MP3 file,
         e.g. <code>ffmpeg -i "Jeff Wayne - War of the Worlds.mp3"
        -f alsa -ar 22050 default:CARD=vc4hdmi0</code></li>
      <li>Use <code>Ctrl+C</code> or <code>q</code> to end playback early, if you
        wish</li>
      <li>If you cannot hear anything, first check that the mixer's volume is
        not set too low; run <code>alsamixer</code>, and adjust the volume
        (<code>J</code> for down, <code>K</code> for up) before exiting
        (<code>Esc</code>) and retrying playback</li>
    </ul>
      </dd>
  <dd>Audio can be heard through the device</dd>


  <dt>
    With an HDMI monitor that supports audio plugged into
    the HDMI1 output, and an available MP3 file:
      </dt>
      <dd>
    <ul>
      <li>Install ffmpeg and amixer with <code>sudo apt install ffmpeg
        alsa-utils</code></li>
      <li>Find the correct card name for the HDMI1 port:
        <code>cat /proc/asound/cards</code> and note the name in [brackets]
        for the HDMI1 port</li>
      <li>Attempt to play your MP3 file with: <code>ffmpeg -i
        <em>music.mp3</em> -f alsa -ar 22050 default:CARD=<em>name</em></code>
        substituting <em>name</em> for the card name found during the
        previous step, and <em>music.mp3</em> for your choice of MP3 file,
         e.g. <code>ffmpeg -i "Jeff Wayne - War of the Worlds.mp3"
        -f alsa -ar 22050 default:CARD=vc4hdmi0</code></li>
      <li>Use <code>Ctrl+C</code> or <code>q</code> to end playback early, if you
        wish</li>
      <li>If you cannot hear anything, first check that the mixer's volume is
        not set too low; run <code>alsamixer</code>, and adjust the volume
        (<code>J</code> for down, <code>K</code> for up) before exiting
        (<code>Esc</code>) and retrying playback</li>
    </ul>
      </dd>
  <dd>Audio can be heard through the device</dd>


  <dt>
    Check auto-configuration of ethernet
      </dt>
      <dd>
    <ul>
      <li>Run <code>ip addr</code></li>
      <li>Check that a valid IP address is recorded on the eth0 interface</li>
      <li>Check <code>ping google.com</code> successfully pings a few times
        (<code>Ctrl+C</code> to cancel)</li>
    </ul>
      </dd>
  <dd>
    The "eth0" interface should have a DHCP
    assigned IP address and you should be able to ping google.com
  </dd>


  <dt>
    Configure wifi via netplan
      </dt>
      <dd>
    <ul>
      <li>Place the following in <code>/etc/netplan/wifi.yaml</code>
      (substituting the SSID and password as necessary):</li>
      <li><pre>
    network:
      version: 2
        wifis:
          wlan0:
            dhcp4: true
            access-points:
              my-ssid-here:
                password: my-password-here</pre>
      </li>
      <li>Run <code>sudo netplan apply</code></li>
      <li>Wait a few seconds (to allow DHCP to complete), then run <code>ip
        addr</code></li>
      <li>Check that a valid IP address is recorded on the wlan0 interface</li>
      <li>Check <code>ping google.com</code> successfully pings a few times
        (<code>Ctrl+C</code> to cancel)</li>
    </ul>
      </dd>
  <dd>
    The "wlan0" interface should have a DHCP
    assigned IP address and you should be able to ping google.com
  </dd>


  <dt>
    Configure bluetooth, scan for, and pair, a device
      </dt>
      <dd>
    <ul>
      <li>Install bluez with <code>sudo apt install bluez</code></li>
      <li>Run <code>sudo bluetoothctl</code></li>
      <li>Check bluetoothctl prints <code>Agent registered</code></li>
      <li>Check the MAC address looks "real" (not some obviously blank
        value like AA:AA:AA:AA:AA:AA)</li>
      <li>Run <code>scan on</code></li>
      <li>Make some other Bluetooth device visible for pairing (e.g. go into
        Bluetooth settings on your Android phone)</li>
      <li>Verify the other Bluetooth device appears in console output</li>
        <li>Run <code>pair XX:XX:XX:XX:XX:XX</code>
        where XX:XX:XX:XX:XX:XX is the other device's MAC address, as it
        appears in scan output
      </li>
      <li>Verify the passcode on both devices</li>
      <li>Check output includes "Pairing successful"</li>
      <li>Disable scanning with <code>scan off</code></li>
      <li>Exit tool with <code>quit</code></li>
    </ul>
      </dd>
  <dd>
    The Bluetooth interface should have a valid MAC address (not
    AA:AA:AA:AA:AA:AA), can see and pair with another Bluetooth device.
  </dd>


  <dt>
    Check the CPU clock speed using <code>vcgencmd</code>
      </dt>
      <dd>
    <ul>
      <li>Stress the CPU by doing <code>yes &gt; /dev/null &amp;</code></li>
      <li>Run <code>sudo vcgencmd measure_clock arm</code> after about 5 sec</li>
      <li>Kill the stress process</li>
    </ul>
      </dd>
  <dd>The output should be around 2.4GHz (obtained from online specs)</dd>


  <dt>
    Run <code>sudo vcmailbox 0x00010004 8 8 0 0</code>
  </dt>
  <dd>
    The output should have the board serial number as the 6th integer.
  </dd>


  <dt>
    Test <code>dtmerge</code>
      </dt>
      <dd>
    <ul>
      <li>Copy the live device tree using <code>dtc -I fs -O dtb -o test.dtb /proc/device-tree</code></li>
      <li>Use dtmerge to overclock the SD card. <code>dtmerge test.dtb merged.dtb - sd_overclock=62</code></li>
      <li>Check the contents of the new DTB. <code>dtdiff test.dtb merged.dtb</code></li>
      <li>Delete both test.dtb and merged.dtb</li>
    </ul>
      </dd>
  <dd>
    merged.dtb should have <code>brcm,overclock-50 = 0x3e</code> under the SD card device.
  </dd>


<dt>
  Test <code>dtoverlay</code>
    </dt>
    <dd>
  <ul>
    <li>Run <code>sudo dtoverlay pwm</code></li>
    <li>Run <code>sudo dtoverlay -l</code></li>
  </ul>
    </dd>
<dd>The PWM Overlay should show up as loaded. Remove it by running <code>sudo dtoverlay -r pwm</code></dd>


<dt>
  Test <code>dtparam</code>
    </dt>
    <dd>
  <ul>
    <li>Run <code>sudo dtparam sd_overclock=62</code></li>
    <li>Run <code>sudo dtparam -l</code></li>
  </ul>
    </dd>
<dd>The sd_overclock parameter should show up as set. Remove it by running <code>sudo dtparam -r 0</code></dd>


  <dt>
    Run <code>sudo pinctrl</code>
  </dt>
  <dd>The output should have status of the GPIO pins.</dd>


  <dt>
    Run <code>sudo raspinfo</code>
  </dt>
  <dd>The output should have an information dump about the Pi.</dd>


  </dl>
  <p>If <strong>all</strong> actions produce the expected results listed,
    please <a href="results#add_result">submit</a> a 'passed' result.</p>
  <p>If <strong>any</strong> action fails, or produces an unexpected result,
    please <a href="results#add_result">submit</a> a 'failed' result and <a href="../../buginstructions">file a bug</a>. Please be sure to include
    the bug number when you <a href="results#add_result">submit</a> your
    result.</p>


