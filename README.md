# Internet-Download-Manager-Deletion-of-Keys

---

## 🗑️ STEP 1: **Delete IDM Folders Manually**

Copy and paste the entire block below into **Command Prompt (Admin):**

```bash
rd /s "%appdata%\IDM"
rd /s "%localappdata%\IDM"
rd /s "%programfiles%\Internet Download Manager"
rd /s "%programfiles(x86)%\Internet Download Manager"
```

These commands remove:
- AppData settings  
- Local configuration  
- Program files  

✅ If you see *"File Not Found"* or *"The system cannot find the file specified"*, it means the folders are already gone — which is good!

---

## 🔑 STEP 2: **Delete IDM Registry Keys**

Run these commands in **Command Prompt (Admin):**

```bash
reg delete "HKEY_LOCAL_MACHINE\SOFTWARE\Internet Download Manager" /f
reg delete "HKEY_CURRENT_USER\SOFTWARE\Internet Download Manager" /f
reg delete "HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Internet Download Manager" /f
```

ℹ️ The `/f` means **force delete**.  
✅ If you see *"ERROR: The system was unable to find..."*, it means the key was already deleted — still good!

---

## 📋 STEP 3: **Remove IDM from "Add or Remove Programs" List**

Check for entries using:

```bash
reg query "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall" /s | findstr /i "internet download manager"
```

If any GUID appears (e.g., `{XXXX-XXXX-XXXX}`), delete it with:

```bash
reg delete "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall\{YOUR-GUID}" /f
```

🔍 Most of the time, nothing shows up — meaning it’s already clean.

---

## 🕵️ STEP 4: **Check for Hidden Leftovers (VirtualStore, Temp, etc.)**

Navigate to:

```
C:\Users\YourName\AppData\Local\VirtualStore\Program Files (x86)\
```

- Enable **hidden items** in the *View* tab to see AppData.  
- Make sure everything is deleted (repeat **Step 1** if needed).  

✅ Once done, your system is fully clean of IDM! 🎉

---

# 🎯 FINAL NOTE
If all steps are followed correctly, IDM will be completely removed from your system.

