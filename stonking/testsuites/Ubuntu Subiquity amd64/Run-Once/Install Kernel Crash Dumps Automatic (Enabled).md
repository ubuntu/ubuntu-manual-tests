<p>
<strong>This test is only valid for Oracular (24.10) and later releases. If testing pre-Oracular media, please just mark this test as passing.</strong>
</p>
<p>
The purpose of this testcase is to test that kernel crash dumps are <strong>successfully enabled</strong> on installed systems which meet certain criteria. The result of this test case will depend on the specifics of your hardware and the steps you perform during the course of the install. Please perform the test using a system that <strong>meets</strong> the following criteria:
</p>

<ul>
    <li><strong> CPU Architecture</strong>: amd64 (x86_64), arm64 (aarch64), or s390x </li>
    <li><strong> CPU Cores</strong>: >=4 </li>
    <li><strong> Memory (RAM + SWAP)</strong>: 8GiB</li>
    <li><strong> Disk size </strong>: 100GiB</li>
</ul>


<em>
    Proceed in your native language if you wish. Instructions will remain in
    English.
</em>

<p> The test steps are as follows: </p>

<ol>
    <li> Perform the install as desired, up until the "Guided storage configuration" (Server) or "Disk setup" (Desktop) screen. Follow step 2 for Server and step 3 for Desktop.</li>
    <li> Server:
    <ol>
        <li> Ensure that "Use an entire disk" is selected and <strong> unselect </strong> "Set up this disk as an LVM group".</li>
        <li> Select "Done" then confirm the creation of two partitions on the next screen.
        <ul>
            <li> A partition mounted at "/" with an ext4 filesystem. </li>
            <li> A partition mounted at "/boot/efi" with a fat32 filesystem. </li>
        </ul>
        </li>
        <li> Select "Done" again, confirm the install, and proced with the remainder of the install as desired. </li>
        <li> Go to step 4. </li>
    </ol>
    </li>
    <li> Desktop:
    <ol>
        <li> Choose the default "Erase disk and install Ubuntu" option. </li>
        <li> Continue with the install as desired until the confirmation screen. </li>
        <li> Confirm the creation of two partitions:
        <ul>
            <li> A partition mounted at "/" with an ext4 filesystem. </li>
            <li> A partition mounted at "/boot/efi" with a fat32 filesystem. </li>
        </ul>
        </li>
        <li> Select "Install" and let the install proceed. </li>
        <li> Proceed to step 4. </li>
    </ol>
    </li>
    <li> Once the install has finished, reboot into the newly installed system. </li>
    <li> Check on the status of kdump-tools using the following command in the terminal: <code>kdump-config show</code></li>
    <li> Compare the result of the command with the guidance below. </li>
</ol>

<p> The result of the <code>kdump-config show</code> command should show
something similar to:</p>
<div class="box">
    <pre>
       $ kdump-config show
        DUMP_MODE:              kdump
        USE_KDUMP:              1
        KDUMP_COREDIR:          /var/crash
        crashkernel addr: 0x
           /var/lib/kdump/vmlinuz: symbolic link to /boot/vmlinuz-6.11.0-7-generic
        kdump initrd:
           /var/lib/kdump/initrd.img: symbolic link to /var/lib/kdump/initrd.img-6.11.0-7-generic
        current state:    ready to kdump

        crashkernel suggested size: 223M

        kexec command:
          /sbin/kexec -p --command-line="BOOT_IMAGE=/boot/vmlinuz-6.11.0-7-generic root=UUID=8c19e778-298a-40ad-91cd-f6725092446a ro reset_devices systemd.unit=kdump-tools-dump.service nr_cpus=1 irqpoll usbcore.nousb" --initrd=/var/lib/kdump/initrd.img /var/lib/kdump/vmlinuz
    </pre>
</div>

<p> Ensure that: </p>
<ul>
    <li><strong>current state</strong> shows <strong> ready to dump</strong>.</li>
    <li> <strong>USE_KDUMP</strong> is set to <strong>1</strong></li>
    <li> The <em>crashkernel</em> parameter  is set on the kernel command line.
    (this can be checked using: <code>sudo cat /proc/cmdline)</code></li>
</ul>


<strong> Some special notes about testing: </strong>
<ul>
    <li> If the results are not as expected, please include:
    <ul>
        <li> The output of the following command in your bug report: <code>sudo /usr/share/kdump-tools/kdump_set_default</code> </li>
        <li> The contents of "/var/log/installer/curtin-install.log" </li>
    </ul>
    </li>
    <li> If performing the test with a VM, note that it has been reported that
    thin provisioning of disk images may cause the enablement to fail
    where it was otherwise expected. Check the output of
    <code>df -h /var</code> within the VM (in the newly installed system) in these cases.
    </li>
</ul>

<strong>If you finish the installation, please <a href="results#add_result">submit</a> a 'passed' result.
    If any action fails, or produces an unexpected result, please <a href="results#add_result">submit</a> a 'failed' result and <a href="../../buginstructions">file a bug</a>. Please be sure to include the bug number when you <a href="results#add_result">submit</a> your result.</strong>



