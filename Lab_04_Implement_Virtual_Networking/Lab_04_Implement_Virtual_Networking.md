### Lab 04 - Implement Virtual Networking

#### Lab Introduction
This lab was the first of three labs focusing on virtual networking. In this lab, the basics of virtual networking and subnetting were covered. Additionally, the steps to protect the network with network security groups and application security groups, as well as information about DNS zones and records, were explored.

This lab required an Azure subscription. The subscription type could affect the availability of features in this lab. The region could be changed, but the steps were written using East US.

#### Task 1: Create a Virtual Network with Subnets Using the Portal

The organization planned for significant growth in core services. In this task, a virtual network and associated subnets were created to accommodate existing resources and planned growth.

1. **Signed in to the Azure portal:** [https://portal.azure.com](https://portal.azure.com)

2. **Searched for and selected Virtual Networks.**

3. **Selected Create** on the Virtual networks page.

4. **Completed the Basics tab** for the CoreServicesVnet:

   - **Resource Group:** az104-rg4 (created new)
   - **Name:** CoreServicesVnet
   - **Region:** (US) East US

5. **Moved to the IP Addresses tab:**

   - **IPv4 address space:** Replaced the prepopulated IPv4 address space with `10.20.0.0/16`

6. **Selected + Add a subnet.** Completed the name and address information for each subnet. Added each new subnet and deleted the default subnet either before or after creating the other subnets.

   - **SharedServicesSubnet:**
     - **Subnet name:** SharedServicesSubnet
     - **Starting address:** 10.20.10.0
     - **Size:** /24
   - **DatabaseSubnet:**
     - **Subnet name:** DatabaseSubnet
     - **Starting address:** 10.20.20.0
     - **Size:** /24

7. **Selected Review + create** to finish creating the CoreServicesVnet and its associated subnets.

8. **Verified the configuration** passed validation, and then selected Create.

9. **Waited for the virtual network to deploy** and then selected Go to resource.

10. **Verified the Address space and the Subnets.**

11. **In the Automation section,** selected Export template and waited for the template to be generated.

12. **Downloaded the template.**

13. **Navigated to the local machine's Downloads folder** and Extracted all the files in the downloaded zip file.

14. **Ensured having the template.json file.** This template was used to create the ManufacturingVnet in the next task.

#### Task 2: Create a Virtual Network and Subnets Using a Template

In this task, the ManufacturingVnet virtual network and associated subnets were created. The organization anticipated growth for the manufacturing offices, so the subnets were sized for the expected growth.

1. **Located the template.json file** exported in the previous task. It should have been in the Downloads folder.

2. **Edited the file using an editor of choice.** Made the following changes:
   
   - Replaced all occurrences of `CoreServicesVnet` with `ManufacturingVnet`.
   - Replaced all occurrences of `10.20.0.0` with `10.30.0.0`.

3. **Made changes for the ManufacturingVnet subnets:**
   
   - Changed all occurrences of `SharedServicesSubnet` to `SensorSubnet1`.
   - Changed all occurrences of `10.20.10.0/24` to `10.30.20.0/24`.
   - Changed all occurrences of `DatabaseSubnet` to `SensorSubnet2`.
   - Changed all occurrences of `10.20.20.0/24` to `10.30.21.0/24`.

4. **Ensured everything looked correct** and Saved the changes.

5. **Located the parameters.json file** exported in the previous task. Edited the file using an editor of choice.

6. **Replaced the one occurrence** of `CoreServicesVnet` with `ManufacturingVnet`.

7. **Saved the changes.**

8. **Deployed the custom template:**
   
   - In the portal, searched for and selected Deploy a custom template.
   - Selected Build your own template in the editor and then Load file.
   - Selected the templates.json file with the Manufacturing changes, then selected Save.
   - Selected Review + create and then Create.
   - Waited for the template to deploy, then confirmed in the portal that the Manufacturing virtual network and subnets were created.

#### Task 3: Create and Configure Communication Between an Application Security Group and a Network Security Group

In this task, an Application Security Group and a Network Security Group were created. The NSG had an inbound security rule that allowed traffic from the ASG. The NSG also had an outbound rule that denied access to the internet.

1. **Created the Application Security Group (ASG):**
   
   - In the Azure portal, searched for and selected Application security groups.
   - Clicked Create and provided the basic information:
     - **Subscription:** your subscription
     - **Resource group:** az104-rg4
     - **Name:** asg-web
     - **Region:** East US
   - Clicked Review + create and then after validation, clicked Create.

2. **Created the Network Security Group and associated it with the ASG subnet:**
   
   - In the Azure portal, searched for and selected Network security groups.
   - Selected + Create and provided information on the Basics tab:
     - **Subscription:** your subscription
     - **Resource group:** az104-rg4
     - **Name:** myNSGSecure
     - **Region:** East US
   - Clicked Review + create and then after validation, clicked Create.
   - After the NSG was deployed, clicked Go to resource.
   - Under Settings, clicked Subnets and then Associate:
     - **Virtual network:** CoreServicesVnet (az104-rg4)
     - **Subnet:** SharedServicesSubnet
   - Clicked OK to save the association.

3. **Configured an inbound security rule to allow ASG traffic:**
   
   - Continued working with the NSG. In the Settings area, selected Inbound security rules.
   - Reviewed the default inbound rules. Noticed that only other virtual networks and load balancers were allowed access.
   - Selected + Add.
   - On the Add inbound security rule blade, used the following information to add an inbound port rule. This rule allowed ASG traffic. When finished, selected Add:
     - **Source:** Application security group
     - **Source application security groups:** asg-web
     - **Source port ranges:** *
     - **Destination:** Any
     - **Service:** Custom
     - **Destination port ranges:** 80,443
     - **Protocol:** TCP
     - **Action:** Allow
     - **Priority:** 100
     - **Name:** AllowASG

4. **Configured an outbound NSG rule that denied Internet access:**
   
   - After creating the inbound NSG rule, selected Outbound security rules.
   - Noticed the AllowInternetOutboundRule rule. Also noticed the rule could not be deleted and the priority was 65001.
   - Selected + Add and then configured an outbound rule that denied access to the internet. When finished, selected Add:
     - **Source:** Any
     - **Source port ranges:** *
     - **Destination:** Service tag
     - **Destination service tag:** Internet
     - **Service:** Custom
     - **Destination port ranges:** 8080
     - **Protocol:** Any
     - **Action:** Deny
     - **Priority:** 4096
     - **Name:** DenyAnyCustom8080Outbound

### Task 4: Configure Public and Private Azure DNS Zones

#### Configure a Private DNS Zone

A private DNS zone provides name resolution services within virtual networks. A private DNS zone is only accessible from the virtual networks that it is linked to and can’t be accessed from the internet.

1. **In the portal, searched for and selected Private dns zones.**

2. **Selected + Create.**

3. **On the Basics tab of Create private DNS zone, entered the information as listed:**
   
   - **Subscription:** Selected your subscription
   - **Resource group:** az-104-rg4
   - **Name:** private.contoso56.com (adjusted as necessary)
   - **Region:** East US

4. **Selected Review + create and then Create.**

5. **Waited for the DNS zone to deploy** and then selected Go to resource.

6. **Noticed on the Overview blade** that there were no name server records.

7. **Selected + Virtual network links and then selected + Add.**

   - **Link name:** manufacturing-link
   - **Virtual network:** ManufacturingVnet

8. **Selected OK and waited for the link to create.**

9. **From the Overview blade, selected + Record set.** Added a record for the virtual machine that needed private name-resolution support:

   - **Name:** sensorvm
   - **Type:** A
   - **TTL:** 1
   - **IP address:** 10.1.1.4