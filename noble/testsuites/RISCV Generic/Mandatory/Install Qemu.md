The scope of this test is to ensure that riscv64+unleashed and riscv64+unmatched images boot in qemu. 

Boot with qemu
    Follow instructions from the [documentation](<>) on how to boot with QEMU
Login and change password
    Login using ubuntu for both username and password
    Reenter ubuntu password again
    Set new password
    Confirm the new password
Perform generic testing
    Check that apt update works
    Run any command that is not installed, check that command-not-found recommends things to install
    e.g. hello
    Install a package and check that it works, e.g. hello
Perform snap testing
    Install a snap and check that it works, e.g. hello
Poweroff
    Console messages should reach poweroff target
    There should be final kernel dmsg powering off
    Press ""CTRL+a c"" and type quit
**If all actions produce the expected results listed, please[submit](<>) a 'passed' result. If an action fails, or produces an unexpected result, please [submit](<>) a 'failed' result and [file a bug](<>). Please be sure to include the bug number when you [submit](<>) your result.**
