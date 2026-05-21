
<p><em>Proceed in your native language if you wish. Instructions will remain in English.</em></p>
<dl>


<dt>Boot up the image</dt>
  <dd>If you see the GRUB boot menu you should see the following:</dd>
  <dd>
     <ul>
     <li>'Try or Install FAMILY'</li>
     <li>'FAMILY (safe graphics)'</li>
     <li>'OEM install (for manufacturers)'</li>
     <li>'Test memory' (only on BIOS systems)</li>
     </ul>
  </dd>


<dt>Upon reaching the desktop environment, you should be greeted with the "Choose your language" screen.</dt>
  <dd>Pick your desired language.</dd>


<dt>You should be greeted with a panel where you are prompted to set any of your needed or desired accessibility options.</dt>
  <dd>Click through the options, (Seeing, Hearing, Typing, Pointing and clicking, Zoom) and make sure the drop down options are fully functional.</dd>


<dt>You're greeted with the 'Try or install FAMILY' slide. The 'FAMILY' logo should be on the left hand side.</dt>
  <dd>Select "Install Ubuntu" to continue with the installation process, or "Try Ubuntu" to boot into a live session.</dd>


<dt>You should be greeted with a slide asking you to confirm your keyboard layout.</dt>
  <dd>Feel free to either select your desired layout, or use the auto-detect feature at the bottom.</dd>
<dt>Proceed by clicking "Next"</dt>


<dt>The 'Connect to a network' screen should now be displayed</dt>
<dd>The screen should reflect the current status and display the following options (unless you're in a VM):</dd>
  <dd>
     <ul>
     <li>Wired connection</li>
     <li>Connect to a Wi-Fi network followed by a scrollable list of available APs, displaying an active one colored with a leading checkmark</li>
     <li>Connect to a hidden Wi-Fi network</li>
     <li>I don't want to connect to internet for now</li>
     </ul>
  </dd>
<dd>If you ARE installing in a VM, you should check that the VM automatically has internet access. This is usually via a "wired connection".</dd>
<dd>If you're testing a testcase that requires no internet access, make sure the install medium does not have internet access by configuring it properly in this slide.</dd>
<dt>Click "Next"</dt>


<dt>The 'Applications and updates' screen is displayed, listing normal and minimal installation, as well as options for installing updates, third party software and additional media formats.</dt>
<dd>Select any options pertinent to the testcase - though "Default installation" is normally the desired option.</dd>
<dt>Click "Next"</dt>


  <dd>The 'Installation type' screen is displayed</dd>


<dt>Note the state of the 'Erase disk and install FAMILY' radio button</dt>
    <dd>The 'Erase disk and install FAMILY' radio button is selected and the 'Advanced features' button is active</dd>
    <dt>Click on the 'Advanced features...' button</dt>
    <dd>The 'Advanced Features' dialog is displayed</dd>
<dt>Select 'Erase disk and use ZFS'</dt>
    <dd>'Erase disk and use ZFS' is selected</dd>
<dt>Click on the 'OK' button</dt>
    <dd>The dialog closes and 'ZFS selected' is displayed next to the 'Advanced features...' button</dd>
<dt>Click on the 'Install Now' button</dt>
    <dd>'Write the changes to disks' dialogue appears</dd>
<dt>Click Continue</dt>
<dt>If there is only one hard disk, skip to the 'Where are you?' screen. Otherwise, on the 'Installation type' screen verify that the drive selected on the Select drive list corresponds to the drive on the chart (e.g /dev/sda)</dt>
    <dd>Selected drive is displayed on the chart</dd>
<dt>Verify that the full drive space is allocated</dt>
    <dd>Full drive space is allocated for installation</dd>
<dt>Click on the Next button</dt>


<dt>You should be greeted with the "Set up your account" slide</dt>
  <dd>Put in your desired user details.</dd>


<dt>You should be greeted with the "Select your timezone" slide</dt>
  <dd>If your system is connected to the internet, verify that the timezone that was auto-detected is accurate</dd>
  <dd>Note that, if you're on a VPN, the timezone will be affected by this.</dd>
<dt>Click 'Next'</dt>


<dt>You should be greeted by the "Ready to install" slide.</dt>
<dt>On this slide, the devices to be changed and the partition table is shown to the user.</dt>
  <dd>Check that the devices listed and the partition table listed is accurate and representative of the install options you set earlier in the process.</dd>
<dt>Click 'Next'</dt>


<dt>Allow the machine to reboot</dt>
    <dd>The system boots properly</dd>
    <dd>The system loads into FAMILY showing username selected</dd>
    <dd>Upon login, open a terminal, run the following commands and verify it matches the output</dd>
    <dd><code>$ zfs mount | sort
        bpool/BOOT/ubuntu_UUID        /boot
        rpool/ROOT/ubuntu_UUID        /
        rpool/ROOT/ubuntu_UUID/srv    /srv
        rpool/ROOT/ubuntu_UUID/usr/local  /usr/local
        rpool/ROOT/ubuntu_UUID/var/games  /var/games
        rpool/ROOT/ubuntu_UUID/var/lib/AccountsService  /var/lib/AccountsService
        rpool/ROOT/ubuntu_UUID/var/lib/apt  /var/lib/apt
        rpool/ROOT/ubuntu_UUID/var/lib/dpkg  /var/lib/dpkg
        rpool/ROOT/ubuntu_UUID/var/lib/NetworkManager  /var/lib/NetworkManager
        rpool/ROOT/ubuntu_UUID/var/lib  /var/lib
        rpool/ROOT/ubuntu_UUID/var/log  /var/log
        rpool/ROOT/ubuntu_UUID/var/mail  /var/mail
        rpool/ROOT/ubuntu_UUID/var/snap  /var/snap
        rpool/ROOT/ubuntu_UUID/var/spool  /var/spool
        rpool/ROOT/ubuntu_UUID/var/www  /var/www
        rpool/USERDATA/root_0y7dio      /root
        rpool/USERDATA/u_0y7dio         /home/u
    </code></dd>


</dl>
<p>If <strong>all</strong> actions produce the expected results described,
  please <a href="results#add_result">submit</a> a 'passed' result.</p>
<p>If <strong>any</strong> action fails, or produces an unexpected result,
  please <a href="results#add_result">submit</a> a 'failed' result and <a href="../../buginstructions">file a bug</a>. Please be sure to include
  the bug number when you <a href="results#add_result">submit</a> your
  result.</p>


