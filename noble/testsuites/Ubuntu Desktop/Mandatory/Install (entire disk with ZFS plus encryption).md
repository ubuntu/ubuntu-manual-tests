*Proceed in your native language if you wish. Instructions will remain in English.*

**This test involves installing a fresh system with zfs + encryption, then breaking the system in a post-install test step. If the system you are installing on is important to you, and you want to preserve the zfs+encryption installed system, do not do this test.**

Boot up the image
   If you see the GRUB boot menu you should see the following:
   -   'Try or Install FAMILY'
-   'FAMILY (safe graphics)'
-   'OEM install (for manufacturers)'
-   'Test memory' (only on BIOS systems)
   The system boots properly and loads the installer displaying the Welcome dialog with language selection and 'Try FAMILY' and 'Install FAMILY' buttons
Click on the release notes hyperlink to confirm that a browser launches and you are taken to the release notes discourse page.
Click on the Install FAMILY button
   The 'Keyboard layout' screen appears
   The proposed keyboard corresponds with your keyboard
Select your keyboard layout and click on Continue
   The 'Updates and other software' screen is displayed
On the screen 'Updates and other software', note the availability of the following components
   Available options should represent the state of your system accurately
   For Mantic and later releases, the default install is a minimal install. Releases before Mantic the default is a 'full' install, complete with other apps a user might want. The new, default, install does not include these add-ons.
   -   (If network is available) 'Download updates while installing FAMILY'
-   (If on a 'laptop') 'Is plugged to a power source'
-   'Install third-party software...' option available
Click on the Continue button
   The 'Installation type' screen is displayed
Note the state of the 'Erase disk and install FAMILY' radio button
   The 'Erase disk and install FAMILY' radio button is selected and the 'Advanced features' button is active
Click on the 'Advanced features...' button
   The 'Advanced Features' dialog is displayed
Select 'Erase disk and use ZFS'
   'Erase disk and use ZFS' is selected
   Check the tickbox for 'Encrypt the new Ubuntu installation for security'
Click on the 'OK' button
   The dialog closes and 'ZFS selected' is displayed next to the 'Advanced features...' button
Click Continue
The ""Choose a security key"" slide opens
   Enter your desired security key
Click on the 'Install Now' button
   'Write the changes to disks' dialogue appears
Click Continue
If there is only one hard disk, skip to step 18 (On the 'Where are you?' screen...). Otherwise, on the 'Installation type' screen verify that the drive selected on the Select drive list corresponds to the drive on the chart (e.g /dev/sda)
   Selected drive is displayed on the chart
Verify that the full drive space is allocated
   Full drive space is allocated for installation
Click on the Install Now button
   The 'Where are you?' screen is displayed
If your system is connected to the network, note the preselected timezone corresponds with your timezone and the city indicated in the text box
   The timezone and city displayed match your timezone and a major city from your area
Select your timezone, and click on the Continue button
   The 'Who are you?' screen appears
Input your initial user details and password *admin can not be used - it is a dedicated Linux User*
   'Require my password to log in' is shown and selected or if 'Log in automatically' and 'require my password to log in' are shown then 'Require my password to login' is selected. If just 'Require my password to log in' is shown, having it off is the equivalent of having 'Log in automatically' on.
   Name, username and password are accepted.
   Continue button becomes available
Press Continue
   The 'Welcome to FAMILY' slide is displayed
   The slideshow is entirely in your language
Wait for the installer to finish
   An 'Installation Complete' dialog appears
Click the 'Restart Now' button
   GUI is shut down, a prompt to remove media and press Enter appears
Remove the disc and press enter
   The machine is rebooted
Allow the machine to reboot
   The system boots properly and your passphrase works
   The system loads into FAMILY showing username selected
   Upon login, open a terminal, run the following commands and verify it matches the output
   `$ zfs mount | sort bpool/BOOT/ubuntu_UUID /boot rpool/ROOT/ubuntu_UUID / rpool/ROOT/ubuntu_UUID/srv /srv rpool/ROOT/ubuntu_UUID/usr/local /usr/local rpool/ROOT/ubuntu_UUID/var/games /var/games rpool/ROOT/ubuntu_UUID/var/lib/AccountsService /var/lib/AccountsService rpool/ROOT/ubuntu_UUID/var/lib/apt /var/lib/apt rpool/ROOT/ubuntu_UUID/var/lib/dpkg /var/lib/dpkg rpool/ROOT/ubuntu_UUID/var/lib/NetworkManager /var/lib/NetworkManager rpool/ROOT/ubuntu_UUID/var/lib /var/lib rpool/ROOT/ubuntu_UUID/var/log /var/log rpool/ROOT/ubuntu_UUID/var/mail /var/mail rpool/ROOT/ubuntu_UUID/var/snap /var/snap rpool/ROOT/ubuntu_UUID/var/spool /var/spool rpool/ROOT/ubuntu_UUID/var/www /var/www rpool/USERDATA/root_0y7dio /root rpool/USERDATA/u_0y7dio /home/u`
Run the lsblk command and check for this line in the output:
   cryptoswap 252:1 0 2.6G 0 crypt \[SWAP\]
Run the following command to place a file under ~:
   echo ""hello"" > /home/$USER/hello
   We're going to check for this file in a later part of this test case.
Shut down the installed system.
Using the same .iso, boot into the iso using the disk that you just completed the installation on.
Go through the grub menu and instead of installing, select ""Try Ubuntu"".
Open a terminal window, and enter the following:
   sudo su
   fdisk -l /dev/$disk # Where $disk is the disk you completed the install on.
The output should include something similar to the following:
   `/dev/vda1 2048 4095 2048 1M BIOS boot /dev/vda2 4096 1054719 1050624 513M EFI System /dev/vda3 1054720 9037823 7983104 3.8G Linux swap /dev/vda4 9037824 13178879 4141056 2G Solaris boot /dev/vda5 13178880 83884031 70705152 33.7G Solaris root`
   For the rest of this testcase, we will use vda in place of $disk.
Check for the zfs pool names:
   blkid /dev/vda\*
   `/dev/vda: PTUUID=""7dd06581-4867-4632-9a90-23d9c472b039"" PTTYPE=""gpt"" /dev/vda1: PARTUUID=""c061c581-06c1-43e2-8680-d353771bf341"" /dev/vda2: UUID=""2748-996B"" BLOCK_SIZE=""512"" TYPE=""vfat"" PARTLABEL=""EFI System Partition"" PARTUUID=""f7c29e7e-687f-4cbb-a1a1-f8876f809a64"" /dev/vda3: UUID=""8c1d6471-1f90-4212-8fbd-097a9a9ad909"" TYPE=""crypto_LUKS"" PARTUUID=""8ff61492-9bda-40fe-94a8-7d6fe4d220cb"" /dev/vda4: LABEL=""bpool"" UUID=""8851209407646287070"" UUID_SUB=""1631837207961890120"" BLOCK_SIZE=""4096"" TYPE=""zfs_member"" PARTUUID=""8b8b8818-cc94-42bd-b23d-cf7c9e9b73ff"" /dev/vda5: LABEL=""rpool"" UUID=""4519996901618382696"" UUID_SUB=""8860607139843727357"" BLOCK_SIZE=""4096"" TYPE=""zfs_member"" PARTUUID=""5cc65ba9-8ef4-475c-a107-cc130a9be1be""`
   Here, the zfs pool names are the labels of the drives of TYPE ""zfs\_member"". So in this case, the zfs pools are ""bpool"" and ""rpool"".
Now, we will import the pool of the root partition:
   zpool import rpool
Check the output of the following command to see that rpool is imported:
   zpool status -v
After entering the following command, enter your security key in the prompt:
   cryptsetup luksOpen /dev/zvol/rpool/keystore keystore
Mount the keystore:
   mkdir /mnt/keystore
   mount /dev/mapper/keystore /mnt/keystore
Copy the key to necessary location:
   mkdir -p /run/keystore/rpool
   cp -b /mnt/keystore/system.key /run/keystore/rpool
Make the root pool mountable:
   zfs set canmount=on rpool
Load the zfs key:
   zfs load-key rpool
Check for the pool associated with the userdata:
   zfs list -o name,type,keylocation
You want to find a line in the output of the above command in this format:
   $poolname/USERDATA/$username\_$hash
   For example: rpool/USERDATA/tim\_aqj46w
Set mountpoint for USERDATA:
   mkdir -p /mnt/rpool/USERDATA/tim\_aqj46w
   zfs set mountpoint=/mnt/rpool/USERDATA/tim\_aqj46w rpool/USERDATA/tim\_aqj46w
Mount the pool:
   zfs mount -a
Check for the test file we made earlier, for example:
   cat /mnt/rpool/USERDATA/tim\_aqj46w/hello
   The output should be ""hello""

If **all** actions produce the expected results described, please submit a 'passed' result.

If **any** action fails, or produces an unexpected result, please submit a 'failed' result and file a bug. Please be sure to include the bug number when you submit your result.