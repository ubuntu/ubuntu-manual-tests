This test will check that the ""refresh progress bar"" in the dock and in the ""Activities view"" does work as expected.

Open a terminal and list the contents of the **/snap** folder by typing **ls /snap** (and RETURN key)
   You should see a list of folders, each one with the name of one installed snap
Choose one snap that you have installed AND with its launch icon in the Dock. Let's say that we choose ""Telegram"" snap.
Find the corresponding folder for that snap in the list shown in the terminal. In our example, it should be ""telegram-desktop"".
Check which revisions are available by peeking inside its folder by typing **ls /snap/SNAP-NAME** (and RETURN key) in the terminal. In our example, it should be **ls /snap/telegram-desktop**
   The last command should show three entries: one called **current** and two made with numbers (order is not important). In our example, it would show **6168 6216 current** (but the specific numbers can be different).
   If you only see two entries, **current** and one made with numbers, it means that your system has only one revision of that snap, so we can't use it for the test. Choose a different snap and repeat this check until you see two entries made with numbers.
Revert the snap to the oldest revision, by typing the command **sudo snap revert SNAP-NAME** (and RETURN key) in the terminal. In our example, it would be **sudo snap revert telegram-desktop**, to revert it from revision 6216 to revision 6168.
   After several ""progress messages"", the command should end with a message telling you that the snap has been reverted to version X.Y.Z.
   If, instead, you receive an error message telling you that the snap can't be reverted because it has running apps, you must close all the apps from that snap and retry the command.
Now, remove the newest revision by typing the command **sudo snap remove SNAP-NAME --revision BIGGEST-NUMBER-IN-SNAP-FOLDER** (and RETURN key) in the terminal. In our example, the command would be **sudo snap remove telegram-desktop --revision 6216**. This will remove the revision 6216 from your system and leave only the revision 6168. Remember, again, that these numbers in this example are ""random""; yours can be different.
   You should receive a message telling you that the specified revision of the snap has been removed.
   If you receive an error telling you that it's not possible to remove the active revision, that means that the 'revert' command failed. Try again to revert the snap, or try with a different snap.
Ensure that your dock is fully visible (just in case that you have enabled the **intellihide** option, and/or a window is covering it).
Type the command **sudo snap refresh SNAP-NAME** (and RETURN key) in the terminal. In our example, the command should be **sudo snap refresh telegram-desktop**.
   A progress bar must appear over the icon of the chosen snap. The progress bar should increase along with the refresh process stages.
While the progress bar is visible, click over the icon to launch the application.
   A message must pop-up over the icon informing that the snap can't be launched because it is being updated, and to try again later.
When the **refresh** command ends, the progress bar must disappear. Clicking on the icon must launch the application.

**If all actions produce the expected results listed, please submit a 'passed' result. If an action fails, or produces an unexpected result, please submit a 'failed' result and file a bug. Please be sure to include the bug number when you submit your result.**