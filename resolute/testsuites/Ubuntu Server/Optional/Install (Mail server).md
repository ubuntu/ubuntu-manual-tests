Scope of this test is to verify that the system is installed, you can login into it and the mail server is up and running. _Proceed in your native language if you wish. Instructions will remain in English_

Boot up the image
Choose the desired language
Select ""Install Ubuntu Server""
Choose the language
Select your location
Configure locales
At configure keyboard page, select NO 
Select the country of the keyboard
Select the keyboard layout
Select hostname ubuntu as default
Insert the name for the new user
Insert the name for the account
Choose a password
Reinsert the password
At encrypt request select NO
Verify or setup the timezone
At partitioning select ""Guided - Use entire disk""
Select disk to partition
At ""Write changes to disks"", verify that everythings is right and select YES
At ""http proxy"" request, leave it blank and press enter
At managing upgrades select ""No automatic updates""
At Software selection, choose ""Mail server"" with arrows, select it with ""space bar"" and confirm with ""Enter""
At Postfix Configuration select ""Internet Site""
At System mail name, let ubuntu
At Configuring dovecot-core select ""Yes""
At Configuring dovecot-core verify the hostname is ""localhost"" and select ""Continue""
Select to install Grub in the master boot record
Remove the installation media (CDROM or USB key)
Wait that the system reboot then login
Verify that postfix is running:
    telnet 127.0.0.1 25
    Has to return: Ubuntu ESMTP Postfix (Ubuntu). Type quit to exit
Verify that dovecot pop3 and imap servers are running:
    sudo netstat -ltnp | grep dovecot
    should list 8 dovecot instances (port 110, 143, 993 and 995) 4 for tcp and 4 tcp6
Try to send a test email:
    echo foo | mail -s test ${USER}
    Run mutt and press enter to see the mail, press **q** to exit
**If all actions produce the expected results listed, please[submit](<>) a 'passed' result. If an action fails, or produces an unexpected result, please [submit](<>) a 'failed' result and [file a bug](<>). Please be sure to include the bug number when you [submit](<>) your result.**
