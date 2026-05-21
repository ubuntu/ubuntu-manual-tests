
<p><em>Proceed in your native language if you wish. Instructions will remain in English.</em></p>
<dl>

<dd><p><strong>This test involves installing a fresh system with zfs + encryption, then breaking the system in a post-install test step. If the system you are installing on is important to you, and you want to preserve the zfs+encryption installed system, do not do this test.</strong></dd>

<dt>Boot up the image</dt>
    <dd>If you see the GRUB boot menu you should see the following:</dd>
    <dd>
       <ul>
       <li>'Try or Install FAMILY'</li>
       <li>'FAMILY (safe graphics)'</li>
       <li>'OEM install (for manufacturers)'</li>
       <li>'Test memory' (only on BIOS systems)</li>
       </ul>
    </dd>
    <dd>The system boots properly and loads the installer displaying the Welcome dialog with language selection and 'Try FAMILY' and 'Install FAMILY' buttons</dd>
<dt>Click on the release notes hyperlink to confirm that a browser launches and you are taken to the release notes discourse page.</dt>
<dt>Click on the Install FAMILY button</dt>
    <dd>The 'Keyboard layout' screen appears</dd>
    <dd>The proposed keyboard corresponds with your keyboard</dd>
<dt>Select your keyboard layout and click on Continue</dt>
    <dd>The 'Updates and other software' screen is displayed</dd>
<dt>On the screen 'Updates and other software', note the availability of the following components</dt>
    <dd>Available options should represent the state of your system accurately</dd>
    <dd>For Mantic and later releases, the default install is a minimal install. Releases before Mantic the default is a 'full' install, complete with other apps a user might want. The new, default, install does not include these add-ons.</dd>
    <dd>
        <ul>
            <li>(If network is available) 'Download updates while installing FAMILY'</li>
            <li>(If on a 'laptop') 'Is plugged to a power source'</li>
            <li>'Install third-party software...' option available</li>
        </ul>
    </dd>
<dt>Click on the Continue button</dt>
    <dd>The 'Installation type' screen is displayed</dd>


<dt>Note the state of the 'Erase disk and install FAMILY' radio button</dt>
    <dd>The 'Erase disk and install FAMILY' radio button is selected and the 'Advanced features' button is active</dd>
    <dt>Click on the 'Advanced features...' button</dt>
    <dd>The 'Advanced Features' dialog is displayed</dd>
<dt>Select 'Erase disk and use ZFS'</dt>
    <dd>'Erase disk and use ZFS' is selected</dd>
    <dd>Check the tickbox for 'Encrypt the new Ubuntu installation for security'</dd>
<dt>Click on the 'OK' button</dt>
    <dd>The dialog closes and 'ZFS selected' is displayed next to the 'Advanced features...' button</dd>
<dt>Click Continue</dt>
<dt>The "Choose a security key" slide opens</dt>
    <dd>Enter your desired security key</dd>
<dt>Click on the 'Install Now' button</dt>
    <dd>'Write the changes to disks' dialogue appears</dd>
<dt>Click Continue</dt>
<dt>If there is only one hard disk, skip to step 18 (On the 'Where are you?' screen...). Otherwise, on the 'Installation type' screen verify that the drive selected on the Select drive list corresponds to the drive on the chart (e.g /dev/sda)</dt>
    <dd>Selected drive is displayed on the chart</dd>
<dt>Verify that the full drive space is allocated</dt>
    <dd>Full drive space is allocated for installation</dd>
<dt>Click on the Install Now button</dt>
    <dd>The 'Where are you?' screen is displayed</dd>


<dt>If your system is connected to the network, note the preselected timezone corresponds with your timezone and the city indicated in the text box</dt>
    <dd>The timezone and city displayed match your timezone and a major city from your area</dd>
<dt>Select your timezone, and click on the Continue button</dt>
    <dd>The 'Who are you?' screen appears</dd>
<dt>Input your initial user details and password <em>admin can not be used - it is a dedicated Linux User</em></dt>
    <dd>'Require my password to log in' is shown and selected or if 'Log in automatically' and 'require my password to log in' are shown then 'Require my password to login' is selected. If just 'Require my password to log in' is shown, having it off is the equivalent of having 'Log in automatically' on.</dd>
    <dd>Name, username and password are accepted.</dd>
    <dd>Continue button becomes available</dd>
<dt>Press Continue</dt>
    <dd>The 'Welcome to FAMILY' slide is displayed</dd>
    <dd>The slideshow is entirely in your language</dd>
<dt>Wait for the installer to finish</dt>
    <dd>An 'Installation Complete' dialog appears</dd>
<dt>Click the 'Restart Now' button</dt>
    <dd>GUI is shut down, a prompt to remove media and press Enter appears</dd>
<dt>Remove the disc and press enter</dt>
    <dd>The machine is rebooted</dd>


<dt>Allow the machine to reboot</dt>
    <dd>The system boots properly and your passphrase works</dd>
    <dd>The system loads into FAMILY showing username selected</dd>
    <dd>Upon login, open a terminal, run the following commands and verify it matches the output</dd>
    <dd><code>$ zfs mount | sort
        bpool/BOOT/ubuntu_UUID        /boot
        rpool/ROOT/ubuntu_UUID        /
        rpool/ROOT/ubuntu_UUID/srv    /srv
        rpool/ROOT/ubuntu_UUID/usr/local  /usr/local
        rpool/ROOT/ubuntu_UUID/var/games  /var/games
        rpool/ROOT/ubuntu_UUID/var/lib/AccountsService  /var/lib/AccountsService
        rpool/ROOT/ubuntu_UUID/var/lib/apt  /var/lib/apt
        rpool/ROOT/ubuntu_UUID/var/lib/dpkg  /var/lib/dpkg
        rpool/ROOT/ubuntu_UUID/var/lib/NetworkManager  /var/lib/NetworkManager
        rpool/ROOT/ubuntu_UUID/var/lib  /var/lib
        rpool/ROOT/ubuntu_UUID/var/log  /var/log
        rpool/ROOT/ubuntu_UUID/var/mail  /var/mail
        rpool/ROOT/ubuntu_UUID/var/snap  /var/snap
        rpool/ROOT/ubuntu_UUID/var/spool  /var/spool
        rpool/ROOT/ubuntu_UUID/var/www  /var/www
        rpool/USERDATA/root_0y7dio      /root
        rpool/USERDATA/u_0y7dio         /home/u
    </code></dd>
<dt>Run the lsblk command and check for this line in the output:</dt>
  <dd>cryptoswap   252:1    0   2.6G  0 crypt [SWAP]</dd>
<dt>Run the following command to place a file under ~:</dt>
  <dd>echo "hello" &gt; /home/$USER/hello</dd>
  <dd>We're going to check for this file in a later part of this test case.</dd>


<dt>Shut down the installed system.</dt>
<dt>Using the same .iso, boot into the iso using the disk that you just completed the installation on.</dt>
<dt>Go through the grub menu and instead of installing, select "Try Ubuntu".</dt>
<dt>Open a terminal window, and enter the following:</dt>
    <dd>sudo su</dd>
    <dd>fdisk -l /dev/$disk # Where $disk is the disk you completed the install on.</dd>
<dt>The output should include something similar to the following:</dt>
    <dd><code>/dev/vda1      2048     4095     2048    1M BIOS boot
              /dev/vda2      4096  1054719  1050624  513M EFI System
              /dev/vda3   1054720  9037823  7983104  3.8G Linux swap
              /dev/vda4   9037824 13178879  4141056    2G Solaris boot
              /dev/vda5  13178880 83884031 70705152 33.7G Solaris root</code></dd>
    <dd>For the rest of this testcase, we will use vda in place of $disk.</dd>
<dt>Check for the zfs pool names:</dt>
    <dd>blkid /dev/vda*</dd>
    <dd><code>/dev/vda: PTUUID="7dd06581-4867-4632-9a90-23d9c472b039" PTTYPE="gpt"
              /dev/vda1: PARTUUID="c061c581-06c1-43e2-8680-d353771bf341"
              /dev/vda2: UUID="2748-996B" BLOCK_SIZE="512" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="f7c29e7e-687f-4cbb-a1a1-f8876f809a64"
              /dev/vda3: UUID="8c1d6471-1f90-4212-8fbd-097a9a9ad909" TYPE="crypto_LUKS" PARTUUID="8ff61492-9bda-40fe-94a8-7d6fe4d220cb"
              /dev/vda4: LABEL="bpool" UUID="8851209407646287070" UUID_SUB="1631837207961890120" BLOCK_SIZE="4096" TYPE="zfs_member" PARTUUID="8b8b8818-cc94-42bd-b23d-cf7c9e9b73ff"
              /dev/vda5: LABEL="rpool" UUID="4519996901618382696" UUID_SUB="8860607139843727357" BLOCK_SIZE="4096" TYPE="zfs_member" PARTUUID="5cc65ba9-8ef4-475c-a107-cc130a9be1be"</code></dd>
    <dd>Here, the zfs pool names are the labels of the drives of TYPE "zfs_member". So in this case, the zfs pools are "bpool" and "rpool".</dd>
<dt>Now, we will import the pool of the root partition:</dt>
    <dd>zpool import rpool</dd>
<dt>Check the output of the following command to see that rpool is imported:</dt>
    <dd>zpool status -v</dd>
<dt>After entering the following command, enter your security key in the prompt:</dt>
    <dd>cryptsetup luksOpen /dev/zvol/rpool/keystore keystore</dd>
<dt>Mount the keystore:</dt>
    <dd>mkdir /mnt/keystore</dd>
    <dd>mount /dev/mapper/keystore /mnt/keystore</dd>
<dt>Copy the key to necessary location:</dt>
    <dd>mkdir -p /run/keystore/rpool</dd>
    <dd>cp -b /mnt/keystore/system.key /run/keystore/rpool</dd>
<dt>Make the root pool mountable:</dt>
    <dd>zfs set canmount=on rpool</dd>
<dt>Load the zfs key:</dt>
    <dd>zfs load-key rpool</dd>
<dt>Check for the pool associated with the userdata:</dt>
    <dd>zfs list -o name,type,keylocation</dd>
<dt>You want to find a line in the output of the above command in this format:</dt>
    <dd>$poolname/USERDATA/$username_$hash</dd>
    <dd>For example: rpool/USERDATA/tim_aqj46w</dd>
<dt>Set mountpoint for USERDATA:</dt>
    <dd>mkdir -p /mnt/rpool/USERDATA/tim_aqj46w</dd>
    <dd>zfs set mountpoint=/mnt/rpool/USERDATA/tim_aqj46w rpool/USERDATA/tim_aqj46w</dd>
<dt>Mount the pool:</dt>
    <dd>zfs mount -a</dd>
<dt>Check for the test file we made earlier, for example:</dt>
    <dd>cat /mnt/rpool/USERDATA/tim_aqj46w/hello</dd>
    <dd>The output should be "hello"</dd>


</dl>
<p>If <strong>all</strong> actions produce the expected results described,
  please <a href="results#add_result">submit</a> a 'passed' result.</p>
<p>If <strong>any</strong> action fails, or produces an unexpected result,
  please <a href="results#add_result">submit</a> a 'failed' result and <a href="../../buginstructions">file a bug</a>. Please be sure to include
  the bug number when you <a href="results#add_result">submit</a> your
  result.</p>


