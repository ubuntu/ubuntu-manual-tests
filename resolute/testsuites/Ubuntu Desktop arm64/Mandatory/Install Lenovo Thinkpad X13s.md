This test case is to be carried out on a Lenovo Thinkpad X13s

Boot up the image
    Ubuntu boot screen is displayed
Install Ubuntu, make sure to select the ""Install third-party software for graphics and Wi-Fi hardware"" option when it comes up and reboot once finished
    The system boots properly into the fresh installation and the first boot screen is displayed
On the freshly installed system run 'apt list --installed | grep x13s'
    hwe-lenovo-x13s-meta, ubuntu-x13s-settings-nogrub and ubuntu-x13s-settings show up in the list of installed packages
Reboot and add the 'break' kernel command line option before booting.
     The system boots into an interactive visible shell running in the initrd. This makes sure the frame buffer driver attaches early enough for initrd hooks like cryptsetup to have graphics support. 
**If all actions produce the expected results listed, please[submit](<>) a 'passed' result. If an action fails, or produces an unexpected result, please [submit](<>) a 'failed' result and [file a bug](<>). Please be sure to include the bug number when you [submit](<>) your result.**
