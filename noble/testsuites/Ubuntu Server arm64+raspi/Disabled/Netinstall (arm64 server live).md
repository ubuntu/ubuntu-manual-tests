This testcase is to run netboot installation on arm64 machines. You need an installed Ubuntu machine in the same network. _Proceed in your native language if you wish. Instructions will remain in English._ RELEASE is the current development codename. HOST is the IP address of installed Ubuntu machine. On your installed Ubuntu machine. 

sudo apt install -y tftpd-hpa apache2
sudo curl http://cdimage.ubuntu.com/ubuntu-server/daily-live/current/RELEASE-live-server-arm64.iso -o /var/www/html/test-live-server-arm64.iso
sudo mkdir /var/lib/tftpboot/grub /var/lib/tftpboot/casper
sudo mount -o loop,ro /var/www/html/test-live-server-arm64.iso /mnt
sudo cp /mnt/casper/initrd /var/lib/tftpboot/casper
sudo cp /mnt/casper/vmlinuz /var/lib/tftpboot/casper
sudo curl http://ports.ubuntu.com/ubuntu-ports/dists/RELEASE/main/uefi/grub2-arm64/current/grubnetaa64.efi.signed -o /var/lib/tftpboot/grubnetaa64.efi.signed
echo ""menuentry \""Netboot from Ubuntu Live image\"" {"" | sudo tee /var/lib/tftpboot/grub/grub.cfg
echo "" set gfxpayload=keep | sudo tee -a /var/lib/tftpboot/grub/grub.cfg
echo "" linux /casper/vmlinuz url=http://HOST/test-live-server-arm64.iso only-ubiquity ip=dhcp ---"" | sudo tee -a /var/lib/tftpboot/grub/grub.cfg
echo "" initrd /casper/initrd"" | sudo tee -a /var/lib/tftpboot/grub/grub.cfg
echo ""}"" | sudo tee -a /var/lib/tftpboot/grub/grub.cfg
Reconfigure the dhcp server for grubnetaa64.efi.signed as filename and next-server as installed Ubuntu machine. e.g. host testbed { hardware ethernet 00:00:00:11:22:33; next-server 192.168.10.1; filename ""grubnetaa64.efi.signed""; } Power on your arm64 machine and boot from ethernet. Connect to console output and you shall see grub menu. Press ENTER to load kernel and finish the installation. **If you finish the installation, please[submit](<>) a 'passed' result. If any action fails, or produces an unexpected result, please [submit](<>) a 'failed' result and [file a bug](<>). Please be sure to include the bug number when you [submit](<>) your result.**
