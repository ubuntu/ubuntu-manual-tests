# Install (entire disk with ZFS)

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
  - Select "Use ZFS without encryption".
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

----
**If all actions produce the expected results listed, please submit a `passed` result.**

**If an action fails, or produces an unexpected result, please submit a `failed` result and file a bug. Please be sure to include the bug number when you submit your result.**