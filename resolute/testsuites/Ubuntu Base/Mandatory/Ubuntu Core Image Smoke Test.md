This testcase is intended to confirm the base chroot tarball is in proper working order. To test this image on an already running system (of similar architecture), download the tarball and execute the following in the same local directory.

From the terminal, run the following commands
mkdir base
sudo tar -C base -zxf (release)-base-(arch).tar.gz
for m in proc sys dev dev/pts; do sudo mount --bind /$m base/$m; done
sudo cp /etc/resolv.conf base/etc/
sudo chroot base
apt update; apt install (some package)

**If all actions produce the expected results listed, please submit a 'passed' result. If an action fails, or produces an unexpected result, please submit a 'failed' result and file a bug. Please be sure to include the bug number when you submit your result.**