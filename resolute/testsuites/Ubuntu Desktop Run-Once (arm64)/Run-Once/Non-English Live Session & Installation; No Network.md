The goal of this test case is to check that localization support is functional during the installation from a live cd session, that language packs are installed correctly for those languages in the ISO, and that an informational message is shown prompting users to connect to the Internet to fully install language support for those languages not included. 

Boot up the image
Select a non-English language and press Enter
    The boot screen is displayed in the selected language
Select the Try FAMILY option
    Confirm after booting into live session that relevant items are in the correct language
Click the 'Install FAMILY' application on the desktop
Once Ubiquity starts click on Forward
Select the same non English language from the list and click Forward
Check your keyboard layout is correct or alter click Forward
Select Erase and use the entire disk and click Forward
Select your timezone and click Forward
Input your initial user details and password (Note admin can not be used it is a dedicated Linux User)
Tick Log in automatically and click on Forward
Check the details are correct on the final page and click Install
Once the installer has finished choose to Restart the system now
Remove the disc and press Enter
Allow the machine to reboot and login
Verify that your system is localized:
    

  * Language packs included in the Live CD: Bengali (bn), German (de), English (en), Spanish (es), French(fr), Portuguese (pt), Xhosa (xh) (Note: this list might vary between milestones)
  * If your language is one in the list above: 
    * Common translations are installed as part of language packs
    * A pop up shows saying your language support is not complete
  * If your language is not in the list above: 
    * Common translations in language packs will not be installed
    * A pop up shows saying your language support is not complete


Check that the calendar shows the regional settings correctly (Note: only in languages on the list above)
**If all actions produce the expected results listed, please [submit](<>) a 'passed' result. If an action fails, or produces an unexpected result, please [submit](<>) a 'failed' result and [file a bug](<>). Please be sure to include the bug number when you [submit](<>) your result.**
