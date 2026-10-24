
# IT Troubleshooting Lab

## Overview

This project documents 10 common IT support troubleshooting scenarios that a 1st Line IT Support Technician or Service Desk Analyst may encounter.

Each scenario explains the problem, the steps to investigate and resolve it, and how to confirm the issue has been fixed.

The purpose of this project is to develop my understanding of IT troubleshooting, Windows support, Active Directory, networking, Microsoft Outlook and general helpdesk responsibilities.

These are documented troubleshooting procedures for learning and reference, rather than records of completed practical tests.

---

## Table of Contents

1. [User Account Locked Out](#1-user-account-locked-out)
2. [Password Reset Request](#2-password-reset-request)
3. [No Internet Connection](#3-no-internet-connection)
4. [Printer Not Working](#4-printer-not-working)
5. [Computer Running Slow](#5-computer-running-slow)
6. [Unable to Connect to Wi-Fi](#6-unable-to-connect-to-wi-fi)
7. [Outlook Not Receiving Emails](#7-outlook-not-receiving-emails)
8. [Blue Screen of Death](#8-blue-screen-of-death-bsod)
9. [Computer Won't Turn On](#9-computer-wont-turn-on)
10. [User Cannot Access a Shared Drive](#10-user-cannot-access-a-shared-drive)

---

## Troubleshooting Scenarios

### 1. User Account Locked Out

**Problem:** A user cannot sign in to their Windows computer because their Active Directory account is locked.

**Troubleshooting Steps:**

1. Confirm the user's identity using the company's verification process.
2. Open **Active Directory Users and Computers (ADUC)**.
3. Search for the affected user account.
4. Right-click the account and select **Properties**.
5. Open the **Account** tab.
6. If the account is locked, select **Unlock account**.
7. Click **Apply** and **OK**.
8. Ask the user to sign in again.
9. If the account continues locking, investigate failed sign-in attempts using **Event Viewer**.
10. Check for saved passwords on other devices, services or applications that may be causing repeated failed logins.

**Expected Result:** The account is unlocked and the user can successfully sign in.

**Skills Covered:** Active Directory, account management, user authentication, Event Viewer.

---

### 2. Password Reset Request

**Problem:** A user has forgotten their Windows domain password and cannot sign in.

**Troubleshooting Steps:**

1. Verify the user's identity before resetting their password.
2. Open **Active Directory Users and Computers**.
3. Locate the user's account.
4. Right-click the account and select **Reset Password**.
5. Enter a temporary password that meets the organisation's password policy.
6. Select **User must change password at next logon**.
7. Click **OK**.
8. Communicate the temporary password through an approved secure method.
9. Ask the user to sign in and change their password.
10. Confirm the user can access their account.

**Expected Result:** The user successfully signs in using their new password.

**Skills Covered:** Active Directory, password management, identity verification, customer support.

---

### 3. No Internet Connection

**Problem:** A user reports that their computer is connected to the network but cannot access the internet.

**Troubleshooting Steps:**

1. Check whether other devices on the same network can access the internet.
2. Confirm the network cable or Wi-Fi connection is working.
3. Open **Command Prompt**.
4. Run the following commands:

   ```cmd
   ipconfig /all
   ```

   Check the IP address, default gateway and DNS server settings.

   ```cmd
   ping 8.8.8.8
   ```

   Test external IP connectivity.

   ```cmd
   ping google.com
   ```

   Test connectivity using a domain name.

   ```cmd
   nslookup google.com
   ```

   Check whether DNS resolution is working.

5. If the computer uses DHCP and has an invalid IP address, try:

   ```cmd
   ipconfig /release
   ipconfig /renew
   ```

6. Restart the network adapter if required.
7. Check whether the problem affects only one computer or multiple users.
8. Escalate to the network team if the issue appears to involve shared network infrastructure.

**Expected Result:** The computer receives valid network settings and can access the internet.

**Skills Covered:** TCP/IP, DHCP, DNS, Windows networking, Command Prompt.

---

### 4. Printer Not Working

**Problem:** A user cannot print because print jobs are stuck in the queue or the printer displays an error.

**Troubleshooting Steps:**

1. Check that the printer is switched on.
2. Confirm that the printer is connected to the network or computer.
3. Check for paper jams, low toner or printer error messages.
4. Open **Settings > Bluetooth & devices > Printers & scanners**.
5. Select the affected printer and open its print queue.
6. Cancel stuck print jobs where appropriate.
7. Open **Services** by running:

   ```cmd
   services.msc
   ```

8. Find **Print Spooler**.
9. Right-click the service and select **Restart**.
10. Try printing a test page.
11. If the issue continues, check the printer driver.
12. Remove and re-add the printer if necessary.

**Expected Result:** Print jobs are processed successfully and the user can print again.

**Skills Covered:** Windows printer support, Print Spooler, device drivers, hardware troubleshooting.

---

### 5. Computer Running Slow

**Problem:** A user reports that their Windows computer is slow, freezing or taking too long to open applications.

**Troubleshooting Steps:**

1. Open **Task Manager** using **Ctrl + Shift + Esc**.
2. Select the **Performance** tab.
3. Check CPU, memory and disk usage.
4. Open the **Processes** tab.
5. Identify applications using excessive system resources.
6. Close unnecessary applications after confirming they are safe to close.
7. Check available disk storage.
8. Run a malware scan using **Windows Security / Microsoft Defender**.
9. Review unnecessary startup applications in Task Manager.
10. Use Windows storage cleanup tools to remove unnecessary temporary files.
11. Restart the computer.
12. Check whether performance has improved.
13. Escalate if hardware limitations or faults are suspected.

**Expected Result:** The computer becomes more responsive and applications run normally.

**Skills Covered:** Windows troubleshooting, Task Manager, performance monitoring, Microsoft Defender.

---

### 6. Unable to Connect to Wi-Fi

**Problem:** A user's laptop cannot connect to the office Wi-Fi network.

**Troubleshooting Steps:**

1. Confirm that Wi-Fi is enabled on the laptop.
2. Check that Airplane mode is disabled.
3. Check whether the correct wireless network is available.
4. Ask whether other users can connect to the same network.
5. If appropriate, forget the saved Wi-Fi network and reconnect.
6. Open **Command Prompt** and run:

   ```cmd
   netsh wlan show interfaces
   ```

   Check the wireless adapter connection status.

7. Run:

   ```cmd
   ipconfig /all
   ```

   Check the IP address and network configuration.

8. If a DNS issue is suspected, run:

   ```cmd
   ipconfig /flushdns
   ```

9. Check the wireless adapter in **Device Manager**.
10. Restart the adapter if necessary.
11. Check for driver problems.
12. Escalate if the issue appears to involve the wireless access point or network authentication.

**Expected Result:** The laptop connects to the correct Wi-Fi network and can access required services.

**Skills Covered:** Wireless networking, TCP/IP, DNS, Device Manager, network troubleshooting.

---

### 7. Outlook Not Receiving Emails

**Problem:** A user reports that Microsoft Outlook has stopped receiving new emails.

**Troubleshooting Steps:**

1. Confirm the computer has an internet connection.
2. Check whether the user can access their mailbox through Outlook on the web.
3. Check the **Junk Email** and **Other** folders.
4. Check whether Outlook is in **Work Offline** mode, where that option is available.
5. Review the Outlook connection status.
6. Check mailbox storage usage and quota.
7. Restart Outlook.
8. Check for any Microsoft 365 service issues using the Microsoft 365 Admin Center, if authorised.
9. If necessary, repair or recreate the Outlook profile after checking company procedures.
10. Test whether new emails are being received.
11. Escalate to the email administrator if the problem continues.

**Expected Result:** Outlook reconnects and new emails appear in the user's mailbox.

**Skills Covered:** Microsoft Outlook, Microsoft 365, email troubleshooting, mailbox management.

---

### 8. Blue Screen of Death (BSOD)

**Problem:** A Windows computer crashes and displays a blue screen error before restarting.

**Troubleshooting Steps:**

1. Record the error message or stop code displayed.
2. Ask the user when the crashes started.
3. Check whether any software or drivers were recently installed.
4. Open **Event Viewer**.
5. Navigate to **Windows Logs > System**.
6. Look for critical errors around the time of the crash.
7. Open **Reliability Monitor** to review the crash history.
8. Run the following command in an elevated Command Prompt:

   ```cmd
   sfc /scannow
   ```

9. Check disk health and consider running a disk repair command if appropriate.
10. Investigate recently updated drivers and roll back faulty drivers if required.
11. Run **Windows Memory Diagnostic** if a memory fault is suspected.
12. Escalate if hardware failure is suspected.

**Expected Result:** The cause of the crashes is identified and the computer operates without further blue screen errors.

**Skills Covered:** Windows diagnostics, Event Viewer, system repair, driver troubleshooting.

---

### 9. Computer Won't Turn On

**Problem:** A user presses the power button, but the computer does not start.

**Troubleshooting Steps:**

1. Check that the power cable is connected correctly.
2. Test a different power socket.
3. Check the power adapter or charger.
4. For a laptop, connect the charger and allow time for the battery to charge.
5. Look for power indicator lights.
6. Check whether the computer produces any fan noise or display output.
7. Disconnect unnecessary external devices.
8. Perform a manufacturer-approved power reset if appropriate.
9. Check whether the issue is with the monitor rather than the computer.
10. If the device still does not power on, escalate for hardware inspection.

**Expected Result:** The computer powers on successfully, or the suspected hardware fault is identified for further investigation.

**Skills Covered:** Hardware troubleshooting, power supply checks, laptop and desktop support.

---

### 10. User Cannot Access a Shared Drive

**Problem:** A user receives an Access Denied error when attempting to open a shared network folder.

**Troubleshooting Steps:**

1. Confirm the user is signed in with the correct domain account.
2. Check whether the computer is connected to the company network.
3. Open **File Explorer > This PC**.
4. Check whether the shared drive is mapped.
5. If the drive is missing, select **Map network drive**.
6. Enter the correct shared folder path, for example:

   ```text
   \\server\SharedDrive
   ```

7. Check whether the user can access the shared folder.
8. Open **Active Directory Users and Computers**.
9. Check the user's security group membership.
10. If access is approved but the required group membership is missing, arrange for the correct group to be assigned.
11. Ask the user to sign out and sign back in if required.
12. Check share permissions and NTFS permissions if access is still denied.
13. Escalate permission changes when necessary.

**Expected Result:** The user can access the shared network folder with the correct permissions.

**Skills Covered:** Active Directory, security groups, shared folders, NTFS permissions, Windows networking.

---

## Troubleshooting Skills Summary

| Area | Skills Covered |
|---|---|
| Active Directory | Account unlocks, password resets, security groups |
| Windows 11 | Performance issues, system errors, hardware support |
| Networking | TCP/IP, DNS, DHCP, Wi-Fi troubleshooting |
| Microsoft 365 | Outlook connectivity and mailbox troubleshooting |
| Hardware | Printers, power issues, device drivers |
| Command Line | ipconfig, ping, nslookup, netsh, sfc |
| IT Support | Investigation, troubleshooting, documentation and escalation |

---

## Troubleshooting Approach

When dealing with an IT support issue, I aim to follow a consistent process:

1. **Identify the problem** – Understand the user's issue and collect relevant information.
2. **Investigate** – Check error messages, settings, logs and possible causes.
3. **Troubleshoot** – Apply appropriate fixes, starting with the least disruptive.
4. **Test** – Confirm whether the problem has been resolved.
5. **Document** – Record the problem, actions taken and outcome.
6. **Escalate** – Refer the issue to the appropriate support team when necessary.

---

## Conclusion

This troubleshooting guide covers 10 common issues encountered in 1st Line IT Support and Service Desk environments.

It provides a reference for diagnosing problems involving Windows computers, Active Directory, networking, printers, Microsoft Outlook and user access.

The guide supports my ongoing learning and preparation for an entry-level IT Support or Service Desk Analyst role.

The procedures are intended as educational documentation. Practical troubleshooting exercises and verified results can be added as the lab develops.

