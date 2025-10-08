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

In this task, you will review and monitor the NSG flow logs in the Traffic Analytics.

1. In the Azure portal, search for **Network Watcher** and select it.

   ![](images/updateimg-26.png)

1. Once you're on the Network Watcher page, go to the left-hand menu under the **Monitoring** section and click on **Traffic Analytics**.
   
   ![](images/updateimg-27.png)
      
1. On the **Traffic Analytics** page, set the **Time interval** to **Last 30 minutes** and the **Flow log type** to **VNet**.

   ![](images/081025(11).png)
   
   > **Note: If you observe the Time interval is greyed out, click on Meanwhile, click here to see just resource data and perform the above step**.
   
   > It may take up to 30 to 60 minutes to click on **Meanwhile, click here to see just resource data and perform the above step option to come up**.

      ![](images1/timeinterval-1.png)
      
1. Now, you can observe the total number of network traffic flows from **Traffic Visualization** present in the **Traffic Analytics** page.

    ![](images/081025(12).png)

    > **Note: The dashboard may take up to 60-90 minutes to appear when deployed for the first time. This is because Traffic Analytics must first aggregate enough data for it to derive meaningful insights. If it takes more time, you can perform the next task and come back later and check on this**.
           
1. Under **Traffic Analytics**, Scroll down to **Your Environment** to view the total number of **Deployed Azure regions (1)**, **Talking to Internet (2)**, **Virtual networks (3)**, and **Virtual subnetworks (4)**.

    ![](images/081025(13).png)
      
1. To visualize the traffic distribution by geography, click on **View map**. The geo-map shows the traffic distribution to a data center from countries/regions and continents communicating with it.

    ![](images/081025(14).png)
     
1. In the **Traffic Analytics Geo Map View** page, click on the **Green** icon which indicates the Azure region, and observe the resources deployed under the region, to explore more select **More details**.

    ![](images/081025(15).png)
      
1. Under the **More Insights** blade, scroll down and explore traffic distribution for deployments of the East US region.

    ![](images/081025(16).png)
     
1. To close the **Traffic Analytics Geo Map View**, click on the cross at the top right corner.

     ![close](images1/close-1.png)
      
1. Close the **Ports receiving traffic from the Internet** page by clicking the **Cross (X) icon** in the top right corner.
      
1. Under the Traffic Analytics page, scroll down to **Traffic Distribution** to view the analytics of traffic flows across the host, subnet, VNet, and VMSS.

    ![](images/081025(18).png)
     
1. To view the analytics of traffic flows across the host, select **IP (1)**, then select **See all (2)** from **Traffic Distribution**.

    ![](images/081025(19).png)
    
1. You can observe the graph of the **Time trending chart for the top 5 talking IPs** from the **Traffic distribution across the top IPs** page.

    ![](images/081025(20).png)
    
1. Under **Details of top 5 talking IPs**, select VM IP to explore more about traffic distribution.

    ![](images/081025(21).png)
     
1. Close the **Traffic distribution across top IPs** by clicking the **cross (X) icon** at the top-left corner of the page.
    
1. In the same way, you can explore more about **Malicious traffic**, and **Blocked traffic** 

1. Now scroll down to **Application ports (1)**, to view analytics for application ports utilized across your environment and select **See all (2)**.

    ![](images/081025(22).png)
     
1. From the **Most frequent L7 protocols** page, you can explore more about the ports and their ranging.

    ![](images/081025(23).png)

1. Under **Details of Most frequent L7 protocols**, select VM IP to explore more about traffic distribution.

    ![](images/081025(24).png)

## Summary
 
In this exercise, you have covered the following:
  
- Monitored the network watcher traffic.

## You have successfully completed the lab!