
<p><em>Proceed in your native language if you wish. Instructions will remain in English.</em></p>
<dl>

<dt>In this test case, make sure that the machine you're installing on does not have the HW requirements for TPM FDE.</dt>

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

<dt>The 'Update available' screen MAY be displayed</dt>
<dd>If there is an update for the installer, a screen allowing to update it will appear. Click on the "Update now" button, exit the installer, launch it again from the dock (or from the "Install Ubuntu 26.04" icon on the desktop), and repeat the previous steps.</dd>


<dt>You're greeted with the 'Install type' slide, with three options: "Interactive install", "Automatic with an autoinstall file", and "Automatic with Landscape".</dt>
  <dd>Select "Interactive install" to continue with the installation process.</dd>

<dt>Now you are greeted with the 'Applications' slide, listing normal and enhanced installation options</dt>
<dd>Choose "Predetermined selection" to continue.</dd>

<dt>The 'Optimize your device' screen is displayed, where you can choose wheter to install or not other drivers, like the nVidia ones or certain privative Wi-Fi drivers. Also allows to install third-party multimedia formats.</dt>
<dd>Select any options pertinent to the testcase.</dd>
<dt>Click "Next"</dt>

<dt>The 'Disk configuration' page will be displayed. Here you can choose whether to delete the entire disk, or manually partition it</dt>
<dd>Select any options pertinent to the testcase.</dd>

  <dd>The 'Encryption and file system' screen is displayed</dd>

<dt>For this check, please use a system with no TPM enabled hardware. Try choosing "Use hardware-backed encryption". The installer should show a new page notifying that it wasn't possible to enable it, and only allowing to go back. Now choose "No encryption" and ensure that the system is installed correctly.</dt>

</dl>
<p>If <strong>all</strong> actions produce the expected results described,
  please <a href="results#add_result">submit</a> a 'passed' result.</p>
<p>If <strong>any</strong> action fails, or produces an unexpected result,
  please <a href="results#add_result">submit</a> a 'failed' result and <a href="../../buginstructions">file a bug</a>. Please be sure to include
  the bug number when you <a href="results#add_result">submit</a> your
  result.</p>


