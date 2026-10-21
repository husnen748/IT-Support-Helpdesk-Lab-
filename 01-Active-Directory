# Active Directory Lab – Windows Server 2022

## Project Overview

This project demonstrates how to install, configure and manage Active Directory Domain Services (AD DS) using Windows Server 2022 and Windows 11.

The lab covers the basic administrative tasks commonly performed by IT Support Technicians and Service Desk Analysts.

### Technologies Used

- Windows Server 2022
- Windows 11 Pro
- Oracle VirtualBox
- Active Directory Domain Services (AD DS)
- DNS Server
- Group Policy Management
- Active Directory Users and Computers (ADUC)

### Lab Environment

| Component | Configuration |
|---|---|
| Domain Controller | Windows Server 2022 |
| Client Computer | Windows 11 Pro |
| Virtualisation | Oracle VirtualBox |
| Server Hostname | DC01 |
| Domain Name | corp.local (example lab domain) |
| Server IP Address | 192.168.56.10 (example) |
| Subnet Mask | 255.255.255.0 |
| Preferred DNS | 192.168.56.10 |

**Note:** The example IP addresses assume an appropriately configured VirtualBox lab network. Adjust them to match your environment. The server and client must be able to communicate with one another.

---

# Part 1: Set Up Active Directory

## Step 1: Configure a Static IP Address

Before installing Active Directory, configure a static IP address on the Windows Server 2022 virtual machine.

A static IP address ensures that the domain controller keeps the same network address.

### Check the Network Configuration

1. Open **Command Prompt**.
2. Enter the following command:

```cmd
ipconfig /all
```

3. Identify the current IP address, subnet mask, default gateway and DNS settings.
4. Check the VirtualBox network configuration.
5. Choose an unused static IP address that matches your lab network.

### Configure the Static IP

1. Open **Server Manager**.
2. Click **Local Server** on the left.
3. Next to **Ethernet**, click the network connection link.
4. Right-click your network adapter.
5. Select **Properties**.
6. Select **Internet Protocol Version 4 (TCP/IPv4)**.
7. Click **Properties**.
8. Select **Use the following IP address**.
9. Enter the static IP settings.

### Example IP Configuration

| Field | Example Value |
|---|---|
| IP Address | 192.168.56.10 |
| Subnet Mask | 255.255.255.0 |
| Default Gateway | Leave blank if the lab has no router |
| Preferred DNS | 192.168.56.10 |
| Alternate DNS | Leave blank for this single-DC lab |

10. Click **OK** to save.

**Important:** Once the DNS Server role is installed, the domain controller should use its own DNS service. If external internet DNS resolution is required, configure DNS forwarders on the DNS server.

### Screenshots

*Add screenshots showing the Windows Server network adapter and static IP configuration.*

---

## Step 2: Add Roles and Features

1. Open **Server Manager**.
2. Click **Manage** in the top-right corner.
3. Select **Add Roles and Features**.
4. Click **Next** on the Before You Begin page.
5. Select **Role-based or feature-based installation**.
6. Click **Next**.
7. Select the local Windows Server 2022 server, such as **DC01**.
8. Click **Next**.

### Screenshots

*Add screenshots showing Server Manager and the Add Roles and Features wizard.*

---

## Step 3: Install Active Directory Domain Services

1. On the **Server Roles** page, select **Active Directory Domain Services**.
2. When prompted, click **Add Features**.
3. Click **Next**.
4. Leave the default selections on the Features page.
5. Click **Next** through the AD DS information page.
6. Click **Install**.
7. Wait for the installation to complete.

**Note:** Installing the AD DS role does not automatically make the server a domain controller. The server must be promoted.

### Screenshots

*Add screenshots showing AD DS selected and the installation results.*

---

## Step 4: Promote the Server to a Domain Controller

1. Open **Server Manager**.
2. Click the notification flag in the top-right corner.
3. Select **Promote this server to a domain controller**.
4. Choose **Add a new forest**.
5. Enter the root domain name:

```text
corp.local
```

6. Click **Next**.

**Note:** `corp.local` is used here as a lab example. For production environments, an organisation should generally use a DNS namespace it owns.

### Screenshots

*Add screenshots showing the promotion wizard and forest configuration.*

---

## Step 5: Configure Domain Controller Options

1. Leave **DNS Server** selected.
2. Leave **Global Catalog (GC)** selected.
3. Keep the appropriate default forest and domain functional levels.
4. Create a **Directory Services Restore Mode (DSRM)** password.
5. Store the password securely.
6. Click **Next**.

**Important:** The DSRM password is used for Active Directory recovery and is separate from the normal domain administrator password.

### Screenshots

*Add screenshots showing the Domain Controller Options page. Do not expose passwords.*

---

## Step 6: Complete the Domain Controller Configuration

1. On **DNS Options**, review any warnings. A DNS delegation warning may be expected when creating a new lab forest.
2. Click **Next**.
3. Confirm the NetBIOS domain name is **CORP**.
4. Click **Next**.
5. Leave the default paths for the Active Directory database, log files and SYSVOL.
6. Click **Next**.
7. Review the configuration settings.
8. Click **Next**.
9. Wait for the prerequisite checks to finish.
10. Resolve any blocking errors.
11. Click **Install**.

The server will now configure Active Directory, install and configure the DNS Server role, create the new forest and become a domain controller.

### Screenshots

*Add screenshots showing the configuration review, prerequisite checks and completed installation.*

---

## Step 7: Restart and Log In

After the promotion process, the server should restart automatically.

At the Windows login screen, sign in using the domain administrator account.

Example:

```text
CORP\Administrator
```

Alternatively:

```text
Administrator@corp.local
```

Enter the domain administrator password configured for the account.

### Screenshots

*Add a screenshot showing successful domain administrator login. Do not include credentials.*

---

# Part 2: Join Windows 11 to the Domain

## Domain Join Experience

This section demonstrates how to connect a Windows 11 client computer to the Active Directory domain.

### Step 1: Prepare the Windows 11 VM

1. Create a second virtual machine using **Windows 11 Pro**.
2. Connect it to the same accessible lab network as the domain controller.
3. Start Windows 11.
4. Confirm the client can communicate with the domain controller.

**Note:** Windows 11 Home does not support joining a traditional Active Directory domain.

### Step 2: Configure Client DNS

1. Open **Network Connections**.
2. Right-click the network adapter.
3. Select **Properties**.
4. Open **Internet Protocol Version 4 (TCP/IPv4)**.
5. Set the Preferred DNS server to the domain controller's IP address.

Example:

```text
192.168.56.10
```

6. Save the settings.

### Step 3: Join the Domain

1. Press **Windows + R**.
2. Enter:

```cmd
sysdm.cpl
```

3. Select the **Computer Name** tab.
4. Click **Change**.
5. Select **Domain**.
6. Enter:

```text
corp.local
```

7. Click **OK**.
8. Enter authorised domain administrator credentials when prompted.
9. Wait for the domain welcome message.
10. Restart Windows 11.

### Step 4: Log In With a Domain Account

After restarting, select **Other user** and sign in using an existing domain user account.

Example:

```text
CORP\jsmith
```

Alternatively:

```text
jsmith@corp.local
```

### Screenshots

*Add screenshots showing the domain join process, successful join message and domain login.*

---

# Part 3: Group Policy Management

Group Policy allows administrators to apply and manage Windows settings across users and computers in an Active Directory domain.

## Step 1: Open Group Policy Management

1. Log in to Windows Server 2022.
2. Open **Server Manager**.
3. Click **Tools**.
4. Select **Group Policy Management**.
5. Expand the Active Directory forest and domain.

## Step 2: Create a Group Policy Object

1. Expand **Group Policy Objects**.
2. Right-click **Group Policy Objects**.
3. Select **New**.
4. Enter a name for the policy.

Example:

```text
Desktop Lockdown Policy
```

5. Click **OK**.

## Step 3: Configure the Policy

1. Right-click the newly created Group Policy Object.
2. Select **Edit**.
3. Navigate to the relevant settings.

Example:

```text
User Configuration
   > Policies
   > Administrative Templates
   > Control Panel
```

4. Select the setting you want to configure.
5. Enable or disable the policy as required.
6. Save the configuration.

## Step 4: Link the GPO to an OU

1. Return to Group Policy Management.
2. Find the relevant Organisational Unit.
3. Right-click the OU.
4. Select **Link an Existing GPO**.
5. Choose the Group Policy Object.
6. Click **OK**.

## Step 5: Apply and Verify the Policy

On the Windows 11 client, open Command Prompt with appropriate permissions and run:

```cmd
gpupdate /force
```

To view the applied policies, run:

```cmd
gpresult /r
```

**Note:** Standard domain-account password policies are normally configured at the domain level, rather than through a GPO linked only to a departmental OU.

### Screenshots

*Add screenshots showing the GPO, configured settings, OU link and policy verification.*

---

# Part 4: Organisational Units (OUs)

Organisational Units are containers used to organise Active Directory objects such as users, groups and computers.

They also allow administrators to apply Group Policy settings and delegate administration.

## Step 1: Open Active Directory Users and Computers

1. Open **Server Manager**.
2. Click **Tools**.
3. Select **Active Directory Users and Computers**.
4. Expand the domain:

```text
corp.local
```

## Step 2: Create an Organisational Unit

1. Right-click the domain.
2. Select **New**.
3. Click **Organizational Unit**.
4. Enter the OU name.
5. Click **OK**.

Example organisational units:

```text
corp.local
│
├── IT
│
├── HR
│
├── Finance
│
├── Sales
│
└── Workstations
```

## Step 3: Organise Active Directory Objects

1. Select an existing user or computer object.
2. Right-click the object.
3. Select **Move**.
4. Choose the appropriate Organisational Unit.
5. Click **OK**.

OUs can also be used to apply specific Group Policy settings to different departments.

### Screenshots

*Add screenshots showing the newly created OUs and their objects.*

---

# Part 5: User and Group Management

Active Directory Users and Computers (ADUC) allows administrators to manage user accounts, security groups and computer objects.

## Step 1: Create a User Account

1. Open **Active Directory Users and Computers**.
2. Expand:

```text
corp.local
```

3. Open the relevant departmental OU, such as **HR**.
4. Right-click the OU.
5. Select **New > User**.
6. Enter the user's first name and last name.
7. Enter the username.

Example:

| Field | Example |
|---|---|
| First Name | James |
| Last Name | Smith |
| Username | jsmith |
| Domain | corp.local |
| Department | HR |

8. Click **Next**.
9. Create a temporary password.
10. Select **User must change password at next logon**, if appropriate.
11. Click **Next**.
12. Click **Finish**.

The new user should now appear inside the selected OU.

### Screenshots

*Add screenshots showing user creation and the completed account.*

---

## Step 2: Create a Security Group

1. Open **Active Directory Users and Computers**.
2. Navigate to the appropriate OU.
3. Right-click the OU.
4. Select **New > Group**.
5. Enter the group name.

Example:

```text
HR-Staff
```

6. Select **Global** as the group scope.
7. Select **Security** as the group type.
8. Click **OK**.

### Screenshots

*Add screenshots showing the newly created security group.*

---

## Step 3: Add Users to Security Groups

1. Open **Active Directory Users and Computers**.
2. Locate the security group.
3. Double-click the group.
4. Select the **Members** tab.
5. Click **Add**.
6. Enter the username.

Example:

```text
jsmith
```

7. Click **Check Names**.
8. Click **OK**.
9. Click **Apply** to save.

The user should now appear in the group's membership list.

### Screenshots

*Add screenshots showing the user successfully added to the security group.*

---

# Project Summary

This Active Directory lab provides a foundation for understanding and practising common IT administration tasks in a Windows domain environment.

### Skills Covered

- Configuring a static IP address
- Installing Active Directory Domain Services
- Promoting Windows Server 2022 to a domain controller
- Configuring domain DNS
- Joining Windows 11 to a domain
- Creating and managing Organisational Units
- Creating and managing user accounts
- Creating security groups and assigning users
- Creating and applying Group Policy Objects

## Future Improvements

The following exercises will be added as the lab develops:

- [ ] Add screenshots documenting each setup stage
- [ ] Practise password resets and account unlocking
- [ ] Simulate new employee onboarding
- [ ] Simulate employee offboarding
- [ ] Troubleshoot domain login problems
- [ ] Troubleshoot Group Policy issues
- [ ] Document practical service desk support tickets
- [ ] Add verification commands and test results

---

**Project Status:** Initial documentation / Lab foundation

*This project forms part of my wider IT Support & Helpdesk Lab portfolio.*
