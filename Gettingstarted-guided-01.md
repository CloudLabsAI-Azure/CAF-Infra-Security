# Getting Started with Your Microsoft Azure Infrastructure and Application Security Workshop

### Overall Estimated Duration: 60 Minutes

## Overview 
Organizations require robust tools to ensure secure administration and efficient management of network resources in the cloud. Azure offers a suite of services that enable comprehensive monitoring, visualization, and secure access to resources. This lab demonstrates how to utilize Azure Monitor Network Insights for real-time health monitoring, visualize network relationships using Azure Network Watcher, and securely connect to virtual machines through Azure Bastion. Additionally, it guides the configuration of NSG Flow Logs and diagnostic settings to capture and analyze network traffic for enhanced security and compliance.  

By completing this lab, you will gain practical experience in improving network security, troubleshooting connectivity issues, and monitoring traffic patterns to maintain a resilient and secure Azure environment.

## Objective  

**Secure Administration and Management:** Gain practical expertise in securing and managing Azure network resources by leveraging key Azure features and tools. Learn to monitor network health using Azure Monitor Network Insights, visualize the network topology with Azure Network Watcher, and establish secure access to virtual machines through Azure Bastion. Additionally, configure NSG Flow Logs and diagnostic settings to capture traffic data for comprehensive monitoring and analysis. This hands-on lab equips you with the skills needed to enhance the security, visibility, and efficiency of your Azure networking environment.

## Prerequisites

Participants should have: 

- **Understanding of Azure Networking Concepts:** Familiarity with virtual networks, subnets, and network security groups (NSGs) is essential for configuring and analyzing network topology and security.  

- **Knowledge of Azure Monitoring Tools:** Prior experience with tools like Azure Network Watcher and analyzing logs is necessary to set up monitoring environments and interpret NSG flow logs effectively.  

- **Secure Access Practices:** Understanding secure remote access methods, including Azure Bastion, to enable secure management of virtual machines and network resources.  

- **Troubleshooting Skills:** Basic troubleshooting knowledge to diagnose and resolve network health issues.

## Architecture

The architecture for this lab focuses on securing administration and managing Azure environments effectively. It integrates multiple Azure services to ensure comprehensive monitoring, secure access, and traffic analysis. The flow begins with monitoring network health and visualizing topology, then enforces secure access using a Bastion Host, and finally prepares a robust monitoring setup with Network Watcher and NSG Flow logs. This architecture ensures end-to-end visibility and secure management of the network environment.

## Architecture Diagram 

![](./images/Lab001.png) 

## Explanation of Components 

The architecture for this lab involves the following key components: 

- **Network Health:** Azure Monitor provides tools to track and visualize the performance and health of your Azure resources. It collects metrics, logs, and diagnostics to identify bottlenecks, latency, or downtime issues. With custom dashboards and alerts, you can proactively address potential network problems, ensuring seamless operations.  

- **Network Topology:** Azure Network Watcher's topology feature offers a graphical representation of your network resources, such as virtual networks, subnets, and connected devices. This visualization helps you understand your network structure and analyze connectivity issues, providing insights into the dependencies between resources.  

- **Secure Access via Bastion Host:** Azure Bastion is a secure and fully managed service that allows remote access to your virtual machines directly from the Azure portal without exposing RDP or SSH ports over the internet. This eliminates security risks associated with public IP exposure, ensuring safe administration of your VMs.  

- **Prepare the Monitoring Environment and NSG Flow:** NSG Diagnostic Logs offer comprehensive insights into the configuration, rules evaluation, and overall health of Network Security Groups, enabling the identification of misconfigurations and unauthorized access attempts. Additionally, NSG Flow Logs capture detailed traffic data, such as source and destination IPs, ports, and protocols, facilitating network traffic analysis, threat detection, and the investigation of security incidents to ensure secure and efficient network operations.  

## Getting Started with the Lab 

Once you're ready to dive in, your virtual machine and lab guide will be right at your fingertips within your web browser.

![](./images/GS6.png) 

## Virtual Machine & Lab Guide

In the integrated environment, the lab VM serves as the designated workspace, while the lab guide is accessible on the right side of the screen.

**Note:** Kindly ensure that you are following the instructions carefully to ensure the lab runs smoothly and provides an optimal user experience.

## Exploring Your Lab Resources

To get a better understanding of your lab resources and credentials, navigate to the **Environment Details** tab.

![](./images/GS17.png)
   
## Utilizing the Split Window Feature
 
For convenience, you can open the lab guide in a separate window by selecting the **Split Window** button from the Top right corner.
 
![](./images/GS8.png)

## Lab Guide Zoom In/Zoom Out
 
To adjust the zoom level for the environment page, click the **A↕ : 100%** icon located next to the timer in the lab environment. 

![08](./images/zoom.png)  

## Managing Your Virtual Machine

Feel free to start, stop, or restart your virtual machine as needed from the **Resources** tab. Your experience is in your hands!

![](./images/GS5.png)
  
## Let's Get Started with Azure Portal

1. On your virtual machine, click on the Azure Portal icon as shown below:

   ![](./images/GS1.png)
   
1. You'll see the **Sign into Microsoft Azure** tab. Here, enter your credentials:
 
   - **Email/Username:** <inject key="AzureAdUserEmail"></inject>
 
      ![](./images/GS2.png "Enter Email")

1. Next, provide your password:
 
   - **Password:** <inject key="AzureAdUserPassword"></inject>
 
      ![](./images/GS3.png "Enter Password")

1. If **Action Required** window pop up click on **Ask later**. 

    ![](./images/imagescre.png)
 
1. If prompted to Stay signed in, you can click "No." 

    ![](./images/GS9.png)

1. If a **Welcome to Microsoft Azure** popup window appears, click **Cancel** to skip the tour.

## Support Contact
 
The CloudLabs support team is available 24/7, 365 days a year, via email and live chat to ensure seamless assistance at any time. We offer dedicated support channels tailored specifically for both learners and instructors, ensuring that all your needs are promptly and efficiently addressed.

Learner Support Contacts:
- Email Support: cloudlabs-support@spektrasystems.com
- Live Chat Support: https://cloudlabs.ai/labs-support

Now, click on **Next** from the lower right corner to move on to the next page. 

![](./images/next.png)

### Happy Learning!!
