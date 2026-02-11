The purpose of this testcase is to run netboot installation on amd64 machines with **BIOS** firmware using live images. You need an installed Ubuntu machine in the same network, configured with a static IP, which will be functioning as a PXE server with DHCP. This testcase includes instructions for setting up the PXE server with DHCPv4 via dnsmasq. You can find additional information and alternative methods of setting up DHCP at https://wiki.ubuntu.com/UEFI/SecureBoot/PXE-IPv6.

*Proceed in your native language if you wish. Instructions will remain in English.*

-   HOST is the IP address of the machine acting as the PXE server.
-   NETBOOT-URL is the compressed netboot artifacts archive, as listed in the download links for the test case.
-   INTERFACE is the relevant network interface on the PXE server.
-   STARTADDR and ENDADDR are the start and end points for dhcp addresses to be handed out on this test network. Choose appropriate values to match the static network configuration of the PXE server, and see the manpage for dnsmasq for more details.

Install dnsmasq on the PXE server:

1.  sudo apt install -y dnsmasq

Configure the PXE server with DHCP and TFTP by modifying */etc/dnsmasq.conf* with:

\# Base DHCP and TFTP settings
interface=INTERFACE
bind-interfaces
dhcp-range=INTERFACE,STARTADDR,ENDADDR
enable-tftp
tftp-root=/srv/tftp

# PXE boot settings
dhcp-boot=amd64/pxelinux.0

Restart dnsmasq:

1.  sudo systemctl restart dnsmasq.service

Download and place the netboot artifacts:

1.  sudo wget -O /tmp/netboot-artifacts.tar.gz NETBOOT-URL
2.  sudo mkdir -p /srv/tftp/
3.  sudo tar -zxvf /tmp/netboot-artifacts.tar.gz -C /srv/tftp/

Power on the test machine and ensure that it boots from the network device. Complete the installation, using the provided defaults where possible. Reboot the machine and ensure that you can log into the system with the username and password you provided.

**If you finish the installation, please submit a 'passed' result. If any action fails, or produces an unexpected result, please submit a 'failed' result and file a bug. Please be sure to include the bug number when you submit your result.**