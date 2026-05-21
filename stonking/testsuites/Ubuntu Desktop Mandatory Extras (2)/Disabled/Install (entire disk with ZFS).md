
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
    <dd>The system boots properly and loads the installer displaying the Welcome dialog with language selection and 'Try FAMILY' and 'Install FAMILY' buttons</dd>
<dt>Click on the release notes hyperlink to confirm that a browser launches and you are taken to the release notes discourse page.</dt>
<dt>Click on the Install FAMILY button</dt>
    <dd>The 'Keyboard layout' screen appears</dd>
    <dd>The proposed keyboard corresponds with your keyboard</dd>
<dt>Select your keyboard layout and click on Continue</dt>
    <dd>The 'Updates and other software' screen is displayed</dd>
<dt>On the screen 'Updates and other software', note the availability of the following components</dt>
    <dd>Available options should represent the state of your system accurately</dd>
    <dd>
        <ul>
            <li>(If network is available) 'Download updates while installing FAMILY'</li>
            <li>(If on a 'laptop') 'Is plugged to a power source'</li>
            <li>'Install third-party software...' option available</li>
        </ul>
    </dd>
<dt>Click on the Continue button</dt>
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
<dt>If there is only one hard disk, skip to step 18 (On the 'Where are you?' screen...). Otherwise, on the 'Installation type' screen verify that the drive selected on the Select drive list corresponds to the drive on the chart (e.g /dev/sda)</dt>
    <dd>Selected drive is displayed on the chart</dd>
<dt>Verify that the full drive space is allocated</dt>
    <dd>Full drive space is allocated for installation</dd>
<dt>Click on the Install Now button</dt>
    <dd>The 'Where are you?' screen is displayed</dd>


<dt>If your system is connected to the network, note the preselected timezone corresponds with your timezone and the city indicated in the text box</dt>
    <dd>The timezone and city displayed match your timezone and a major city from your area</dd>
<dt>Select your timezone, and click on the Continue button</dt>
    <dd>The 'Who are you?' screen appears</dd>
<dt>Input your initial user details and password <em>admin can not be used - it is a dedicated Linux User</em></dt>
    <dd>'Require my password to log in' is shown and selected or if 'Log in automatically' and 'require my password to log in' are shown then 'Require my password to login' is selected. If just 'Require my password to log in' is shown, having it off is the equivalent of having 'Log in automatically' on.</dd>
    <dd>Name, username and password are accepted.</dd>
    <dd>Continue button becomes available</dd>
<dt>Press Continue</dt>
    <dd>The 'Welcome to FAMILY' slide is displayed</dd>
    <dd>The slideshow is entirely in your language</dd>
<dt>Wait for the installer to finish</dt>
    <dd>An 'Installation Complete' dialog appears</dd>
<dt>Click the 'Restart Now' button</dt>
    <dd>GUI is shut down, a prompt to remove media and press Enter appears</dd>
<dt>Remove the disc and press enter</dt>
    <dd>The machine is rebooted</dd>


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


