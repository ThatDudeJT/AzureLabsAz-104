# Lab 02a - Manage Subscriptions and RBAC

**Date:** [Insert Date]

## Lab Introduction

In this lab, we explore role-based access control (RBAC) in Azure and learn how to manage subscriptions effectively using management groups. RBAC allows us to control access to Azure resources based on roles assigned to users, groups, or applications.

## Lab Scenario

To streamline Azure resource management within our organization, we focus on the following tasks:

- Creating a management group to organize Azure subscriptions.
- Assigning permissions to manage virtual machines and create support requests.
- Implementing custom RBAC roles to meet specific access requirements.

## Architecture Diagram

[Insert Architecture Diagram if applicable]

## Job Skills

### Task 1: Implement Management Groups

1. **Sign in to the Azure portal:**
   - Navigate to [https://portal.azure.com](https://portal.azure.com).
   - Sign in with your credentials.

2. **Navigate to Microsoft Entra ID:**
   - Search for and select "Microsoft Entra ID" from the Azure portal.
   - Navigate to the Manage blade > Properties.

3. **Review Access Management for Azure Resources:**
   - Ensure access management is configured to handle Azure subscriptions and management groups in your tenant.

4. **Create a Management Group:**
   - Navigate to Management groups in the Azure portal.
   - Click on + Create and configure the new management group:
     - **Management group ID:** az104-mg1 (must be unique in the directory)
     - **Management group display name:** az104-mg1
   - Submit the configuration and refresh the page to view the newly created management group.

### Task 2: Review and Assign a Built-in Azure Role

1. **Select the Management Group:**
   - Navigate to the newly created az104-mg1 management group in the Azure portal.

2. **Access Control (IAM) Settings:**
   - Go to the Access control (IAM) blade and select the Roles tab.
   - Browse through the available built-in roles (e.g., Owner, Contributor, Reader).

3. **Assign the Virtual Machine Contributor Role:**
   - Click on + Add > Add role assignment.
   - Search for and select the "Virtual Machine Contributor" role.
   - Proceed to the Members tab and select the appropriate group (e.g., helpdesk group).
   - Review and confirm the role assignment.

### Task 3: Create a Custom RBAC Role

1. **Create a Custom Role:**
   - In the Access control (IAM) blade, select the Check access tab.
   - Click on Add under Create a custom role.

2. **Configure the Custom Role:**
   - Basics tab:
     - **Custom role name:** Custom Support Request
     - **Description:** A custom contributor role for support requests.
     - Clone a role: Support Request Contributor.

3. **Refine Permissions:**
   - Permissions tab:
     - Click on + Exclude permissions.
     - Enter .Support in the resource provider search field and select Microsoft.Support.
     - Exclude the permission for "Registers Support Resource Provider" as a NotAction.

4. **Assignable Scopes:**
   - Assignable scopes tab:
     - Ensure the management group (az104-mg1) is listed.
     - Proceed to the next step.

5. **Review and Create:**
   - Review the JSON configuration for Actions, NotActions, and AssignableScopes.
   - Click on Review + Create and then Create to finalize the custom role creation.

### Task 4: Monitor Role Assignments with the Activity Log

1. **View Activity Log:**
   - Locate the az104-mg1 resource in the Azure portal.
   - Navigate to Activity log to monitor subscription-level events.

2. **Filter and Review Role Assignments:**
   - Apply filters in the Activity log to view specific operations related to role assignments.
   - Monitor activities related to the creation and modification of role assignments.

## Conclusion

In this lab, we successfully implemented management groups in Azure to organize subscriptions and applied RBAC principles to manage access effectively. We reviewed and assigned built-in roles, created a custom RBAC role tailored to specific requirements, and monitored role assignments using the Activity log. These skills are essential for maintaining security and compliance in Azure environments.

Notes: