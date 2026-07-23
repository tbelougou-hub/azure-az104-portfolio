# Day 01 – Identity & Governance I (RBAC)

**Exam domain:** Identity & Governance
**Date completed:20/07/2026**

## What I built
- I created two Microsoft Entra ID test users (testuser1, testuser2) and added both to a new security group (TestAdmins).
- I Created a resource group (rg-lab-day1) and assigned the built-in Reader role to the group at resource-group scope via Access Control (IAM). Then built a custom RBAC role (LabViewerPlus) that grants only permission to start VMs, and validated the group's effective access using the Check Access tool.
  
## Key commands / concepts used
Portal paths used: Microsoft Entra ID > Users > + New user Microsoft Entra ID > Groups > + New group (Security) Resource groups > + Create Access control (IAM) > Add role assignment > Reader Access control (IAM) > Roles > + Add > Add custom role - custom permission: Microsoft.Compute/virtualMachines/start/action Access control (IAM) > Check access

## What I learned / what surprised me
Custom roles are just JSON permission sets — instead of using an overly broad built-in role, I could start from scratch and add one narrowly scoped action.
RBAC assignments can be scoped as tightly as a single resource group, not just the
whole subscription.

## Screenshots
![Entra ID users created](screenshots/01-users-created.png)
![Security group membership](screenshots/02-group-members.png)
![Role assignment at resource group scope](screenshots/03-role-assignment.png)
![Custom role permissions JSON](screenshots/04-custom-role-json.png)
![Final resource group overview](screenshots/05-final-overview.png)
