# Test RISC-V server install image on QEMU

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
        -machine virt,acpi=on -m 4G -smp cpus=2 \
        -nographic \
        -drive if=pflash,format=raw,unit=0,file=/usr/share/qemu-efi-riscv64/RISCV_VIRT_CODE.fd,readonly=on \
        -drive if=pflash,format=raw,unit=1,file=RISCV_VIRT_VARS.fd,readonly=off \
        -netdev user,id=net0 \
        -device virtio-net-device,netdev=net0 \
        -device virtio-rng-pci \
        -drive file=disk,format=raw,if=none,id=DISK \
        -device virtio-blk,drive=DISK,bootindex=1 \
        -drive file=<release>-live-server-riscv64.iso,format=raw,readonly=on,if=none,id=ISO \
        -device virtio-blk,drive=ISO,bootindex=2

* Follow the on screen instructions.
   * The installation finishes without reporting failures.
* Reboot
   * The system boots via GRUB.
* Login in with the username and password defined during the installation.
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

  * There should be final kernel message indicating powering off like

        [  104.670221] reboot: Power down

  * The host console should be reached.

For reference see the
[Ubuntu boards documentation](https://canonical-ubuntu-hardware-support.readthedocs-hosted.com/boards/how-to/ubuntu_supported/qemu-riscv/index.html).

If all actions produce the expected results listed, please submit a 'passed'
result.

If an action fails, or produces an unexpected result, please submit  a 'failed'
result and file a bug. Please include the bug number in the test report.
