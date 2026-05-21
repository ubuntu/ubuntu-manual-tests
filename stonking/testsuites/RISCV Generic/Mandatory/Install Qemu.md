# Test RISC-V preinstalled server image QEMU

* Install prerequisites.

      sudo apt-get update
      sudo apt-get install \
        opensbi \
        qemu-efi-riscv64 \
        qemu-system-riscv

* Create a local copy of the EFI variables file.

      cp /usr/share/qemu-efi-riscv64/RISCV_VIRT_VARS.fd .

* Download the preinstalled server image.
* Uncompress the image.

      xz -d <release>-preinstalled-server-riscv64.img.xz

* Resize it

      qemu-img resize \
        -f raw \
        <release>-preinstalled-server-riscv64.img \
        +5G

* Boot with device-tree.

      qemu-system-riscv64 \
        -cpu rva23s64 \
        -machine virt,acpi=off -m 4G -smp cpus=2 \
        -nographic \
        -drive if=pflash,format=raw,unit=0,file=/usr/share/qemu-efi-riscv64/RISCV_VIRT_CODE.fd,readonly=on \
        -drive if=pflash,format=raw,unit=1,file=RISCV_VIRT_VARS.fd,readonly=off \
        -netdev user,id=net0 \
        -device virtio-net-device,netdev=net0 \
        -device virtio-rng-pci \
        -drive file=<release>-preinstalled-server-riscv64.img,format=raw,if=virtio

  * A message like

        Cloud-init v. 26.1-0ubuntu1 finished at Fri, 20 Mar 2026 09:32:17 +0000.

    is shown.

* Login and change password
  * Login using *ubuntu* for both username and password.
  * Reenter *ubuntu* password again.
  * Set new password.
  * Confirm the new password.
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

* Reboot and login again.

      sudo reboot

  * The system should reboot and show the login message again.
  * Login should be successful.
* Power off

      sudo poweroff

  * There should be final kernel message indicating powering off like

        [  104.670221] reboot: Power down

  * The host console should be reached.

* Boot with ACPI.

      qemu-system-riscv64 \
        -cpu rva23s64 \
        -machine virt,acpi=on -m 4G -smp cpus=2 \
        -nographic \
        -drive if=pflash,format=raw,unit=0,file=/usr/share/qemu-efi-riscv64/RISCV_VIRT_CODE.fd,readonly=on \
        -drive if=pflash,format=raw,unit=1,file=RISCV_VIRT_VARS.fd,readonly=off \
        -netdev user,id=net0 \
        -device virtio-net-device,netdev=net0 \
        -device virtio-rng-pci \
        -drive file=<release>-preinstalled-server-riscv64.img,format=raw,if=virtio

  * The system should boot and show the login message again.
* Login.
  * Login should be successful.
* Power off.

      sudo poweroff

  * The host console should be reached.

For reference see the
[Ubuntu boards documentation](https://canonical-ubuntu-hardware-support.readthedocs-hosted.com/boards/how-to/ubuntu_supported/qemu-riscv/index.html).

If all actions produce the expected results listed, please submit a 'passed'
result.

If an action fails, or produces an unexpected result, please submit  a 'failed'
result and file a bug. Please include the bug number in the test report.
