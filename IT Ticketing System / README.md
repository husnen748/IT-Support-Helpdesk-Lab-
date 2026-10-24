
# IT Support Helpdesk – Ticketing System Lab

## Project Overview

This project documents example IT support tickets across three widely used IT Service Management (ITSM) platforms:

- ServiceNow
- Freshservice
- Jira Service Management

The purpose is to study how IT support teams receive, categorise, prioritise, investigate, escalate and resolve technical issues.

The scenarios focus on common 1st Line IT Support responsibilities, including Active Directory account management, password resets, new employee onboarding, Outlook troubleshooting, printer issues and service requests.

> **Evidence notice:** The ServiceNow and Freshservice screenshots are AI-generated illustrative examples. The Jira screenshots are reference material from another GitHub project. They are included for learning and workflow analysis, not as evidence of independently completed hands-on ticketing tasks.

---

## Skills and Concepts Covered

- IT helpdesk incident management
- Ticket categorisation and prioritisation
- ITIL incident and service request concepts
- Active Directory account administration
- Password reset procedures
- New employee onboarding
- Microsoft Outlook troubleshooting
- Printer troubleshooting scenarios
- Service Level Agreements (SLAs)
- Customer communication
- Work notes and resolution documentation
- Ticket assignment and escalation

---

# 1. ServiceNow – Incident Management

The ServiceNow section contains three example incidents demonstrating common helpdesk scenarios.

## Ticket 1 – Active Directory Account Lockout

**Incident:** INC0010045  
**Category:** Software  
**Priority:** 4 – Low  
**Status shown:** New

### Issue

A user is unable to sign in to a Windows 11 workstation after multiple incorrect password attempts.

**Lab environment referenced:**

- Windows Server 2022
- Active Directory domain: `jslab.local`
- Domain controller: `DC-LAB`
- Windows 11 workstation: `WIN11`
- User account: `jslab\helpdesk`

### Investigation and Troubleshooting

The example work notes describe:

1. Verifying the user's identity.
2. Checking the account in Active Directory.
3. Identifying an account lockout.
4. Unlocking the account and resetting the password.
5. Asking the user to test their login.

**Note:** The screenshot contains work notes describing successful access, but the main ticket status remains New. It does not show a consistently completed ticket.

### Screenshot

![ServiceNow AD Account Lockout](01-servicenow-ad-account-lockout-example.png.png)

---

## Ticket 2 – New Employee Onboarding

**Incident:** INC0010056  
**Priority:** 2 – Medium  
**Status shown:** Resolved

### Issue

A new Finance employee requires access to company systems before their start date.

### Systems and Access Requested

- Active Directory account
- Finance security group
- Email account
- VPN access
- SAP financial system access
- Configured laptop

### Work Notes and Resolution

The example describes account provisioning, group membership, system configuration and access testing.

The screenshot shows the ticket marked Resolved, with resolution information recorded.

### Screenshot

![ServiceNow New Employee Onboarding](02-servicenow-new-employee-onboarding-example.png.png)

---

## Ticket 3 – Microsoft Outlook Not Receiving Emails

**Incident:** INC0010078  
**Category:** Software / Email  
**Priority:** 3 – Moderate  
**Status shown:** New

### Issue

A user reports that Microsoft Outlook has stopped receiving new emails, while webmail continues to work.

### Investigation and Troubleshooting

The example work notes describe:

1. Checking Outlook connectivity.
2. Investigating mailbox capacity.
3. Identifying a nearly full mailbox.
4. Freeing mailbox space.
5. Restarting Outlook.
6. Checking that email synchronisation resumes.

### Outcome

The activity history describes the issue as resolved, but the main ticket status still shows New.

This screenshot is therefore an example of troubleshooting documentation rather than consistent evidence of a closed incident.

### Screenshot

![ServiceNow Outlook Email Issue](03-servicenow-outlook-email-issue-example.png.png)

---

# 2. Freshservice – Password Reset Incident

## Ticket 1 – Active Directory Password Reset

**Incident:** INC-3  
**Category:** Access & Accounts  
**Subcategory:** Password Reset  
**Priority:** Medium  
**Final example status:** Resolved

### Issue

A user contacts the IT Support team after forgetting their account password.

The example follows three stages of an incident lifecycle.

## Stage 1 – Ticket Created

The initial screenshot shows:

- A new incident raised by email.
- The user's password reset request.
- Priority and ticket classification.
- An acknowledgement from the IT Support team.

![Freshservice Initial Password Reset Ticket](01-freshservice-password-reset-ticket-example.png.png)

## Stage 2 – Investigation and Troubleshooting

The second screenshot illustrates:

1. Reviewing the user's Active Directory account.
2. Checking the account status.
3. Recording a password reset in the internal work notes.
4. Requiring a password change at next login.
5. Updating the user through the ticket.

**Status shown:** In Progress

![Freshservice Password Reset Investigation](02-freshservice-password-reset-investigation-example.png.png)

## Stage 3 – Resolution

The final screenshot illustrates:

- User confirmation of successful login.
- Password change confirmation.
- Private resolution notes.
- Ticket status updated to Resolved.
- First-response and resolution SLA indicators.

![Freshservice Password Reset Resolution](03-freshservice-password-reset-resolution-example.png.png)

### Ticket Lifecycle

New → In Progress → Resolved

This example illustrates the importance of documenting troubleshooting, keeping users informed and confirming that an issue is fixed before resolving the ticket.

**Security consideration:** Passwords should not be recorded in public tickets, screenshots or GitHub repositories. Approved secure password reset and identity verification procedures should be followed.

---

# 3. Jira Service Management – Helpdesk Requests

This section contains reference screenshots of two service desk tickets, including the customer portal, agent interface and SLA information.

## Ticket 1 – Shared Printer Not Printing

**Ticket:** NDIV-4  
**Request type:** Hardware Issue  
**Priority:** High  
**Status shown:** Open

### Issue

A user reports that print jobs remain stuck in the queue when printing to a shared office printer.

The printer is powered on and other users may also be affected.

### Screenshot 1 – Customer Portal

Shows the request from the customer's perspective, including urgency, business impact and affected hardware.

![Jira Printer Customer Portal](01-jira-printer-customer-portal.png.png)

### Screenshot 2 – IT Support Agent View

Shows how the IT Support Agent reviews the ticket, including its assignment, classification and priority.

![Jira Printer Agent View](02-jira-printer-agent-view.png.png)

### Screenshot 3 – SLA Tracking

Shows the first-response and resolution targets associated with the printer incident.

![Jira Printer SLA](03-jira-printer-sla.png.png)

### Learning Points

- Handling hardware incidents
- Understanding urgency and business impact
- Assigning and reviewing support tickets
- Monitoring SLA deadlines

**Resolution status:** No completed troubleshooting or resolution is shown in these reference screenshots.

---

## Ticket 2 – New Employee Access Request

**Ticket:** NDIV-6  
**Request type:** New User Access Request  
**Priority:** Medium  
**Status shown:** Waiting for Support

### Issue

A manager requests account and system access for a new employee starting the following week.

### Access Requested

- Windows login / computer account
- Microsoft 365 / Email
- Shared drive / file access

### Screenshot 1 – Access Request Form

Shows the form used to collect account requirements, business justification, urgency, impact and manager approval details.

![Jira New User Request Form](06-jira-new-user-request-form.png.png)

### Screenshot 2 – Customer Ticket

Shows the submitted access request in the customer portal.

![Jira New User Customer Ticket](07-jira-new-user-customer-ticket.png.png)

### Screenshot 3 – IT Support Agent View

Shows the ticket assigned to an IT Support Agent, with requested access, approver information and priority.

![Jira New User Agent View](08-jira-new-user-agent-view.png.png)

### Learning Points

- Service request management
- User access requirements
- Manager approval workflows
- Ticket assignment
- Onboarding coordination

**Resolution status:** The screenshots do not show completed account provisioning or confirmed access.

---

# 4. Comparison of Ticketing Platforms

| Feature | ServiceNow | Freshservice | Jira Service Management |
|---|---|---|---|
| Incident management | Illustrated | Illustrated | Illustrated |
| Service requests | Onboarding example | Not shown | Access request example |
| Priority classification | Yes | Yes | Yes |
| Work notes | Yes | Yes | Agent interface shown |
| Customer communication | Yes | Yes | Portal shown |
| SLA tracking | Not demonstrated | Yes | Yes |
| Resolution documentation | Example notes | Three-stage example | Not shown |

---

# 5. What I Learned

Reviewing these examples helped me understand:

1. How IT support incidents and service requests are structured.
2. Why accurate ticket categorisation and priority are important.
3. How IT teams document troubleshooting steps and communicate with users.
4. How SLAs are used to track support response and resolution targets.
5. Why a ticket should only be marked Resolved after the solution has been confirmed.
6. How ticketing systems can support Active Directory administration and common Windows troubleshooting tasks.

---

# 6. Future Hands-On Development

The next stage is to recreate these scenarios in live practice environments and replace illustrative screenshots with genuine evidence.

Planned exercises include:

- Creating and resolving ServiceNow incidents.
- Recording Active Directory account unlocks and password resets.
- Managing Freshservice tickets from creation through resolution.
- Creating Jira Service Management requests with investigation notes and final outcomes.
- Documenting SLA tracking, escalation and customer communication.
- Linking real ticket evidence to the Active Directory lab.

---

## Disclaimer

This repository contains educational ticketing examples and workflow references. AI-generated screenshots and third-party reference images are not presented as authentic records of work performed in ServiceNow, Freshservice or Jira Service Management.

