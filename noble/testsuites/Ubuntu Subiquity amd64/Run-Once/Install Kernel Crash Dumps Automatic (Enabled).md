**This test is only valid for Oracular (24.10) and later releases. If testing pre-Oracular media, please just mark this test as passing.**

The purpose of this testcase is to test that kernel crash dumps are **successfully enabled** on installed systems which meet certain criteria. The result of this test case will depend on the specifics of your hardware and the steps you perform during the course of the install. Please perform the test using a system that **meets** the following criteria: 

  * **CPU Architecture** : amd64 (x86_64), arm64 (aarch64), or s390x 
  * **CPU Cores** : >=4 
  * **Memory (RAM + SWAP)** : 8GiB
  * **Disk size** : 100GiB

_Proceed in your native language if you wish. Instructions will remain in English._

The test steps are as follows: 

  1. Perform the install as desired, up until the ""Guided storage configuration"" (Server) or ""Disk setup"" (Desktop) screen. Follow step 2 for Server and step 3 for Desktop.
  2. Server: 
     1. Ensure that ""Use an entire disk"" is selected and **unselect** ""Set up this disk as an LVM group"".
     2. Select ""Done"" then confirm the creation of two partitions on the next screen. 
        * A partition mounted at ""/"" with an ext4 filesystem. 
        * A partition mounted at ""/boot/efi"" with a fat32 filesystem. 
     3. Select ""Done"" again, confirm the install, and proced with the remainder of the install as desired. 
     4. Go to step 4. 
  3. Desktop: 
     1. Choose the default ""Erase disk and install Ubuntu"" option. 
     2. Continue with the install as desired until the confirmation screen. 
     3. Confirm the creation of two partitions: 
        * A partition mounted at ""/"" with an ext4 filesystem. 
        * A partition mounted at ""/boot/efi"" with a fat32 filesystem. 
     4. Select ""Install"" and let the install proceed. 
     5. Proceed to step 4. 
  4. Once the install has finished, reboot into the newly installed system. 
  5. Check on the status of kdump-tools using the following command in the terminal: `kdump-config show`
  6. Compare the result of the command with the guidance below. 



The result of the `kdump-config show` command should show something similar to:
    
    
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
              /sbin/kexec -p --command-line=""BOOT_IMAGE=/boot/vmlinuz-6.11.0-7-generic root=UUID=8c19e778-298a-40ad-91cd-f6725092446a ro reset_devices systemd.unit=kdump-tools-dump.service nr_cpus=1 irqpoll usbcore.nousb"" --initrd=/var/lib/kdump/initrd.img /var/lib/kdump/vmlinuz
        

Ensure that: 

  * **current state** shows **ready to dump**.
  * **USE_KDUMP** is set to **1**
  * The _crashkernel_ parameter is set on the kernel command line. (this can be checked using: `sudo cat /proc/cmdline)`

**Some special notes about testing:**

  * If the results are not as expected, please include: 
    * The output of the following command in your bug report: `sudo /usr/share/kdump-tools/kdump_set_default`
    * The contents of ""/var/log/installer/curtin-install.log"" 
  * If performing the test with a VM, note that it has been reported that thin provisioning of disk images may cause the enablement to fail where it was otherwise expected. Check the output of `df -h /var` within the VM (in the newly installed system) in these cases. 

**If you finish the installation, please [submit](<>) a 'passed' result. If any action fails, or produces an unexpected result, please [submit](<>) a 'failed' result and [file a bug](<>). Please be sure to include the bug number when you [submit](<>) your result.**
