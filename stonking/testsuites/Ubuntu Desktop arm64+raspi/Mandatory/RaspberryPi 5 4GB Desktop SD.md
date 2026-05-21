

  <p>This test case is to be carried out on a Raspberry Pi 5 4GB.</p>
  <p>Follow the installation steps at <a href="https://ubuntu.com/download/iot/installation-media">
    IoT installation media</a>, and write the image to an SD card.
    Then, using <code>sudo rpi-eeprom-config</code>, ensure the EEPROM's
    <code><a href="https://www.raspberrypi.com/documentation/computers/raspberry-pi.html#BOOT_ORDER">BOOT_ORDER</a></code>
    is set to 0xf1.
  </p>
  <dl>


  <dt>Watch the power LED</dt>
    <dd>
      Ensure it turns on at boot time, and stays lit as the kernel starts
      (when the rainbow screen disappears)
    </dd>


  <dt>Watch the boot screen</dt>
  <dd>Check that the Ubuntu logo, and spinner appear during boot time</dd>


  <dt>
    Ensure you have speakers on your monitor or headphones plugged into it
  </dt>
  <dd>
    Check that the Ubuntu start up sound plays through the monitor's audio
    output before the initial System Configuration appears
  </dd>


  <dt>Select your timezone, and click on the Continue button</dt>
  <dd>The 'Who are you?' screen appears</dd>


  <dt>
    Input your initial user details and password
    <em>admin</em> can not be used - it is a dedicated Linux User
  </dt>
  <dd>
    Name, username and password are accepted. Login options and home folder
    encryption choices shown
  </dd>
  <dd>Continue button becomes available</dd>


  <dt>
    Run <code>sudo flash-kernel</code>
  </dt>
  <dd>
    Exit code is clean (0) and no error messages are reported
  </dd>


  <dt>
    Click the power icon at the top right of the screen, and expand the "Power
    Off / Log Out" entry in the menu that appears, then "Restart..." from that
    menu, and confirm "Restart" in the dialog that appears
  </dt> <dd>
    System reboots successfully to a login prompt
  </dd>


  <dt>
    Click the power icon at the top right of the screen, and expand the "Power
    Off / Log Out" entry in the menu that appears, then "Power Off..." from
    that menu, and confirm "Power Off" in the dialog that appears
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
    Launch Settings from
    the menu that appears, then "About" in the left panel of the window that
    appears
  </dt>
  <dd>
    Reported "Memory" is consistent with a Raspberry Pi 5 4GB.
    It should be in the region of 3.6-3.8GB.
  </dd>

  <!-- include ref="dual-monitor" -->

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
    Configure wifi via Network Manager
      </dt>
      <dd>
    <ul>
      <li>Launch settings</li>
      <li>Select the WiFi entry from the menu</li>
      <li>Select your local WiFi network from the visible networks list</li>
      <li>Enter the password for your local WiFi network when prompted</li>
      <li>Wait a few seconds (to allow DHCP to complete), then run <code>ip
        addr</code></li>
      <li>Check that a valid IP address is recorded on the wlan0 interface</li>
      <li>Disconnect ethernet, if any is plugged in</li>
      <li>Check <code>ping google.com</code> successfully pings a few times
        (<code>Ctrl+C</code> to cancel)</li>
      <li>Reconnect ethernet, if it was connected before</li>
    </ul>
      </dd>
  <dd>
    The "wlan0" interface should have a DHCP
    assigned IP address and you should be able to ping google.com
  </dd>


  <dt>
    Configure bluetooth and pair a device
      </dt>
      <dd>
    <ul>
      <li>Launch settings</li>
      <li>Select the Bluetooth entry from the menu (you must be on this page
        for the Pi to be "discoverable")</li>
      <li>On another Bluetooth device (e.g. an Android phone) make sure it
        is "discoverable" (e.g. on Android go into Bluetooth
        settings)</li>
      <li>Ensure the other device shows up in the "Devices" list
        on the Bluetooth settings page, then select it</li>
      <li>Confirm the pincode on both devices</li>
      <li>Ensure the other device now shows as anything other that "Not
        Set Up" in the "Devices" list</li>
      </ul>
      </dd>
    <dd>
      The Bluetooth interface can scan for, and pair with, another device
    </dd>


  <dt>
    Start Firefox and play a YouTube video
      </dt>
      <dd>
    <ul>
      <li>Ensure you have functioning speakers / a headset plugged into your
        monitor</li>
      <li>Click on the Firefox icon on the left of the screen</li>
      <li>Navigate to <a href="https://youtube.com">YouTube</a></li>
      <li>Select a video (with audio!) to play</li>
    </ul>
      </dd>
  <dd>
    Check the video plays smoothly, and that audio is output through the
    monitor, or speakers / headset plugged into the monitor
  </dd>


  <dt>
    Download and play BigBuckBunny in the built-in video player
      </dt>
      <dd>
    <ul>
      <li>Ensure you have functioning speakers / a headset plugged into your
        monitor</li>
      <li>Start a terminal session</li>
      <li>Run <code>wget https://archive.org/download/BigBuckBunny_124/Content/big_buck_bunny_720p_surround.mp4</code></li>
      <li>Once the download has completed, run <code>totem big_buck_bunny_720p_surround.mp4</code></li>
      <li>The utility may prompt to install codecs; accept the recommendation
        and install whatever codecs are required</li>
    </ul>
      </dd>
  <dd>
    Check the video plays smoothly, and that audio is output through the
    monitor, or speakers / headset plugged into the monitor
  </dd>


  <dt>
    Press <code>Super+L</code> and wait for the lock screen to appear, then
    fade, then for the monitor to suspend. Move the mouse to wake up the
    monitor, then enter your password to unlock the desktop.
  </dt>
  <dd>
    Ensure the monitor suspends correctly, that it awakens again correctly,
    and that the desktop unlocks successfully (without the system hanging).
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
  <dd>THe output should have status of the GPIO pins.</dd>


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


