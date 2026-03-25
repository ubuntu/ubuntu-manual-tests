# Install (entire disk with ZFS plus encryption)

* Boot up the image
  - If you see the GRUB menu, select the "Try or install Ubuntu" option to boot into the live session.

* Wait for the system to boot into the live session. The desktop installer should open automatically and play a welcome sound.

* You should see the "Choose your language" page.
  - Pick your desired language. (The instructions will remain in English).
  - Click "Next".

* You should see the "Accessibility" page.
  - Click through the options, (Seeing, Hearing, Typing, Pointing and clicking, Zoom) and make sure the drop down options are fully functional.
  - Click "Next".

* You should see the "Keyboard layout" page.
  - Choose your desired layout.
  - Click "Next".

* You should see the "Connect to the internet" page.
  - Use the UI to connect to a network.
  - Click "Next".

* You should see the "Try or install Ubuntu" page.
  - Click "Install Ubuntu".

* You should see the "Type of installation" page.
  - Select "Interactive installation".
  - Click "Next".

* You should see the "Applications" page.
  - Select "Default selection".
  - Click "Next".

* You should see the "Optimise your computer" page.
  - Leave the checkboxes unchecked.
  - Click "Next".

* You should see the "Disk setup" page.
  - Select "Erase disk and install Ubuntu".
  - Click "Next".

* You should see the "Encryption and file system" page.
  - Click on "Advanced opttions".
  - Select "Encrypt with a passphrase using ZFS".
  - Click "Next".

* You should see the "Set an encryption passphrase" page.
  - Enter your desired passphrase.
  - Click "Next".

* You should see the "Create your account" page.
  - Fill in the details for your user account.
  - Click "Next".

* You should see the "Select your timezone" page.
  - If your system is connected to the internet, verify that the timezone that was auto-detected is accurate.
  - Click "Next".

* You should see the "Ready to install" page.
  - Check that the summary of the installation options you selected throughout the process is accurate.
  - Click "Install".

* You should see a slideshow while the installation is taking place.
  - Wait for the installation to complete.

* You should see the "Installation complete" page.
  - Click "Restart Now".

* Allow the machine to reboot.

* You should see the login screen with the username you created during the installation process.
  - Log in with the password you set during the installation process.

* Open a terminal, run the following commands and verify their output:
    - `zfs mount | sort`
      ```
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
      ```

    - `lsblk`, and check for this line in the output:
      ```
      cryptoswap   252:1    0   2.6G  0 crypt [SWAP]
      ```

* Run the following command to create a test file in the home directory:
    - `echo "hello" > /home/$USER/hello && sync`
    - We're going to check for this file in a later part of this test case.

* Shut down the installed system.

* Using the same .iso, boot into the iso using the disk that you just completed the installation on.

* Go through the grub menu and instead of installing, select "Try Ubuntu".

* Open a terminal window, and run the following commands:
    - `sudo su`
    - `fdisk -l /dev/$disk`,  Where `$disk` is the disk you completed the install on.
    - The output should include something similar to the following:
        ```
        /dev/vda1      2048     4095     2048    1M BIOS boot
        /dev/vda2      4096  1054719  1050624  513M EFI System
        /dev/vda3   1054720  9037823  7983104  3.8G Linux swap
        /dev/vda4   9037824 13178879  4141056    2G Solaris boot
        /dev/vda5  13178880 83884031 70705152 33.7G Solaris root
        ```
    - For the rest of this testcase, we will use `vda` in place of `$disk`.

* Check for the zfs pool names:
    - `blkid /dev/vda*`
        ```
        /dev/vda: PTUUID="7dd06581-4867-4632-9a90-23d9c472b039" PTTYPE="gpt"
        /dev/vda1: PARTUUID="c061c581-06c1-43e2-8680-d353771bf341"
        /dev/vda2: UUID="2748-996B" BLOCK_SIZE="512" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="f7c29e7e-687f-4cbb-a1a1-f8876f809a64"
        /dev/vda3: UUID="8c1d6471-1f90-4212-8fbd-097a9a9ad909" TYPE="crypto_LUKS" PARTUUID="8ff61492-9bda-40fe-94a8-7d6fe4d220cb"
        /dev/vda4: LABEL="bpool" UUID="8851209407646287070" UUID_SUB="1631837207961890120" BLOCK_SIZE="4096" TYPE="zfs_member" PARTUUID="8b8b8818-cc94-42bd-b23d-cf7c9e9b73ff"
        /dev/vda5: LABEL="rpool" UUID="4519996901618382696" UUID_SUB="8860607139843727357" BLOCK_SIZE="4096" TYPE="zfs_member" PARTUUID="5cc65ba9-8ef4-475c-a107-cc130a9be1be"
        ```
    - Here, the zfs pool names are the labels of the drives of TYPE `zfs_member`. So in this case, the zfs pools are `bpool` and `rpool`.

* Now, we will import the pool of the root partition:
    - `zpool import rpool`
* Check the output of the following command to see that rpool is imported: 
    - `zpool status -v`
* After entering the following command, enter your security key in the prompt:
    - `cryptsetup luksOpen /dev/zvol/rpool/keystore keystore`
* Mount the keystore:
    - `mkdir /mnt/keystore`
    - `mount /dev/mapper/keystore /mnt/keystore`
* Copy the key to necessary location:
    - `mkdir -p /run/keystore/rpool`
    - `cp -b /mnt/keystore/system.key /run/keystore/rpool`
* Make the root pool mountable:
    - `zfs set canmount=on rpool`
* Load the zfs key:
    - `zfs load-key rpool`
* Check for the pool associated with the userdata:
    - `zfs list -o name,type,keylocation`
* You want to find a line in the output of the above command in this format:
    - `$poolname/USERDATA/$username_$hash`
    - For example: `rpool/USERDATA/tim_aqj46w`
* Set mountpoint for USERDATA:
    - `mkdir -p /mnt/rpool/USERDATA/tim_aqj46w`
    - `zfs set mountpoint=/mnt/rpool/USERDATA/tim_aqj46w rpool/USERDATA/tim_aqj46w`
* Mount the pool:
    - `zfs mount -a`
* Check for the test file we made earlier, for example:
    - `cat /mnt/rpool/USERDATA/tim_aqj46w/hello`
    - The output should be "hello"

----
**If all actions produce the expected results listed, please submit a `passed` result.**

**If an action fails, or produces an unexpected result, please submit a `failed` result and file a bug. Please be sure to include the bug number when you submit your result.**