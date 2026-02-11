This test will make sure the Xubuntu Core upgrade will not pull in the xubuntu-desktop metapackage. 

Install the core task in a current release.
Obtain all updates for your system.
Make sure xubuntu-desktop is not installed.
Upgrade to the development release.
    This should upgrade without installing any metapackages.
This test will make sure a Xubuntu upgrade with neither xubuntu-core nor xubuntu-desktop will install xubuntu-core. 

Install the core task in a current release.
Obtain all updates for your system.
Uninstall both xubuntu-core and xubuntu-desktop, if installed.
Upgrade to the development release.
    This should install xubuntu-core during upgrade, and you should end up with out the xubuntu-desktop package
**If all actions produce the expected results listed, please[submit](<>) a 'passed' result. If an action fails, or produces an unexpected result, please [submit](<>) a 'failed' result and [file a bug](<>). Please be sure to include the bug number when you [submit](<>) your result.**
