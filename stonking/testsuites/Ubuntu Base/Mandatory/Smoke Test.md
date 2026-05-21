# Test Ubuntu base chroot tarball

This testcase is intended to confirm that the base chroot tarball is in proper
working order.

* Install dependencies

  When testing on a host system with a different architecture you will
  need to install the qemu-user package:

      sudo apt-get update
      sudo apt-get install \
        qemu-user \
        qemu-user-binfmt

* Download the test image tarball.
* Create the directory for the chroot.

       mkdir base

  The test will fail on a mount which any of the following mount options:
  ro, noexec, nosuid, nodev.
* Extract the tarball.

      sudo tar -C base -zxf (release)-base-(arch).tar.gz

* Create necessary mounts.

      for m in proc sys dev dev/pts; do sudo mount --bind /$m base/$m; done

* Enable DNS.

      sudo cp /etc/resolv.conf base/etc/

* Enter the chroot.

      sudo chroot base

* Install and execute a package of your choice, e.g.

      apt update
      apt install hello
      /usr/bin/hello

* Exit the chroot.

      exit

* Remove mounts in reverse order.

      for m in dev/pts dev sys proc; do sudo umount base/$m; done

---
**If all actions produce the expected results listed,
please submit a `passed` result.**

**If an action fails, or produces an unexpected result,
please submit a `failed` result and file a bug.
Please be sure to include the bug number when you submit your result.**
