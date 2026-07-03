This case tests provisioning tar-based WSL image with relevant cloud-config user data.

It requires a working Microsoft Windows 11 or higher installation with WSL version 2.4.10 or later. Installing Windows and enabling WSL 2 is outside of the scope of this  test case.

Since the release of Ubuntu LTS 24.04.2 Noble Numbat, tar-based images are found at [https://cdimages.ubuntu.com/ubuntu-wsl/](https://cdimages.ubuntu.com/ubuntu-wsl/)
and their file extension is ".wsl" instead of ".tar.gz".

For example for latest noble image:  [https://cdimages.ubuntu.com/ubuntu-wsl/noble/daily-live/pending/noble-wsl-amd64.wsl](https://cdimages.ubuntu.com/ubuntu-wsl/noble/daily-live/pending/noble-wsl-amd64.wsl)
Make sure to download the image matching the correct release under test from the download link associated to this test case.

Those images have cloud-init seeded. To make sure your environment doesn't contain any files that could
cause cloud-init to change the expected results of this test cases, empty the following directories on the
host (Windows) filesystem (if they exist):

- `%USERPROFILE%\.cloud-init`
- `%USERPROFILE%\.ubuntupro\cloud-init`

After downloading the image, open PowerShell and execute the test case below:

**Prepare the user data file**

Open a text editor of your choice, create a new file with the following contents and save it as
`%USERPROFILE%\.cloud-init\Ubuntu-24.04.user-data` (adjust the filename to match the
release version under test, here assumed to be noble):

```
#cloud-config
locale: en_GB
users:
- name: ubuntu
  gecos: Ubuntu User
  groups: [adm,dialout,cdrom,floppy,sudo,audio,dip,video,plugdev,netdev]
  sudo: ALL=(ALL) NOPASSWD:ALL
  shell: /bin/bash

write_files:
- path: /etc/wsl.conf
  append: true
  content: |
    [user]
    default=ubuntu

packages: [hello, x11-apps, gtk-4-examples]
```

**Install a new instance from the image you downloaded**

```
> wsl.exe --install --from-file .\noble-wsl-amd64.wsl
```

Verify that the new instance has been registered by running the following command:

```
> wsl.exe --list --all --verbose
NAME             STATE           VERSION
*Ubuntu          Running         2
Ubuntu-24.04     Stopped         2
Ubuntu-20.04     Stopped         2
TestUbuntuWSL    Stopped         2
```

**Launch the new instance.**

On the Windows Start Menu open the Windows Terminal. When open, at the top, at the right side of
the new tab button, click on the dropdown and select the "Ubuntu-24.04" profile. A new tab
will appear.

The provisioning (OOBE) command will run and eventually will run a shell
with the user described in the user data file logged in.

In the example below the Windows user name is ubuntu:

```
Provisioning the new WSL instance Ubuntu-24.04
This might take a while...
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

Welcome to Ubuntu 24.04.2 LTS (GNU/Linux 5.15.167.4-microsoft-standard-WSL2 x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/pro

 System information as of Tue Feb 11 11:43:37 -03 2025

  System load:  0.17                Processes:             31
  Usage of /:   0.1% of 1006.85GB   Users logged in:       0
  Memory usage: 6%                  IPv4 address for eth0: 172.22.8.90
  Swap usage:   15%

This message is shown once a day. To disable it please create the
/home/ubuntu/.hushlogin file.
ubuntu@mib01:/mnt/c/Users/ubuntu$
```

Read through the entire message of the day. Make sure there is no warnings nor errors coming from
cloud-init.

Verify that the background and foreground colors match the Ubuntu colors and the terminal
icon is the Ubuntu logo.

Verify that the text is rendered with the Ubuntu font.

Verify that you're running the right distribution (point) release. For example run:

```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 24.04.2 LTS
Release:        24.04
Codename:       noble
```

**Check systemd status**

Tar-based images have systemd enabled by default, so make sure it's running and that there are no failed units:

```
$ systemctl is-system-running
running
$ systemctl --failed
  UNIT LOAD ACTIVE SUB DESCRIPTION

  0 loaded units listed.
```

**The default user**

You should be logged in with the user that you just created:

```
$ whoami
ubuntu
```

Run a command as root with sudo, for instance:

```
$ sudo apt update
```

Verify that the command ends successfully.

Apply any update:

```
$ sudo apt full-upgrade
```

Verify that the command ends successfully and that any package that must be upgraded has been upgraded.

**CLI and graphical applications installed by cloud-init**

Verify that the "hello" package has been successfully installed and the application can run:

```
$ hello
Hello, world!
```

Start one of the graphical application from the x11-apps package, like xcalc for example:

```
$ xcalc
(Wait a moment until the application starts and is displayed)
```

Start the GTK demo application with the default backend:

```
$ gtk4-demo
(Wait a moment until the application starts and is displayed)
```

Start the GTK demo application with the Wayland backend:

```
$ GDK_BACKEND=wayland gtk4-demo
(Wait a moment until the application starts and is displayed)
```

It's possible that it fails due [this WSL bug](https://github.com/microsoft/WSL/issues/11261). To confirm that try again with a different XDG_RUNTIME_DIR as below:

```
$ GDK_BACKEND=wayland XDG_RUNTIME_DIR=/mnt/wslg/runtime-dir gtk4-demo
(Wait a moment until the application starts and is displayed)
```

**Check that Windows interoperability is still working**

Launch a Windows application:

```
> notepad.exe # It should open.
```

List the contents of the `C:\Windows`:

```
> ls -l /mnt/c/Windows
dr-xr-xr-x 1 root root     512 Feb 11 08:58  AppReadiness
dr-xr-xr-x 1 root root     512 Apr  1  2024  Boot
dr-xr-xr-x 1 root root     512 Apr  1  2024  Branding
dr-xr-xr-x 1 root root     512 Oct  7 14:37  BrowserCore
dr-xr-xr-x 1 root root     512 Jun  4  2024  CSCmnt
[...]
```

**Exit WSL**

```
logout
```

Check that your back to the PowerShell prompt.

**Unregister the distro instance**

```
> wsl.exe --unregister Ubuntu-24.04
```

The instance is no longer listed:

```
> wsl --list
Windows Subsystem for Linux Distributions:
Ubuntu (Default)
Ubuntu-20.04
TestUbuntuWSL
```

**If all actions produce the expected results listed, please [submit](results#add_result) a 'passed' result.
If an action fails, or produces an unexpected result, please [submit](results#add_result) a 'failed' result and [file a bug](../../buginstructions). Please be sure to include the bug number when you [submit](results#add_result) your result.**
