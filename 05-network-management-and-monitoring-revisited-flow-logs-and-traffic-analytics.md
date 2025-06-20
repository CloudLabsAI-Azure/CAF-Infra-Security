# Exercise 5: Network Management and Monitoring Revisited: Flow Logs and Traffic Analytics

### Estimated Duration: 60 Minutes

## Overview:

Network management and monitoring play a crucial role in maintaining a secure and efficient network infrastructure. In addition to traditional monitoring methods, **Flow logs** and **Traffic analytics** provide valuable insights into network traffic patterns and behaviour.

**Flow logs** capture detailed information about network flows, including source and destination IP addresses, ports, protocols, and packet counts. They offer visibility into network traffic at the packet level, aiding in troubleshooting, detecting anomalies, and understanding network behaviour.

Combining flow logs and traffic analytics enables network administrators to gain comprehensive visibility, streamline troubleshooting, and make data-driven decisions for network optimization and security enhancement.

## Lab Objectives

You will be able to complete the following tasks:

- Task 1: Network Watcher Traffic Analytics to monitor the network
  
## Task 1: Network Watcher Traffic Analytics to monitor the network

In this task, you will enable the Traffic Analytics in the NSG flow logs and review the logs.
 
1. Navigate to the Azure portal. Using the search bar, search for **Application gateways (1)** and **select (2)** from the suggestions..
 
     ![](images/searchgateway.png "search gateway")
 
 1. Select your **Application Gateway**.
 
     ![](images/upd-40.png "select gateway")
 
 1. Select the **Frontend public IP address** of the application gateway.
 
     ![](images/upd-41.png "select gateway")
  
 1. Copy the **Public IP address** and save it to Notepad for later use.

     ![](images/upd-42.png )

 1. To test the application, copy and paste the Frontend public IP address of **Application Gateway** in a new browser tab and generate some traffic by refreshing the browser.
 
     ![](images/upd-43.png)

      > **Note**: You will see that your website is running. If the website is not running, make sure the firewall policy of the application gateway is in detection mode.

    ![](images/upd-44.png)

1. Navigate to the resource group **FirewallVM-rg**, and from the **Overview** tab, select **AzureFirewall**.

   ![loadbalancer](images/upd-45.png)
   
1. Select **Firewall Public IP** from the Overview tab.

    ![pip](images/upd-46.png)
    
1. Copy the **IP address** and save it in a text editor.

    ![ip](images/upd-47.png)
      
1. Navigate to the Firewall's public IP address and refresh the page multiple times to generate some traffic.

   ![pip](images/upd-48.png)

1. In the Azure portal, search for **Network Watcher** and select it.

   ![](images/updateimg-26.png)

1. Once you're on the Network Watcher page, go to the left-hand menu under the **Monitoring** section and click on **Traffic Analytics**.
   
   ![](images/updateimg-27.png)
      
1. On the **Traffic Analytics** page, set the time interval to the **Last 30 minutes**.

   ![time interval](images/upd-49.png)
   
   > **Note: If you observe the Time interval is greyed out, click on Meanwhile, click here to see just resource data and perform the above step**.
   
   > It may take up to 30 to 60 minutes to click on **Meanwhile, click here to see just resource data and perform the above step option to come up**.

      ![](images1/timeinterval-1.png)
      
1. Now, you can observe the total number of network traffic flows from **Traffic Visualization** present in the **Traffic Analytics** page.

    ![traffic visualization](images/upd-013.png)

    > **Note: The dashboard may take up to 60-90 minutes to appear when deployed for the first time. This is because Traffic Analytics must first aggregate enough data for it to derive meaningful insights. If it takes more time, you can perform the next task and come back later and check on this**.
           
1. Under **Traffic Analytics**, Scroll down to **Your Environment** to view the total number of **Deployed Azure regions (1)**, **TA Enabled NSGs (2)**, **Virtual networks (3)**, and **Virtual subnetworks (4)**.

    ![env](images/E5T2S13.png)
      
1. To visualize the traffic distribution by geography, click on **View map**. The geo-map shows the traffic distribution to a data center from countries/regions and continents communicating with it.

    ![map](images1/viewmap.png)
     
1. In the **Traffic Analytics Geo Map View** page, click on the **Green** icon which indicates the Azure region, and observe the resources deployed under the region, to explore more select **More details**.

    ![md](images1/moredetails.png)
      
1. Under the **More Insights** blade, scroll down and explore traffic distribution for deployments of the East US region.

    ![comm](images1/moreinsights.png)
     
1. To close the **Traffic Analytics Geo Map View**, click on the cross at the top right corner.

     ![close](images1/close-1.png)
      
1. Close the **Ports receiving traffic from the Internet** page by clicking the **Cross (X) icon** in the top right corner.
      
1. Under the Traffic Analytics page, scroll down to **Traffic Distribution** to view the analytics of traffic flows across the host, subnet, VNet, and VMSS.

    ![tr](images/upd-015.png)
     
1. To view the analytics of traffic flows across the host, select **IP (1)**, then select **See all (2)** from **Traffic Distribution**.

    ![td](images/upd-016.png)
    
1. You can observe the graph of the **Time trending chart for the top 5 talking IPs** from the **Traffic distribution across the top IPs** page.

    ![see more](images/upd-017.png)
    
1. Under **Details of top 5 talking IPs**, select VM IP to explore more about traffic distribution.

     ![see more](images/upd-018.png)
     
1. Close the **Traffic distribution across top IPs** by clicking the **cross (X) icon** at the top-left corner of the page.
    
1. In the same way, you can explore more about **Malicious traffic**, and **Blocked traffic** 

1. Now scroll down to **Application ports**, to view analytics for application ports utilized across your environment and select **See all**.

    ![ap](images/upd-019.png)
     
1. From the **Most frequent L7 protocols** page, you can explore more about the ports and their ranging.

    ![l7](images/upd-020.png)

## Summary
 
In this exercise, you have covered the following:
  
- Monitored the network watcher traffic.

### You have successfully completed the lab
