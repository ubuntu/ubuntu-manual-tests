A copy of Windows must already be installed for this test case. See <a href="https://wiki.ubuntu.com/Testing/Backing_Up">https://wiki.ubuntu.com/Testing/Backing_Up</a> for information on saving a Windows image for repeated installs.

<em>Proceed in your native language if you wish. Instructions will remain in English</em>

<dl>
    <dt>Switch on your machine and log in to Windows</dt>
    <dt>Take any FAMILY CDs out of your CD-ROM drives</dt>
    <dt><a href="../../downloads">Download the Wubi executable</a></dt>
    <dt>Double click on the saved executable</dt>
        <dd>The wubi program starts</dd>
    <dt>Click on Install inside Windows</dt>
    <dt>Ensure that the "Desktop Environment" drop down menu lists multiple supported distributions</dt>
    <dt>Add a username, select a language, and optionally enable some of the accessibility options (these don't appear to be functional)</dt>
    <dt>Type in your password twice and click on Install</dt>
        <dd>The (windows side) installation finishes</dd>
    <dt>Select Reboot now and click Finish and remove the cd</dt>
        <dd>The system reboots, and Windows Boot menu now has FAMILY Listed</dd>
    <dt>Press the down arrow to select FAMILY and press Enter</dt>
        <dd>The Automated Linux install will now install Linux for you and will then reboot</dd>
    <dt>On the Windows Boot menu select FAMILY again and press Enter</dt>
        <dd>FAMILY boots up</dd>
</dl>
<strong>If all actions produce the expected results listed, please <a href="results#add_result">submit</a> a 'passed' result.
    If an action fails, or produces an unexpected result, please <a href="results#add_result">submit</a> a 'failed' result and <a href="../../buginstructions">file a bug</a>. Please be sure to include the bug number when you <a href="results#add_result">submit</a> your result.</strong>


