The scope of this test is to ensure that riscv64+visionfive2 image boots from SD card on Milk-V Mars board

<dl>
    <dt>Flash downloaded image onto SD card</dt>
        <dd>You can use Gnome Disks app to restore img.xz onto the SD card</dd>
        <dd>Alternatively you can use xz -d to decompress, and then dd to copy the image to the SD card</dd>
    <dt>Connect networking, serial console to the board</dt>
        <dd>Ethernet cable for networking</dd>
        <dd>USB to TTL adapter for serial console (pinout available here: https://milkv.io/docs/mars/getting-started/setup)</dd>
    <dt>Connect to the serial console</dt>
        <dd>sudo screen /dev/ttyUSB0 115200</dd>
    <dt>Power on the board</dt>
        <dd>You should see U-BOOT output</dd>
        <dd>It should then boot GRUB after a delay</dd>
        <dd>You should see GRUB menu</dd>
        <dd>It should then boot the default kernel after a delay</dd>
        <dd>After a while cloud-init will run</dd>
	<dd>Wait for the 'Cloud-init finished' message</dd>
        <dd>Then one will be able to login</dd>
    <dt>Login and change password</dt>
        <dd>Login using ubuntu for both username and password</dd>
        <dd>Reenter ubuntu password again</dd>
        <dd>Set new password</dd>
        <dd>Confirm the new password</dd>
    <dt>Perform generic testing</dt>
        <dd>Check that apt update works</dd>
        <dd>Run any command that is not installed, check that command-not-found recommends things to install</dd>
        <dd>e.g. hello</dd>
        <dd>Install a package and check that it works, e.g. hello</dd>
    <dt>Reboot</dt>
        <dd>The board should reboot normally</dd>
    <dt>Poweroff</dt>
        <dd>Console messages should reach poweroff target</dd>
        <dd>There should be final kernel dmsg powering off</dd>
        <dd>Manually turn power-off from the board</dd>
</dl>
<strong>If all actions produce the expected results listed, please <a href="results#add_result">submit</a> a 'passed' result.
    If an action fails, or produces an unexpected result, please <a href="results#add_result">submit</a> a 'failed' result and <a href="../../buginstructions">file a bug</a>. Please be sure to include the bug number when you <a href="results#add_result">submit</a> your result.</strong>


