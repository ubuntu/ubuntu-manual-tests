Scope of this test is to verify that the system is installed, you can login into it, Apache and MySQL are working. *Proceed in your native language if you wish. Instructions will remain in English*

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
At Software selection, choose ""LAMP server"" with arrows, select it with ""space bar"" and confirm with ""Enter""
Select to install Grub in the master boot record
Remove the installation media (CDROM or USB key)
Wait that the system reboot and login
Test Apache:
   w3m http://127.0.0.1/
   Press q and confirm to exit
Test MySQL:
   sudo mysql
   You should then be presented with a mysql prompt mysql> where you can enter some mysql commands:

show databases; connect mysql; select host,user from user;

   that will produce an output like:

                +--------------------+
                | Database           |
                +--------------------+
                | information\_schema |
                | mysql              |
                | performance\_schema |
                | sys                |
                +--------------------+
                4 rows in set (0.00 sec)

                Reading table information for completion of table and column names
                You can turn off this feature to get a quicker startup with -A

                Connection id:    7
                Current database: mysql

                +-----------+------------------+
                | host      | user             |
                +-----------+------------------+
                | localhost | debian-sys-maint |
                | localhost | mysql.session    |
                | localhost | mysql.sys        |
                | localhost | root             |
                +-----------+------------------+
                4 rows in set (0.00 sec)
Type exit to exit mysql
Test PHP (command line)
   php -r 'phpinfo();'
   That will produce about 600 lines.
Test PHP (Apache mod\_php)
Create a file called /var/www/html/phptest.php:
   sudo nano /var/www/html/phptest.php
   add the following text to the file:

<?php phpinfo(); ?>
run it on w3m
   w3m localhost/phptest.php
   Verify it outputs the text from phpinfo()

**If all actions produce the expected results listed, please submit a 'passed' result. If an action fails, or produces an unexpected result, please submit a 'failed' result and file a bug. Please be sure to include the bug number when you submit your result.**