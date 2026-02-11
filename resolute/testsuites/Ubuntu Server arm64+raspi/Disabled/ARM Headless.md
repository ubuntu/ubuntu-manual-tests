Follow the installation steps at [OMAPHeadlessInstall](<>)
Once logged in, verify that:
    The root filesystem uses most of the SD card.
    There will be some space used for the hidden boot partition.
    Check for errors in dmesg & jasper log. 

  * `dmesg | less`
  * `cat /var/log/jasper.log | less`


Reboot. System should boot up to login prompt without delay.
Check dmesg for any abnormal messages or errors.
    `dmesg | less`
Check to make sure the architecture is correct for the image you installed:
    `dpkg --print-architecture`
    it should match the image arch type you installed i.e. armhf or armel
**If all actions produce the expected results listed, please[submit](<>) a 'passed' result. If an action fails, or produces an unexpected result, please [submit](<>) a 'failed' result and [file a bug](<>). Please be sure to include the bug number when you [submit](<>) your result**. 
