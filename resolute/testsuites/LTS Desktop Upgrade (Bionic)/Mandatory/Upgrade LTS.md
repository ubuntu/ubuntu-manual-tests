To execute this test, a pre-existing Ubuntu (or derivative) installation is needed _Proceed in your native language if you wish. Instructions will remain in English._

Install all updates available for the release you want to upgrade by running update-manager, then click ""Install now"" to install the updates.
Ensure the upgrade process is looking for any new LTS version by running 'Software & Updates' or clicking ""Settings ..."" in update-manager. Select the updates tab, and make sure the 'Notify me of a new Ubuntu version' option has the 'For long-term support versions' value selected
Run update-manager -d -c from a terminal
Click the upgrade version button
Watch it upgrade, noting any errors
Reboot into your new system:
    

  * Were any errors encountered during the upgrade?
  * Were any errors encountered after rebooting to new desktop?
  * Does your hardware still work properly?
  * Are you experiencing any application or background service crashes?


Open a terminal and enter the command `grep Prompt= /etc/update-manager/release-upgrades`
    Terminal will show Prompt=lts
**If all actions produce the expected results listed, please [submit](<>) a 'passed' result. If an action fails, or produces an unexpected result, please [submit](<>) a 'failed' result and [file a bug](<>). Please be sure to include the bug number when you [submit](<>) your result.**
