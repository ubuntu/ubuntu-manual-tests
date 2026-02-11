The testcase tests the installation and basic functionality of a Primary Backend with Frontend.

Go though the Ubiquity install as you would any other install. Most options won't matter for this testcase, but be sure to choose the following options
   -   Do NOT name the user mythtv
-   Automatic (Guided) Partitioning
-   ""Primary Backend w/ Frontend""
-   ""MythTV service"" checkbox is checked
-   If you have no remote, choose no remote suppport
Once installation is finished, remove the installation media and reboot.
Once the installed system boots, it will boot into the MythTV frontend. Exit the frontend by hitting escape and selecting ""yes, exit now""
Download a demo file. I recommend a MP4 trailer (for example, the 480p MP4 trailer at http://www.sintel.org/download ).
Once downloaded, move this file to the /srv/ directory (it must be outside your home directory)
Change ownership on the test file to mythtv:mythtv
Open the Applications menu and choose system and then ""Mythtv backend setup"".
Say yes to stop the running mythtv-backend service
Once in mythtv-setup, go to ""1. General""
On the first screen, edit the following options
   -   IP Address (Under Local Backend): \[use the machine's IP address (not 127.0.0.1)\]
-   Security PIN (required): 1234
-   IP Address (Under Master Backend): \[use the machine's IP address (not 127.0.0.1)\]
Hit next until you get back to the main menu
Go to ""2. Capture cards"" and select ""(New capture card)""
Setup the new card using the following options
   -   Card Type: Import test recorder
-   File path: file:/srv/sintel\_trailer-480p.mp4
   When you put in the file path, it should detect the ""File info"" and ""File size""
Hit Finish, then escape to go back to the main menu
Go to ""4. Video sources"" and select ""(New video source)""
Setup the video source with the following options
   -   Video source name: NoGrabber
-   Listings grabber: No grabber
Hit Finish, then escape to go back to the main menu
Go to ""5. Input connections"", and select the only option in there (the DEMO recorder)
Setup as follows
   -   Video source: NoGrabber
Hit Next, then finish, then escape to go back to the main menu.
Hit escape and exit the backend setup.
   You may get a warning that the tuner is set to start on a channel that doesn't exist. This can be safely ignored since we are using a test recorder.
Select yes to start the backend
Select no when prompted to run mythfilldatabase
Start the frontend via Applications > Multimedia > MythTV Frontend
Select ""Watch TV"".
   The demo video should start playing.

**If all actions produce the expected results listed, please submit a 'passed' result. If an action fails, or produces an unexpected result, please submit a 'failed' result and file a bug. Please be sure to include the bug number when you submit your result**.