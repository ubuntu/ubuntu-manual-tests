Login as the user you created, or ensure that you are auto-logged in as the user created during setup if you checked the auto-login option
    The new user's desktop is presented
Execute the following commands on the command line:
    
    
    lsb_release -rd

    Both the description and the release presented matches the version of FAMILY you installed
    
    
    arch

    The result correctly lists the architecture of the installation you installed. For example, x86_64 for 64-bit x86 machine.
    
    
    sudo sfdisk -l

    The partition scheme displayed matches the partition scheme you chose during installation
    
    
    sudo apt-get update

    Apt hits each of the package mirrors and updates all of them without error
Launch 'software-updater' (update-manager if launched via the terminal) and install any updates presented
    The updates are downloaded and installed without error
Launch 'firefox' and navigate to http://www.ubuntu.com
    The ubuntu homepage is loaded and displays properly
Launch 'Date & Time' settings menu and note the timezone information and local time and date
    The timezone, date and time should match the settings you selected during installation
If you installed a non-english version of FAMILY, note the language used on the desktop
    The desktop should be localized into your language, or it should have prompted you upon initial login to install the missing components for your language
After installing a system, follow the two test cases here to test the GNOME suite of applications:
    https://wiki.ubuntu.com/DesktopTeam/TestPlans/gjs
This test case is primarily useful when there have been updates to gjs, but is still worthy of testing on every release.
**If all actions produce the expected results listed, please[submit](<>) a 'passed' result. If an action fails, or produces an unexpected result, please [submit](<>) a 'failed' result and [file a bug](<>). Please be sure to include the bug number when you [submit](<>) your result.**
