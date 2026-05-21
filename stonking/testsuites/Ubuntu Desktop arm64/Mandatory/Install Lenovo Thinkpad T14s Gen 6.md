<p>This test case is to be carried out on a Lenovo Thinkpad T14s or a similar supported Snapdragon X Elite laptop (Dell XPS 13 9345, Lenovo Yoga Slim 7x)</p>

<dl>
    <dt>Boot up the image</dt>
    <dd>Ubuntu boot screen is displayed</dd>

    <dt>Install Ubuntu, make sure to select the "Install third-party software for graphics and Wi-Fi hardware" option when it comes up and reboot once finished</dt>
    <dd>The system boots properly into the fresh installation and the first boot screen is displayed</dd>

    <dt>On the freshly installed system run 'apt list --installed | grep x1e'</dt>
    <dd>hwe-lenovo-x1e-meta, ubuntu-x1e-settings-nogrub and ubuntu-x1e-settings show up in the list of installed packages</dd>

    <dt>Run snap list</dt>
    <dd>The gnome-42-2204 snap is tracking adreno/stable and mesa-2404 is tracking beta/kisak</dd>

    <dt>Install 'snap install --channel 22/stable graphics-test-tools' and run  graphics-test-tools.glxinfo</dt>
    <dd>Hardware acceleration is detected: OpenGL vendor string is freedreno, OpenGL renderer string shows Adreno X1-85</dd>

    <dt>Install 'snap install --channel 24/stable graphics-test-tools' and run  graphics-test-tools.glxinfo</dt>
    <dd>Hardware acceleration is detected: OpenGL vendor string is freedreno, OpenGL renderer string shows Adreno X1-85</dd>

    <dt>Reboot and add the 'break' kernel command line option before booting.</dt>
    <dd>
      The system boots into an interactive visible shell running in the initrd.  This makes sure the frame buffer driver
      attaches early enough for initrd hooks like cryptsetup to have graphics support.
    </dd>
</dl>

<strong>If all actions produce the expected results listed, please <a href="results#add_result">submit</a> a 'passed' result.
    If an action fails, or produces an unexpected result, please <a href="results#add_result">submit</a> a 'failed' result and <a href="../../buginstructions">file a bug</a>. Please be sure to include the bug number when you <a href="results#add_result">submit</a> your result.</strong>


