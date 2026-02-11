**This test is only valid for Oracular (24.10) and later releases. If testing pre-Oracular media, please just mark this test as passing.**

The purpose of this testcase is to test that kernel crash dumps are **successfully disabled** on installed systems which do not meet certain criteria. The result of this test case will depend on the specifics of your hardware. Please perform the test using a system that **does not meet** the following minimum criteria: 

  * **CPU Architecture** : amd64 (x86_64), arm64 (aarch64), or s390x 
  * **CPU Cores** : >=4 
  * **Memory (RAM + SWAP)** : >=6GiB
  * **Disk size** : >= 5 x (Memory)

_Proceed in your native language if you wish. Instructions will remain in English._

The test steps are as follows: 

  1. Perform a standard install using the linked installation media. No other special steps are required during the installation. 
  2. Reboot into the newly installed system. 
  3. Check on the status of kdump-tools using the following command: `kdump-config show`
  4. Compare the result of the command with the guidance below. 



The result of the `kdump-config show` command should show something similar to:
    
    
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
              /sbin/kexec -p --command-line=""BOOT_IMAGE=/boot/vmlinuz-6.11.0-7-generic root=UUID=8c19e778-298a-40ad-91cd-f6725092446a ro reset_devices systemd.unit=kdump-tools-dump.service nr_cpus=1 irqpoll usbcore.nousb"" --initrd=/var/lib/kdump/initrd.img /var/lib/kdump/vmlinuz
        

Ensure that: 

  * **current state** shows **Not ready to dump**.
  * **USE_KDUMP** is set to **0**

**Some special notes about testing:**

  * If the results are not as expected, please include the output of the following command in your bug report: `sudo /usr/share/kdump-tools/kdump_set_default`

**If you finish the installation, please[submit](<>) a 'passed' result. If any action fails, or produces an unexpected result, please [submit](<>) a 'failed' result and [file a bug](<>). Please be sure to include the bug number when you [submit](<>) your result.**
