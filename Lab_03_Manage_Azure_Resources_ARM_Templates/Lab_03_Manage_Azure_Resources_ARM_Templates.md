## Lab 03 - Manage Azure resources by using Azure Resource Manager Templates

### Lab introduction
In this lab, I learned how to automate resource deployments using Azure Resource Manager templates and Bicep templates. I explored different methods of deploying these templates.

### Estimated timing: 50 minutes

### Job skills
**Task 1: Created an Azure Resource Manager template**
In this task, I created a managed disk in the Azure portal and exported a template for future deployments.

1. Signed in to the Azure portal.
2. Searched for and selected **Disks**.
3. Created a managed disk named **az104-disk1** in the **East US** region under the **az104-rg3** resource group.
4. Exported the template and parameters files and saved them locally.

**Task 2: Edited an Azure Resource Manager template and redeployed the template**
I used the exported template to deploy a new managed disk with some modifications.

1. Searched for and selected **Deploy a custom template** in the Azure portal.
2. Uploaded the template.json file and made necessary changes.
3. Deployed the template to create **az104-disk2** in the **az104-rg3** resource group.

**Task 3: Configured the Cloud Shell and deployed a template with PowerShell**
Used Azure Cloud Shell and PowerShell to deploy a template.

1. Selected the Cloud Shell icon, chose PowerShell, and configured the storage account.
2. Uploaded the template and parameters files to Cloud Shell.
3. Edited and deployed the template using PowerShell to create **az104-disk3**.

**Task 4: Deployed a template with the CLI**
Deployed a template using Azure CLI.

1. Switched to Bash in Cloud Shell.
2. Edited and deployed the template using Azure CLI to create **az104-disk4**.

**Task 5: Deployed a resource by using Azure Bicep**
Deployed a managed disk using Azure Bicep.

1. Uploaded and edited the azuredeploydisk.bicep file in Cloud Shell.
2. Deployed the Bicep template to create **Disk4** with specific configurations.

### Cleanup of resources
Deleted lab resources using Azure PowerShell to minimize cost and ensure resources are freed up.