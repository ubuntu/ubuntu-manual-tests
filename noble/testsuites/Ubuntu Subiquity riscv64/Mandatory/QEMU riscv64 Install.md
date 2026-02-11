This testcase checks the installation of the live installer image for the riscv64 architecture on QEMU. On your installed Ubuntu machine. 

sudo apt install -y opensbi qemu-system-misc u-boot-qemu
rm -f disk
truncate -s 16G disk
Start the installer with (needs QEMU > 10.1, available on Ubuntu 25.10): 
    
    
    /usr/bin/qemu-system-riscv64 -machine virt -m 4G -smp cpus=2 -nographic \
        -kernel /usr/lib/u-boot/qemu-riscv64_smode/u-boot.bin \
        -netdev user,id=net0 \
        -device virtio-net-device,netdev=net0 \
        -drive file=disk,format=raw,if=virtio \
        -drive file=<release>-live-server-riscv64.iso,format=raw,if=virtio,readonly=on \
        -device virtio-rng-pci -cpu rva23s64
    

Install on the 16 GiB drive.
    The installation finishes without reporting failures.
Reboot     The system boots via GRUB.
Login in with the username and password defined during the installation
Run any command that is not installed, e.g. hello.
    Check that command-not-found recommends things to install
Install a package, e.g. hello.
    Check that the package performs correctly.
Install a snap, e.g. hello.
    check that the snap works correctly.
Check grub.cfg
    If installing to real hardware using a device-tree, /boot/dtb- should exists and /boot/grub/grub.cfg should contain a devicetree command loading the this device-tree.
Poweroff
    Console messages should reach the poweroff target
    There should be final message 'reboot: Power down'
    QEMU should terminate automatically
**If all actions produce the expected results listed, please [submit](<>) a 'passed' result. If an action fails, or produces an unexpected result, please [submit](<>) a 'failed' result and [file a bug](<>). Please be sure to include the bug number when you [submit](<>) your result.**
