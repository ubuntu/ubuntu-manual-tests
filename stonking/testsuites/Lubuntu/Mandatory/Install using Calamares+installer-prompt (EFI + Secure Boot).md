# Lubuntu: Install using Calamares + installer-prompt (EFI + Secure Boot)

*Proceed in your native language if you wish. Instructions will remain in English*

- Before running this test, ensure that you are using EFI firmware with Secure Boot enabled to boot
- Boot up the image
  - Lubuntu boot screen is displayed
- When installer-prompt starts, connect to the Internet using the network menu
  - Network connection is successful
  - Current internet connection is shown in the network menu
- Select your language from the language menu if it is something other than US English
  - If a new language was selected, it is installed if necessary, the installer prompt restarts, and the language is still selected after the restart
- Press "Install Lubuntu" and wait for Calamares installer to start
  - Language menu in Calamares has your language pre-selected
  - Text in the installer is properly translated
- After the "Welcome" pane is shown click "Next"
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
  - In the top left corner, "EFI" is displayed
- Select the disk to install to from the "Select storage device" menu
  - The "Current" partition layout shown at the bottom of the screen matches the selected device
- Select the "Erase disk" radio button
  - Two menus appear under the "Erase disk" option, set to "Swap to file" and "ext4"
  - The "Swap to file" menu contains "No swap" as the other available option
  - The "ext4" menu contains "btrfs" and "xfs" as the other available options
  - Above the partition layout, "Encrypt system" should be unchecked
  - The "After" partition layout shown at the bottom of the screen shows a 300 MiB EFI system partition followed by a `lubuntu_2604` partition covering the rest of the disk
  - No "Bootloader location" menu is shown below the partition layout
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
  - The system boots properly and loads into Lubuntu showing the username you entered

**If all actions produce the expected results listed, please [submit](results#add_result) a 'passed' result.**

**If an action fails, or produces an unexpected result, please [submit](results#add_result) a 'failed' result and [file a bug](../../buginstructions). Please be sure to include the bug number when you [submit](results#add_result) your result.**
