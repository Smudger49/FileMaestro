# FileMaestro

File Maestro - User Guide




Document Title 	File Maestro - User Guide
Version Number 	1
 
Document Author 
Author 	Alex Smith

App Creator	Smudger
Website	XXXXXXXXXXXXX
 
Document History 
Version No. 	Date 
1.0	15/04/2025
	
	










Contents
1. Introduction	3
2. Getting Started	3
Installation	3
Launching the App	3
3. Main Window Overview	3
Left Pane	3
Right Pane	4
Bottom Status Bar	4
4. Managing Monitored Folders	4
Adding a Folder	4
Removing a Folder	4
Folder Settings	4
5. Creating & Managing Rules	5
Sorting vs. Cleanup Rules	5
Adding a Rule	5
The Rule Editor	5
Rule Name & Enable	5
Conditions	5
Action & Parameter	6
Optional Tagging	6
Editing a Rule	6
Removing a Rule	6
Enabling/Disabling Rules Quickly	7
Process Folder Now	7
6. The "All Rules" View	7
7. Running the Monitor	7
8. System Tray Icon	8
9. Application Settings	8
10. Viewing Logs	8
11. About Window	8
12. Important Notes & Tips	9



 1. Introduction
Welcome to File Maestro! This guide will help you use the application to automatically organize and clean up files on your computer.

File Maestro helps you keep your folders tidy automatically. You tell it which folders to watch and set up rules based on file properties (like name, date, size, or tags). When files appear or change in those folders, File Maestro checks your rules and performs actions like moving, renaming, recycling, deleting, or tagging files.

 2. Getting Started

 Installation
File Maestro is typically installed using the provided MSIX package (`.msix` or `.msixbundle` file).

1.  Enable Sideloading/Developer Mode: If you haven't already, enable this in Windows Settings (Search for "Developer settings").
2.  Trust Certificate (If Self-Signed): If using a non-Store package, you may need to install the included `.cer` certificate file into your "Trusted Root Certification Authorities" store (Local Machine). Double-click the `.cer` file and follow the prompts.
3.  Install: Double-click the `.msix` or `.msixbundle` file and click "Install" in the App Installer window.

 Launching the App
After installation, find "File Maestro" in your Windows Start Menu and click it to launch the application.

 3. Main Window Overview
The main window is divided into several sections:
Left Pane
•	Logo: The application logo.
•	Monitored Folders Title: Label for the list below.
•	Start/Stop Monitoring Buttons: Manually start or stop the background file monitoring service. Only one button is visible at a time.
•	Settings/About/Log Buttons: Open respective windows.
•	Folder List: Shows the folders you have added for monitoring. Click a folder here to see its rules and settings on the right.
•	Add/Remove Folder Buttons: Manage the list of monitored folders.
•	Process Folder Now Button: For the selected folder, apply all configured rules to all files currently in the folder.
Right Pane
•	Sorting Rules: View and manage rules primarily designed to move, copy, or rename files.
•	Cleanup Rules: View and manage rules primarily designed to recycle or delete files.
•	Folder Settings: Configure options for the selected folder (enable/disable, include subdirectories).
•	All Rules: View *all* rules from *all* folders in a single list.

Bottom Status Bar
Displays the current status of the application (e.g., "Idle", "Monitoring X folder(s)", "Processing file...").

 4. Managing Monitored Folders
This is where you tell File Maestro which folders to keep an eye on.
 Adding a Folder
1.  Click the "Add Folder" button (bottom left).
2.  A folder browser dialog will appear. Navigate to and select the folder you want to monitor.
3.  Click "OK".
4.  The selected folder will be added to the "Monitored Folders" list.
    * Note: You cannot add protected system folders (like C:\Windows, C:\Program Files) for safety reasons. You will receive a warning if you try.

 Removing a Folder
1.  Select the folder you want to remove from the "Monitored Folders" list.
2.  Click the "Remove Selected" button (bottom left).
3.  A confirmation dialog will appear. Click "Yes" to remove the folder from File Maestro's monitoring list (this does *not* delete the actual folder from your computer). Clicking "No" cancels the removal.

 Folder Settings
1.  Select a folder in the "Monitored Folders" list.
2.  Click the "Folder Settings" tab on the right.
3.  You can configure:
    * Enable monitoring for this folder: Check this box to have File Maestro actively watch this folder when monitoring is running. Uncheck it to temporarily disable monitoring for this specific folder without removing it. Changes take effect immediately if monitoring is active.
    * Include subdirectories: Check this box if you want rules for this folder to also apply to files within its subfolders. Uncheck it to only monitor files directly inside the selected folder. Changes take effect immediately if monitoring is active.

 5. Creating & Managing Rules
Rules define what File Maestro should do when certain conditions are met for a file.
 Sorting vs. Cleanup Rules
While technically similar, rules are organized into tabs based on their primary Action:
•	Sorting Rules Tab: Typically used for actions like `Move`, `Copy`, `Rename`.
•	Cleanup Rules Tab: Typically used for actions like `CopyToRecycleBin`, `DeletePermanently`.
(Note: The `AddTag` action can be used with any primary action and doesn't determine which tab a rule appears under).

 Adding a Rule
1.  Select the folder you want to add a rule to from the "Monitored Folders" list.
2.  Go to either the "Sorting Rules" or "Cleanup Rules" tab.
3.  Click the "Add Sorting Rule" or "Add Cleanup Rule" button at the bottom of the tab.
4.  The "Edit Rule" window will appear for you to define the new rule.

 The Rule Editor
This window lets you configure a rule's details:

Rule Name & Enable
•	Rule Name: Give your rule a descriptive name (e.g., "Move Invoice PDFs", "Delete Old Downloads").
•	Enable this rule: Check this box to make the rule active. Uncheck it to disable the rule without deleting it.

Conditions
This section lists the conditions that a file must meet for the rule to apply.
•	ALL conditions listed must be true for the rule to trigger (AND logic).
•	Click "Add" to add a new condition row.
•	Click "Remove" to delete the currently selected condition row.
•	For each condition:
o	Condition Type: Select the type of check (e.g., `NameContains`, `ExtensionIs`, `CreatedOlderThanDays`, `HasTag`).
o	Value: Enter the value to check against (e.g., `Invoice`, `pdf`, `30`, `Processed`). For date conditions, enter the number of days. For size conditions, enter the size in KB. For tag conditions, enter the tag name.
o	Match Case: Check this box for text-based conditions (`NameContains`, `ExtensionIs`, `HasTag`, etc.) if you want the comparison to be case-sensitive (e.g., match "Report" but not "report"). It's hidden for non-text conditions.

Action & Parameter
•	Action: Select the primary action to perform if all conditions are met (e.g., `Move`, `CopyToRecycleBin`, `Rename`, `Copy`, `DeletePermanently`).
•	Action Parameter: Enter the necessary information for the selected action:
o	`Move`/`Copy`: Enter the full path to the destination folder. Use the "Browse..." button to select it easily.
o	`Rename`: Enter the new base filename (without extension). The original extension will be kept. (e.g., entering `Processed File` for `report.docx` will result in `Processed File.docx`).
o	`CopyToRecycleBin`/`DeletePermanently`: This field is hidden/ignored as no parameter is needed.

Optional Tagging
•	Add this tag after action completes: Check this box if you want to add a Windows tag to the file *after* the primary action (Move, Copy, Rename, etc.) is successfully completed.
•	Tag Name TextBox: If the checkbox is checked, enter the desired tag name here (e.g., `Processed`, `Archived`).
    * Note: Native Windows tagging only works for supported file types (JPG, DOCX, XLSX, etc.) on NTFS drives. Tags may not be added to unsupported file types.

 Editing a Rule
1.  Select the folder containing the rule.
2.  Go to the appropriate tab ("Sorting Rules" or "Cleanup Rules").
3.  Select the rule you want to edit in the grid.
4.  Click the "Edit Selected" button.
5.  The "Edit Rule" window appears with the rule's current settings. Modify as needed and click "Save".

 Removing a Rule
1.  Select the folder containing the rule.
2.  Go to the appropriate tab ("Sorting Rules" or "Cleanup Rules").
3.  Select the rule you want to remove in the grid.
4.  Click the "Remove Selected" button.
5.  A confirmation dialog will appear. Click "Yes" to permanently delete the rule.

 Enabling/Disabling Rules Quickly
You can quickly toggle rules on or off without editing them:
1.  Select the folder containing the rule.
2.  Go to the appropriate tab ("Sorting Rules" or "Cleanup Rules").
3.  Click the checkbox directly in the "Enabled" column for the desired rule in the grid. The change is saved automatically when you close the application.

Process Folder Now
File Maestro monitors files & folders from the moment rules are created or modified for the folders you have selected. If you wish to run the rules for a folder as a one-off job, use the Process Folder Now button – this will apply the configured rules to all files within the folder selected before pressing the button.

 6. The "All Rules" View
•	Clicking the "All Rules" tab on the right shows a read-only grid displaying *every single rule* from *all* your monitored folders.
•	This view includes a "Folder Path" column to show where each rule applies.
•	It's useful for getting an overview or finding a specific rule across all folders.
* Tip: Double-clicking a rule in this grid will automatically select the corresponding folder on the left and switch to the correct "Sorting Rules" or "Cleanup Rules" tab, selecting that specific rule, making it easy to jump to editing.

 7. Running the Monitor
File Maestro doesn't process rules constantly; you need to tell it when to start watching.
•	Start Monitoring: Click this button (top left) to activate the background file monitoring service for all *enabled* folders. The status bar will update. Rules will now be processed automatically as file changes occur.
•	Stop Monitoring: Click this button (appears when monitoring is active) to deactivate the background service. No rules will be processed until you start it again.

Monitoring status is also reflected in the System Tray icon's context menu.
 8. System Tray Icon
When File Maestro is running, you'll see its icon in the Windows system tray (notification area).
•	Minimize to Tray: Minimizing the main window will hide it from the taskbar, leaving only the tray icon.
•	Close to Tray (Default Disabled): By default, clicking the main window's 'X' button now prompts for exit confirmation.
•	Double-Click: Double-clicking the tray icon will show/restore the main window.
•	Right-Click (Context Menu):
o	Show Window: Restores the main window if it's hidden.
o	Start/Stop Monitoring: Toggles the monitoring service on or off (text changes based on current state).
o	Exit: Shows the confirmation prompt and then completely closes File Maestro (saves settings first).

 9. Application Settings
•	Click the "Settings..." button (top left) to open the Settings window.
•	Application Startup: Click the link to open settings – find File Maestro in the list and set to enabled to add File Maestro to your Windows startup sequence. It will launch automatically when you log in. Uncheck it to remove it from startup. 
•	Automatically Start Monitoring When App Launches: Check this box to automatically start the folder monitoring as soon as the app opens.

 10. Viewing Logs
•	Click the "View Log..." button (top left) to open the Application Log window.
•	This window shows recent activity, including monitoring start/stop, detected file events, rules being processed, actions taken, and any errors encountered.
•	Use the "Clear Log" button within this window to clear the displayed messages (it doesn't delete the log file).
•	Detailed logs are also saved to rolling text files in the application's data directory (`%LOCALAPPDATA%\FileMaestro\Logs\`).

 11. About Window
•	Click the "About..." button (top left) to open the About window.
•	This shows the application name, version number, copyright information, and a placeholder website link.


 12. Important Notes & Tips

•	Backup: While actions like `CopyToRecycleBin` are safer, always be cautious when setting up rules with `DeletePermanently` or `Move` actions, especially when monitoring important folders. Consider backing up data first.
•	Protected Folders: File Maestro prevents monitoring or modifying files directly within critical system folders (like C:\Windows) for safety.
•	Rule Loops: Be careful when creating `Rename` rules. If the new name *still* matches the rule's conditions, the rule might run repeatedly. The app has protection against *immediate* loops, but try to make rename parameters result in names that won't re-trigger the same rule.
•	Native Tagging Limits: The `AddTag`, `HasTag`, and `DoesNotHaveTag` features rely on Windows' built-in metadata support. This works for many common file types (JPG, DOCX, XLSX, etc.) but not all (e.g., plain TXT files). Tags added this way might be stripped if files are moved to non-NTFS drives or shared via some methods.
•	Performance: Monitoring a huge number of folders or folders with extremely frequent changes might impact system performance. Use specific rules and avoid monitoring unnecessary locations. Check the Log for any buffer overflow warnings from the monitoring service.
•	Saving: Settings, folders, and rules are saved automatically when you exit the application using the tray icon's "Exit" command or confirming "Yes" on the close prompt.


