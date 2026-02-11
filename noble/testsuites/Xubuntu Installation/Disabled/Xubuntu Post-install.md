If options are available, these tests are to be undertaken _following_ a successful install of Xubuntu. Network connections 

If you have access to more than one method to connect to Internet, connect to them all
    You are able to connect as expected
If you have other partitions... 

Open the file manager
    Confirm they are listed in the file manager
    Confirm you are able to read files from it
If you have a USB drive available 

If you have a USB drive, plug it in
    The USB drive is mounted, the file manager opens and you can open files from USB
_Lock and suspend testing_ _If unlocking requires more than one password entry - fail the testcase_ **To test desktop locking, a new user should be created with the User and Groups option from Settings menu** **Testing on Hardware** Test Suspend 

Open any application and suspend machine
    Machine suspends
Restart suspended machine and unlock
    Desktop shows previously started application
Test Desktop Locking 

Open any application and lock desktop
    Desktop locks
Unlock desktop
    Desktop shows previously started application
Test Lock/new User use/Unlock 

Open any application then lock desktop
    Desktop locks
Login as new user
Logout from new user
Login to normal user, unlocking
    Desktop shows previously started application
**When testing on virtual machine** Test Desktop Locking 

Open any application and lock desktop
    Desktop locks
Unlock desktop
    Desktop shows previously started application
Test Lock/new user Session use/Unlock 

Open any application then lock desktop
    Desktop locks
Login as new user
Logout from new user
Login to normal user, unlocking
    Desktop shows previously started application
**If all actions produce the expected results listed, please[submit](<>) a 'passed' result. If an action fails, or produces an unexpected result, please [submit](<>) a 'failed' result and [file a bug](<>). Please be sure to include the bug number when you [submit](<>) your result.**
