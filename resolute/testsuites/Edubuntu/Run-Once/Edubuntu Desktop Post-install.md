By default, Edubuntu is set-up to work for a collegiate/tertiary-level environment with all packages installed. In this test, we will re-configure it to be in an elementary/primary school-level environment and restrict access to some icons for non-admin users.

Log-in to the session
   Edubuntu desktop starts properly
Open the Activities Overview and type ""Edubuntu Installer""
   ""Edubuntu Installer"" launches, and updates packages. Close Qapt window.
After a short wait, Edubuntu Installer main window will open.
   Uncheck all boxes except ""ubuntu-edu-primary"", ""edubuntu-fonts"", and check ""Change\_Default\_Setup"". Click ""Modify Installed Package Selection"".
The next window will appear to select the default setup.
   Select the radio button for ""Primary/Elementary"". Click ""Continue""
You will be required to enter your password. Enter it and type ""enter"" or click ""Authenticate""
You will next be told what packages \*may\* be removed (which may not be accurate since some may be required by the primary school metapackage). Click ""Continue"".
   You will need to enter your password again to authenticate the package removal. This may take a while.
The main window will come back. Close it.
Log out and back in.
   The background should be changed and the favorites in the dock should be changed

Next, we will check to make sure non-admin policies are working.

Open the Activities Overview and type ""Edubuntu Menu Administration""
   The main window will come up with some pre-selected items.
Choose an item or items to remove from the application overview.
   **REMEMBER THIS/THESE ITEM(S)!**
Click ""Apply (Password Required)"", enter your password.
Click ""Close"".
Go to Settings
   Go to Users. Unlock. Enter your password.
   Add a user. Make sure this user is **not** an administrator. Set a password. Click ""Add"".
Log Out
Log in as this new user
Verify that items selected in Edubuntu Menu Administration are **NOT** shown in the Applications Overview

**If all actions produce the expected results listed, please submit a 'passed' result. If an action fails, or produces an unexpected result, please submit a 'failed' result and file a bug. Please be sure to include the bug number when you submit your result.**