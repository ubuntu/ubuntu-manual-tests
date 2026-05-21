# Ubuntu Unity: Install using Calamares (manual partitioning)

*Proceed in your native language if you wish. Instructions will remain in English*

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
- Select the "Manual partitioning" radio button
  - Above the partition layout, "Encrypt system" should be unchecked
- Click "Next"
  - The manual partitioning pane is shown
- In the "Storage device" menu, select the disk to install to
  - The partition layout at the top of the screen matches the selected disk
  - The table below the bar lists the partitions, file system, label, mount point, and size
- Click "New Partition Table"
  - A popup appears asking what kind of partition table to create, "MBR" is autoselected on BIOS systems, "GPT" is autoselected on EFI systems
- Click "OK" to accept the default partition table type
  - Popup disappears, table and partition layout bar shows all space on the disk as free space
- Set up your partitions as desired using the "Create", "Edit", and "Delete" buttons, do NOT use the volume group buttons
  - The partition layout and table match the layout you specified
- If using a BIOS system, set the "Install boot loader on" menu to the "Master Boot Record" of the disk specified in the "Storage device" menu
- Click "Next"
  - The "Users" pane is shown
  - A popup may appear recommending that one use a GPT partition layout even on BIOS systems
- If the popup described above appears, dismiss it
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
  - The system boots properly and loads into Ubuntu Unity showing the username you entered

**If all actions produce the expected results listed, please [submit](results#add_result) a 'passed' result.**

**If an action fails, or produces an unexpected result, please [submit](results#add_result) a 'failed' result and [file a bug](../../buginstructions). Please be sure to include the bug number when you [submit](results#add_result) your result.**
