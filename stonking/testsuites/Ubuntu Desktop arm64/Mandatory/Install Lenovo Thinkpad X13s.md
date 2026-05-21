<p>This test case is to be carried out on a Lenovo Thinkpad X13s</p>

<dl>
    <dt>Boot up the image</dt>
    <dd>Ubuntu boot screen is displayed</dd>

    <dt>Install Ubuntu, make sure to select the "Install third-party software for graphics and Wi-Fi hardware" option when it comes up and reboot once finished</dt>
    <dd>The system boots properly into the fresh installation and the first boot screen is displayed</dd>

    <dt>On the freshly installed system run 'apt list --installed | grep x13s'</dt>
    <dd>hwe-lenovo-x13s-meta, ubuntu-x13s-settings-nogrub and ubuntu-x13s-settings show up in the list of installed packages</dd>

    <dt>Reboot and add the 'break' kernel command line option before booting.</dt>
    <dd>
      The system boots into an interactive visible shell running in the initrd.  This makes sure the frame buffer driver
      attaches early enough for initrd hooks like cryptsetup to have graphics support.
    </dd>
</dl>

<strong>If all actions produce the expected results listed, please <a href="results#add_result">submit</a> a 'passed' result.
    If an action fails, or produces an unexpected result, please <a href="results#add_result">submit</a> a 'failed' result and <a href="../../buginstructions">file a bug</a>. Please be sure to include the bug number when you <a href="results#add_result">submit</a> your result.</strong>


