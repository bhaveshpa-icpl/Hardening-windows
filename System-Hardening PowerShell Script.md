# System Hardening PowerShell Script

This PowerShell script provides a comprehensive solution for securing Windows systems by enabling system protection, creating backups, logging actions, and enforcing security hardening policies via registry modifications.

## Prerequisites
- Ensure the script is run as an **Administrator** to execute all commands successfully.
- PowerShell version 5.1 or higher.
  
## Overview

This script performs the following actions:
1. **Creates Required Directories**: Establishes directories for backups and log files in `C:\Hardening`.
2. **Logging**: Logs all actions into `Hardening-process.log` to allow review and troubleshooting.
3. **Enables System Protection**: Enables Windows System Protection to create restore points.
4. **Pre-Hardening Backup**: Generates a system restore point, exports crucial registry keys, and generates a group policy report.
5. **System Hardening**: Downloads and applies hardening settings, using the HardeningKitty module and additional registry configurations.
6. **Organizes Files**: Moves log files and registry backup files to the `C:\Hardening` directory for organized storage.
7. **Cleanup**: Removes temporary files and notifies users of successful hardening.

## Script Steps

### 1. Create Required Directories
The script creates a base directory `C:\Hardening` and a subdirectory `Windows_Backup` to store backup files and logs.

### 2. Start Logging
All actions taken by the script are logged in `Hardening-process.log` within the `C:\Hardening` directory.

### 3. Enable System Protection
- Ensures System Protection is enabled on the `C:` drive, allowing the creation of restore points.
- Checks for existing restore points and enables System Protection if not already enabled.

### 4. Pre-Hardening Backup
The script:
- Creates a system restore point labeled "Pre-Hardening Backup."
- Backs up specific registry keys and group policy configurations to `C:\Hardening\Windows_Backup`.

### 5. System Hardening Process
1. **Download Hardening Tools**: Downloads HardeningKitty and other hardening scripts.
2. **Run Hardening Process**: Applies security policies based on custom hardening lists.
3. **Registry Modifications**: Enforces several security configurations, including:
   - Disabling vulnerable Windows services.
   - Enforcing network and system security policies.
   - Configuring Windows Defender Exploit Guard and Advanced Security Rules (ASR).

### 6. Organize and Move Files
- Moves generated log files, backups, and configuration reports to `C:\Hardening`.
- Checks and moves the `HKLM` folder if present.

### 7. Cleanup
The script removes any temporary files used during the hardening process and notifies users of the successful hardening completion.

### 8. End Logging
Stops logging to finalize `Hardening-process.log`.

---

## Usage
1. **Run as Administrator**:
   - Open PowerShell as Administrator.
   - Execute the script: `.\Updated-Script-for-Hardening.ps1`

2. **Logs**:
   - Review `C:\Hardening\Hardening-process.log` for a full log of actions.

## Additional Notes
- **HardeningKitty Module**: The script downloads and applies hardening configurations using the [HardeningKitty](https://github.com/bhaveshpa-icpl/Hardening-windows) module.

- **Registry Settings**: The script is highly customizable with registry values; adjust configurations in the script as needed for your security policies.
