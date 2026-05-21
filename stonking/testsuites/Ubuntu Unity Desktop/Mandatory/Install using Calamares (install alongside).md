# Ubuntu Unity: Install using Calamares (install alongside)

*Proceed in your native language if you wish. Instructions will remain in English*

- Before starting this test, ensure your target disk has another operating system on it
- Boot up the image
  - Ubuntu Unity desktop is displayed
- Connect to the Internet using the network widget
  - Network connection is successful
- Double-click the "Install Ubuntu Unity" icon on the desktop
  - Calamares starts
- On the "Welcome" pane, select your language from the language menu
  - Text in the installer changes to match your chosen language
- Click "Next"
  - The "Location" pane is shown with a map and options to select region, time zone, language, and number/date locale
- Select the appropriate locale options
  - The display should reflect your selections    
- Click "Next"
  - The "Keyboard" pane is shown
- Select your keyboard layout, then type in the "Type here to test your keyboard" input box
  - Keyboard layout is set properly
- Click "Next"
  - The "Customize" pane is shown
  - "Normal Installation" should be selected, but there are also options for "Full Installation" and "Minimal Installation"
  - "Download and install updates following installation" are unchecked
  - The checkboxes under "Install additional third-party packages" are unchecked
- Click "Next" without adjusting any settings
  - The "Partitions" pane is shown
- Select the disk to install to from the "Select storage device" menu
  - The "Current" partition layout shown at the bottom of the screen matches the selected device
- Select the "Install alongside" radio button
  - Above the partition layout, "Encrypt system" should be unchecked
- Click on the partition you want to shrink in the "Current" partition layout
  - The "After" bar should show the existing partition layout, with the selected partition split into two parts, one for the existing OS and one for the new OS
- Click and drag the arrow on the "After" bar left and right before settling on something roughly equally split
  - The splitter should move in either direction, within reasonable limits as there needs to be enough space to install to
- If "BIOS" is displayed in the upper-left corner of the pane, set the "Bootloader location" below the partition layout to the "Master Boot Record" of the disk specified in the "Select storage device" menu
- Click "Next"
  - The "Users" pane is shown
- At the "Users" pane, enter details about the main system user
  - All details should be correctly filled in
- Click "Next"
  - The "Summary" pane is shown
- Confirm the details you entered throughout the install are accurately shown
- Click "Install"
  - A popup appears confirming that you really do want to install
- Click "Install now"
  - The installation starts and the "Install" pane is shown
  - The slideshow displays correctly
  - Once the installation finishes, the "Finish" pane is automatically shown
  - The "Restart now" checkbox in the "Finish" pane is automatically checked
- Click "Done"
  - System begins shutdown and prompts you to remove the installation media
- Remove the media when prompted and hit enter as instructed
- Allow the machine to reboot
  - The system boots into a GRUB boot menu
  - The OS that was previously installed has a boot entry present near the bottom of the menu
  - After sitting for a few seconds, the system automatically continues boot and loads into Ubuntu Unity showing the username you entered
- Reboot the system again
- Select the previously installed OS and press Enter
  - The previously installed OS boots successfully

**If all actions produce the expected results listed, please [submit](results#add_result) a 'passed' result.**

**If an action fails, or produces an unexpected result, please [submit](results#add_result) a 'failed' result and [file a bug](../../buginstructions). Please be sure to include the bug number when you [submit](results#add_result) your result.**
