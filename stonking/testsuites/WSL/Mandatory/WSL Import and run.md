This test case imports a WSL image from a rootfs and runs it.

It requires a working Microsoft Windows 11 or higher installation with WSL version 2.5.7 or later. Instructions about how to install Windows and enable WSL 2 is outside of the scope of this document.

To run this test you must download the image from [http://cloud-images.ubuntu.com/](http://cloud-images.ubuntu.com/)

> Since the release of Ubuntu LTS 24.04.2 Noble Numbat, new images are found at [https://cdimages.ubuntu.com/ubuntu-wsl/](https://cdimages.ubuntu.com/ubuntu-wsl/)
> and their file extension is ".wsl" instead of ".tar.gz".

For example for latest focal image download: [http://cloud-images.ubuntu.com/focal/current/focal-server-cloudimg-amd64-wsl.rootfs.tar.gz](http://cloud-images.ubuntu.com/focal/current/focal-server-cloudimg-amd64-wsl.rootfs.tar.gz)
and for the latest noble image:  [https://cdimages.ubuntu.com/ubuntu-wsl/noble/daily-live/pending/noble-wsl-amd64.wsl](https://cdimages.ubuntu.com/ubuntu-wsl/noble/daily-live/pending/noble-wsl-amd64.wsl)
Make sure to download the image from the download link associated to this test case.

Latest releases have cloud-init seeded. To make sure your environment doesn't contain any files that could
cause cloud-init to change the expected results of this test cases, remove the following directories on the
host (Windows) filesystem (if they exist):

- `%USERPROFILE%\.cloud-init`
- `%USERPROFILE%\.ubuntupro\cloud-init`

Open Windows Terminal or PowerShell and execute the test case below:

**Import the image in WSL**

```
> wsl.exe --import <name of the distro> <location to unpack rootfs> <rootfs> [--version <version of WSL>]
```

For example:

```
> wsl.exe --import Ubuntu20.04.3 .\wsl\ .\Downloads\focal-server-cloudimg-amd64-wsl.rootfs.tar.gz --version 2
```

Verify that the image has been imported by running the following command:

```
> wsl.exe --list --all --verbose
NAME             STATE           VERSION
*Ubuntu          Running         2
Ubuntu20.04.3    Stopped         2
Ubuntu-Preview   Stopped         2
Ubuntu-20.04     Stopped         2
TestUbuntuWSL    Stopped         2
```

Check the the name used in previous command appears in the list.

**Launch the newly installed application**

```
> wsl -d Ubuntu20.04.3
```

Verify that you're inside the WSL instance and running the right distribution. For example run:

```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 20.04.3 LTS
Release:        20.04
Codename:       focal
```

**Since Jammy (22.04) systemd is also enabled by default, so make sure it's running and that there are no
failed units:**

```
$ systemctl is-system-running
running
$ systemctl --failed
  UNIT LOAD ACTIVE SUB DESCRIPTION

  0 loaded units listed.
```

**Wait for cloud-init to finish its job, if it's present in the system (cloud-init is only present in recent releases):**

```
$ which cloud-init && cloud-init status --wait
/usr/bin/cloud-init

status: disabled
```

**Since the image has been installed directly and not with the distro launcher, you're logged in a root by default and have to create a first user manually. But first, verify that there is no other user already created by default:**

```
$ id 1000
id: '1000': no such user: No such file or directory
$ id ubuntu
id: 'ubuntu': no such user
$ egrep ':100[0-9]:' /etc/passwd        # should output nothing.
```

**Create a new user named 'ubuntu':**

```
$ adduser ubuntu
Adding user `ubuntu' ...
Adding new group `ubuntu' (1000) ...
Adding new user `ubuntu' (1000) with group `ubuntu' ...
Creating home directory `/home/ubuntu' ...
Copying files from `/etc/skel' ...
New password:
Retype new password:
passwd: password updated successfully
Changing the user information for ubuntu
Enter the new value, or press ENTER for the default
Full Name []:
Room Number []:
Work Phone []:
Home Phone []:
Other []:
Is the information correct? [Y/n]
```

**Add the newly created user to the sudo group:**

```
$ usermod -aG sudo ubuntu
```

Verify that you can switch to the new user:

```
$ su ubuntu
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.
$ whoami
ubuntu
```

**Exit WSL.** Type CTRL+D twice until you're back to the PowerShell prompt.

**Start a WSL session directly with the newly created user.**

```
> wsl -d Ubuntu20.04.3 -u ubuntu
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

Welcome to Ubuntu 20.04.3 LTS (GNU/Linux 5.10.43.3-microsoft-standard-WSL2 x86_64)

* Documentation:  https://help.ubuntu.com
* Management:     https://landscape.canonical.com
* Support:        https://ubuntu.com/advantage

System information as of Mon Aug 23 03:31:35 PDT 2021

System load:  0.16               Processes:             8
Usage of /:   0.5% of 250.98GB   Users logged in:       0
Memory usage: 6%                 IPv4 address for eth0: 172.30.131.4
Swap usage:   0%

1 update can be applied immediately.
To see these additional updates run: apt list --upgradable

This message is shown once a day. To disable it please create the
/home/ubuntu/.hushlogin file.
ubuntu@WSL:/mnt/c/Users/ubuntu$
```

**Run a command as root with sudo, for instance**

```
$ sudo apt update
```

Verify that the command ends successfully.

**Apply any update**

```
$ sudo apt full-upgrade
```

Verify that the command ends successfully and that any package that must be upgraded has been upgraded.

**Install a package**

```
$ sudo apt install hello
```

Verify that the package has been successfully installed and the application can run: 

```
$ hello
Hello, world!
```

**Install a snap package**

```
$ sudo apt remove hello
```

Verify that the package has been successfully uninstalled and the application can run:

```
$ hello
Command 'hello' not found, but can be installed with:
sudo snap install hello  # version 2.10, or
sudo apt  install hello  # version 2.10-5build1
See 'snap info hello' for additional versions.
```

Then install the snap version:

```
$ sudo snap install hello
```

Verify that the package has been successfully installed and the application can run
(If `/snap/bin` is not automatically added to your `PATH` then run `source /etc/profile`): 

```
$ hello
Hello, world!
$ snap run hello
Hello, world!
```

**Install and run graphical applications**

```
$ sudo apt install x11-apps gtk-4-examples              # gtk-3-examples for focal
[...]
```

Start one of the graphical applications from the x11-apps package, like xcalc for example:

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

Try a graphical snap as well:

```
sudo snap install gnome-system-monitor
gnome-system-monitor
gnome-system-monitor
libpxbackend-1.0.so: cannot open shared object file: No such file or directory
Failed to load module: /home/user/snap/gnome-system-monitor/common/.cache/gio-modules/libgiolibproxy.so

(gnome-system-monitor:6963): Gtk-WARNING **: 16:02:47.323: Trying to measure GtkButton 0x5757299c71e0 for width of 80, but it needs at least 88

(gnome-system-monitor:6963): Gtk-CRITICAL **: 16:02:47.324: Allocation width too small. Tried to allocate 80x31, but GtkButton 0x5757299c71e0 needs at least 88x31.
```

_Some warnings may show up, the exact ones may depend on the application and version, but the window should render correctly and be functional_.

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
> wsl.exe --unregister Ubuntu20.04.3
```

The application is no longer listed:

```
> wsl --list
Windows Subsystem for Linux Distributions:
Ubuntu (Default)
Ubuntu-Preview
Ubuntu-20.04
TestUbuntuWSL
```

And the directory is either missing or empty:

```
> ls .\wsl
>
```

---- 

**If all actions produce the expected results listed, please submit a `passed` result.** 

**If an action fails, or produces an unexpected result, please submit a `failed` result and file a bug. Please be sure to include the bug number when you submit your result.**
