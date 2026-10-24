# Active Directory Lab – Windows Server 2022

## Project Overview

This project demonstrates the installation, configuration and management of Active Directory Domain Services (AD DS) using Windows Server 2022 and Windows 11 Pro in a virtual lab environment.

The purpose of this project is to develop and demonstrate practical IT Support and Service Desk skills, including Windows Server administration, domain management, user accounts, security groups and Group Policy.

The lab was built using Oracle VirtualBox and focuses on tasks commonly performed by 1st Line IT Support Technicians and Service Desk Analysts.

## Technologies Used

- Windows Server 2022
- Windows 11 Pro
- Oracle VirtualBox
- Active Directory Domain Services (AD DS)
- DNS Server
- Group Policy Management
- Active Directory Users and Computers (ADUC)
- Windows Command Prompt

## Lab Environment

| Component | Configuration |
|---|---|
| Domain Controller | Windows Server 2022 |
| Client Computer | Windows 11 Pro |
| Virtualisation | Oracle VirtualBox |
| Server Hostname | DC-LAB |
| Domain Name | jslab.local |
| Server IP Address | 192.168.1.226 (observed in lab screenshots) |
| Subnet Mask | 255.255.255.0 |
| Client Preferred DNS | 192.168.1.226 |
| Windows 11 Computer Name | WIN11 |

**Note:** The IP address above was observed in the lab screenshots. The server was using DHCP when the network configuration was captured. A static IP address or DHCP reservation is recommended for a domain controller.

---

# Part 1: Active Directory Setup

## Step 1: Configure and Check Windows Server Networking

Before installing Active Directory, the Windows Server must have a working network connection.

### Check the Network Configuration

1. Open Command Prompt on Windows Server 2022.
2. Enter the following command:

`ipconfig /all`

3. Check the server's IP address, subnet mask, gateway and DNS settings.
4. Confirm that the server is connected to the correct VirtualBox network.

### Recommended Static IP Configuration

For a stable domain controller, configure a fixed IP address:

1. Open Server Manager.
2. Select Local Server.
3. Click the Ethernet network connection.
4. Open the network adapter properties.
5. Select Internet Protocol Version 4 (TCP/IPv4).
6. Select Use the following IP address.
7. Enter an appropriate unused address for the lab network.
8. Save the settings.

Once the DNS Server role is configured, the domain controller should use its own DNS service.

### Screenshot 01 — Windows Server Network Configuration

![Windows Server Network Configuration](screenshots/01-server-network-config.png)

This screenshot shows the Windows Server network information obtained using `ipconfig /all`.

---

## Step 2: Open Server Manager

Server Manager is used to install and manage Windows Server roles and features.

1. Open Server Manager.
2. Select Local Server.
3. Review the server name, operating system, network configuration and domain information.

### Screenshot 02 — Windows Server Manager Overview

![Windows Server Manager](screenshots/02-server-manager.png)

This screenshot shows Windows Server 2022 running in Oracle VirtualBox.

---

## Step 3: Install Active Directory Domain Services

Active Directory Domain Services allows administrators to centrally manage domain users, computers and security settings.

### Installation Steps

1. Open Server Manager.
2. Click Manage.
3. Select Add Roles and Features.
4. Select Role-based or feature-based installation.
5. Select the Windows Server.
6. On Server Roles, select Active Directory Domain Services.
7. Click Add Features when prompted.
8. Continue through the installation wizard.
9. Click Install.

The DNS Server role is also required for Active Directory domain name resolution.

### Screenshot 03 — Installed Server Roles

![Installed Server Roles](screenshots/03-installed-server-roles.png)

This screenshot shows Active Directory Domain Services and DNS Server listed as installed server roles.

---

## Step 4: Promote the Server to a Domain Controller

After installing AD DS, the server must be promoted to a domain controller.

### Configuration Steps

1. Open Server Manager.
2. Click the notification flag.
3. Select Promote this server to a domain controller.
4. Select Add a new forest.
5. Enter the domain name:

`jslab.local`

6. Leave DNS Server and Global Catalog selected.
7. Create a Directory Services Restore Mode password.
8. Review the configuration.
9. Complete the prerequisite checks.
10. Click Install.

The server restarts after the domain controller promotion process.

### Screenshot 04 — Active Directory Server Configuration

![Active Directory Server](screenshots/04-active-directory-server.png)

This screenshot shows the AD DS server in Server Manager after configuration.

---

## Step 5: Verify the Domain Controller

After installation, verify that the server is operating as a domain controller.

Open Command Prompt and enter:

`echo %LOGONSERVER%`

The command displays the logon server associated with the current session.

In this lab, the result was:

`\\DC-LAB`

### Screenshot 05 — Domain Controller Verification

![Domain Controller Verification](screenshots/05-domain-controller-verification.png)

This screenshot shows the logon server returned by Windows.

---

## Step 6: Verify DNS Configuration

DNS is an important part of Active Directory because domain computers use it to locate domain controllers and other domain services.

### Verification Steps

1. Open Server Manager.
2. Select Tools.
3. Open DNS.
4. Expand the server.
5. Expand Forward Lookup Zones.
6. Select `jslab.local`.
7. Review the DNS records.

The DNS configuration should contain records associated with the domain controller.

### Screenshot 06 — DNS Server Configuration

![DNS Server Configuration](screenshots/06-dns-configuration.png)

This screenshot shows the Active Directory DNS zone and associated records.

---

## Step 7: Verify Active Directory Users and Computers

Active Directory Users and Computers is used to manage domain accounts, security groups, computers and organisational units.

### Verification Steps

1. Open Server Manager.
2. Select Tools.
3. Open Active Directory Users and Computers.
4. Expand `jslab.local`.
5. Confirm the Active Directory containers are available.

### Screenshot 08 — Active Directory Verification

![Active Directory Verification](screenshots/08-active-directory-verification.png)

This screenshot shows Active Directory Users and Computers with the `jslab.local` domain.

---

# Part 2: Windows 11 Domain Join

This section demonstrates how to connect a Windows 11 computer to the Active Directory domain.

## Step 1: Prepare Windows 11

1. Create a Windows 11 Pro virtual machine in Oracle VirtualBox.
2. Connect the virtual machine to the same accessible network as the domain controller.
3. Start Windows 11.
4. Confirm that the computer can communicate with the server.

Windows 11 Pro supports joining an Active Directory domain.

## Step 2: Configure Windows 11 DNS

The Windows 11 client must use the domain controller's DNS service to locate the Active Directory domain.

### Configuration Steps

1. Open Windows 11 Settings.
2. Navigate to Network & Internet.
3. Open the network connection properties.
4. Select DNS server assignment.
5. Change the setting to Manual.
6. Enable IPv4.
7. Enter the domain controller IP address.

**Preferred DNS:** `192.168.1.226`

8. Save the settings.

### Screenshot 09 — Windows 11 DNS Configuration

![Windows 11 DNS Configuration](screenshots/09-client-dns.png)

This screenshot shows Windows 11 configured to use the domain controller as its preferred DNS server.

---

## Step 3: Join Windows 11 to Active Directory

### Domain Join Steps

1. Press Windows + R.
2. Enter `sysdm.cpl`.
3. Open the Computer Name tab.
4. Click Change.
5. Select Domain.
6. Enter `jslab.local`.
7. Enter authorised domain credentials when prompted.
8. Complete the domain join process.
9. Restart Windows 11.

After joining the domain, the computer becomes part of the Active Directory environment.

### Screenshot 10 — Windows 11 Domain Membership

![Windows 11 Domain Membership](screenshots/10-domain-membership.png)

This screenshot shows the Windows 11 computer with the full device name `win11.jslab.local`.

---

## Step 4: Verify the Computer in Active Directory

After joining Windows 11 to the domain, the computer account should appear in Active Directory.

### Verification Steps

1. Open Active Directory Users and Computers.
2. Expand `jslab.local`.
3. Select Computers.
4. Locate the Windows 11 computer account.

### Screenshot 11 — Active Directory Computer Verification

![Active Directory Computer Verification](screenshots/11-domain-verification.png)

This screenshot shows the `WIN11` computer object registered in Active Directory.

---

## Step 5: Log In Using a Domain Account

After joining Windows 11 to the domain, users can sign in using Active Directory accounts.

Example account:

`JSLAB\helpdesk`

### Verification Steps

1. Start Windows 11.
2. Sign in using the domain user account.
3. Open Command Prompt.
4. Run:

`whoami`

The command should display the domain and username.

Example result:

`jslab\helpdesk`

### Screenshot 12 — Windows 11 Domain Login

![Windows 11 Domain Login](screenshots/12-domain-login.png)

This screenshot shows a successful Windows 11 domain user session verified using `whoami`.

---

# Part 3: Group Policy Management

Group Policy allows administrators to manage Windows settings across domain users and computers.

This section covers creating a Group Policy Object, configuring a restriction and linking the policy to an organisational unit.

## Step 1: Open Group Policy Management

1. Open Server Manager.
2. Click Tools.
3. Select Group Policy Management.
4. Expand Forest: jslab.local.
5. Expand Domains.
6. Select `jslab.local`.

---

## Step 2: Create a Group Policy Object

### Configuration Steps

1. Expand Group Policy Objects.
2. Right-click Group Policy Objects.
3. Select New.
4. Enter the policy name:

`Desktop Lockdown Policy`

5. Click OK.

### Screenshot 13 — Group Policy Object Creation

![Group Policy Object Creation](screenshots/13-gpo-created.png)

This screenshot shows the Desktop Lockdown Policy listed in Group Policy Management.

---

## Step 3: Configure Group Policy Settings

The Desktop Lockdown Policy is designed to restrict access to Control Panel and Windows Settings for selected test users.

### Configuration Steps

1. Right-click Desktop Lockdown Policy.
2. Select Edit.
3. Navigate to:

User Configuration → Policies → Administrative Templates → Control Panel

4. Open Prohibit access to Control Panel and PC settings.
5. Select Enabled.
6. Click Apply.
7. Click OK.

### Screenshot 14 — Group Policy Settings

![Group Policy Settings](screenshots/14-gpo-settings.png)

This screenshot shows the Control Panel restriction configured as Enabled.

---

## Step 4: Link the GPO to an Organisational Unit

A Group Policy Object must be linked to an appropriate domain, site or OU for its settings to apply.

### Configuration Steps

1. Open Group Policy Management.
2. Expand `jslab.local`.
3. Expand Company.
4. Select the GPO-Test OU.
5. Right-click the OU.
6. Select Link an Existing GPO.
7. Select Desktop Lockdown Policy.
8. Click OK.

The linked policy should appear under Linked Group Policy Objects.

### Screenshot 15 — GPO Linked to an OU

![GPO Linked to OU](screenshots/15-gpo-linked.png)

*Illustrative example showing Desktop Lockdown Policy linked to GPO-Test.*

---

## Step 5: Verify Group Policy on Windows 11

After a user-targeted GPO is linked to an OU containing the intended test user, Windows can process the policy during Group Policy refresh and sign-in.

### Verification Steps

1. Sign in to Windows 11 using an appropriate domain test account.
2. Open Command Prompt.
3. Run:

`gpupdate /force`

4. Sign out and sign back in if required.
5. Run:

`gpresult /r`

6. Check whether Desktop Lockdown Policy appears in the applied user policies.
7. Attempt to open Control Panel.

If the restriction is applied correctly, Windows should prevent the user from opening Control Panel.

### Screenshot 16 — Group Policy Verification

![Group Policy Verification Example](screenshots/16-gpo-verification-example.png)

*Illustrative example showing a successful Group Policy refresh and a Windows restriction message. This is not a verified test result from the lab.*

---

# Part 4: Organisational Units (OUs)

Organisational Units help administrators organise Active Directory users, groups and computers.

They can also be used to apply Group Policy settings to specific departments and delegate administrative responsibilities.

## Step 1: Create Organisational Units

### Configuration Steps

1. Open Active Directory Users and Computers.
2. Expand `jslab.local`.
3. Right-click the domain.
4. Select New → Organizational Unit.
5. Enter the OU name.
6. Click OK.
7. Repeat for additional departments.

### Example OU Structure

```text
jslab.local
│
└── Company
    ├── Finance
    ├── HR
    ├── IT
    └── GPO-Test
```

### Screenshot 17 — Active Directory OU Structure

![Active Directory OU Structure](screenshots/17-ou-structure.png)

*Illustrative example showing departmental OUs under Company.*

---

## Step 2: Organise Users Within an OU

Users can be placed into departmental OUs to make account management easier.

### Configuration Steps

1. Open Active Directory Users and Computers.
2. Expand `jslab.local`.
3. Expand Company.
4. Select the relevant department, such as HR.
5. Create a user inside the OU or move an existing user into it.
6. Verify that the user appears in the correct OU.

### Screenshot 18 — Users Within an OU

![Users Within an OU](screenshots/18-ou-contents.png)

*Illustrative example showing user accounts organised within the HR OU.*

---

# Part 5: User and Group Management

This section demonstrates common Active Directory administration tasks, including user account creation, security group configuration and group membership management.

## Step 1: Create an Active Directory User Account

### Configuration Steps

1. Open Active Directory Users and Computers.
2. Expand `jslab.local`.
3. Open Company → HR.
4. Right-click the HR OU.
5. Select New → User.
6. Enter the account details.

### Example User Account

| Field | Value |
|---|---|
| First Name | James |
| Last Name | Smith |
| Username | jsmith |
| Domain | jslab.local |
| Department | HR |

7. Click Next.
8. Create a temporary password.
9. Select User must change password at next logon, if appropriate.
10. Complete the wizard.
11. Open the user account properties to review the details.

### Screenshot 19 — Active Directory User Account

![Active Directory User Account Example](screenshots/19-user-account-example.png)

*Illustrative example showing the properties of the jsmith user account within the HR OU.*

---

## Step 2: Create a Security Group

Security groups allow administrators to manage permissions and access for multiple users.

### Configuration Steps

1. Open Active Directory Users and Computers.
2. Navigate to Company → HR.
3. Right-click the HR OU.
4. Select New → Group.
5. Enter the group name:

`HR-Staff`

6. Select Global as the group scope.
7. Select Security as the group type.
8. Click OK.

### Screenshot 20 — Active Directory Security Group

![Security Group Example](screenshots/20-security-group-example.png)

*Illustrative example showing HR-Staff configured as a Global Security group.*

---

## Step 3: Add a User to a Security Group

### Configuration Steps

1. Open Active Directory Users and Computers.
2. Navigate to the HR OU.
3. Double-click HR-Staff.
4. Select the Members tab.
5. Click Add.
6. Enter the username:

`jsmith`

7. Click Check Names.
8. Click OK.
9. Click Apply.
10. Verify that the user appears in the Members list.

### Screenshot 21 — Security Group Membership

![Security Group Membership Example](screenshots/21-group-membership-example.png)

*Illustrative example showing jsmith as a member of the HR-Staff security group.*

---

# Project Summary

This Active Directory lab provides a foundation for understanding Windows Server administration and Active Directory support tasks.

The project covers Windows Server setup, Active Directory installation, Windows 11 domain membership, Group Policy configuration, organisational units, user accounts and security groups.

## Skills Covered

- Windows Server 2022 administration
- Virtual machine setup using Oracle VirtualBox
- Windows network configuration
- Active Directory Domain Services installation
- Domain controller configuration
- DNS configuration and verification
- Windows 11 domain joining
- Domain user authentication
- Active Directory Users and Computers
- Organisational Unit management
- Group Policy Object creation and configuration
- Security group management
- User account administration
- Windows command-line verification

## Screenshot Documentation

The project has 20 planned screenshot references across five sections.

| Section | Screenshots |
|---|---|
| Part 1 — Active Directory Setup | 01–06, 08 |
| Part 2 — Windows 11 Domain Join | 09–12 |
| Part 3 — Group Policy Management | 13–16 |
| Part 4 — Organisational Units | 17–18 |
| Part 5 — User and Group Management | 19–21 |

**Evidence note:** Some screenshots are illustrative examples rather than captures from the live lab. These are identified in their captions. They demonstrate the intended configuration but should not be treated as proof that the corresponding actions were completed in the virtual machines.

## Future Improvements

The following practical exercises are planned to expand the project:

- [ ] Replace illustrative screenshots with genuine lab captures
- [ ] Configure a static IP address or DHCP reservation for the domain controller
- [ ] Practise Active Directory password resets
- [ ] Practise unlocking user accounts
- [ ] Simulate new employee onboarding
- [ ] Simulate employee offboarding
- [ ] Troubleshoot domain login problems
- [ ] Troubleshoot DNS resolution problems
- [ ] Troubleshoot Group Policy application issues
- [ ] Document practical service desk support tickets
- [ ] Practise user account disabling and re-enabling
- [ ] Add verification commands and test results

---

**Project Status:** Lab foundation documented; further hands-on verification and service desk exercises planned.

*This project forms part of my wider IT Support and Helpdesk portfolio, focusing on practical skills relevant to 1st Line IT Support and Service Desk Analyst positions.*
