# PXE UEFI Netboot (Desktop Live)

The purpose of this testcase is to run netboot installation on amd64 machines
with **UEFI** firmware using live images. You need an installed Ubuntu machine
in the same network, configured with a static IP, which will be functioning as
a PXE server with DHCP. This testcase includes instructions for setting up the
PXE server with DHCPv4 via dnsmasq. You can find additional information and alternative
methods of setting up DHCP at [https://wiki.ubuntu.com/UEFI/SecureBoot/PXE-IPv6](https://wiki.ubuntu.com/UEFI/SecureBoot/PXE-IPv6).

*Proceed in your native language if you wish. Instructions will remain in
English.*

- HOST is the IP address of the machine acting as the PXE server.
- NETBOOT-URL is the compressed netboot artifacts archive, as listed in the
  download links for the test case.
- ISO-URL is the url for the installation ISO, as listed in the
  download links for the test case.
- INTERFACE is the relevant network interface on the PXE server.
- STARTADDR and ENDADDR are the start and end points for dhcp addresses to
  be handed out on this test network. Choose appropriate values to match
  the static network configuration of the PXE server, and see the manpage for
  dnsmasq for more details.

Install dnsmasq on the PXE server:

1. sudo apt install -y dnsmasq

Configure the PXE server with DHCP and TFTP by modifying */etc/dnsmasq.conf* with:

```text
# Base DHCP and TFTP settings
interface=INTERFACE
bind-interfaces
dhcp-range=INTERFACE,STARTADDR,ENDADDR
enable-tftp
tftp-root=/srv/tftp

# PXE boot settings
dhcp-match=set:efi-x86_64,option:client-arch,7
dhcp-boot=tag:efi-x86_64,amd64/bootx64.efi
```

Restart dnsmasq:

1. sudo systemctl restart dnsmasq.service

Download and place the netboot artifacts:

1. sudo wget -O /tmp/netboot-artifacts.tar.gz NETBOOT-URL
2. sudo mkdir -p /srv/tftp/
3. sudo tar -zxvf /tmp/netboot-artifacts.tar.gz -C /srv/tftp/

Replace the kernel and initrd from the netboot artifacts with extracted
versions from the Desktop ISO:

1. sudo wget -O /tmp/desktop-installer.iso ISO-URL
2. sudo mkdir -p /mnt/desktop-iso/
3. sudo mount /tmp/desktop-installer.iso /mnt/desktop-iso/
4. sudo cp /mnt/desktop-iso/casper/vmlinuz /srv/tftp/amd64/linux
5. sudo cp /mnt/desktop-iso/casper/initrd /srv/tftp/amd64/initrd
6. sudo umount /mnt/desktop-iso

Update the grub configuration in the netboot directory to point to ISO-URL:

1. sudo sed -i -e 's?iso-url=[^ ]*?iso-url=ISO_URL?' /srv/tftp/amd64/grub/grub.cfg

Power on the test machine and ensure that it boots from the network device.
Complete the installation, using the provided defaults where possible.
Reboot the machine and ensure that you can log into the system with the username
and password you provided.

**If you finish the installation, please submit a 'passed' result.
If any action fails, or produces an unexpected result, please submit
a 'failed' result and file a bug. Please be sure to include
the bug number when you submit your result.**
