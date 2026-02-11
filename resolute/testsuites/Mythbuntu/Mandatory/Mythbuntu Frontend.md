The testcase tests the installation and basic functionality of a Frontend. You will need a MythTV backend in the network to do this testcase completely.

Go though the Ubiquity install as you would any other install. Most options won't matter for this testcase, but be sure to choose the following options
'
   -   Do NOT name the user mythtv
-   Automatic (Guided) Partitioning
-   ""Frontend""
-   If you have no remote, choose no remote suppport
-   For the security key, enter the PIN from the backend (in the backend testcase, this is set to 1234)
Once installation is finished, remove the installation media and reboot.
Once the machine boots up, it should boot into the frontend.
Select ""Watch TV"". (this will only work if you have a backend already in the network)
   The demo video should start playing.

**If all actions produce the expected results listed, please submit a 'passed' result. If an action fails, or produces an unexpected result, please submit a 'failed' result and file a bug. Please be sure to include the bug number when you submit your result**.