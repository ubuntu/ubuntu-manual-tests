To execute this test, a pre-existing Ubuntu (or derivative) installation is needed *Proceed in your native language if you wish. Instructions will remain in English.*

Install all updates available for the release you want to upgrade by running update-manager. Click Check if any update is available, and click Install to install them
Ensure FAMILY is looking from all new versions by running 'Software & Updates'. Select the updates tab, and make sure the 'Notify me of a new FAMILY version' option has the 'For any new version' selection
Run update-manager -d -c from a terminal
Click the upgrade version button
Watch it upgrade, noting any errors
Reboot into your new system:
   -   Were any errors encountered during the upgrade?
-   Were any errors encountered after rebooting to new desktop?
-   Does your hardware still work properly?
-   Are you experiencing any application or background service crashes?
Open a terminal and enter the command `grep Prompt= /etc/update-manager/release-upgrades`
   For a *normal to normal*upgrade, terminal will show Prompt=normal
   For a *normal to LTS* upgrade, terminal will show Prompt=lts
   For a *LTS to normal* upgrade, terminal will show Prompt=normal
   For a *LTS to LTS* upgrade, terminal will show Prompt=lts
Open a terminal and enter the command `lsb_release -r`
   Terminal will show the upgraded version

**If all actions produce the expected results listed, please submit a 'passed' result. If an action fails, or produces an unexpected result, please submit a 'failed' result and file a bug. Please be sure to include the bug number when you submit your result.**