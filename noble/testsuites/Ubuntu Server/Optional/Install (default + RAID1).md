Server basic RAID1 install _Proceed in your native language if you wish. Instructions will remain in English_

NB: A more exhaustive set of test instructions to be used in KVM environments can be found on the [BootDegradedRaid wiki page](<>)
Boot CD and run the CD self-check (then reboot)
Select Install Ubuntu Server or """"Install to Hard Disk""""
Choose your language, country and keyboard layout
Set hostname: default - ubuntu
Confirm time zone detection.
Partitioning method: ""Manual"".
    RAID1 array for /
    RAID1 array for swap
    RAID1 array for /home (testing non-rootfs raid)
Select ""Yes"" to the ""boot degraded?"" question
User account: enter username and password
No software selection.
Reboot and login.
Make sure that the root and home file systems are mounted from md devices:
    sudo mount
Make sure that the swap partition is mounted from a md device:
    sudo cat /proc/swaps
Make sure that the raid arrays are working:
    cat /proc/mdstat
Make sure that grub has been installed on both disks:
    sudo apt-get install -y binutils
    for i in $(sudo mdadm -Q --detail $(df -P /boot | grep ^/dev/ | cut -d"" "" -f1) | grep "" /dev/"" | awk '{print $NF}' | sed -e 's/[0-9]$//'); do sudo dd if=$i bs=512 count=1 2>/dev/null | strings -a | grep -q GRUB && echo $i: ok || echo $i: FAIL; done
Make sure that the BOOT_DEGRADED setting is ""TRUE"" in /etc/initramfs-tools/conf.d/mdadm:
    cat /etc/initramfs-tools/conf.d/mdadm
Test booting from a cold-degraded array:
    Power off the system
    Disconnect one of the disk (disk 2) - disk 1 connected, disk2 disconnected.
    Power on the system
    Check that system boots correctly from the degraded RAID1 array on a single disk (note that you may have to wait up to 5 minutes for mdadm to time out and boot into degraded mode):
    cat /proc/mdstat
    Power off the system
    /!\ If you simply disconnect the first disk (disk1) and reconnect the second disk (disk2) - disk 1 disconnected, disk 2 connected - you risk disk corruption; see bug 557429)
    Reconnect the second disk (disk2) - both disks now connected.
    Power on the system
    Check that the system boots correctly (there should be no error or delay)
    Check the status of the raid arrays:
    cat /proc/mdstat
    All arrays should have been assembled completely again, possibly still syncing.
    You may have to add any missing devices back to the RAIDs manually. This is not a bug (see bug 791454)! A manual addition would be:
    sudo mdadm --add /dev/mdX /dev/MISSING-DEVICE
    Note that this may fail with a message requiring you to zero the superblock first, this is a result of an added check in mdadm 3.2, and should only happen on precise or later (see bug 943397).
    make sure that all disk arrays are synchronized before proceeding, if the array is doing a full re-sync, it may take a few minutes, use
    cat /proc/mdstat
    Poweroff the system.
    Disconnect the first disk (disk1) - disk 1 disconnected, disk 2 connected.
    Poweron the system.
    Check that system boots correctly from the degraded RAID1 array on a single disk:
    cat /proc/mdstat
Test automatic syncing of degraded array:
    Power off the system
    Reconnect the first disk (so both are now connected)
    Power on the system
Wait for both drives to be back in sync:
    cat /proc/mdstat
Change ""Do you want to boot degraded?"" answer to ""No"":
    sudo dpkg-reconfigure mdadm
Make sure that the BOOT_DEGRADED setting is ""FALSE"" in /etc/initramfs-tools/conf.d/mdadm:
    cat /etc/initramfs-tools/conf.d/mdadm
Test booting from a cold-degraded array:
    Power off the system
    Disconnect one of the disk (disk 2) - disk 1 connected, disk2 disconnected.
    Power on the system
    Check that on boot a question to enable and boot from a degraded array is asked.
    Say yes
    Check that system boots correctly from the degraded RAID1 array:
    cat /proc/mdstat
    Power off the system
    Disconnect the first disk (disk1) and reconnect the second disk (disk2) - disk 1 disconnected, disk 2 connected.
    Power on the system.
    Check that on boot a question to enable and boot from a degraded array is asked.
    Say yes
    Check that system boots correctly from the degraded RAID1 array:
    cat /proc/mdstat
Re-add/sync the arrays again
    Power off the system
    Reconnect the first disk (so both are now connected)
    Power on the system
    Add the missing drives back to the RAIDs:
    sudo mdadm -a /dev/mdX /dev/MISSING-DEVICE
Test booting from a hot-degraded array:
    Remove (unplug/fail) one disk from the running system.
    Check if users/admin get a notification message and beep about the failing raid.
    Reboot, verify that system comes up degraded without failure. (BOOT_DEGRADED setting bogus, Bug #539597)
Server with LUKS on RAID1 install 

Boot CD and run the CD self-check (then reboot)
Select Install to hard disk
Choose your language, country and keyboard layout
Set hostname: default - ubuntu
Partition disks: Custom partition scheme.
    RAID1 array for /boot
    RAID1 array with LUKS on it for /
    RAID1 array for swap (should it get encrypted automatically?)
    RAID1 array with LUKS on it for /home
Select ""Yes"" to the ""boot degraded?"" question
Select your time zone and set the system clock to UTC
User account: enter username and password
No software selection.
Reboot and login.
Make sure that the root and home file systems are mounted from luks devices:
    sudo mount
Make sure that the swap partition is mounted from a md device (and encrypted?):
    sudo cat /proc/swaps
Make sure that the luks devices and /boot use md devices:
    sudo dmsetup deps
Make sure that the raid arrays are working:
    cat /proc/mdstat
Make sure that grub has been installed on both disks:
    sudo apt-get install -y binutils
    for i in $(sudo mdadm -Q --detail $(df -P /boot | grep ^/dev/ | cut -d"" "" -f1) | grep "" /dev/"" | awk '{print $NF}' | sed -e 's/[0-9]$//'); do sudo dd if=$i bs=512 count=1 2>/dev/null | strings -a | grep -q GRUB && echo $i: ok || echo $i: FAIL; done
Make sure that the BOOT_DEGRADED setting is ""TRUE"" in /etc/initramfs-tools/conf.d/mdadm:
    cat /etc/initramfs-tools/conf.d/mdadm
Test booting from a cold-degraded array:
    Power off the system
    Disconnect one of the disk (disk 2) - disk 1 connected, disk2 disconnected.
    Power on the system
    Check that system boots correctly from the degraded RAID1 array on a single disk (note that you may have to wait up to 5 minutes for mdadm to time out and boot into degraded mode):
    cat /proc/mdstat
    Power off the system
    Disconnect the first disk (disk1) and reconnect the second disk (disk2) - disk 1 disconnected, disk 2 connected. This results in booting the other half of the array, to see if this array segmentation is detected correctly afterwards. (see Bug #557429)
    Power on the system.
    Check that system boots correctly from the degraded RAID1 array on a single disk:
    cat /proc/mdstat
Test automatic re-syncing of degraded array:
    Power off the system
    Reconnect the first disk (so both are now connected)
    Power on the system
Wait for both drives to be back in sync:
    cat /proc/mdstat
Change ""Do you want to boot degraded?"" answer to ""No"":
    sudo dpkg-reconfigure mdadm
Make sure that the BOOT_DEGRADED setting is ""FALSE"" in /etc/initramfs-tools/conf.d/mdadm:
    cat /etc/initramfs-tools/conf.d/mdadm
Test booting from a cold-degraded array:
    Power off the system
    Disconnect one of the disk (disk 2) - disk 1 connected, disk2 disconnected.
    Power on the system
    Check that on boot a question to enable and boot from a degraded array is asked.
    Say yes
    Check that system boots correctly from the degraded RAID1 array:
    cat /proc/mdstat
    Power off the system
    Disconnect the first disk (disk1) and reconnect the second disk (disk2) - disk 1 disconnected, disk 2 connected.
    Power on the system.
    Check that on boot a question to enable and boot from a degraded array is asked.
    Say yes
    Check that system boots correctly from the degraded RAID1 array:
    cat /proc/mdstat
Re-add/sync the arrays again
    Poweroff the system
    Reconnect the first disk (so both are now connected)
    Poweron the system
    Add the missing drives back to the RAIDs:
    sudo mdadm -a /dev/mdX /dev/MISSING-DEVICE
Test booting from a hot-degraded array:
    Remove (unplug/fail) one disk from the running system.
    Check if users/admin get a notification message and beep about the failing raid.
    Reboot, verify that system comes up degraded without failure. (BOOT_DEGRADED setting bogus, Bug #539597)
Server with LVM on LUKS on RAID1 install 

Boot CD and run the CD self-check (then reboot)
Select Install to hard disk
Choose your language, country and keyboard layout
Set hostname: default - ubuntu
Partition disks: Custom partition scheme.
    RAID1 array for /boot
    RAID1 array with LUKS on it, with LVM on it, for /, /swap and /home
Select ""Yes"" to the ""boot degraded?"" question
Select your time zone and set the system clock to UTC
User account: enter username and password
No software selection.
Reboot and login.
Make sure that the root and home file systems are mounted from mapper devices:
    sudo mount
Make sure that the swap partition is mounted from a mapper device:
    sudo cat /proc/swaps
Make sure that lvm uses luks, and luks is using a md device:
    sudo dmsetup deps
Make sure that the raid arrays are working:
    cat /proc/mdstat
Make sure that grub has been installed on both disks:
    sudo apt-get install -y binutils
    for i in $(sudo mdadm -Q --detail $(df -P /boot | grep ^/dev/ | cut -d"" "" -f1) | grep "" /dev/"" | awk '{print $NF}' | sed -e 's/[0-9]$//'); do sudo dd if=$i bs=512 count=1 2>/dev/null | strings -a | grep -q GRUB && echo $i: ok || echo $i: FAIL; done
Make sure that the BOOT_DEGRADED setting is ""TRUE"" in /etc/initramfs-tools/conf.d/mdadm:
    cat /etc/initramfs-tools/conf.d/mdadm
Test booting from a cold-degraded array:
    Poweroff the system
    Disconnect one of the disk (disk 2) - disk 1 connected, disk2 disconnected.
    Poweron the system
    Check that system boots correctly from the degraded RAID1 array on a single disk (note that you may have to wait up to 5 minutes for mdadm to time out and boot into degraded mode):
    cat /proc/mdstat
    Poweroff the system
    Disconnect the first disk (disk1) and reconnect the second disk (disk2) - disk 1 disconnected, disk 2 connected.
    Poweron the system.
    Check that system boots correctly from the degraded RAID1 array on a single disk:
    cat /proc/mdstat
Test automatic syncing of degraded array:
    Poweroff the system
    Reconnect the first disk (so both are now connected)
    Poweron the system
Wait for both drives to be back in sync:
    cat /proc/mdstat
Change ""Do you want to boot degraded?"" answer to ""No"":
    sudo dpkg-reconfigure mdadm
Make sure that the BOOT_DEGRADED setting is ""FALSE"" in /etc/initramfs-tools/conf.d/mdadm:
    cat /etc/initramfs-tools/conf.d/mdadm
Test booting from a cold-degraded array:
    Poweroff the system
    Disconnect one of the disk (disk 2) - disk 1 connected, disk2 disconnected.
    Poweron the system
    Check that on boot a question to enable and boot from a degraded array is asked.
    Say yes
    Check that system boots correctly from the degraded RAID1 array:
    cat /proc/mdstat
    Poweroff the system
    Disconnect the first disk (disk1) and reconnect the second disk (disk2) - disk 1 disconnected, disk 2 connected.
    Poweron the system.
    Check that on boot a question to enable and boot from a degraded array is asked.
    Say yes
    Check that system boots correctly from the degraded RAID1 array:
    cat /proc/mdstat
Re-add/sync the arrays again
    Poweroff the system
    Reconnect the first disk (so both are now connected)
    Poweron the system
    Add the missing drives back to the RAIDs:
    sudo mdadm -a /dev/mdX /dev/MISSING-DEVICE
Test booting from a hot-degraded array:
    Remove (unplug/fail) one disk from the running system.
    Check if users/admin get a notification message and beep about the failing raid.
    Reboot, verify that system comes up degraded without failure. (BOOT_DEGRADED setting bogus, Bug #539597)
**If all actions produce the expected results listed, please [submit](<>) a 'passed' result. If an action fails, or produces an unexpected result, please [submit](<>) a 'failed' result and [file a bug](<>). Please be sure to include the bug number when you [submit](<>) your result**. 
