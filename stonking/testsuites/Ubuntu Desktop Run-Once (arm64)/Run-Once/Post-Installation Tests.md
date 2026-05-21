<dl>
    <dt>Login as the user you created, or ensure that you are auto-logged in as the user created during setup if you checked the auto-login option</dt>
        <dd>The new user's desktop is presented</dd>
    <dt>Execute the following commands on the command line:</dt>
    <dt><code>lsb_release -rd</code></dt>
        <dd>Both the description and the release presented matches the version of FAMILY you installed</dd>
    <dt><code>arch</code></dt>
        <dd>The result correctly lists the architecture of the installation you installed. For example, x86_64 for 64-bit x86 machine.</dd>
    <dt><code>sudo sfdisk -l</code></dt>
        <dd>The partition scheme displayed matches the partition scheme you chose during installation</dd>
    <dt><code>sudo apt-get update</code></dt>
        <dd>Apt hits each of the package mirrors and updates all of them without error</dd>
    <dt>Launch 'software-updater' (update-manager if launched via the terminal) and install any updates presented</dt>
        <dd>The updates are downloaded and installed without error</dd>
    <dt>Launch 'firefox' and navigate to http://www.ubuntu.com</dt>
        <dd>The ubuntu homepage is loaded and displays properly</dd>
    <dt>Launch 'Date & Time' settings menu and note the timezone information and local time and date</dt>
        <dd>The timezone, date and time should match the settings you selected during installation</dd>
    <dt>If you installed a non-english version of FAMILY, note the language used on the desktop</dt>
        <dd>The desktop should be localized into your language, or it should have prompted you upon initial login to install the missing components for your language</dd>
    <dt>After installing a system, follow the two test cases here to test the GNOME suite of applications:</dt>
        <dd>https://wiki.ubuntu.com/DesktopTeam/TestPlans/gjs</dd>
    <dt>This test case is primarily useful when there have been updates to gjs, but is still worthy of testing on every release.</dt>

</dl>
<strong>If all actions produce the expected results listed, please <a href="results#add_result">submit</a> a 'passed' result.
    If an action fails, or produces an unexpected result, please <a href="results#add_result">submit</a> a 'failed' result and <a href="../../buginstructions">file a bug</a>. Please be sure to include the bug number when you <a href="results#add_result">submit</a> your result.</strong>


