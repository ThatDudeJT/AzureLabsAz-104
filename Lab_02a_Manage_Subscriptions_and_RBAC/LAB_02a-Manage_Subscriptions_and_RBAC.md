# Lab 02a - Manage Subscriptions and RBAC

**Date:** June 24, 2024

## Lab Introduction

In this lab, we explored role-based access control (RBAC) in Azure and learned how to manage subscriptions effectively using management groups. RBAC allows us to control access to Azure resources based on roles assigned to users, groups, or applications.

## Lab Scenario

To streamline Azure resource management within our organization, we focused on the following tasks:

- Creating a management group to organize Azure subscriptions.
- Assigning permissions to manage virtual machines and create support requests.
- Implementing custom RBAC roles to meet specific access requirements.

## Job Skills

### Task 1: Implement Management Groups

1. **Signed in to the Azure portal:**
   - Navigated to [https://portal.azure.com](https://portal.azure.com).
   - Signed in with my credentials.

2. **Navigated to Microsoft Entra ID:**
   - Searched for and selected "Microsoft Entra ID" from the Azure portal.
   - Went to the Manage blade > Properties.

3. **Reviewed Access Management for Azure Resources:**
   - Ensured access management was configured to handle Azure subscriptions and management groups in the tenant.

4. **Created a Management Group:**
   - Navigated to Management groups in the Azure portal.
   - Clicked on + Create and configured the new management group:
     - **Management group ID:** az104-mg1 (unique in the directory)
     - **Management group display name:** az104-mg1
   - Submitted the configuration and refreshed the page to view the newly created management group.

### Task 2: Review and Assign a Built-in Azure Role

1. **Created a Help Desk Group:**
   - Navigated to "Groups" in the Azure portal.
   - Clicked on + New group and configured the new group:
     - **Group name:** Help Desk
     - **Group description:** Group for Help Desk staff
     - **Group type:** Security
   - Clicked on Create to finalize the new group.

2. **Selected the Management Group:**
   - Navigated to the newly created az104-mg1 management group in the Azure portal.

3. **Access Control (IAM) Settings:**
   - Went to the Access control (IAM) blade and selected the Roles tab.
   - Browsed through the available built-in roles (e.g., Owner, Contributor, Reader).

4. **Assigned the Virtual Machine Contributor Role:**
   - Clicked on + Add > Add role assignment.
   - Searched for and selected the "Virtual Machine Contributor" role.
   - Proceeded to the Members tab and selected the Help Desk group created earlier.
   - Reviewed and confirmed the role assignment.

### Task 3: Create a Custom RBAC Role

1. **Created a Custom Role:**
   - In the Access control (IAM) blade, selected the Check access tab.
   - Clicked on Add under Create a custom role.

2. **Configured the Custom Role:**
   - Basics tab:
     - **Custom role name:** Custom Support Request
     - **Description:** A custom contributor role for support requests.
     - Cloned a role: Support Request Contributor.

3. **Refined Permissions:**
   - Permissions tab:
     - Clicked on + Exclude permissions.
     - Entered .Support in the resource provider search field and selected Microsoft.Support.
     - Excluded the permission for "Registers Support Resource Provider" as a NotAction.

4. **Assignable Scopes:**
   - Assignable scopes tab:
     - Ensured the management group (az104-mg1) was listed.
     - Proceeded to the next step.

5. **Reviewed and Created:**
   - Reviewed the JSON configuration for Actions, NotActions, and AssignableScopes.
   - Clicked on Review + Create and then Create to finalize the custom role creation.

### Task 4: Monitor Role Assignments with the Activity Log

1. **Viewed Activity Log:**
   - Located the az104-mg1 resource in the Azure portal.
   - Navigated to Activity log to monitor subscription-level events.

2. **Filtered and Reviewed Role Assignments:**
   - Applied filters in the Activity log to view specific operations related to role assignments.
   - Monitored activities related to the creation and modification of role assignments.

## Conclusion

In this lab, we successfully implemented management groups in Azure to organize subscriptions and applied RBAC principles to manage access effectively. We reviewed and assigned built-in roles, created a custom RBAC role tailored to specific requirements, and monitored role assignments using the Activity log. These skills are essential for maintaining security and compliance in Azure environments.

**Note:** All screenshots taken during the lab have been uploaded to the relevant directory in the GitHub repository.
