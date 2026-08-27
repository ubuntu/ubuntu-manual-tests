# Test RISC-V Xubuntu minimal desktop installation on QEMU

The test assumes a Ubuntu 26.04 LTS or higher host system.

* Install prerequisites

      sudo apt-get update
      sudo apt install \
        opensbi \
        qemu-efi-riscv64 \
        qemu-system-riscv

* Create a local copy of the EFI variables file.

      cp /usr/share/qemu-efi-riscv64/RISCV_VIRT_VARS.fd .

* Download the live installer image.
* Create the disk image file that we will install to.

      rm -f disk
      truncate -s 16G disk

* Start the installer with:

      qemu-system-riscv64 \
        -cpu rva23s64 \
        -machine virt,acpi=off -m 4G -smp cpus=2 \
	-accel kvm \
        -serial mon:stdio \
        -device virtio-gpu-pci \
        -device qemu-xhci \
        -device usb-kbd \
        -device usb-tablet \
        -drive if=pflash,format=raw,unit=0,file=/usr/share/qemu-efi-riscv64/RISCV_VIRT_CODE.fd,readonly=on \
        -drive if=pflash,format=raw,unit=1,file=RISCV_VIRT_VARS.fd,readonly=off \
        -netdev user,id=net0 \
        -device virtio-net-device,netdev=net0 \
        -device virtio-rng-pci \
        -drive file=disk,format=raw,if=none,id=DISK \
        -device virtio-blk,drive=DISK,bootindex=1 \
        -drive file=<release>-desktop-riscv64.iso,format=raw,readonly=on,if=none,id=ISO \
        -device virtio-blk,drive=ISO,bootindex=2

  If your host is not a RISC-V system, remove '-accel kvm' from the command.

* In the console the output of the serial console is shown.
* In a new window the graphical output is presented. Activate this window.
* In the GRUB menu select 'Try or Install Ubuntu'
* Via Settings -> Display you can choose a higher screen resolution.
* Open the 'Install Xubuntu Minimal' application.
* Follow the on screen instructions.
   * Choose your installation language.
   * Choose a keyboard layout up matching your physical keyboard.
   * In the 'Connect to the Internet' dialog select 'Use wired connection'.
   * In the 'How would you like to install Xubuntu' dialog select 'Interactive installation'.
   * In the 'What apps would you like to install to start with' dialog select 'Xubuntu Minimal'.
   * In the 'Install recommended proprietary software' dialog nothing needs to be selected.
   * In the 'How do you want to install Xubuntu' dialog choose 'Erase disk and install Xubuntu'.
   * In the 'Encryption and file system dialog' make your choice. Using 'No encryption' is file.
   * In the 'Create your account' dialog fill all fields.
   * Choose a time zone.
   * Review your choices and start the installation.
   * The installation finishes without reporting failures.
   * Close the installer app.
* Reboot
   * Open a terminal to reboot.
   * The system boots via GRUB.
* Login in with the username and password defined during the installation.
* Open a terminal.
* Perform generic testing
  * Check that apt update works.

        sudo apt-get update

  * Install a package and check that it works, e.g. hello.

        sudo apt-get install hello
        /usr/bin/hello

* Perform snap testing
  * Install a snap and check that it works, e.g. hello.

        sudo snap install hello
        /snap/bin/hello

* Check GRUB device-tree loading.
   * If installing to real hardware using a device-tree, file
     /boot/dtb-&lt;kernel-version> should exist and file /boot/grub/grub.cfg
     should contain a *devicetree* command loading this device-tree.
* Reboot and login again.

      sudo reboot

  * The system should reboot and show the login message again.
  * Login should be successful.
* Power off

      sudo poweroff

  * The host console should be reached.

If all actions produce the expected results listed, please submit a 'passed'
result.

If an action fails, or produces an unexpected result, please submit  a 'failed'
result and file a bug. Please include the bug number in the test report.
