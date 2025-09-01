# Internet-Download-Manager-Deletion-of-Keys

##Step1: Delete IDM Folders Manually
Copy and paste the **entire block below** into **Command Prompt (Admin)**:
rd /s "%appdata%\IDM"
rd /s "%localappdata%\IDM"
rd /s "%programfiles%\Internet Download Manager"
rd /s "%programfiles(x86)%\Internet Download Manager"

These commands remove: 

AppData settings
Local configuration
Program files
✅ If you see "File Not Found" or "The system cannot find the file specified", it means the folders are already gone — which is good! 


##Step2: Delete IDM Registry Keys
reg delete "HKEY_LOCAL_MACHINE\SOFTWARE\Internet Download Manager" /f
reg delete "HKEY_CURRENT_USER\SOFTWARE\Internet Download Manager" /f
reg delete "HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Internet Download Manager" /f

The /f means force delete
✅ If you see "ERROR: The system was unable to find...", it means the key was already deleted — still good! 

##Step3: Remove IDM from "Add or Remove Programs" List
reg query "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall" /s | findstr /i "internet download manager"

If any GUID appears (e.g., {XXXX-XXXX-XXXX}), delete it:
reg delete "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall\{YOUR-GUID}" /f

🔍 Most of the time, nothing shows up — meaning it’s already clean. 

##Step4: Check for Hidden Leftovers (VirtualStore, Temp, etc.)
C:\Users\YourName\AppData\Local\VirtualStore\Program Files (x86)\

Enable hidden items in View tab to see AppData.

Ensure all things by doing step1. 
We all are set!!!!!!!!!!!!!!!!!!

