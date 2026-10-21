# Microsoft 365 Administration Lab

## Project Overview

This project documents common Microsoft 365 administrative tasks performed by Level 1 IT Support Technicians and Service Desk Analysts.

The aim is to develop practical experience managing Microsoft 365 users, licences, security groups, passwords, OneDrive sharing permissions and administrative settings.

Each lab includes a scenario, objective, step-by-step instructions and space for screenshots and verification results.

## Technologies and Tools

- Microsoft 365 Admin Centre
- Microsoft Entra ID
- Microsoft Exchange Online
- Microsoft Teams Admin Centre
- Microsoft SharePoint Admin Centre
- Microsoft OneDrive
- Microsoft 365 Groups

## Lab Environment

| Component | Description |
|---|---|
| Administration portal | https://admin.microsoft.com |
| Identity management | Microsoft Entra ID |
| User management | Microsoft 365 Admin Centre |
| Licence management | Microsoft 365 Admin Centre |
| Email administration | Exchange Admin Centre |
| Collaboration | Microsoft Teams |
| File storage | OneDrive and SharePoint |
| Environment | Microsoft 365 test tenant |

**Note:** The exercises require a Microsoft 365 tenant with suitable administrator permissions. Some features require specific subscriptions or licences.

---

# Part 1: Create a User and Assign a Microsoft 365 Licence

## Scenario

A new employee joins the organisation and requires a Microsoft 365 account to access company email, Teams, OneDrive and other business applications.

## Objective

Create a new user account in Microsoft 365 and assign an appropriate licence.

## Step 1: Open the Microsoft 365 Admin Centre

1. Open a web browser.
2. Navigate to https://admin.microsoft.com.
3. Sign in using an authorised administrator account.
4. From the navigation menu, select **Users**.
5. Click **Active users**.
6. Select **Add a user**.

## Step 2: Enter User Information

1. Enter the employee's first name.
2. Enter their last name.
3. Create a username.
4. Select the appropriate domain.
5. Configure the initial password settings.
6. Require the user to change the temporary password at first sign-in, where available and appropriate.
7. Click **Next**.

### Example User Details

| Field | Example |
|---|---|
| First Name | James |
| Last Name | Smith |
| Display Name | James Smith |
| Username | james.smith |
| Department | IT |
| Account Type | Standard User |

## Step 3: Assign a Microsoft 365 Licence

1. Open the **Product licences** section.
2. Select the appropriate usage location.
3. Review the available licences.
4. Select a licence appropriate for the user's role.

Example:

**Microsoft 365 E5**, if available in the lab tenant.

5. Review the included services.
6. Click **Next**.

**Note:** A licence must be available in the tenant before it can be assigned. Different Microsoft 365 subscriptions include different features.

## Step 4: Complete Account Creation

1. Review the user information.
2. Confirm the selected licence.
3. Click **Finish adding**.
4. Return to **Users > Active users**.
5. Search for the newly created user.
6. Open their profile to verify the account information and assigned licence.

## Verification

- Confirm the user appears in Active users.
- Confirm the correct licence is assigned.
- Verify that the account is enabled for sign-in.
- Test access to an appropriately licensed service when possible.

### Screenshots

*Add screenshots showing the user creation wizard, licence selection, confirmation page and completed user profile.*

---

# Part 2: Create a Microsoft 365 Group and Add a User

## Scenario

A new department requires a Microsoft 365 group so employees can collaborate and access shared resources.

## Objective

Create a Microsoft 365 group, configure its settings and add an existing user as a member.

## Step 1: Open Group Management

1. Sign in to https://admin.microsoft.com.
2. Expand **Teams & groups**.
3. Select **Active teams & groups**.
4. Click **Add a group**.
5. Select **Microsoft 365** as the group type.
6. Click **Next**.

## Step 2: Configure the Group

1. Enter a group name.
2. Add a description explaining its purpose.
3. Configure the group email address, where prompted.
4. Select suitable privacy settings.
5. Continue through the setup wizard.

### Example Group

| Field | Example |
|---|---|
| Group Name | IT Support Team |
| Description | Collaboration group for IT Support staff |
| Group Type | Microsoft 365 |
| Privacy | Private |
| Department | IT |

## Step 3: Add Members

1. Select the option to assign owners and members.
2. Choose an appropriate group owner.
3. Search for the user account.
4. Select the user.
5. Add the user as a member.
6. Review the configuration.
7. Complete group creation.

## Step 4: Verify Group Membership

1. Return to **Active teams & groups**.
2. Locate the new group.
3. Open its details.
4. Navigate to **Members**.
5. Verify that the correct user appears in the membership list.

## Verification

- Confirm the Microsoft 365 group exists.
- Confirm the correct user has been added.
- Check group ownership and privacy settings.
- Verify access to the group's available resources.

**Note:** Microsoft 365 groups can support shared resources such as group mailboxes, calendars and SharePoint sites. A Microsoft Teams team is not automatically created for every Microsoft 365 group, and shared mailboxes can also be managed separately in Exchange Online.

### Screenshots

*Add screenshots showing group creation, settings, member selection and confirmed membership.*

---

# Part 3: Reset a User's Microsoft 365 Password

## Scenario

An employee contacts the IT Service Desk because they have forgotten their Microsoft 365 password and cannot access their account.

## Objective

Reset the user's password securely and restore account access.

## Step 1: Verify the User

1. Confirm the employee's identity using an approved verification procedure.
2. Confirm that a password reset is required.
3. Record the support request in the ticketing system, if available.

## Step 2: Open the User Account

1. Sign in to https://admin.microsoft.com.
2. Select **Users > Active users**.
3. Search for the affected employee.
4. Select the user's account.
5. Click **Reset password**.

## Step 3: Reset the Password

1. Choose the option to generate a temporary password, if available.
2. Require the user to change the password at the next sign-in, where supported.
3. Confirm the reset.
4. Provide the temporary password through an approved secure communication channel.

**Important:** Never include an actual password in screenshots, public GitHub repositories or support ticket notes.

## Step 4: Verify Account Access

1. Ask the user to attempt signing in.
2. Confirm that the user can set a new password.
3. Verify access to Microsoft 365 services.
4. Update the support ticket with the outcome.

**Note:** For organisations using synchronised or federated identities, password reset procedures may depend on the identity configuration and password writeback capabilities.

### Screenshots

*Add screenshots showing the password reset option and confirmation page, with any sensitive information hidden.*

---

# Part 4: Disable and Delete a User Account – Offboarding

## Scenario

An employee leaves the organisation and their Microsoft 365 account must be secured and removed according to the company's offboarding procedure.

## Objective

Block the user's access, review their resources and safely remove the account when authorised.

## Step 1: Locate the User

1. Sign in to https://admin.microsoft.com.
2. Navigate to **Users > Active users**.
3. Search for the employee.
4. Open their user profile.

## Step 2: Block Sign-In

1. Select **Block sign-in**.
2. Change the sign-in status to blocked.
3. Save the changes.
4. Confirm the account shows the updated status.

Blocking sign-in helps prevent further authentication using the account. Existing sessions may remain active temporarily, so administrators should revoke active sessions where required.

## Step 3: Review User Resources

Before deleting the account:

1. Review the user's assigned licences.
2. Identify their mailbox and OneDrive data.
3. Check any required mailbox delegation or data retention.
4. Review Microsoft 365 group memberships.
5. Arrange transfer of business data to authorised employees.
6. Confirm that the offboarding process has been approved.

## Step 4: Delete the User

1. Navigate to **Users > Active users**.
2. Select the affected account.
3. Click **Delete user**.
4. Review the deletion information.
5. Confirm deletion only when authorised.

## Step 5: Review Deleted Users

1. Navigate to **Users > Deleted users**.
2. Locate the deleted account.
3. Confirm that the account appears in the deleted users list.

Deleted Microsoft Entra ID user objects are generally recoverable for 30 days, subject to relevant conditions. Mailbox and OneDrive retention behaviours can differ.

**Important:** Permanent deletion should only be performed when explicitly authorised and after checking applicable retention and data recovery requirements. Do not permanently delete accounts merely to complete an offboarding exercise.

## Verification

- Confirm sign-in has been blocked.
- Confirm the account has been deleted if that was the approved action.
- Review relevant access and resource assignments.
- Record the completed offboarding actions.

### Screenshots

*Add screenshots showing sign-in blocking, the deletion process and the deleted users list.*

---

# Part 5: Manage OneDrive Sharing Permissions

## Scenario

A department requests a change to OneDrive folder permissions to ensure only authorised employees can access shared files.

## Objective

Review organisation-level sharing settings and manage access to a specific OneDrive folder.

## Step 1: Open the SharePoint Admin Centre

1. Sign in to https://admin.microsoft.com.
2. Select **Show all**, if necessary.
3. Open **Admin centres**.
4. Select **SharePoint**.
5. Navigate to **Policies > Sharing**.

## Step 2: Review Organisation-Wide Sharing

1. Review the current SharePoint sharing settings.
2. Review the OneDrive external sharing settings.
3. Identify the level of external sharing currently permitted.
4. Check whether the configured settings meet the organisation's security requirements.

Examples of sharing levels include:

- Anyone
- New and existing guests
- Existing guests
- Only people in your organisation

For an internal-only lab, select **Only people in your organisation** if the exercise requires preventing external sharing.

**Important:** Organisation-wide sharing changes may affect many users. Only make these changes in your own test tenant or with appropriate authorisation.

## Step 3: Open a User's OneDrive

1. Open **Microsoft 365 Admin Centre**.
2. Navigate to **Users > Active users**.
3. Select the appropriate user.
4. Open the user's **OneDrive** settings, if available.
5. Use the available authorised access method to open their OneDrive.

## Step 4: Modify Folder Permissions

1. Locate the required folder.
2. Select the folder.
3. Open **Manage access**.
4. Review existing users and sharing links.
5. Remove access for users who no longer require it.
6. Configure an appropriate permission level for authorised users.

Examples:

- **Can view** – Users can view the files.
- **Can edit** – Users can modify the files.

7. Save the changes.

## Step 5: Verify the Permissions

1. Reopen **Manage access**.
2. Confirm that only the intended users or groups have access.
3. Review whether any existing sharing links remain.
4. Test the permitted access level using an appropriate test account.

### Screenshots

*Add screenshots showing SharePoint sharing policies, OneDrive folder permissions and updated access settings.*

---

# Part 6: Explore Outlook, Teams and OneDrive Administration

## Scenario

An IT Support Technician needs to understand where Microsoft 365 collaboration and email services are managed.

## Objective

Explore the administrative settings available for Exchange Online, Microsoft Teams and OneDrive.

## Step 1: Review Microsoft 365 Organisation Settings

1. Sign in to https://admin.microsoft.com.
2. Navigate to **Settings > Org settings**.
3. Review the available organisational settings.
4. Identify settings that apply across the tenant.
5. Record the settings relevant to IT support.

## Step 2: Explore Exchange Online Administration

1. Open the **Exchange Admin Centre**.
2. Navigate to the recipients section.
3. Review user mailboxes.
4. Explore shared mailbox settings.
5. Review available mailbox delegation options.
6. Identify common mailbox administration tasks.

### Examples

- Reviewing mailbox properties
- Managing shared mailboxes
- Assigning mailbox permissions
- Checking mailbox storage
- Investigating basic mail-flow issues

## Step 3: Explore Microsoft Teams Administration

1. Open the **Teams Admin Centre**.
2. Review available user management settings.
3. Explore Teams policies.
4. Review guest access settings.
5. Review external access settings.
6. Identify settings that administrators can manage for users and the organisation.

**Note:** Guest access and external access are separate Teams capabilities and may be controlled through different administrative settings.

## Step 4: Explore OneDrive Administration

1. Open the **SharePoint Admin Centre**.
2. Review **OneDrive** settings.
3. Explore storage management.
4. Review sharing permissions.
5. Review synchronisation settings and available policies.
6. Identify settings relevant to user support.

## Step 5: Record Findings

Document which admin centre is responsible for each service.

| Service | Administration Tool |
|---|---|
| User accounts | Microsoft 365 Admin Centre / Entra Admin Centre |
| User licences | Microsoft 365 Admin Centre |
| Outlook mailboxes | Exchange Admin Centre |
| Microsoft Teams | Teams Admin Centre |
| OneDrive | SharePoint Admin Centre |
| Identity and security groups | Entra Admin Centre |

### Screenshots

*Add screenshots showing the Exchange, Teams and SharePoint administrative interfaces and the settings reviewed.*

---

# General Microsoft 365 Administration Process

When responding to Microsoft 365 support requests, follow a consistent support procedure.

1. **Identify the request:** Determine what the employee needs.
2. **Verify authorisation:** Confirm their identity and that the requested change is permitted.
3. **Investigate:** Review the relevant Microsoft 365 settings.
4. **Perform the task:** Make the approved administrative change.
5. **Verify:** Confirm the expected result.
6. **Document:** Record the actions taken and outcome.
7. **Close or escalate:** Resolve the request or refer it to the appropriate administrator.

---

# Project Summary

This Microsoft 365 Administration Lab provides a foundation for understanding and practising common cloud administration tasks performed by IT Support Technicians and Service Desk Analysts.

## Skills Covered

- Microsoft 365 Admin Centre navigation
- Creating and managing user accounts
- Assigning and reviewing licences
- Creating Microsoft 365 groups
- Managing group membership
- Resetting user passwords
- Blocking user sign-in
- User offboarding and deletion
- Managing OneDrive folder permissions
- Understanding Exchange Online administration
- Exploring Microsoft Teams administrative settings
- Reviewing Microsoft 365 organisational policies

## Future Improvements

- [ ] Add screenshots for all six exercises
- [ ] Complete user creation and licence assignment
- [ ] Create a group and verify membership
- [ ] Practise a password reset
- [ ] Simulate user offboarding
- [ ] Test OneDrive folder permissions
- [ ] Explore Exchange Online mailbox management
- [ ] Explore Microsoft Teams administration
- [ ] Add Microsoft Entra ID user and MFA administration labs
- [ ] Add support tickets demonstrating Microsoft 365 issues
- [ ] Document verification results and lessons learned

---

**Project Status:** Initial documentation / Lab foundation

*This project forms part of my IT Support & Helpdesk Lab GitHub portfolio.*
