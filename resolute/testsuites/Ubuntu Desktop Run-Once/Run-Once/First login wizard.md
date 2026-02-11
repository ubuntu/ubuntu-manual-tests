*Proceed in your native language if you wish. Instructions will remain in English.*

Start the session
   The initial setup should autostart and the 'Online Accounts' screen display and the following account types should be displayed
   -   Google
-   Nextcloud
-   Microsoft
Select one of the accounts and go through the steps to configure it. If you are not connected to the Internet skip this test.
   The accounts list should be displayed again but with the configure account ID displayed on the corresponding entry
Click 'Next'
   The 'Help improve Ubuntu' screen is displayed and the 'Yes, send system info to Canonical' option is selected
Click 'Show the First Report'
   A new dialog opens showing the collect information
Verify that the report's contents makes sense and that it doesn't include anything private or that shouldn't be collected
Close the dialog and click 'Legal notice'
   The default webbrowser opens and display the 'Legal Notice – System Information' page from the Canonical website
Close the browser, go back to the wizard and click 'Next'
   The 'privacy' screen is displayed, the location services toggle is off
Go to Settings->Privacy screen and check that the status
   It should reflect the wizard status
Go back to the wizard and change the toggle status
   The settings screen show reflect the status change
Click 'Next'
   The 'Ready to go' screen is displayed including a grid of icons representing popular software
If you are connected to the Internet click on one of the software
   'Ubuntu Software' is started and show the page corresponding to the selected software
Click 'Install'
   The software should install and be available once it's finished
Close the store, go back to the wizard and click 'Open Ubuntu Software now'
   'Ubuntu Software' is started and displays the frontpage
Close the store, go back to the wizard and click 'Done'
   The wizard closes, and you have a working desktop session
In a terminal run '$ ubuntu-report send yes'
   If you are connected to the Internet it should tell you that the report for that machine has already been sent. If you are not connected it should retry later or on next login.

If **all** actions produce the expected results described, please submit a 'passed' result.

If **any** action fails, or produces an unexpected result, please submit a 'failed' result and file a bug. Please be sure to include the bug number when you submit your result.