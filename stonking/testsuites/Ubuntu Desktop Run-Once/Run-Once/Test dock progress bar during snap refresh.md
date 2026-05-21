<p>This test will check that the "refresh progress bar" in the dock and in the "Activities view" does work as expected.</p>
<dl>
    <dt>Open a terminal and list the contents of the <strong>/snap</strong> folder by typing <strong>ls /snap</strong> (and RETURN key)</dt>
        <dd>You should see a list of folders, each one with the name of one installed snap</dd>
    <dt>Choose one snap that you have installed AND with its launch icon in the Dock. Let's say that we choose "Telegram" snap.</dt>
    <dt>Find the corresponding folder for that snap in the list shown in the terminal. In our example, it should be "telegram-desktop".</dt>
    <dt>Check which revisions are available by peeking inside its folder by typing <strong>ls /snap/SNAP-NAME</strong> (and RETURN key) in the terminal. In our example, it should be <strong>ls /snap/telegram-desktop</strong></dt>
        <dd>The last command should show three entries: one called <strong>current</strong> and two made with numbers (order is not important). In our example, it would show <strong>6168 6216 current</strong> (but the specific numbers can be different).</dd>
        <dd>If you only see two entries, <strong>current</strong> and one made with numbers, it means that your system has only one revision of that snap, so we can't use it for the test. Choose a different snap and repeat this check until you see two entries made with numbers.</dd>
    <dt>Revert the snap to the oldest revision, by typing the command <strong>sudo snap revert SNAP-NAME</strong> (and RETURN key) in the terminal. In our example, it would be <strong>sudo snap revert telegram-desktop</strong>, to revert it from revision 6216 to revision 6168.</dt>
        <dd>After several "progress messages", the command should end with a message telling you that the snap has been reverted to version X.Y.Z.</dd>
        <dd>If, instead, you receive an error message telling you that the snap can't be reverted because it has running apps, you must close all the apps from that snap and retry the command.</dd>
    <dt>Now, remove the newest revision by typing the command <strong>sudo snap remove SNAP-NAME --revision BIGGEST-NUMBER-IN-SNAP-FOLDER</strong> (and RETURN key) in the terminal. In our example, the command would be <strong>sudo snap remove telegram-desktop --revision 6216</strong>. This will remove the revision 6216 from your system and leave only the revision 6168. Remember, again, that these numbers in this example are "random"; yours can be different.</dt>
        <dd>You should receive a message telling you that the specified revision of the snap has been removed.</dd>
        <dd>If you receive an error telling you that it's not possible to remove the active revision, that means that the 'revert' command failed. Try again to revert the snap, or try with a different snap.</dd>
    <dt>Ensure that your dock is fully visible (just in case that you have enabled the <strong>intellihide</strong> option, and/or a window is covering it).</dt>
    <dt>Type the command <strong>sudo snap refresh SNAP-NAME</strong> (and RETURN key) in the terminal. In our example, the command should be <strong>sudo snap refresh telegram-desktop</strong>.</dt>
        <dd>A progress bar must appear over the icon of the chosen snap. The progress bar should increase along with the refresh process stages.</dd>
    <dt>While the progress bar is visible, click over the icon to launch the application.</dt>
        <dd>A message must pop-up over the icon informing that the snap can't be launched because it is being updated, and to try again later.</dd>
    <dt>When the <strong>refresh</strong> command ends, the progress bar must disappear. Clicking on the icon must launch the application.</dt>
</dl>
<strong>If all actions produce the expected results listed, please <a href="results#add_result">submit</a> a 'passed' result.
    If an action fails, or produces an unexpected result, please <a href="results#add_result">submit</a> a 'failed' result and <a href="../../buginstructions">file a bug</a>. Please be sure to include the bug number when you <a href="results#add_result">submit</a> your result.</strong>




