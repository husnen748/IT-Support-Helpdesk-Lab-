# IT Troubleshooting Lab – Windows 11 & IT Support

## Project Overview

This project documents common IT troubleshooting scenarios encountered by Level 1 IT Support Technicians and Service Desk Analysts.

The purpose of this lab is to develop practical troubleshooting skills, understand common technical problems and practise resolving IT support incidents using a structured approach.

Each scenario includes the reported problem, troubleshooting steps and a section for documenting results and screenshots.

## Technologies and Tools

- Windows 11
- Windows Server 2022
- Active Directory Users and Computers (ADUC)
- Command Prompt and PowerShell
- Windows Event Viewer
- Windows Task Manager
- Windows Defender
- Microsoft Outlook
- Windows Print Management
- Device Manager
- Windows Services
- Network troubleshooting utilities

---

# IT Troubleshooting Scenarios

## Scenario 1: User Account Locked Out

### Problem

A user contacts the IT Service Desk because they cannot log in to their Windows computer.

The following message appears:

**"The referenced account is currently locked out and may not be logged on to."**

### Troubleshooting Steps

1. Verify the user's identity before modifying their account.
2. Open **Active Directory Users and Computers (ADUC)** on Windows Server 2022.
3. Locate the affected user account.
4. Right-click the user and select **Properties**.
5. Open the **Account** tab.
6. If the account is locked, select **Unlock account**.
7. Click **Apply**, followed by **OK**.
8. Ask the user to attempt logging in again.
9. Confirm that the account is accessible.

### Further Troubleshooting

If the account repeatedly becomes locked:

1. Open **Event Viewer** on the relevant domain controller.
2. Navigate to **Windows Logs > Security**.
3. Look for account lockout events, particularly **Event ID 4740**.
4. Identify whether saved credentials, scheduled tasks or other devices are causing repeated authentication failures.
5. Resolve the underlying cause before closing the incident.

### Screenshots

*Add screenshots showing the locked account, ADUC account properties and successful resolution.*

---

## Scenario 2: Password Reset Request

### Problem

A user has forgotten their Windows domain password and is unable to log in.

### Troubleshooting Steps

1. Verify the user's identity according to company security procedures.
2. Open **Active Directory Users and Computers**.
3. Search for the affected user.
4. Right-click the account.
5. Select **Reset Password**.
6. Enter a temporary password that meets the organisation's password policy.
7. Select **User must change password at next logon**.
8. Click **OK**.
9. Provide the temporary password using an approved secure method.
10. Ask the user to log in and create a new password.
11. Confirm successful access.

### Verification

Check that the user can log in with the new password and access the necessary company resources.

### Screenshots

*Add screenshots showing the password reset process. Do not display actual passwords.*

---

## Scenario 3: No Internet Connection

### Problem

A user reports that their Windows 11 computer cannot access websites or other internet services.

### Troubleshooting Steps

1. Confirm whether the issue affects one computer or multiple users.
2. Check whether the Ethernet cable or Wi-Fi connection is active.
3. Open **Command Prompt**.
4. Check the network configuration:

```cmd
ipconfig /all
```

5. Identify the IP address, subnet mask, default gateway and DNS servers.
6. Test connectivity to the default gateway:

```cmd
ping 192.168.1.1
```

*Replace the example IP address with the actual gateway.*

7. Test connectivity to an external IP address:

```cmd
ping 8.8.8.8
```

8. Test DNS resolution:

```cmd
nslookup google.com
```

9. If necessary, clear the DNS cache:

```cmd
ipconfig /flushdns
```

10. If the computer uses DHCP and has an invalid address, renew the network configuration:

```cmd
ipconfig /release
ipconfig /renew
```

11. Disable and re-enable the network adapter if required.
12. Test internet connectivity again.

### Further Troubleshooting

If the problem continues:

- Check whether the DHCP server is available.
- Verify the configured DNS servers.
- Check network adapter drivers.
- Investigate firewall, VPN or proxy settings.
- Escalate wider network problems to the network administrator.

**Note:** Some networks block ICMP ping requests. A failed ping does not always mean that the destination is unreachable.

### Screenshots

*Add screenshots showing network configuration, diagnostic commands and successful connectivity.*

---

## Scenario 4: Printer Not Working

### Problem

A user cannot print documents, or their print jobs remain stuck in the queue.

### Troubleshooting Steps

1. Confirm that the printer is powered on.
2. Check the printer's network or USB connection.
3. Check for paper jams, low toner or printer error messages.
4. On Windows 11, open **Settings > Bluetooth & devices > Printers & scanners**.
5. Select the affected printer.
6. Open the print queue.
7. Cancel any stuck print jobs where appropriate.
8. Open **Run** using **Windows + R**.
9. Enter:

```cmd
services.msc
```

10. Locate the **Print Spooler** service.
11. Right-click and select **Restart**, if appropriate.
12. Return to Printers & Scanners.
13. Print a test page.
14. Confirm whether printing works.

### Further Troubleshooting

If the printer is still not working:

- Verify the correct printer is selected.
- Check whether the printer is offline.
- Check the printer IP address for network printers.
- Update or reinstall the printer driver when necessary.
- Remove and re-add the printer if appropriate.
- Escalate print server or hardware faults.

**Note:** Restarting the Print Spooler can affect other queued print jobs on the same system. Check the impact before doing so.

### Screenshots

*Add screenshots showing the print queue, Print Spooler service and successful test page.*

---

## Scenario 5: Computer Running Slowly

### Problem

A user reports that their Windows 11 computer is slow, freezes frequently or takes too long to open applications.

### Troubleshooting Steps

1. Ask when the problem started.
2. Determine whether the issue affects the entire computer or a particular application.
3. Press **Ctrl + Shift + Esc** to open Task Manager.
4. Open the **Performance** tab.
5. Review CPU, memory, disk and network usage.
6. Open the **Processes** tab.
7. Identify applications consuming unusually high resources.
8. Close unnecessary applications safely.
9. Check the available storage space.
10. Open **Settings > Apps > Startup**.
11. Disable unnecessary startup applications where permitted.
12. Run a malware scan using **Windows Security**.
13. Use **Storage Sense** or Disk Cleanup to remove unnecessary files.
14. Restart the computer when appropriate.
15. Check whether performance has improved.

### Further Troubleshooting

If the problem continues:

- Check Windows Update status.
- Investigate disk health.
- Review Event Viewer for recurring errors.
- Check whether a recent software update introduced the issue.
- Consider whether additional RAM or storage is required.

**Important:** Avoid ending unknown system processes or deleting user data without appropriate checks.

### Screenshots

*Add screenshots showing Task Manager performance information and troubleshooting results.*

---

## Scenario 6: Unable to Connect to Wi-Fi

### Problem

A user reports that their Windows 11 laptop cannot find or connect to the office Wi-Fi network.

### Troubleshooting Steps

1. Confirm that Wi-Fi is enabled.
2. Check that Airplane mode is turned off.
3. Open the Wi-Fi settings and check whether the required network appears.
4. Determine whether other devices can connect to the network.
5. If the network is visible, attempt to reconnect.
6. If appropriate, forget the saved Wi-Fi network and reconnect using authorised credentials.
7. Open Command Prompt.
8. Check wireless interface information:

```cmd
netsh wlan show interfaces
```

9. Check the network configuration:

```cmd
ipconfig /all
```

10. Verify whether the laptop has received a valid IP address.
11. Open **Device Manager**.
12. Locate the Wi-Fi network adapter.
13. Check whether the adapter is disabled or reporting errors.
14. Restart the adapter if necessary.
15. Test Wi-Fi connectivity again.

### Further Troubleshooting

- Check whether the wireless network is available.
- Investigate driver problems.
- Check signal strength.
- Verify the correct security settings.
- Investigate authentication failures.
- Escalate wireless access point or infrastructure problems.

### Screenshots

*Add screenshots showing Wi-Fi settings, adapter information and successful connection.*

---

## Scenario 7: Outlook Not Receiving Emails

### Problem

A user reports that Microsoft Outlook is no longer receiving new emails.

### Troubleshooting Steps

1. Confirm that the computer has internet connectivity.
2. Check whether the user can access their mailbox using Outlook on the web.
3. Check the **Junk Email**, **Deleted Items** and **Other** folders.
4. Confirm that messages are not being redirected by inbox rules.
5. If using classic Outlook, check the **Send/Receive** tab and confirm **Work Offline** is disabled.
6. Check whether the mailbox has reached its storage limit.
7. Restart Outlook.
8. Check for any account sign-in or synchronisation errors.
9. If using Microsoft 365, check **Service health** in the Microsoft 365 admin centre, where authorised.
10. Test whether the user can receive a new email.

### Further Troubleshooting

If the problem persists:

- Check the Microsoft 365 service status.
- Verify the account has an appropriate Exchange Online licence.
- Review Outlook profile issues.
- Check for mailbox rules or filtering.
- Create a new Outlook profile if necessary and approved.
- Escalate unresolved mailbox or mail-flow issues to the Microsoft 365 administrator.

**Important:** Do not remove an Outlook account or profile without checking for locally stored data and the possible impact.

### Screenshots

*Add screenshots showing the Outlook connection status, mailbox settings and verification results.*

---

## Scenario 8: Blue Screen of Death (BSOD)

### Problem

A user's Windows 11 computer unexpectedly crashes and displays a blue-screen error.

### Troubleshooting Steps

1. Ask the user when the crashes started.
2. Record the displayed stop code, if available.
3. Determine whether new software, hardware or drivers were recently installed.
4. Restart Windows if it is safe to do so.
5. Open **Event Viewer**.
6. Navigate to **Windows Logs > System**.
7. Look for relevant errors around the time of the crash.
8. Open **Reliability Monitor** by running:

```cmd
perfmon /rel
```

9. Review the system's reliability history.
10. Open Command Prompt as administrator.
11. Run:

```cmd
sfc /scannow
```

12. Review the results.
13. Check available disk space and Windows Update status.
14. Investigate recently installed drivers.
15. Restart and monitor the computer.

### Further Troubleshooting

If crashes continue:

- Investigate the relevant stop code.
- Check disk health.
- Run Windows Memory Diagnostic if memory errors are suspected.
- Investigate drivers and recently installed updates.
- Use additional Windows repair tools when justified.
- Escalate persistent crashes for further investigation.

**Note:** Before performing repairs that could affect files or system availability, ensure important data is backed up.

### Screenshots

*Add screenshots showing Event Viewer, Reliability Monitor and diagnostic results.*

---

## Scenario 9: Computer Will Not Turn On

### Problem

A user reports that their desktop computer or laptop does not respond when the power button is pressed.

### Troubleshooting Steps

1. Ask the user what happens when they press the power button.
2. Check whether any lights, fans or sounds are present.
3. Verify that the power cable is securely connected.
4. Test an approved alternative power outlet.
5. For laptops, check the charger and charging indicator.
6. Where possible, test with a known-working compatible charger.
7. For desktop computers, verify that the external power supply switch is on.
8. Disconnect unnecessary external devices.
9. Follow the manufacturer's recommended power-reset procedure, if applicable.
10. Attempt to power on the computer again.

### Further Troubleshooting

If the computer still does not start:

- Check for a faulty charger or power adapter.
- Investigate possible power supply failure.
- Check for hardware faults.
- Escalate the issue for hardware inspection or replacement.

**Important:** Never open a power supply unit. Internal electrical components can retain dangerous voltages even after the equipment has been disconnected.

### Screenshots

*Add photos or screenshots of the relevant diagnostics when available.*

---

## Scenario 10: User Cannot Access a Shared Drive

### Problem

A user receives an **Access Denied** error when attempting to open a shared network folder.

### Troubleshooting Steps

1. Confirm the user is logged in with the correct domain account.
2. Ask which shared folder they are trying to access.
3. Identify the exact error message.
4. Open **File Explorer**.
5. Select **This PC**.
6. Check whether the shared drive is mapped.
7. If necessary, attempt to access the shared folder using its network path.

Example:

```text
\\FILESERVER\SharedDrive
```

8. Check whether the file server is reachable.
9. Open Active Directory Users and Computers.
10. Locate the affected user.
11. Open **Properties > Member Of**.
12. Check whether the user belongs to the appropriate security group.
13. If access has been authorised, add the user to the required group.
14. Ask the user to sign out and sign back in so that their group membership is refreshed.
15. Test access to the shared folder again.

### Further Troubleshooting

If access is still denied:

- Check share permissions.
- Check NTFS permissions.
- Verify the group has the required access.
- Check for incorrect or outdated saved credentials.
- Confirm the shared folder still exists.
- Escalate permission or file server problems to the system administrator.

**Note:** Users should only receive access to folders and files required for their job role.

### Screenshots

*Add screenshots showing the access error, AD group membership and successful resolution.*

---

# Troubleshooting Commands Reference

The following Windows commands are useful for common service desk investigations.

| Command | Purpose |
|---|---|
| `ipconfig /all` | Display network configuration |
| `ping` | Test ICMP network connectivity |
| `nslookup` | Test DNS name resolution |
| `ipconfig /flushdns` | Clear the local DNS resolver cache |
| `ipconfig /renew` | Request renewed DHCP configuration |
| `netsh wlan show interfaces` | Display wireless adapter information |
| `gpupdate /force` | Refresh Group Policy settings |
| `gpresult /r` | Display applied Group Policy information |
| `sfc /scannow` | Check and repair protected Windows system files |
| `services.msc` | Open Windows Services |
| `eventvwr.msc` | Open Event Viewer |
| `perfmon /rel` | Open Reliability Monitor |
| `sysdm.cpl` | Open System Properties |

---

# General IT Support Troubleshooting Process

A structured troubleshooting method can help resolve incidents efficiently and minimise disruption.

1. **Identify the problem:** Ask the user about the issue and record the symptoms.
2. **Gather information:** Collect error messages, device details and relevant diagnostic results.
3. **Investigate the cause:** Check the most likely causes before making changes.
4. **Apply a solution:** Perform appropriate troubleshooting or corrective actions.
5. **Verify the result:** Confirm with the user that the original issue has been resolved.
6. **Document the incident:** Record the cause, actions taken and final resolution.
7. **Escalate if required:** Refer complex or unresolved issues to the appropriate support team.

---

# Project Summary

This troubleshooting lab provides a foundation for practising common IT support incidents involving Windows 11, Active Directory, networking, Microsoft Outlook, printers and basic hardware troubleshooting.

## Skills Covered

- Windows 11 technical troubleshooting
- Active Directory account support
- Password resets and account unlocking
- Network connectivity diagnostics
- DNS and DHCP troubleshooting
- Printer support
- Outlook troubleshooting
- System performance investigation
- Windows error investigation
- Basic hardware diagnostics
- Shared folder access troubleshooting
- Incident documentation and escalation

## Future Improvements

- [ ] Add screenshots for each troubleshooting scenario
- [ ] Perform and document the troubleshooting exercises
- [ ] Add simulated IT service desk tickets
- [ ] Document the cause and resolution of each incident
- [ ] Add troubleshooting verification results
- [ ] Link scenarios to the IT Ticketing System project
- [ ] Add additional Windows 11 and Microsoft 365 troubleshooting exercises

---

**Project Status:** Initial documentation / Lab foundation

*This project forms part of my IT Support & Helpdesk Lab GitHub portfolio.*
