<p>
<strong>This test is only valid for Oracular (24.10) and later releases. If testing pre-Oracular media, please just mark this test as passing.</strong>
</p>
<p>
The purpose of this testcase is to test that kernel crash dumps are <strong>successfully disabled</strong> on installed systems which do not meet certain criteria. The result of this test case will depend on the specifics of your hardware. Please perform the test using a system that <strong>does not meet</strong> the following minimum criteria:
</p>

<ul>
    <li><strong> CPU Architecture</strong>: amd64 (x86_64), arm64 (aarch64), or s390x </li>
    <li><strong> CPU Cores</strong>: >=4 </li>
    <li><strong> Memory (RAM + SWAP)</strong>: >=6GiB</li>
    <li><strong> Disk size</strong>: >= 5 x (Memory)</li>
</ul>

<em>
    Proceed in your native language if you wish. Instructions will remain in
    English.
</em>

<p> The test steps are as follows: </p>

<ol>
    <li> Perform a standard install using the linked installation media.
    No other special steps are required during the installation. </li>
    <li> Reboot into the newly installed system. </li>
    <li> Check on the status of kdump-tools using the following command: <code>kdump-config show</code></li>
    <li> Compare the result of the command with the guidance below. </li>
</ol>


<p> The result of the <code>kdump-config show</code> command should show
something similar to:</p>
<div class="box">
    <pre>
        $ kdump-config show
         * /etc/default/kdump-tools: USE_KDUMP is not set or zero
        DUMP_MODE:              kdump
        USE_KDUMP:              0
        KDUMP_COREDIR:          /var/crash
        crashkernel addr: 0x
           /var/lib/kdump/vmlinuz: symbolic link to /boot/vmlinuz-6.11.0-7-generic
        kdump initrd:
           /var/lib/kdump/initrd.img: symbolic link to /var/lib/kdump/initrd.img-6.11.0-7-generic
        current state:    Not ready to kdump

        crashkernel suggested size: 215M

        kexec command:
          /sbin/kexec -p --command-line="BOOT_IMAGE=/boot/vmlinuz-6.11.0-7-generic root=UUID=8c19e778-298a-40ad-91cd-f6725092446a ro reset_devices systemd.unit=kdump-tools-dump.service nr_cpus=1 irqpoll usbcore.nousb" --initrd=/var/lib/kdump/initrd.img /var/lib/kdump/vmlinuz
    </pre>
</div>

<p> Ensure that: </p>
<ul>
    <li><strong>current state</strong> shows <strong>Not ready to dump</strong>.</li>
    <li> <strong>USE_KDUMP</strong> is set to <strong>0</strong></li>
</ul>


<strong> Some special notes about testing: </strong>
<ul>
    <li> If the results are not as expected, please include the output of the
    following command in your bug report:
    <code>sudo /usr/share/kdump-tools/kdump_set_default</code>
    </li>
</ul>

<strong>If you finish the installation, please <a href="results#add_result">submit</a> a 'passed' result.
    If any action fails, or produces an unexpected result, please <a href="results#add_result">submit</a> a 'failed' result and <a href="../../buginstructions">file a bug</a>. Please be sure to include the bug number when you <a href="results#add_result">submit</a> your result.</strong>



