# Install (UEFI Secure Boot with nVidia)

This test is to ensure that the image boots in UEFI, that the resulting installation can boot in UEFI as well, regardless of network availability and that nVidia proprietary drivers are installed and loaded.
Boot up the image in UEFI mode with Secure Boot enabled.

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
  - Check the "Install third-party software for graphics and Wi-Fi hardware and additional media formats" option.
  - Click "Next".

* You should see the "Disk setup" page.
  - Select "Erase disk and install Ubuntu".
  - Click "Next".

* You should see the "Encryption and file system" page.
  - Select "No encryption".
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

* Open a terminal, run the following commands and verify their output (the exact output depends on your hardware):
  - `nvidia-smi`
    ```
    Thu Apr 23 11:40:22 2020       
    +-----------------------------------------------------------------------------+
    | NVIDIA-SMI 440.64       Driver Version: 440.64       CUDA Version: 10.2     |
    |-------------------------------+----------------------+----------------------+
    | GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
    | Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
    |===============================+======================+======================|
    |   0  GeForce MX150       Off  | 00000000:01:00.0 Off |                  N/A |
    | N/A   48C    P0    N/A /  N/A |      0MiB /  2002MiB |      0%      Default |
    +-------------------------------+----------------------+----------------------+

    +-----------------------------------------------------------------------------+
    | Processes:                                                       GPU Memory |
    |  GPU       PID   Type   Process name                             Usage      |
    |=============================================================================|
    |  No running processes found                                                 |
    +-----------------------------------------------------------------------------+
    ```
  - `sudo prime-supported`
    ```
    yes
    ```
  - `nvidia-settings`

    Verify that settings are displayed and you can configure the card.
    
----
**If all actions produce the expected results listed, please submit a `passed` result.**

**If an action fails, or produces an unexpected result, please submit a `failed` result and file a bug. Please be sure to include the bug number when you submit your result.**