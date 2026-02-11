This test case is to be carried out on a Lenovo Thinkpad T14s or a similar supported Snapdragon X Elite laptop (Dell XPS 13 9345, Lenovo Yoga Slim 7x)

Boot up the image
   Ubuntu boot screen is displayed
Install Ubuntu, make sure to select the ""Install third-party software for graphics and Wi-Fi hardware"" option when it comes up and reboot once finished
   The system boots properly into the fresh installation and the first boot screen is displayed
On the freshly installed system run 'apt list --installed | grep x1e'
   hwe-lenovo-x1e-meta, ubuntu-x1e-settings-nogrub and ubuntu-x1e-settings show up in the list of installed packages
Run snap list
   The gnome-42-2204 snap is tracking adreno/stable and mesa-2404 is tracking beta/kisak
Install 'snap install --channel 22/stable graphics-test-tools' and run graphics-test-tools.glxinfo
   Hardware acceleration is detected: OpenGL vendor string is freedreno, OpenGL renderer string shows Adreno X1-85
Install 'snap install --channel 24/stable graphics-test-tools' and run graphics-test-tools.glxinfo
   Hardware acceleration is detected: OpenGL vendor string is freedreno, OpenGL renderer string shows Adreno X1-85
Reboot and add the 'break' kernel command line option before booting.
   The system boots into an interactive visible shell running in the initrd. This makes sure the frame buffer driver attaches early enough for initrd hooks like cryptsetup to have graphics support.

**If all actions produce the expected results listed, please submit a 'passed' result. If an action fails, or produces an unexpected result, please submit a 'failed' result and file a bug. Please be sure to include the bug number when you submit your result.**