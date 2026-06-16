# Remote Support Troubleshooting Guide

## Table of Contents
1. [VPN Issues](#vpn-issues)
2. [Wi-Fi Connectivity](#wi-fi-connectivity)
3. [Outlook Email Problems](#outlook-email-problems)
4. [Multi-Factor Authentication (MFA)](#multi-factor-authentication-mfa)
5. [Printer Access](#printer-access)
6. [Slow Computer Performance](#slow-computer-performance)

---

## VPN Issues

### Problem: Unable to Connect to VPN

**Step 1: Check Internet Connection**
- [ ] Verify you have active internet connectivity
- [ ] Open a web browser and visit a public website (e.g., google.com)
- [ ] If no internet, troubleshoot your internet connection first
- [ ] Note your ISP or network provider for escalation if needed

**Step 2: Verify VPN Client Installation**
- [ ] Check if VPN client software is installed on your computer
- [ ] On Windows: Go to Control Panel > Programs > Programs and Features
- [ ] On Mac: Check Applications folder
- [ ] If missing, contact IT for installation package
- [ ] Document the VPN client version you have

**Step 3: Update VPN Client**
- [ ] Open VPN client application
- [ ] Check Help > About or Settings for current version
- [ ] Visit your company's software portal or IT website
- [ ] Download and install the latest version
- [ ] Restart your computer after installation
- [ ] Restart VPN client

**Step 4: Clear VPN Configuration**
- [ ] Close VPN client completely
- [ ] **Windows:**
  - [ ] Press Win+R, type `%appdata%`
  - [ ] Find VPN client folder
  - [ ] Backup existing config files
  - [ ] Delete configuration files
  - [ ] Reopen VPN client to rebuild configuration
- [ ] **Mac:**
  - [ ] Open Finder > Go > Go to Folder
  - [ ] Navigate to `~/Library/Application Support/`
  - [ ] Find VPN client folder
  - [ ] Backup and delete configuration files

**Step 5: Firewall and Antivirus Check**
- [ ] Temporarily disable firewall (Windows Defender, ZoneAlarm, etc.)
- [ ] Temporarily disable antivirus software
- [ ] Attempt VPN connection
- [ ] If successful, add VPN client to firewall/antivirus exceptions
- [ ] Re-enable firewall and antivirus

**Step 6: VPN Credentials Verification**
- [ ] Verify username and password are correct
- [ ] Check for CAPS LOCK when entering credentials
- [ ] Confirm you're using correct domain (e.g., `DOMAIN\username`)
- [ ] Reset password if credentials have been changed
- [ ] Clear saved credentials and re-enter them

**Step 7: Network Port Verification**
- [ ] Check if ports required for VPN are open
- [ ] Common VPN ports: 443 (HTTPS), 1194 (OpenVPN), 500/4500 (IPSec)
- [ ] Ask IT to confirm your ISP isn't blocking VPN ports
- [ ] Try alternate VPN protocol if available

**When to Escalate:**
- VPN client crashes repeatedly
- Connection succeeds but immediately disconnects
- All other steps completed without success
- Error messages indicate authentication server issues

---

## Wi-Fi Connectivity

### Problem: Unable to Connect to Company Wi-Fi

**Step 1: Verify Wi-Fi Network Visibility**
- [ ] Check available networks list on your device
- [ ] Confirm company Wi-Fi network name (SSID) appears
- [ ] If not visible:
  - [ ] Ask if network is hidden
  - [ ] Verify Wi-Fi is enabled on device
  - [ ] Manually enter SSID if required

**Step 2: Check Wi-Fi Radio**
- [ ] **Windows:** Settings > Network & Internet > Wi-Fi > Wi-Fi settings toggle is ON
- [ ] **Mac:** Click Wi-Fi icon in menu bar > check Wi-Fi is on
- [ ] If airplane mode is on, turn it off
- [ ] Restart Wi-Fi adapter

**Step 3: Forget and Reconnect to Network**
- [ ] **Windows:**
  - [ ] Settings > Network & Internet > Wi-Fi > Manage known networks
  - [ ] Select company network > Forget
  - [ ] Reconnect and re-enter credentials
- [ ] **Mac:**
  - [ ] System Preferences > Network > Wi-Fi > Advanced
  - [ ] Select company network > Remove (-)
  - [ ] Click OK
  - [ ] Reconnect with credentials

**Step 4: Update Wi-Fi Drivers**
- [ ] **Windows:**
  - [ ] Right-click Start > Device Manager
  - [ ] Expand Network adapters
  - [ ] Right-click Wi-Fi adapter > Update driver
  - [ ] Select "Search automatically for updated driver"
  - [ ] Restart computer after installation
- [ ] **Mac:**
  - [ ] Software Update is automatic
  - [ ] Go to Apple menu > System Preferences > Software Update
  - [ ] Install any available updates

**Step 5: Verify Wi-Fi Security Type**
- [ ] Confirm network uses WPA2 or WPA3 security
- [ ] Check IT documentation for correct security protocol
- [ ] Verify certificate requirements (if using 802.1X)
- [ ] Request IT-provided certificate if needed
- [ ] Ensure device supports required security standard

**Step 6: Disable VPN Temporarily**
- [ ] Disconnect from VPN
- [ ] Attempt Wi-Fi connection
- [ ] If successful, coordinate with IT on VPN/Wi-Fi compatibility
- [ ] Some networks require specific VPN configuration

**Step 7: Network Profile Reset**
- [ ] **Windows:**
  - [ ] Settings > System > About > Advanced system settings
  - [ ] Network > Reset network settings
  - [ ] Restart computer
  - [ ] Reconnect to Wi-Fi
- [ ] **Mac:**
  - [ ] Go > Utilities > Terminal
  - [ ] Type: `sudo rm /Library/Preferences/com.apple.airport.preferences.plist`
  - [ ] Restart computer

**Step 8: Check Wi-Fi Signal Strength**
- [ ] Move closer to Wi-Fi router
- [ ] Minimize obstacles between device and router
- [ ] Note signal strength (should be -50 dBm to -70 dBm minimum)
- [ ] If weak, request router placement assessment

**When to Escalate:**
- Device connects but immediately disconnects
- Persistent "Authentication failed" errors
- Cannot connect to any Wi-Fi network (hardware issue)
- Signal strength is adequate but connection fails

---

## Outlook Email Problems

### Problem: Outlook Not Receiving or Sending Emails

**Step 1: Verify Internet Connectivity**
- [ ] Test internet connection with web browser
- [ ] Ping public website to confirm connectivity
- [ ] Check if other applications can access internet
- [ ] Restart internet connection if needed

**Step 2: Check Outlook Account Status**
- [ ] Open Outlook
- [ ] Click File > Account Settings > Account Settings
- [ ] Verify your email account is listed
- [ ] Check account status shows no errors
- [ ] Note the account type (Exchange, IMAP, POP3, etc.)

**Step 3: Verify Credentials**
- [ ] File > Account Settings > Change > More Settings
- [ ] Confirm username format matches IT documentation
- [ ] Common formats: `email@company.com` or `DOMAIN\username`
- [ ] If using app password, verify it's correct (different from email password)
- [ ] Update credentials if recently changed

**Step 4: Test Server Connectivity**
- [ ] **Windows:**
  - [ ] Press Win+R, type `cmd`
  - [ ] Type: `ping outlook.office365.com`
  - [ ] Confirm connection (0% packet loss)
- [ ] **Mac:**
  - [ ] Open Terminal
  - [ ] Type: `ping outlook.office365.com`
  - [ ] Confirm connection

**Step 5: Check Outlook Configuration**
- [ ] File > Account Settings > Account Settings
- [ ] Click your account > Change
- [ ] Verify incoming server: outlook.office365.com
- [ ] Verify outgoing server (SMTP): smtp.office365.com
- [ ] Port settings should be 993 (IMAP) or 995 (POP3)
- [ ] Ensure "Require SSL" is checked
- [ ] Click Next > Finish

**Step 6: Disable Firewall Temporarily**
- [ ] Temporarily disable Windows Defender Firewall or antivirus
- [ ] Check if Outlook can send/receive emails
- [ ] If successful, add Outlook.exe to firewall exceptions
- [ ] Re-enable firewall

**Step 7: Clear Outlook Cache**
- [ ] Close Outlook completely
- [ ] **Windows:**
  - [ ] Press Win+R, type `%appdata%\Microsoft\Outlook`
  - [ ] Look for .ost files (Outlook Data Files)
  - [ ] Backup these files
  - [ ] Delete .ost files
  - [ ] Restart Outlook (will rebuild cache)
- [ ] **Mac:**
  - [ ] Quit Outlook
  - [ ] Open Finder > Go > Go to Folder
  - [ ] Navigate to `~/Library/Group Containers/UBF8T346G9.Office/`
  - [ ] Delete cache files
  - [ ] Restart Outlook

**Step 8: Check Mailbox Size**
- [ ] Web access: Go to outlook.office365.com
- [ ] Click Settings (gear icon) > Mail > Mailbox settings
- [ ] Check used storage percentage
- [ ] If >98%, delete old emails or archive
- [ ] Move large attachments to cloud storage

**Step 9: Update Outlook**
- [ ] Click File > Office Account
- [ ] Click Update Options > Update Now
- [ ] If no update available, restart Outlook
- [ ] Check Help > About Outlook for current version

**Step 10: Repair Office Installation**
- [ ] **Windows:**
  - [ ] Control Panel > Programs > Programs and Features
  - [ ] Find Microsoft Office
  - [ ] Click > Change > Quick Repair
  - [ ] If unsuccessful, run Online Repair
  - [ ] Restart computer
- [ ] **Mac:**
  - [ ] Quit all Office applications
  - [ ] Open Applications > Microsoft Office > Office Remover
  - [ ] Run repair tool or reinstall

**When to Escalate:**
- Error messages mentioning authentication servers
- "Unable to connect to server" persists after all steps
- Multiple email accounts have same issue
- Email sends but others report not receiving

---

## Multi-Factor Authentication (MFA)

### Problem: MFA Not Working or Cannot Access Account

**Step 1: Verify MFA Method is Available**
- [ ] Check which MFA methods are enabled (Microsoft Authenticator, SMS, email, etc.)
- [ ] Ensure your registered phone or device is available
- [ ] Verify phone has power and signal/Wi-Fi
- [ ] Confirm device is not in airplane mode

**Step 2: MFA Prompt Not Appearing**
- [ ] Verify you're on official company login page (check URL)
- [ ] Close browser completely and retry login
- [ ] Clear browser cache: Settings > Clear browsing data
- [ ] Try different web browser
- [ ] Disable browser extensions temporarily
- [ ] Verify cookies are enabled in browser

**Step 3: Troubleshoot Microsoft Authenticator App**
- [ ] Verify app is installed and up-to-date
- [ ] Swipe notification without checking app notification details first
- [ ] If no notification appears:
  - [ ] Verify notifications are enabled: Settings > Apps > Authenticator > Notifications
  - [ ] Check phone screen brightness (app may have timeout)
  - [ ] Restart Authenticator app
  - [ ] On iPhone: Check Do Not Disturb is off
  - [ ] On Android: Check battery saver mode is off

**Step 4: Phone/SMS Method Troubleshooting**
- [ ] Verify phone number on file is correct: Account > Security > Verification methods
- [ ] Ensure you have SMS service or phone signal
- [ ] Check spam/junk SMS folder
- [ ] Wait 30 seconds before checking for SMS
- [ ] If SMS not received, select "Use a different verification option"
- [ ] Verify phone plan includes SMS if using prepaid service

**Step 5: Test Alternative MFA Method**
- [ ] At login screen, click "Can't access your authenticator app?"
- [ ] Select alternative method:
  - [ ] Call me instead (phone call with voice code)
  - [ ] Text me a verification code (SMS)
  - [ ] Use backup codes (if generated previously)
- [ ] Complete verification with alternate method
- [ ] Record which methods work and which don't

**Step 6: Backup Codes**
- [ ] Go to account security page (myaccount.microsoft.com for work accounts)
- [ ] Look for "Backup codes" or "Recovery options"
- [ ] If codes are available, write down 5 codes for future reference
- [ ] Store codes securely (password manager or safe location)
- [ ] Codes are usually 8 digits and can be used once

**Step 7: Re-register Authentication Device**
- [ ] Go to account security settings
- [ ] Find "Verification methods" or "Authentication methods"
- [ ] Remove current device registration
- [ ] Click "Add method" or "Register device"
- [ ] Follow prompts to re-register phone or Authenticator app
- [ ] Test MFA login after re-registration

**Step 8: Check Account Recovery Options**
- [ ] Verify you have at least one active recovery method
- [ ] If all methods are unavailable, contact IT with proof of identity:
  - [ ] Government ID
  - [ ] Company ID badge
  - [ ] Recent pay stub or company documentation
- [ ] IT may need to temporarily disable MFA to regain access

**Step 9: Time Synchronization Issue (Authenticator App)**
- [ ] Authenticator apps generate time-based codes
- [ ] Verify device time is correct
- [ ] **Windows:** Settings > Time & Language > Date & time > Sync now
- [ ] **Mac:** System Preferences > Date & Time > Set date and time automatically
- [ ] **iPhone:** Settings > General > Date & Time > Set Automatically
- [ ] **Android:** Settings > System > Date & time > Automatic date and time

**Step 10: Browser-Level Issues**
- [ ] Check if browser remembers device (reduces MFA frequency)
- [ ] On trusted devices, MFA may be required less often
- [ ] Ensure "Remember this device" is checked if available
- [ ] If device is marked untrusted, re-authenticate on trusted network

**When to Escalate:**
- Multiple recovery methods are all unavailable
- Account locked after failed MFA attempts
- IT needs to perform account unlock or MFA reset
- Phone/device was lost and needs to be removed from account

---

## Printer Access

### Problem: Cannot Print or Cannot Access Network Printer

**Step 1: Verify Printer Power and Network Status**
- [ ] Check if printer is powered on (lights visible on printer)
- [ ] Look for paper jam indicators or error lights
- [ ] Check paper tray has paper
- [ ] Verify toner/ink levels are adequate
- [ ] Restart printer: Power off > Wait 30 seconds > Power on

**Step 2: Test Printer Directly**
- [ ] Press "Test Print" or "Print Configuration" on printer
- [ ] Successful test print = printer hardware is working
- [ ] Failed test print = escalate to facilities/printer support

**Step 3: Verify Network Connectivity**
- [ ] Note printer IP address from display screen
- [ ] **Windows:**
  - [ ] Press Win+R, type `cmd`
  - [ ] Type: `ping [printer-ip-address]`
  - [ ] Should see replies (no timeouts)
- [ ] **Mac:**
  - [ ] Open Terminal
  - [ ] Type: `ping [printer-ip-address]`
  - [ ] Should see replies

**Step 4: Remove and Re-add Printer**
- [ ] **Windows:**
  - [ ] Settings > Devices > Printers & scanners
  - [ ] Click printer name > Remove device
  - [ ] Click "Add a printer or scanner"
  - [ ] Select printer from list (network scan finds it)
  - [ ] If not listed, enter printer IP: `\\[printer-ip]`
  - [ ] Confirm installation
- [ ] **Mac:**
  - [ ] System Preferences > Printers & Scanners
  - [ ] Click printer > Minus (-) button to remove
  - [ ] Click Plus (+) > Add printer
  - [ ] Select network printer
  - [ ] Click Add

**Step 5: Update Printer Drivers**
- [ ] Go to printer manufacturer's website (HP, Canon, Xerox, etc.)
- [ ] Enter your printer model number
- [ ] Download latest driver for your operating system
- [ ] **Windows:** Run installer, restart computer
- [ ] **Mac:** Run installer, restart computer
- [ ] Re-add printer in system settings

**Step 6: Check Print Queue**
- [ ] **Windows:**
  - [ ] Settings > Devices > Printers & scanners
  - [ ] Right-click printer > Open queue
  - [ ] If jobs are stuck, click Printer > Cancel All Documents
  - [ ] Or: Start > Services > Print Spooler > Restart
- [ ] **Mac:**
  - [ ] System Preferences > Printers & Scanners
  - [ ] Right-click printer > Reset printing system
  - [ ] Re-add printer after reset

**Step 7: Firewall and Network Access**
- [ ] Check if printer is on same network/VLAN as your computer
- [ ] **Windows:** Temporarily disable firewall, attempt print
- [ ] If successful, add printer port to firewall exceptions
- [ ] Contact IT to confirm printer network access from your location

**Step 8: VPN Considerations**
- [ ] Some printers may only be accessible on company network
- [ ] Verify if printer is on local network or requires VPN
- [ ] Disconnect from VPN, attempt print if local
- [ ] Reconnect to VPN and retry if on company network
- [ ] Contact IT if printer access varies with VPN state

**Step 9: Set as Default Printer**
- [ ] **Windows:** Settings > Devices > Printers & scanners > Select printer > Make default
- [ ] **Mac:** System Preferences > Printers & Scanners > Select printer > Default printer
- [ ] Test printing from application (File > Print)

**Step 10: Test Print from Different Application**
- [ ] Try printing from Notepad (Windows) or TextEdit (Mac)
- [ ] If successful, issue may be application-specific
- [ ] If unsuccessful, network printer issue confirmed
- [ ] Document which application had problem if app-specific

**When to Escalate:**
- Printer does not appear in network scan
- Printer IP address is unreachable (no ping response)
- Print jobs complete but nothing prints
- Same issue across multiple printers and devices
- Error messages indicate driver or connection issues

---

## Slow Computer Performance

### Problem: Computer Running Slowly or Freezing

**Step 1: Check System Resources**
- [ ] **Windows:**
  - [ ] Right-click Taskbar > Task Manager
  - [ ] Check Performance tab
  - [ ] Note CPU, Memory, Disk, and Network usage percentages
  - [ ] Note which processes use most resources
- [ ] **Mac:**
  - [ ] Open Applications > Utilities > Activity Monitor
  - [ ] Click Memory or CPU tab
  - [ ] Sort by % CPU or Memory
  - [ ] Note top processes using resources

**Step 2: Monitor System Over Time**
- [ ] Leave Task Manager/Activity Monitor open while working
- [ ] Note if CPU or Memory regularly exceeds 80%
- [ ] Identify which applications spike resource usage
- [ ] Record usage patterns for IT diagnosis

**Step 3: Close Unnecessary Applications**
- [ ] Close browser tabs (each tab uses memory)
- [ ] Close applications you're not actively using
- [ ] Disable background apps:
  - [ ] **Windows:** Settings > Privacy & Security > App permissions > Background apps
  - [ ] **Mac:** System Preferences > General > Login Items (remove items)
- [ ] Disable browser extensions
- [ ] Check system tray for unnecessary running services

**Step 4: Restart Computer**
- [ ] Save all work
- [ ] Click Start > Power > Restart
- [ ] **Mac:** Apple menu > Restart
- [ ] Allow 2-3 minutes for complete restart
- [ ] Test performance after restart
- [ ] Often resolves temporary slowness

**Step 5: Check Disk Space**
- [ ] **Windows:**
  - [ ] File Explorer > This PC
  - [ ] Right-click C: drive > Properties
  - [ ] Check available space (should be >10% of total)
  - [ ] If low, delete unnecessary files or uninstall programs
- [ ] **Mac:**
  - [ ] Apple menu > About This Mac > Storage
  - [ ] Check available space
  - [ ] If low, delete files or move to external drive

**Step 6: Scan for Malware**
- [ ] **Windows:**
  - [ ] Settings > Privacy & Security > Virus & threat protection
  - [ ] Click "Scan options"
  - [ ] Select "Full scan"
  - [ ] Click "Scan now"
  - [ ] Scan may take 30-60 minutes
  - [ ] Quarantine any threats found
- [ ] **Mac:**
  - [ ] Open Finder > Applications > Utilities
  - [ ] Run Activity Monitor
  - [ ] Look for suspicious processes
  - [ ] Download and run reputable antivirus (Malwarebytes, etc.)

**Step 7: Check for Software Updates**
- [ ] **Windows:**
  - [ ] Settings > Update & Security > Windows Update
  - [ ] Click "Check for updates"
  - [ ] Install all available updates
  - [ ] Restart computer when prompted
- [ ] **Mac:**
  - [ ] Apple menu > System Preferences > Software Update
  - [ ] Install any available updates
  - [ ] Restart computer when prompted

**Step 8: Disable Visual Effects (Windows)**
- [ ] Settings > System > About
- [ ] Click "Advanced system settings"
- [ ] Go to Performance section > Settings
- [ ] Select "Adjust for best performance"
- [ ] Restart computer
- [ ] Alternative: Manually select which effects to disable

**Step 9: Check Startup Programs**
- [ ] **Windows:**
  - [ ] Press Win+R, type `msconfig`
  - [ ] Click Startup tab
  - [ ] Uncheck unnecessary programs (keep antivirus/security)
  - [ ] Click Apply > OK > Restart
- [ ] **Mac:**
  - [ ] System Preferences > General > Login Items
  - [ ] Select unnecessary items > Minus (-) button
  - [ ] Restart computer

**Step 10: Increase Virtual Memory (Windows)**
- [ ] Right-click "This PC" > Properties
- [ ] Advanced system settings > Performance Settings
- [ ] Advanced tab > Virtual memory > Change
- [ ] Set to 1.5x your RAM size
- [ ] Click Set > OK > Restart

**Step 11: Hard Drive Health Check**
- [ ] **Windows:**
  - [ ] Press Win+R, type `diskmgmt.msc`
  - [ ] Check disk status (should show "Healthy")
  - [ ] Run: Press Win+R > `wmic logicaldisk get name, size, freespace`
  - [ ] Note any drives showing errors
- [ ] **Mac:**
  - [ ] Disk Utility app
  - [ ] Select drive > First Aid > Run
  - [ ] Note any errors reported

**Step 12: Temporary Files Cleanup**
- [ ] **Windows:**
  - [ ] Settings > System > Storage > Temporary files
  - [ ] Click "Delete temporary files"
  - [ ] Allow process to complete
- [ ] **Mac:**
  - [ ] Terminal: `rm -rf ~/.cache/*`
  - [ ] Or use third-party cleanup tool (CCleaner, CleanMyMac)

**Step 13: Check Network Performance**
- [ ] Verify internet speed:
  - [ ] Visit speedtest.net
  - [ ] Run speed test
  - [ ] Note download/upload speeds
  - [ ] Compare to company baseline
- [ ] Check if network-related slowness
- [ ] Contact IT if speeds significantly below normal

**Step 14: Disable Hardware Acceleration**
- [ ] Often causes slowness with incompatible graphics drivers
- [ ] Browser settings > Advanced > toggle Hardware acceleration OFF
- [ ] Microsoft applications: File > Options > Advanced > Display > uncheck hardware acceleration
- [ ] Restart application

**When to Escalate:**
- Consistent high CPU/Memory usage with no identified process
- Disk errors reported by diagnostic tools
- Performance does not improve after all steps
- Multiple symptoms: slow + frequent crashes + high disk activity
- Suspect hardware failure (overheating, failing hard drive)

---

## General Troubleshooting Tips

### Before Calling Support
- [ ] Document the issue: When it started, what triggers it, error messages
- [ ] Note your computer model and operating system version
- [ ] Take screenshots of error messages
- [ ] Document troubleshooting steps already attempted
- [ ] Note if issue affects multiple applications or one only
- [ ] Test issue on alternate device if possible

### Information to Have Ready
- [ ] Your employee ID or username
- [ ] Computer name and model
- [ ] Operating system and version
- [ ] Error codes or exact error messages
- [ ] Network or printer model numbers
- [ ] Approximate time when issue started

### When to Contact IT Support
- Priority 1 (Urgent): No email access, cannot connect to VPN, security concerns
- Priority 2 (High): Cannot access critical applications, printer access lost
- Priority 3 (Medium): Performance issues, single application failures
- Priority 4 (Low): Non-critical feature requests, general questions

### Support Contact Information
- **IT Help Desk:** (insert phone number)
- **Email:** itsupport@company.com
- **Ticket Portal:** (insert URL)
- **Hours:** (insert hours)
- **Emergency After-Hours:** (insert number if available)

---

## Document Version and Updates

- **Version:** 1.0
- **Last Updated:** June 2026
- **Created by:** IT Support Team
- **Next Review Date:** June 2027

### Change Log
| Date | Version | Changes |
|------|---------|---------|
| June 2026 | 1.0 | Initial documentation created |

---

## Additional Resources

- Company IT Knowledge Base: (insert URL)
- Microsoft Office Support: https://support.microsoft.com/office
- Windows Support: https://support.microsoft.com/windows
- macOS Support: https://support.apple.com/mac
- Printer Manufacturer Support: Check printer manual for support portal
