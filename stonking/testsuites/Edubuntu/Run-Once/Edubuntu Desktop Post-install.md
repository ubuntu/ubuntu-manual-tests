By default, Edubuntu is set-up to work for a collegiate/tertiary-level environment with all packages installed. In this test, we will re-configure it to be in an elementary/primary school-level environment and restrict access to some icons for non-admin users.
<dl>
    <dt>Log-in to the session</dt>
        <dd>Edubuntu desktop starts properly</dd>
    <dt>Open the Activities Overview and type "Edubuntu Installer"</dt>
        <dd>"Edubuntu Installer" launches, and updates packages. Close Qapt window.</dd>
    <dt>After a short wait, Edubuntu Installer main window will open.</dt>
        <dd>Uncheck all boxes except "ubuntu-edu-primary", "edubuntu-fonts", and check "Change_Default_Setup". Click "Modify Installed Package Selection".</dd>
    <dt>The next window will appear to select the default setup.</dt>
        <dd>Select the radio button for "Primary/Elementary". Click "Continue"</dd>
    <dt>You will be required to enter your password. Enter it and type "enter" or click "Authenticate"</dt>
    <dt>You will next be told what packages *may* be removed (which may not be accurate since some may be required by the primary school metapackage). Click "Continue".</dt>
        <dd>You will need to enter your password again to authenticate the package removal. This may take a while.</dd>
    <dt>The main window will come back. Close it.</dt>
    <dt>Log out and back in.</dt>
        <dd>The background should be changed and the favorites in the dock should be changed</dd>
</dl>
Next, we will check to make sure non-admin policies are working.
<dl>
    <dt>Open the Activities Overview and type "Edubuntu Menu Administration"</dt>
        <dd>The main window will come up with some pre-selected items.</dd>
    <dt>Choose an item or items to remove from the application overview.</dt>
        <dd><strong>REMEMBER THIS/THESE ITEM(S)!</strong></dd>
    <dt>Click "Apply (Password Required)", enter your password.</dt>
    <dt>Click "Close".
    </dt>
    <dt>Go to Settings</dt>
        <dd>Go to Users. Unlock. Enter your password.</dd>
        <dd>Add a user. Make sure this user is <strong>not</strong> an administrator. Set a password. Click "Add".</dd>
    <dt>Log Out</dt>
    <dt>Log in as this new user</dt>
    <dt>Verify that items selected in Edubuntu Menu Administration are <strong>NOT</strong> shown in the Applications Overview</dt>
</dl>
<strong>If all actions produce the expected results listed, please <a href="results#add_result">submit</a> a 'passed' result.
    If an action fails, or produces an unexpected result, please <a href="results#add_result">submit</a> a 'failed' result and <a href="../../buginstructions">file a bug</a>. Please be sure to include the bug number when you <a href="results#add_result">submit</a> your result.</strong>

