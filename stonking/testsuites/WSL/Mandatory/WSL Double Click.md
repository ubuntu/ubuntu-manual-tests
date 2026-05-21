<p>This case tests the implicit provisioning (double-click install) of a tar-based WSL image.</p>

It requires a working Microsoft Windows 11 or higher installation with WSL version 2.4.10 or later. Installing Windows and enabling WSL 2 is outside of the scope of this  test case.

Since the release of Ubuntu LTS 24.04.2 Noble Numbat, tar-based images are found at <a href="https://cdimages.ubuntu.com/ubuntu-wsl/">https://cdimages.ubuntu.com/ubuntu-wsl/</a>
and their file extension is ".wsl" instead of ".tar.gz".

For example for latest noble image:  <a href="https://cdimages.ubuntu.com/ubuntu-wsl/noble/daily-live/pending/noble-wsl-amd64.wsl">https://cdimages.ubuntu.com/ubuntu-wsl/daily-live/noble/pending/noble-wsl-amd64.wsl</a>
Make sure to download the image matching the correct release under test from the download link associated to this test case.

Those images have cloud-init seeded. To make sure your environment doesn't contain any files that could
cause cloud-init to change the expected results of this test cases, remove the following directories on the
host (Windows) filesystem (if they exist):

<ul>
	<li>%USERPROFILE%\.cloud-init</li>
	<li>%USERPROFILE%\.ubuntupro\cloud-init</li>
</ul>

After downloading the image, navigate to it on Windows explorer:

<dl>
	<dt>Double-click the image to start the installation</dt>
		<dd>A new terminal window will pop-up showing the registration progress. In the end it will
		give instructions to start a new shell into the new instance. Take note of that command. For
		example (for noble):
<pre>
> wsl.exe -d Ubuntu-24.04
</pre>
		</dd>
		<dd>Verify that the new instance has been registered by running the following command:
<pre>
> wsl.exe --list --all --verbose
NAME             STATE           VERSION
*Ubuntu          Running         2
Ubuntu-24.04     Stopped         2
Ubuntu-20.04     Stopped         2
TestUbuntuWSL    Stopped         2
</pre>
		</dd>
		<dd>Check the the name used in previous command appears in the list.</dd>

	<dt>Launch the new instance. The provisioning (OOBE) command will run and eventually will prompt for
		the new user creation. The input line should be prefilled with a user name derived from the
		current Windows user name.</dt>
		<dd>In the example below the Windows user name is ubuntu
<pre>
> wsl -d Ubuntu-24.04
Provisioning the new WSL instance Ubuntu-24.04
This might take a while...
Create a default Unix user account: ubuntu
</pre></dd>
	<dd>Hit enter and proceed with the default user creation. Once done you should be running bash inside
	the distro instance
<pre>
Provisioning the new WSL instance Ubuntu-24.04
This might take a while...
Create a default Unix user account: ubuntu
New password:
Retype new password:
passwd: password updated successfully
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
</pre></dd>

		<dd>Verify that	you're running the right distribution (point) release. For example run:
<pre>
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 24.04.2 LTS
Release:        24.04
Codename:       noble
</pre> </dd>

	<dt>Check systemd status</dt>
		<dd>Tar-based images have systemd enabled by default, so make sure it's running and that there are no failed units:
<pre>
$ systemctl is-system-running
running
$ systemctl --failed
  UNIT LOAD ACTIVE SUB DESCRIPTION

  0 loaded units listed.
</pre></dd>

	<dt>The default user</dt>
		<dd>You should be logged in with the user that you just created
<pre>
$ whoami
ubuntu
</pre></dd>
		<dd>Run a command as root with sudo, for instance
<pre>$ sudo apt update</pre></dd>
		<dd>Verify that the command ends successfully</dd>
		<dd>Apply any update
<pre>$ sudo apt full-upgrade</pre></dd>
		<dd>Verify that the command ends successfully and that any packge that must be upgraded has been upgraded</dd>
		<dd>Install a package
<pre>$ sudo apt install hello</pre></dd>
		<dd>Verify that the package has been successfully installed and the application can run
<pre>
$ hello
Hello, world!
</pre></dd>

	<dt>Install and run graphical applications
	    </dt>
	    <dd>
<pre>
$ sudo apt install x11-apps gtk-4-examples
[...]
</pre>
	    </dd>
		<dd>Start one of the graphical application from the x11-apps package, like xcalc for example:
<pre>
$ xcalc
(Wait a moment until the application starts and is displayed)
</pre></dd>

		<dd>Start the GTK demo application with the default backend:
<pre>
$ gtk4-demo
(Wait a moment until the application starts and is displayed)
</pre></dd>

		<dd>Start the GTK demo application with the Wayland backend:
<pre>
$ GDK_BACKEND=wayland gtk4-demo
(Wait a moment until the application starts and is displayed)
</pre>
		It's possible that it fails due <a href="https://github.com/microsoft/WSL/issues/11261">this
			WSL bug</a>. To confirm that try again with a different XDG_RUNTIME_DIR as below:
<pre>
$ GDK_BACKEND=wayland XDG_RUNTIME_DIR=/mnt/wslg/runtime-dir gtk4-demo
(Wait a moment until the application starts and is displayed)
</pre>
		</dd>

	<dt>Check that Windows interoperability is still working
	</dt>
		<dd> Launch a Windows application
<pre>
> notepad.exe # It should open.
</pre>
		</dd>
		<dd> List the contents of the C:\Windows
<pre>
> ls -l /mnt/c/Windows
dr-xr-xr-x 1 root root     512 Feb 11 08:58  AppReadiness
dr-xr-xr-x 1 root root     512 Apr  1  2024  Boot
dr-xr-xr-x 1 root root     512 Apr  1  2024  Branding
dr-xr-xr-x 1 root root     512 Oct  7 14:37  BrowserCore
dr-xr-xr-x 1 root root     512 Jun  4  2024  CSCmnt
[...]
</pre>
		</dd>

	<dt>Exit WSL
	    </dt>
	    <dd>
<pre>logout</pre>
	    </dd>
		<dd>Check that your back to the PowerShell prompt</dd>

	<dt>Unregister the distro instance
	    </dt>
	    <dd>
<pre>
> wsl.exe --unregister Ubuntu-24.04
</pre>
	    </dd>
		<dd>The isntance no longer listed
<pre>
> wsl --list
Windows Subsystem for Linux Distributions:
Ubuntu (Default)
Ubuntu-20.04
TestUbuntuWSL
</pre></dd>

</dl>

<strong>If all actions produce the expected results listed, please <a href="results#add_result">submit</a> a 'passed' result.
    If an action fails, or produces an unexpected result, please <a href="results#add_result">submit</a> a 'failed' result and <a href="../../buginstructions">file a bug</a>. Please be sure to include the bug number when you <a href="results#add_result">submit</a> your result.</strong>


