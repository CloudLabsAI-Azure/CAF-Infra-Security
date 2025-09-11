# Exercise 1: Secure administration and management

## Estimated Duration: 120 Minutes

## Overview

**Azure Monitor Network Insights** provides a comprehensive and visual representation of the health and metrics of all deployed network resources through topologies, without requiring any configuration. It also offers access to network monitoring capabilities such as Connection Monitor, flow logging for network security groups (NSGs), and traffic analytics.

The topology capability of **Azure Network Watcher** allows you to view all the resources in a virtual network, the resources associated with those in a virtual network, and the relationships between these resources.

**Azure Bastion** is a fully managed service provided by Microsoft Azure that enables secure and seamless Remote Desktop Protocol (RDP) and Secure Shell (SSH) access to virtual machines (VMs) within a virtual network (VNet) without the need for a public IP address or a virtual private network (VPN) connection.

## Lab Objectives

You will be able to complete the following tasks:

- Task 1: Network Health
- Task 2: Network Topology
- Task 3: Secure Access via Bastion Host
- Task 4: Prepare the Network Watcher monitoring environment and Virtual network Flow
  
## Task 1: Network Health

In this task, you'll explore Azure Monitor and examine the resource health of various deployed resources. 

1. Navigate to the Azure portal. Using the search bar, search for **Monitor (1)** and **select (2)** from the suggestions.

   ![](images/a3.png)

1. From the sidebar, select **Networks** from Insights.

   ![](images/E1T1S2.png "search gateway")
   
1. On the **Network health** tab, you can customize the resource health and alerts view using filters such as **Subscription**, **Resource Group**, and **Type**. You can also use the search box to find resources and their associated resources. For example, a public IP may be associated with an application gateway. A search for the public IP's DNS name will return both the public IP and the associated application gateway.

   ![](images/a5-1.png "search gateway")

1. In this, each tile represents a resource's health. The tile displays the number of instances of that resource health deployed across all selected subscriptions. 

   ![](images/a12-1.png "search gateway")

1. You can click on any resource to select the resource view. The resource view helps you visualize how a resource is configured. The resource view is currently available for **Azure Application Gateway**, **Azure Firewall**, and **Bastions**. For example, for Application Gateway, you can access the resource view by selecting the Application Gateway resource name in the metrics grid view. You can do the same thing for Azure Firewall and Bastions.

   ![](images/a146-1.png "search gateway")

1. Click on the **Throughput** icon next to the location to bring up the Metrics.
   
    ![](images/a147.png "search gateway")
     
1. You will see the **Metrics** as given below:

    ![](images/a13.png "search gateway")

## Task 2: Network Topology

 In this task, you'll view resources in a Microsoft Azure virtual network and the relationships between the resources.

1. Navigate to the Azure portal. Using the search bar, search for **Network Watcher (1)** and **select (2)** from the suggestions.

   ![](images/cafinfa1.jpg)

1. From the sidebar, select **Topology** from Monitoring.

   ![](images/infra-app-security-lab1-1.png "search gateway")

1. On the **Topology** page, click on the **Scope** **(1)**.

   ![](./images/infra-app-security-lab1-2.png)

1. Under the **Select Scope** choose the **All subscriptions selected** **(1)** for Subscriptions, **All resource groups selected** **(2)** for Resource Groups, and **<inject key="Region" />** **(3)** for the Locations and then click on **Save**.

   ![](./images/selectscope.png)

1. Hover the mouse on the location pointer inside **Geo Map** and then click **Expand** to see the topology.

   ![](./images/hover.png)

1. Now, you'll be able to **Visualize (1)** the topology. You can explore the different connections to understand how different resources, such as virtual machines, subnets, virtual network gateways, and other network components are interconnected and how they communicate with each other. You can also download the topology by clicking on **Download topology (2)**.

   ![](images/updateimg-3.png "search gateway")

## Task 3: Secure Access via Bastion Host

In this task, you'll learn how to access an Azure virtual machine using the Azure Bastion service.

1. Navigate to the Azure portal. Using the search bar, search for **Virtual networks (1)** and **select (2)** from the suggestions.

   ![](images/a14.png "search gateway")

1. Select the **vnet** from the list.

   ![](images/E1T3S2.png "search gateway")

1. From the sidebar, select **Subnets** from Settings.
   
   ![](images/E1T3S3.png "search gateway")

1. You will see that **AzureBastionSubnet** is already present in the subnets. If you want to see the subnet configuration, then you can click on the **AzureBastionSubnet** subnet and explore this.

   ![](images/upd-021.png "search gateway")

1. Now, using the search bar, search for **Virtual machines (1)** and **select (2)** from the suggestions.

   ![](images/a18.png "search gateway")

1. Select the **FirewallVM** from the list.

   ![](images/E1T3S6.png "search gateway")

1. On the Virtual Machine page, click on **Connect (1)** under **Connect** section and then click on **Go to Bastion (2)**.
 
   ![](images/infra-app-security-lab1-3.png)
 
1. On the Bastion page, follow the instructions below to connect to the Virtual Machine using Bastion:

    - **Authentication Type:** Select **VM Password (1)** from the drop-down
    
    - **Username:** Enter **<inject key="JumpVM Admin Username" />**  **(2)**
    
    - **VM Password:** Enter **<inject key="JumpVM Admin Password" />**  **(3)**
    
    - Click on **Connect (4)**
 
      ![](images/update-6.png)

      >**Note:** If the Connection is blocked by the browser, click on the **Pop-up (1)** button, select **Always allow pop-ups and redirects from https://portal.azure.com (2)** and then click on **Done (3)**.

       ![](images/updateimg-7.png)
 
1. Now, you will be redirected to a new tab where the Bastion VM is opened. If you see the pop-up **See text and images copied to the clipboard**, click on **Allow**.
 
    ![](images1/allowpopup.png)

## Task 4: Prepare the Network Watcher monitoring environment and Virtual network Flow

**Virtual network Diagnostic Logs** are platform logs in Azure that capture information about operations and events within an Azure Virtual Network (VNet) and its related resources (such as subnets, network security groups, and route tables).

**Virtual network flow logs** support connecting at the virtual network, subnet, and network interface level. They provide visibility into the network communications and can be used for analyzing network behaviour, detecting threats, and investigating security incidents.

In this task, you will create Virtual network flow logs and these configurations are used in Exercise 5, which reuses the Virtual network Flow Logs, Traffic Analytics setup, Azure Firewall, and other network resources from Exercise 1 to analyze collected traffic data. Otherwise, it may take 30–40 minutes for data to appear in Traffic Analytics.

1. Navigate to the Azure portal. Using the search bar, search for **Resource groups (1)** and **select (2)** from the suggestions.

    ![](images/cafinfra5.jpg)

1. Select the **FirewallVM-rg** from the list.

    ![](images/E1T4S2.png)

1. From the list of resources, select the Network Security Group named **FirewallVM-nsg**.

    ![](images/E1T4S3.png)

1. Under **Monitoring** section, select **NSG flow logs (1)** and Click on **+ Create (2)** button.

    ![](images/E1T4S4.png)

1. In the Create a flow log page, select the **default subscription (1)**, **Virtual network (2)** as Flow log type, select dropdown button beside **+ Select target resource (3)** then choose **Virtual network (4)** as a Select target resource.

    ![](images/infra-app-security-lab1-44.png)

1. In the **Select Virtual network** page, select **vnet** **(1)** and click on **Confirm selection (2)**.

    ![](images/infra-app-security-lab1-45.png)

1. For the Instance details, provide the following details and click on **Next: Analytics > (4)**

   - **Subscription:** Select **default subscription (1)** from the drop-down.

   - **Storage Account:** Select **nsglogs<inject key="DeploymentID" enableCopy="false" />** from the drop down.

   - **Retention (days):** **30 (3)**

       ![](images/infra-app-security-lab1-46.png)  
   
1. Under the **Analytics** tab, check the box to **Enable traffic analytics (1)**, select **Every 10 mins (2)** under the **Traffic analytics processing interval** and click **Review + create (3)**.

    ![create](images/infra-app-security-lab1-47.png)

1. On the Review + create tab, review the summary and click on **Create** button.

   >**Note:** The deployment might take a few minutes to complete. Wait till the deployment is completed before proceeding to the next step.

   ![](images/infra-app-security-lab1-48.png)  

1. Navigate to the Azure portal. Using the search bar, search for **Resource groups (1)** and **select (2)** from the suggestions.

    ![](images/cafinfra5.jpg)

1. Select the **FirewallVM-rg** from the list.

    ![](images/E1T4S2.png)

1. From the list of resources, select the Network security group named **FirewallVM-nsg**.

    ![](images/E1T4S3.png)

1. From the sidebar, select **Diagnostic settings (1)** under monitoring and click on **+ Add diagnostic setting (2)**.

    ![](images/updateimg-11.png)

1. In the Diagnostic settings page, provide the following details.

   - Diagnostic setting name: **NSG_Flow_Logs (1)**

   - **Logs -> Category groups:** check the **allLogs (2)** checkbox.

   - **Destination details:** Select **Send to Log Analytics workspace (3)**. The existing log analytics workspace should be selected. Also select the **Archive to a storage account (4)** checkbox, and click on **Save (5)**. Make sure the default subscription is selected for subscription and **nsglogs<inject key="DeploymentID" enableCopy="false" />** for the storage account.

      ![](images/E1T4S15.png)

   > **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
   > - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
   > - If not, carefully read the error message and retry the step, following the instructions in the lab guide. 
   > - If you need any assistance, please contact us at labs-support@spektrasystems.com. We are available 24/7 to help you out.
 
   <validation step="f287d359-99b1-4b6c-8519-647983bf4a68" />


## Summary
 
In this exercise, you have covered the following:
  
- Explored Network health 
- Explored on Network topology
- Secured Access via Bastion Host
- Configured the Network Watcher monitoring environment and NSG Flow

## Click on **Next >>** to proceed with next exercise.