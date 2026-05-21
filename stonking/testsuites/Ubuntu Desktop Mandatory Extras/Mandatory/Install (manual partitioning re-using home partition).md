
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


    <dt>Select 'Something Else' and click 'Continue'</dt>
      <dd>A screen showing the current hard disks and partition layouts is displayed</dd>
    <dt>Select the drive you wish to partition and use the Add '+', Change 'Change', and Delete '-' buttons to create your desired scheme</dt>
      <dd>The screen updates showing your desired partitions and mount points</dd>
      <dd><em>Make sure that your scheme also includes a separate /home partition</em></dd>
    <dt>Once you have your required partitioning scheme laid out, click on 'Next'</dt>


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
      <dd>The system boots properly and loads into FAMILY showing username selected</dd>


    <dt>Open a terminal using your FAMILY commands or GUI to do so, in terminal enter <code>df -h</code> and press enter</dt>
		<dt>Terminal echoes the output of the df command</dt>
      <dd>Check that / and /home use different partitions</dd>


    <dt>Create a file in the /home/$USER/ directory to check for later.</dt>
    <dt>Run the following command to create a file we'll check for later:</dt>
      <dd>echo "dummy file" &gt; /home/$USER/dummy_file</dd>
    <dt>It's important that before rebooting from this first installed system, you must also run:</dt>
      <dd>sync</dd>


    <dt>Shutdown the installed system.</dt>
    <dt>Put the installation medium back in, and boot into the installation of a new system.</dt>
    <dt>Once you've booted into the second live session, quit the installer, and mount the /home partition. Inspect the contents of the /home partition and ensure the dummy_file is present</dt>
      <dd>Make sure to unmount the partition once you're done inspecting it.</dd>
    <dt>Now, start the installer and perform the second installation</dt>
      <dd>Do everything as before, but when you get to the manual partitioning screen, make sure to remove the old '/' partition, create a new one, and make sure the partition used for '/home' has also been selected to have '/home' as the mount point (highlight the existing home partition, and click the 'Change' button), but make sure the reformat check box is left unchecked.</dd>
    <dt>Continue installation as normal, and reboot once finished.</dt>


    <dt>Login, and check the following command runs without any errors:</dt>
      <dd>cat /home/$USER/dummy_file</dd>


    </dl>
    <p>If <strong>all</strong> actions produce the expected results described,
      please <a href="results#add_result">submit</a> a 'passed' result.</p>
    <p>If <strong>any</strong> action fails, or produces an unexpected result,
      please <a href="results#add_result">submit</a> a 'failed' result and <a href="../../buginstructions">file a bug</a>. Please be sure to include
      the bug number when you <a href="results#add_result">submit</a> your
      result.</p>

