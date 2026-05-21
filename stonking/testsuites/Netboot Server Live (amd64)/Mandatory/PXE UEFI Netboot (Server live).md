<p>
The purpose of this testcase is to run netboot installation on amd64 machines
with <b>UEFI</b> firmware using live images. You need an installed Ubuntu machine
in the same network, configured with a static IP, which will be functioning as
a PXE server with DHCP. This testcase includes instructions for setting up the
PXE server with DHCPv4 via dnsmasq. You can find additional information and alternative
methods of setting up DHCP at <a href="https://wiki.ubuntu.com/UEFI/SecureBoot/PXE-IPv6">https://wiki.ubuntu.com/UEFI/SecureBoot/PXE-IPv6</a>.

</p>

<em>
    Proceed in your native language if you wish. Instructions will remain in
    English.
</em>

<ul>
    <li>HOST is the IP address of the machine acting as the PXE server.</li>
    <li>NETBOOT-URL is the compressed netboot artifacts archive, as listed in the
    download links for the test case.</li>
    <li>INTERFACE is the relevant network interface on the PXE server.</li>
    <li>STARTADDR and ENDADDR are the start and end points for dhcp addresses to
    be handed out on this test network.  Choose appropriate values to match
    the static network configuration of the PXE server, and see the manpage for
    dnsmasq for more details.</li>
</ul>


<p>Install dnsmasq on the PXE server:</p>
<ol>
    <li>sudo apt install -y dnsmasq</li>
</ol>

<p>Configure the PXE server with DHCP and TFTP by modifying <i>/etc/dnsmasq.conf</i> with:</p>

<pre>
# Base DHCP and TFTP settings
interface=INTERFACE
bind-interfaces
dhcp-range=INTERFACE,STARTADDR,ENDADDR
enable-tftp
tftp-root=/srv/tftp

# PXE boot settings
dhcp-match=set:efi-x86_64,option:client-arch,7
dhcp-boot=tag:efi-x86_64,amd64/bootx64.efi
</pre>

<p>Restart dnsmasq:</p>

<ol>
    <li>sudo systemctl restart dnsmasq.service</li>
</ol>

<p>Download and place the netboot artifacts:</p>
<ol>
    <li>sudo wget -O /tmp/netboot-artifacts.tar.gz NETBOOT-URL </li>
    <li>sudo mkdir -p /srv/tftp/</li>
    <li>sudo tar -zxvf /tmp/netboot-artifacts.tar.gz -C /srv/tftp/</li>
</ol>



<p>
Power on the test machine and ensure that it boots from the network device.
Complete the installation, using the provided defaults where possible.
Reboot the machine and ensure that you can log into the system with the username
and password you provided.
</p>

<strong>If you finish the installation, please <a href="results#add_result">submit</a> a 'passed' result.
    If any action fails, or produces an unexpected result, please <a href="results#add_result">submit</a> a 'failed' result and <a href="../../buginstructions">file a bug</a>. Please be sure to include the bug number when you <a href="results#add_result">submit</a> your result.</strong>


