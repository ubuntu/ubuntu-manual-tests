**_DURING TESTING_**

In any applications you open during the testing, try to open **Help** , **Help -> Contents** and **Help -> Online help** from the menu 
    Does the application help open?
In any applications you open during the testing, try to look for missing icons
    Confirm that there are no missing/wrong icons in the applications you tested
**_POST-INSTALLATION_** **Xubuntu offline documentation**

Try to open **Applications -> Help**
    Does the Xubuntu offline documentation open?
**Network connections**

If you have access to several methods to connect to Internet, try to connect with them all
    Are you able to connect?
**Keyboard layouts**

Go to **Applications -> Settings Manager** , click on **Keyboard** and open the **Layout** tab
Add a few new keyboard layouts
Try to switch between layouts and test in a text editor or the terminal
    Confirm that you are able to switch between keyboard layouts
**Localization**

If you installed Xubuntu using English as the default keyboard layout and language, try to add different languages for your system:
Go to **Language Support** (**Applications -> Settings Manager -> Language Support**)
Press the **Install / Remove Languages...**
Select as many languages as you like, and install them by pressing the **Apply Changes** button
When they have been successfully installed, log out from the session, and select alternating languages at the login screen, next to the right of the session selector **(Xubuntu Session)**
    Confirm that the main menus and outputs in the desktop are translated
**New user**

Go to **Applications -> Settings Manager -> Users and Groups** and add a new user
Logout, and try to login as the new user
    You should be able to login
Logout, then log back in as the initial user
Remove the new user
**Screensaver**

Go to **Applications -> Settings Manager -> Screensaver**
Set the time to 2 or 3 minutes
    Is the screensaver activated (i.e. did the screen go blank)?
**Suspend**

If you are testing a laptop, repeat the following steps, one time for an open source graphics driver, and once again if you also have a device that's supported only with a proprietary driver:

Put your machine to sleep (**Applications -> Logout -> Suspend**)
Try to wake it up by either opening the laptop-lid or pressing the power-button
    Does it wake up succesfully?
Set up your machine to go to sleep after a short period of time
    Does it fall asleep after that time and does it wake up again successfully?
**OTHER PARTITIONS**

If you have a Windows partition...

    Confirm it is listed in the file manager
    Confirm you are able to read files from it
**PERIPHERALS**

Apart from the first point, the rest of this section is optional according to the devices in your possession. Please verify before testing any of the devices, that they are commonly known to have working drivers for Linux. While it's great for the community to get information about devices that don't, the purpose for ISO testing is to make sure the contents of the image are working as they're supposed to, and that no regressions have emerged since the previous milestones.

**Printer**

Plug in your printer and run **Applications -> System -> Printing**
If your printer doesn't show up, add it to the list (click **Add** and follow the wizard)
Try to print a test page
    Did the printer print the test page?

You can repeat the tests with all printers you have access to, including network printers.

**Bluetooth**

Try to pair a Bluetooth device using the Bluetooth symbol in the panel.
    Can you pair your computer and the other device?
Try to send a file from your device to your computer and the other way round
    Can you send and receive files with your computer?
**If all actions produce the expected results listed, please[submit](<>) a 'passed' result. If an action fails, or produces an unexpected result, please [submit](<>) a 'failed' result and [file a bug](<>). Please be sure to include the bug number when you [submit](<>) your result.**
