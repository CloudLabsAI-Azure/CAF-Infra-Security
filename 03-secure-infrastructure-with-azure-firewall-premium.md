# Exercise 3: Secure Infrastructure with Azure Firewall Premium

### Estimated Duration: 120 minutes

## Overview: 

Azure Firewall is a cloud-native and intelligent network firewall security service that provides the best-of-breed threat protection for your cloud workloads running in Azure. It's a fully stateful, firewall-as-a-service with built-in high availability and unrestricted cloud scalability. It provides both east-west and north-south traffic inspection.

Azure Firewall Premium is a next-generation firewall with capabilities that are required for highly sensitive and regulated environments. It includes the following features:

- **TLS Inspection** - decrypts outbound traffic, processes the data, then encrypts the data and sends it to the destination.
- **IDPS** - A network intrusion detection and prevention system (IDPS) allows you to monitor network activities for malicious activity, log information about this activity, report it, and optionally attempt to block it.
- **URL filtering** - extends Azure Firewall’s FQDN filtering capability to consider an entire URL. For example, `www.contoso.com/a/c` instead of `www.contoso.com`.
- **Web categories** - Administrators can allow or deny user access to website categories such as gambling websites, social media websites, and others.
For more information, see `https://learn.microsoft.com/en-us/azure/firewall/premium-features`
 
## Lab Objectives

You will be able to complete the following tasks:

- Task 1: Add firewall diagnostics settings
- Task 2: Test IDPS for HTTP traffic
- Task 3: Web categories testing
- Task 4: Implement and Test URL filtering
- Task 5: IP Groups
- Task 6: Azure Firewall Policies with Firewall Manager

## Task 1: Add firewall diagnostics settings 

In this task, you will enable diagnostic settings in Azure Firewall to collect firewall logs.

1. Navigate to the home page in the Azure portal, search for **Subscriptions (1)** and **select (2)** from suggestions.

   ![](images/scafinfra19.jpg "search gateway")

1. Select the **default subscription** available in the list.

   ![](images/scafinfra20-1.png "search gateway")

1. From the left-side blade, select **Preview features (1)** and select **Microsoft.Network (2)** in the Provider list and click on **Apply (3)**.

   ![](images/scafinfra21-1.png "search gateway")

1. Select **Enable Azure Firewall Structured Logs (1)** and click on **Register (2)**.

   ![](images/scafinfra22-1.png "search gateway")

1. In the Azure portal, navigate to your **JumpVM-rg** resource group and select the **AzureFirewall** resource.

   ![](images/firewall1.png "search gateway")

1. On the firewall page, under **Monitoring**, select **Diagnostic settings**.

   ![](images/firewall2.png "search gateway")

1. Select **+ Add diagnostic setting** on the **Diagnostic settings** page. 

   ![](images/firewall4.png "search gateway")

1. Enter the **Diagnostic setting name** as **fw-diagnostics**

   ![](images/firewall3.png "search gateway")

1. Under **Logs**, select the below mentioned categories.
   
   - Azure Firewall Application Rule
   - Azure Firewall Network Rule
   - Azure Firewall Nat Rule
   - Azure Firewall Threat Intelligence
   - Azure Firewall IDPS Signature
   - Azure Firewall DNS query
   - Azure Firewall FQDN Resolution Failure
   - Azure Firewall Fat Flow Log
   - Azure Firewall Flow Trace Log

     ![](images/scafinfra23.jpg "search gateway")

1. Under **Destination details**, select **Send to Log Analytics workspace (1)**, select **Resource specific (2)** for Destination table option, and then click on **Save (3)**.

   ![](images/scafinfra24.jpg "search gateway")

## Task 2: Test IDPS for HTTP traffic

Azure Firewall Premium provides signature-based IDPS to allow rapid detection of attacks by looking for specific patterns, such as byte sequences in network traffic, or known malicious instruction sequences used by malware.

In this task, you will test IDPS for HTTP traffic.

1.  In the Azure **Home** page, from the search bar search for **Application gateways (1)** and then select **Application gateways (2)**.
 
     ![](images/searchgateway.png "search gateway")
 
1. Select your **Application Gateway**.
 
     ![](images/appgateway.png "select gateway")
 
1. Select the **Frontend public IP address** of the application gateway.
 
    ![](images/image301.png "select gateway")

1. Copy the **Public IP address** and save it to Notepad for later use.

    ![](images/editing12.png )
    
1. On the Azure Portal **Home** page, search **Firewalls (1)** and then select **Firewalls (2)**.

   ![firewall](images/Azurefirewallnew-1.png)
    
1. Click on the **AzureFirewall**.

    ![firewall](images1/azurefirewall.png)
   
1. Select **Firewall Public IP** from the Overview tab.

    ![pip](images1/firewallIP.png)
    
1. Copy the **Public IP address** and save it to Notepad for later use.

    ![ip](images1/firewallip1.png)  
     
1. Navigate back to Azure Firewall, select **Firewall Manager (1)** from the **Settings** tab, and click on **Visit Azure Firewall Manager to configure and manage this firewall (2)**

   ![FM](images/firewallmanager-1.png)
    
1. Select **Azure Firewall Policies (1)** under the **Firewall Manager** page and click on Firewall Policy **firewallpolicy (2)**.

   ![policy](images/selectfirewallpolicy-1.png)
   
1. Select **DNAT rules (1)** from the **Rules** tab under the **Firewall Policy** page and select **+ Add a rule collection (2)**

   ![rule](images/dnat1-1.png)
    
1. Under the **Add a rule collection** page, enter the details below:

    - Name: **afw-contoso-prod-firewall-rulecolection (1)**
    - Rule Collection type: **DNAT (2)**
    - Priority: **100 (3)**
    - Rule collection group: **DefaultDnatRuleCollectionGroup (4)**
    - Under **Rules (5)** mention the below details:
      - Name: **afw-dnat-http**
      - Source type: Select **IP Address** from the drop-down list
      - Source: Enter *
      - Protocol: Select **TCP** from the drop-down list
      - Destination Ports: **80**
      - Destination (Firewall PIP address): Enter the IP address of the **Firewall** which you copied in step 8.
      - Translated type: Select **IP Address** from the drop-down list
      - Translated address or FQDN: Enter the Public IP address of the **Application gateway** which you copied in step 4.
      - Translated port: **80**
     
     - Click on **Add (6)**.

       ![rule](images1/rulecollection.png)

     >**Note:** This might take few minutes for updating the rule collection group. Wait for the updates to get updated before proceeding to next steps.

1. On the JumpVM virtual machine, search for **Command Prompt (1)** and open the **Command Prompt (2)** window.

   ![](images/firewall9.png "search gateway")

1. Type the following command at the command prompt:

   - Replace <your web server address> with Firewall IP.

     `curl -A "HaxerMen" <Firewall Public IP>`
 
        ![](images/firewall7.png "search gateway")
 
 1. In the custom prompt, you will see your Web server response.
 
    ![](images/firewall8.png "search gateway")
 
 1. Navigate to your **JumpVM-rg** resource group and select **AzureFirewall**.
 
     ![](images1/firewall.png)
 
 1. On the **AzureFirewall** page, select **Logs (1)** under Monitoring, click on **X (2)**

    ![](images/logsexit.png)

 1. Select **Logs (1)**, click on **Firewall Logs (Resource Specific Tables - Preview) (2)** and click on **Run (3)** for **IDPS event logs**.
 
    ![](images/scafinfra25.jpg "search gateway")
 
 1. You'll be able to see resource-specific logs for IDPS events.
 
    ![](images/scafinfra26.jpg "search gateway")
 
    >**Note: In case you didn't find the Logs as expected, then it may take up to 6 hours to show up. Please refer to the screenshot for reference and continue with the next steps**.
 
1. Now navigate back to the firewall policy and under **Settings** select **IDPS**.
 
   ![](images/firewall10-1.png "search gateway")
 
1. On the **IDPS** page select the **Signature rules (1)** tab and under **Signature ID**, in the open text box type **2032081 (2)**.
 
   ![](images/firewall11.png "search gateway")
 
1. Select **2032081 (1)** signature id and click on **Edit Rules (2)**.
 
   ![](images/firewall12.png "search gateway")
 
1. Under edit rules, change **Signature Mode** to **Alert and Deny (1)** and click on **Apply (2)**. Wait for the deployment to complete before proceeding.
 
   ![](images/firewall13.png "search gateway")

1. Click on **Apply** to update the firewall policy.

    >**Note:** Wait for a few minutes for the policy to get updated.

1. Navigate back to JumpVM and run the `curl` command again:

    `curl -A "HaxerMen" <Firewall Public IP>`

    Since the HTTP request is now blocked by the firewall, you'll see the following output after the connection timeout expires:

    `curl: (56) Recv failure: Connection was reset`
 
     ![](images/firewall14.png "search gateway")

> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
> - If you receive a success message, you can proceed to the next task.
> - If not, carefully read the error message and retry the step, following the instructions in the lab guide. 
> - If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help you out.

<validation step="e5f9dd50-2ebf-44f8-bcc0-09543bd58111" />

## Task 3: Web categories testing
 
In this task, you will create an application rule to allow access to sports websites.
 
1. In the Azure portal, navigate to your **JumpVM-rg** resource group and select the Route Table **firewallroute**. 
    
    ![](images1/firewallroute.png)
 
1. On the Route table page, select **Routes (1)** under **Settings** and click on **+ Add (2)**.
 
    ![](images1/addroute.png)
 
1. Under the **Add Route** page, enter the following information:
  
    - Route Name: Enter **firewallroute (1)**
    
    - Address prefix destination: Select **IP Addresses (2)** from the drop-down list
    
    - Destination IP address/ CIDR ranges: Enter **0.0.0.0/0 (3)**
    
    - Next hop type: Select **Virtual appliance (4)** from the drop-down list
    
    - Next hop address: Enter the **Private IP Address** of the Firewall **(5)**.
    
    - Select **Add (6)**
 
      ![](images1/addrouterule.png)
 
 1. Now select **Subnets (1)** under Settings and Click on **+ Associate (2)**.

    - Under Associate subnets, enter the following details:

    - Virtual Network: Select **vnet (JumpVM-rg) (3)** from the drop-down list.

    - Subnet: Select **jumpvmsubnet (4)** from the drop-down list.

    - Click on **OK (5)**.
 
      ![](images/addsubnet-1.png)
 
1. Navigate to your **JumpVM-rg** resource group and select **JumpVM-<inject key="Deployment ID" enableCopy="false"/>**. 
 
    ![](images1/selectvm.png)

1. On the Virtual Machine page, under **Connect**, click on **Connect (1)** then click on **Go to Bastion (2)**.
 
     ![](images/connect-1.png)
 
1. On the Bastion page, follow the instructions below to connect to the Virtual Machine using Bastion:
 
    - **Authentication Type**: Select **VM Password (1)** from the drop-down
    - **Username**: Enter **demouser (2)**
    - **VM Password**: Enter **<inject key="JumpVM Admin Password" enableCopy="true"/> (3)**
    - Click on **Connect (4)**
 
      ![](images/bastionconnect-1.png)
 
1. Now, you will be redirected to a new tab where the Bastion VM is opened. If you see the pop-up **See text and images copied to the clipboard**, click on **Allow**.
 
    ![](images1/allowpopup.png)
 
1. Within the Bastion VM, search for **Edge (1)** and select **Microsoft Edge (2)**.
 
    ![](images1/selectedge.png)
 
1. Navigate to the below-mentioned URL, and you can see the error **can't reach this page**.
 
    ```
    https://www.nfl.com
    ```
    
    ![](images1/error.png)

    > **Note:** If the copy-paste functionality isn't working directly, click the arrow icon to copy the content to your clipboard, then paste it where needed.
 
    ![](images/build5.png)
 
    ![](images/build6.png)
 
1. Navigate back to the other tab, where the Azure Portal is open.
 
1. In the Azure portal, go to your **JumpVM-rg** resource group and select **firewallpolicy**.
 
     ![](images/firewall18.png "search gateway")
 
1. Select **TLS inspection (1)** under the **Settings** tab and enter the below details under the **Key vault** tab:
 
    - Parent policy: Choose **Enabled (2)**
    
    - Managed Identity: Select **(New) fw-cert-id-xxxxxxxxxx  (3)** from the drop-down list
    
    - Key Vault: Select **(New) fw-cert-kv-xxxxxxxxxx (4)** from the drop-down
    
    - Certificate: Select **(New) fw-cert-xxxxxxxxxx (5)** from the drop-down
    
    - Click on **Save (6)**
 
      ![](images1/tlsinspection.png)

      >**Note:** This might take 5-6 minutes to update the firewall policy. Wait for the firewall policy to get updated before proceeding to the next steps.

1. Now, select **Application Rules (1)** from the **Settings** tab under the Firewall Policy page and select **+ Add a rule collection (2)**.
   
     ![](images/firewall17.png "search gateway")
 
1. Under the **Add a rule collection** page, enter the details below to enable the web application in Bastion VM:
 
    - Name: **GeneralWeb (1)**
    - Rule Collection type: **Application (2)**
    - Priority: **103 (3)**
    - Rule Collection Action: **Allow**
    - Rule collection group: **DefaultApplicationRuleCollectionGroup (4)**
    - Under **Rules (5)** mention the below details:
      - Name: **AllowSports**
      - Source type: Select **IP Address** from the drop-down list
      - Source: Enter *
      - Protocol: Enter **http,https**
      - TLS inspection: Check TLS inspection
      - Destination Type: Select **Web categories**
      - Destination: Enter `Sports`
     
    - Click on **Add (6)**
 
         ![](images/CAF3.png "search gateway")

     >**Note:** This might take 5-6 minutes to update the firewall policy. Wait for the firewall policy to get updated before proceeding to the next steps. 
 
1.  Once the deployment completes, navigate back to the Bastion VM tab and refresh the page where you have browsed for `https://www.nfl.com`. On the Privacy error connection page, click on **Advanced**.
 
     ![](images1/Advanced.png)
 
1. Click on **Continue to www.nfl.com (unsafe)**.
 
    ![](images1/unsafe.png)

    >**Note**: If you have trouble reaching www.nfl.com, try www.nba.com or www.nhl.com.
     
1. Now you can see the NFL web page.
 
    ![](images/firewall22.png "search gateway")
 
1. Again, navigate to the other tab, where the Azure Portal is opened.
 
1. In the Azure portal, go to your **JumpVM-rg** resource group and select **AzureFirewall**.
 
     ![](images1/firewall.png)
 
1. On the **AzureFirewall** page, select **Logs (1)** under the Monitoring tab, click on **Firewall Logs (Resource Specific Tables - Preview) (2)** and click on **Run (3)** for **Application rule logs**.
 
     ![](images/a124.png)
 
     >**Note: In case you didn't find the Logs as expected, then it may take up to 6 hours to show up. Please refer to the screenshot for reference and continue with the next steps**.

     ![](images/a162.png)

## Task 4: Implement and Test URL filtering
 
1. Navigate back to the tab where you have opened Bastion VM and browse the below-mentioned URL. You can see the error **can't reach this page**.
 
    ```
    www.nytimes.com/section/world
    ```
 
     ![](images1/error1.png)
  
1. Now switch back to the other tab, where **Azure Portal** is opened, in your  **JumpVM-rg** resource group, select **firewallpolicy**.
 
    ![](images/firewall18.png "search gateway")
 
1. Select **Application Rules (1)** from the **Settings** tab under Firewall Policy page and select **+ Add a rule collection (2)**.
 
    ![](images/firewall17.png "search gateway")
 
1. Under the **Add a rule collection** page, enter the details below to enable the web application in the Bastion VM:

    - Name: **Firewall-rulecollection (1)**
    - Rule Collection type: **Application (2)**
    - Priority: **100 (3)**
    - Rule Collection Action: **Allow**
    - Rule collection group: **DefaultApplicationRuleCollectionGroup (4)**
    - Under **Rules (5)** mention the below details:
      - Name: **URLFiltering**
      - Source type: Select **IP Address** from the drop-down list
      - Source: Enter *
      - Protocol: Enter **http,https**
      - TLS inspection: Check TLS inspection
      - Destination Type: Select **URL**
      - Destination: Enter `www.nytimes.com/section/world`
     
     - Click on **Add (6)**
 
         ![](images/CAF2.png "search gateway")

    >**Note:** This might take 5-6 minutes to update the firewall policy. Wait for the firewall policy to get updated before proceeding to the next steps.     

1. Once the deployment completes, navigate back to the Bastion VM tab and refresh the page where you have browsed for `www.nytimes.com/section/world`. On the Privacy error connection page, click on **Advanced**.
 
      ![](images1/Advanced1.png)
 
1. Click on **Continue to www.nytimes.com (unsafe)**.
 
    ![](images1/unsafe1.png)
 
1. Now, you validate that the HTML response is displayed as expected in the browser.
 
    ![](images/CAF1.png "search gateway")
 
1. Again, navigate to the other tab, where the Azure Portal is opened.
 
1. In the Azure portal, go to your **JumpVM-rg** resource group and select **AzureFirewall**.
 
    ![](images1/firewall.png)
 
1. On the **AzureFirewall** page, select **Logs (1)** under the Monitoring tab, click on **Firewall Logs (Resource Specific Tables - Preview) (2)**, and click on **Run (3)** for **Application rule log**.
 
    ![](images/a124.png)

    >**Note: In case you didn't find the Logs as expected, then it may take up to 6 hours to show up. Please refer to the screenshot for reference and continue with the next steps**.

    ![](images/a162.png)

## Task 5: IP Groups

1. Navigate to the home page in the Azure portal, search for **IP groups (1)** and **select (2)** from suggestions.
 
    ![](images/a81.png)
 
1. Click on **+ Create** to create a IP Group.
  
    ![](images/a82.png) 
 
1. On the IP Group page, on the **Basics** tab, enter or select the following information and click on **Next: IP addresses > (4)**.
 
    | **Setting**      | **Value**                                                    |
    | ---------------- | ------------------------------------------------------------ |
    | Subscription     | Select your subscription.                                    |
    | Resource group   | Select the resource group **JumpVM-rg (1)**                  |
    | Name             | Enter **IpGroup (2)**                                        |
    | Region           | Select **East US (3)**                                       |
 
     ![](images/a83.png)

1. On the **IP addresses** tab, enter `*` in the **IP address, range or subnet (1)** field and then click **Review + create (2)**.
 
    ![](images/a122.png)
 
1. Review the Summary, and then select **Create**.
 
    ![](images/a123.png)

1. Navigate back to the tab where you have opened Bastion VM and browse the below-mentioned URL. You can see the error **can't reach this page**.
 
    ```
    www.news18.com
    ```
 
    ![](images/a145.jpg)
  
1. Now switch back to the other tab, where Azure Portal is opened and to your **JumpVM-rg** resource group, then select **firewallpolicy**.
 
    ![](images/firewall18.png "search gateway")
 
1. Select **Application Rules (1)** from the **Settings** tab under Firewall Policy page and select **+ Add a rule collection (2)**.
 
    ![](images/firewall17.png "search gateway")

1. Under the **Add a rule collection** page, enter the details below to enable the web application in the Bastion VM:

    - Name: **Ipgroup-rule (1)**
    - Rule Collection type: **Application (2)**
    - Priority: **104 (3)**
	 - Rule collection action: **Allow (4)**
    - Rule collection group: **DefaultApplicationRuleCollectionGroup (5)**
    - Under **Rules (6)** mention the below details:
      - Name: **URL-Ipgroup**
      - Source type: Select **IP Group** from the drop-down list
      - Source: Enter **Ipgroup**
      - Protocol: Enter **http,https**
      - TLS inspection: Check TLS inspection
      - Destination Type: Select **URL**
      - Destination: Enter `www.news18.com`
     
     - Click on **Add (7)**
 
         ![](images/a141.jpg "search gateway")

     >**Note:** This might take 5-6 minutes to update the firewall policy. Wait for the firewall policy to get updated before proceeding to next steps.

1. Once the deployment completes navigate back to the Bastion VM tab and refresh the page where you have browsed for `www.news18.com`. On the Privacy error connection page, click on **Advanced**.
 
      ![](images/a142.jpg)
 
1. Click on **Continue to www.news18.com (unsafe)**.
 
    ![](images/a143.jpg)

1. Now, you validate that the HTML response is displayed as expected in the browser.
 
    ![](images/a144.jpg "search gateway") 
 
## Task 6: Azure Firewall Policies with Firewall Manager (Optional)

### Task 6.1: Create a Firewall Policy

1. Navigate to the home page in the Azure portal, search for **firewall manager (1)** and **select (2)** from suggestions.
 
     ![](images/a89.png)
 
1. On the Firewall Manager page, from the **Overview (1)** tab, select **View Azure Firewall Policies (2)**.
 
     ![](images/a90.png)
 
1. Select **+ Create Azure Firewall Policy**. 
  
1. On the Azure Firewall Policy page, on the **Basics** tab, enter or select the following information and click on **Next: DNS Settings > (5)**.
 
    | **Setting**      | **Value**                                                    |
    | ---------------- | ------------------------------------------------------------ |
    | Subscription     | Select your subscription.                                    |
    | Resource group   | Select the resource group **JumpVM-rg (1)**                  |
    | Name             | Enter **Policy-01 (2)**                                      |
    | Region           | Select **East US (3)**                                       |
    | Policy tier      | Select **Standard (4)**                                      |
 
     ![](images/a91.png)
 
1. On the **DNS Settings** tab, leave it as default and click on **Next: TLS inspection >**.
 
    ![](images/a92.png)
 
1. On the **TLS inspection** tab, leave it as default and click on **Next: Rules >**.
 
    ![](images/a93.png)

1. On the **Rules** tab, select **+ Add a rule collection**.

    ![](images/a94.png)
 
1. On the **Add a rule collection** page, enter or select the following information
 
    - Name: **App-RC-01 (1)**
    - Rule Collection type: **Network (2)**
    - Priority: **100 (3)**
    - Rule collection action: **Allow (4)**
    - Under **Rules (5)** mention the below details:
      - Name: Enter **AllowWeb**
      - Source type: Select **IP Address** from the drop-down list
      - Source: Enter **192.168.1.0/24**
      - Protocol: Select **TCP**
      - Destination Ports: **80**
      - Destination Type: Select **IP Address**
      - Destination: Enter **10.6.0.0/16**
    - On the next rule row, enter the following information:
      - Name: Enter **AllowRDP**
      - Source type: Select **IP Address** from the drop-down list
      - Source: Enter **192.168.1.0/24**
      - Protocol: Select **TCP**
      - Destination Ports: **3389**
      - Destination Type: Select **IP Address**
      - Destination: Enter **10.6.0.0/16**
    - Click on **Add (6)**
 
      ![](images/a95.png)
 
1. Select **Review + Create**.
 
    ![](images/a96.png)
 
1. Review the Summary page and then select **Create**.
 
    ![](images/a97.png)
 
### Task 6.2: Create the firewall hub virtual network
 
1. Navigate to the home page in the Azure portal, search for **firewall manager (1)** and **select (2)** from suggestions.
 
     ![](images/a89.png)
 
1. On the Firewall Manager, from the **Overview (1)** tab, select **View secured virtual hubs (2)**.
 
     ![](images/a98.png)

1. On the **Virtual hubs** page, select Create **+ Create new secured virtual hub**.
 
     ![](images/create-virtual-hub.png)

1. On the secured virtual hub page, on the **Basics** tab, enter or select the following information and click on **Next: Azure Firewall > (8)**.
   
     | **Setting**                                   | **Value**                                                    |
     | ----------------------------------------------| ------------------------------------------------------------ |
     | Subscription                                  | Select your subscription.                                    |
     | Resource group                                | Select the resource group **JumpVM-rg (1)**                  |
     | Region                                        | Select **East US (2)**                                       |
     | Secured virtual hub name                      | Enter **Hub-01 (3)**                                         |
     | Hub address space                             | Enter **10.2.0.0/16 (4)**                                    |
     | Choose an existing vWAN or create a new one   | Choose **New vWAN (5)**                                      |
     | Virtual WAN Name                              | Enter **Vwan-01 (6)**                                        |
     | Type                                          | Select **Standard (7)**                                      |

      ![](images/a99.png)

1. On the **Azure Firewall** tab, enter or select the following information and click on **Next: Security Partner Provider > (5)**

     | **Setting**                                   | **Value**                                                    |
     | ----------------------------------------------| ------------------------------------------------------------ |
     | Azure Firewall tier                           | **Standard (1)**                                             |
     | Availability zone                             | **None (2)**                                                 |
     | Specify number of Public IP addresses         | **1 (3)**                                                    |
     | Subscription                                  | Select your default subscription **(4)**                     |

     ![](images/firewallshub1-1.png)
 
1. On the **Security Partner Provider** tab, leave it to default and click on **Next: Review + create**.
 
    ![](images/a101.png)

1. Review the **Summary** page and select **Create**.  
  
    ![](images/a102.png)

    >**Note**: Deployment may take up to 30 minutes to complete.
 
### Task 6.3: Associate the firewall policy with the virtual hub
  
1. From the Azure portal home page, select **Firewall Manager**. On the Firewall Manager page, under **Security**, select **Azure Firewall Policies**.
  
    ![](images/a103.png)
 
1. Select the checkbox for **Policy-01 (1)**, select **Manage associations (2)** and then select **Associate hubs (3)**.
 
    ![](images/a104.png)
 
1. On the **Secure hubs with Azure Firewall Policy** page, Select the checkbox for **Hub-01 (1)** and Select **Add (2)**.
  
    ![](images/a105.png)
 
1. When the policy has been attached, select **Refresh**. The association should be displayed.
   
    ![](images/a106.png)
 
1. To open the firewall policy, click **Policy-01**, then under Settings, select **Secured virtual hubs (1)**. You will see that your policy status is **Secured (2)**.
 
    ![](images/a108.png)	

> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
> - If you receive a success message, you can proceed to the next task.
> - If not, carefully read the error message and retry the step, following the instructions in the lab guide. 
> - If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help you out.

<validation step="659469d6-4b83-467d-a4ce-83adf7dc61ba" />

## Summary
 
In this lab, you have covered the following:
  
- Added firewall diagnostics settings 
- Tested IDPS for HTTP traffic
- Performed Web category testing 
- Implemented and tested URL filtering
- Performed IP groups
- Performed Azure Firewall Policies with the Firewall Manager

### You have successfully completed the lab. Click on **Next >>** to proceed with next exercise.
