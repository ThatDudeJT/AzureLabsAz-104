# Lab 02b - Manage Governance via Azure Policy

**Date:** June 25, 2024

## Job Skills

### Task 1: Assign Tags via the Azure Portal

1. **Sign in to the Azure portal:**
   - Navigated to [https://portal.azure.com](https://portal.azure.com).
   - Signed in with my credentials.

2. **Create and Assign a Tag to a Resource Group:**
   - Searched for and selected "Resource groups".
   - Created a new resource group with the following details:
     - **Subscription name:** My subscription
     - **Resource group name:** az104-rg2
     - **Location:** East US
   - Assigned a tag with the following settings:
     - **Name:** Cost Center
     - **Value:** 000

### Task 2: Enforce Tagging via an Azure Policy

1. **Assign the Built-in Policy:**
   - Searched for and selected "Policy" in the Azure portal.
   - In the Authoring blade, selected "Definitions".
   - Browsed and selected the "Require a tag and its value on resources" built-in policy.
   - Assigned the policy to the resource group (az104-rg2) with the following settings:
     - **Scope:** My subscription and az104-rg2
     - **Assignment name:** Require Cost Center tag with Default value
     - **Description:** Require Cost Center tag with default value for all resources in the resource group
     - **Policy enforcement:** Enabled
   - Set the parameters:
     - **Tag Name:** Cost Center
     - **Tag Value:** 000

### Task 3: Apply Tagging via an Azure Policy

1. **Remediate Non-compliant Resources:**
   - Deleted the previous policy assignment.
   - Assigned the "Inherit a tag from the resource group if missing" policy to the resource group (az104-rg2) with the following settings:
     - **Scope:** My subscription and az104-rg2
     - **Assignment name:** Inherit the Cost Center tag and its value 000 from the resource group if missing
     - **Description:** Inherit the Cost Center tag and its value 000 from the resource group if missing
     - **Policy enforcement:** Enabled
     - **Parameters:** Tag Name: Cost Center
     - **Remediation task:** Enabled

### Task 4: Configure and Test Resource Locks

1. **Configure a Resource Lock:**
   - Searched for and selected my resource group (az104-rg2).
   - In the Settings blade, selected "Locks".
   - Added a resource lock with the following settings:
     - **Lock name:** rg-lock
     - **Lock type:** Delete
   - Attempted to delete the resource group and confirmed the deletion was denied due to the lock.

## Conclusion

In this lab, I successfully implemented Azure Policy to enforce governance standards, remediated non-compliant resources, and audited policy effectiveness. I also configured resource locks to protect critical resources. These practices ensure that resources within Azure are compliant with organizational policies and standards.

Note: All screenshots taken during the lab have been uploaded to the relevant directory in the GitHub repository.