# LAB 01 - Manage Entra ID Identities

**Date:** June 23, 2024

## Task 1: Create and Configure User Accounts

### Sign in to the Azure portal
- Accessed the Azure portal at https://portal.azure.com.
- Navigated past the Welcome to Azure splash screen to begin.

### Explore Microsoft Entra ID

- Located and selected Microsoft Entra ID in the Azure portal interface.
- Spent some time familiarizing myself with the Overview and Manage tenants tabs to understand the organizational structure.

### Create a New User

- Under Users, initiated the creation of a new user by selecting New user > Create new user.
- Configured the user principal name as az104-user1 and displayed name as az104-user1.
- Opted for auto-generating the password and ensured the account was enabled.
- Provided additional details such as Job title: IT Lab Administrator, Department: IT, and Usage location: United States.
- Reviewed the settings and confirmed the creation of the new user.
![Create a New User](screenshots/create_a_new_user.png)

## Invite an External User

- Utilized the Invite an external user option under New user.
- Sent an invitation to my personal email address with a welcome message outlining our group project's scope and purpose.
- Entered job title, department, and usage location details to complete the invitation setup.
- Confirmed the invitation was sent and awaited the arrival of the invitation email.

## Task 2: Create Groups and Add Members

### Create a Group

- Accessed Groups in the Azure portal to create a new Security group.
- Named the group IT Lab Administrators with a description emphasizing its role in managing our IT lab environment.
- Chose Assigned as the membership type to maintain control over group membership.
- Acted as the group owner and added `az104-user1` and our invited guest user to ensure comprehensive group membership.
- Successfully created the group and reviewed its setup to verify completeness.

### Review Group Details
- Refreshed the portal page to confirm the creation of the IT Lab Administrators group.
- Reviewed the membership list and ensured both `az104-user1` and the invited guest user were properly added as members.
- Noted the flexibility in managing group settings, including expiration and naming policies, for future reference..
