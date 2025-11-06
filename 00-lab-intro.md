# Infrastructure and Application Security 

### Overall Estimated Duration: 8 Hours

## Overview

Cloud Security in the context of Microsoft Azure infrastructure and application security involves implementing a comprehensive set of practices and tools to protect data, applications, and infrastructure hosted on the Azure platform. This includes securing virtual machines, networks, and storage through built-in security features like Azure Firewall, Network Security Groups, and encryption. Azure also provides robust identity and access management through Entra ID, ensuring that only authorized users can access resources. Additionally, Azure's security tools, such as Defender for Cloud and Microsoft Sentinel, offer continuous monitoring, threat detection, and automated response capabilities to safeguard against vulnerabilities and attacks. Adhering to these practices helps maintain a secure cloud environment, ensuring data integrity, confidentiality, and compliance with regulatory standards.

## Objective

This lab is designed to equip participants with hands-on experience to secure your application’s infrastructure with the help of Azure WAF, Application Gateways, and DDoS protection plans. Also, you’ll gain knowledge about how to 
monitor traffic and flow logs. You’ll be using multiple Azure services to secure your infrastructure.

- **Secure administration and management:** Implement robust access controls and management practices to safeguard administrative activities and ensure that only authorized users can manage Azure resources effectively.
  
- **Secure application:** Apply security best practices, such as vulnerability assessments and secure coding techniques, to protect applications deployed in Azure from potential threats and breaches.
  
- **Secure Infrastructure with Azure Firewall Premium:** Utilize Azure Firewall Premium to enforce advanced network security policies, including threat intelligence and application rules, to protect Azure infrastructure from sophisticated network attacks.
  
- **Protecting Infrastructure with Azure DDoS Protection Plans:** Deploy Azure DDoS Protection Plans to detect and mitigate distributed denial-of-service (DDoS) attacks, ensuring the availability and performance of your Azure services.
  
- **Network Management and Monitoring Revisited: Flow Logs and Traffic Analytics:** Leverage Azure Flow Logs and Traffic Analytics to gain insights into network traffic patterns, monitor potential security threats, and optimize network performance and security.

## Prerequisites

Participants should have the following prerequisites:

- **Basic Understanding of Cloud Computing:** Familiarity with fundamental cloud concepts and services, particularly in the context of Microsoft Azure.
- **Knowledge of Azure Services:** Experience with core Azure services, including Virtual Machines, Azure Storage, and Azure Networking.
- **Fundamentals of Cybersecurity:** Understanding of general cybersecurity principles, including concepts such as firewalls, encryption, and identity management.
- **Experience with Azure Portal:** Proficiency in navigating and using the Azure Portal for managing resources and configurations.
- **Networking Basics:** Knowledge of networking concepts, including IP addressing, subnets, and virtual networks, as they relate to cloud environments.
- **Familiarity with Identity and Access Management (IAM):** Understanding of IAM concepts, such as user roles, permissions, and Entra ID.
- **Understanding of Security Best Practices:** Awareness of security best practices and compliance requirements specific to cloud environments.

## Architechture

Various Azure resources and services are integrated to provide a comprehensive security framework. At the core, **Azure Virtual Machines** and **Azure Virtual Networks** are protected using **Azure Firewall** and **Network Security Groups** to control and monitor traffic. **Microsoft Entra ID** manages identity and access, ensuring secure authentication and authorization. **Defender for Cloud** offers unified security management and advanced threat protection across the Azure environment. **Microsoft Sentinel** provides intelligent security analytics and threat detection through a cloud-native SIEM (Security Information and Event Management) system. Data protection is enhanced using **Azure Key Vault** for managing secrets and **Azure Encryption** services to safeguard data at rest and in transit. Together, these resources create a layered security approach to defend against a wide range of cyber threats and ensure compliance with security policies and regulations.

## Architecture Diagram

![Architecture Diagram](./images/infra-security-arch-diagram.png)

## Explanation of Components

The architecture for this lab involves several key components:

- **Azure Monitor:** Provides comprehensive monitoring and diagnostics for Azure resources, offering insights into performance, health, and security.
- **Network Watcher:** Enables network monitoring and diagnostics, including traffic analysis and network flow logging, to enhance security and troubleshoot issues.
- **Virtual Network:** Creates isolated, secure network environments for Azure resources, allowing controlled communication and traffic management.
- **Virtual Machine:** Provides scalable computing resources for running applications and services, with security controls to protect against threats.
- **Network Security Group (NSG):** Controls inbound and outbound traffic to Azure resources by defining security rules to enforce network access policies.
- **Application Gateway:** A web traffic load balancer that manages and secures traffic for web applications, including features like SSL termination and URL-based routing.
- **Web Application Firewall (WAF) Policies:** Protects web applications from common threats and vulnerabilities by filtering and monitoring HTTP requests through configurable WAF rules.
- **Front Door and CDN Profiles:** Provides global application delivery and content distribution, enhancing performance and security by optimizing traffic routing and providing DDoS protection.
- **Azure App Services (Web App):** A platform for hosting and managing web applications with built-in security features like authentication, access controls, and threat detection.
- **Azure Firewall:** A managed, cloud-based network security service that protects Azure Virtual Networks by filtering traffic and enforcing security policies.
- **DDoS Protection:** Safeguards Azure resources from distributed denial-of-service attacks by providing automated detection and mitigation to maintain service availability.

## Getting Started with the lab
 
Welcome to your Infrastructure and Application Security Workshop! We've prepared a seamless environment for you to explore and learn about Azure services. Let's begin by making the most of this experience:
 
## Accessing Your Lab Environment
 
Once you're ready to dive in, your virtual machine and **Lab Guide** will be right at your fingertips within your web browser.

   ![](./images/environment-1.png)

## Virtual Machine & Lab Guide
 
Your virtual machine is your workhorse throughout the workshop. The lab guide is your roadmap to success.
 
## Exploring Your Lab Resources
 
To get a better understanding of your lab resources and credentials, navigate to the **Environment Details** tab.

   ![](./images/upd-1.png)
 
## Utilizing the Split Window Feature
 
For convenience, you can open the lab guide in a separate window by selecting the **Split Window** button from the Top right corner.
 
   ![](./images/GS8-1.png)
 
## Managing Your Virtual Machine
 
Feel free to start, stop, or restart your virtual machine as needed from the **Resources** tab. Your experience is in your hands!
 
  ![](./images/GS5-100.png)
 
## Let's Get Started with Azure Portal
 
1. On your virtual machine, click on the **Azure Portal** icon as shown below:
 
    ![](./images/GS1.png)
 
2. You'll see the **Sign into Microsoft Azure** tab. Here, enter your credentials:
 
   - **Email/Username:** <inject key="AzureAdUserEmail"></inject>
 
      ![](./images/GS3.png "Enter Email")
 
3. Next, provide your password:
 
   - **Password:** <inject key="AzureAdUserPassword"></inject>
 
      ![](./images/GS4.png "Enter Password")
 
4. If you see the pop-up **Stay Signed in?**, click **No**.

   ![](./images/GS5.png)

5. If you see the pop-up **Action Required**, leave it as default and then click on **Ask later**. Next, on the **Help us protect your account** pop-up click on **Skip for now** (14 days until this is required), and then select **Next**.

   ![](images/skip-for-now.png)

   >**NOTE:** Do not enable MFA. Select **Ask Later**.

6. If a **Welcome to Microsoft Azure** popup window appears, click **Cancel** to skip the tour.

## Steps to Proceed with MFA Setup if "Ask Later" Option is Not Visible

1. At the **"More information required"** prompt, select **Next**.

1. On the **"Keep your account secure"** page, select **Next** twice.

1. **Note:** If you don’t have the Microsoft Authenticator app installed on your mobile device:

   - Open **Google Play Store** (Android) or **App Store** (iOS).
   
   - Search for **Microsoft Authenticator** and tap **Install**.
   
   - Open the **Microsoft Authenticator** app, select **Add account**, then choose **Work or school account**.

1. A **QR code** will be displayed on your computer screen.

1. In the Authenticator app, select **Scan a QR code** and scan the code displayed on your screen.

1. After scanning, click **Next** to proceed.

1. On your phone, enter the number shown on your computer screen in the Authenticator app and select **Next**.
       
1. If prompted to stay signed in, you can click **No**.

1. If a **Welcome to Microsoft Azure** popup window appears, click **Cancel** to skip the tour.

   ![](images/gs1313.png)

## Support Contact
 
The CloudLabs support team is available 24/7, 365 days a year, via email and live chat to ensure seamless assistance at any time. We offer dedicated support channels tailored specifically for both learners and instructors, ensuring that all your needs are promptly and efficiently addressed.

Learner Support Contacts:

- Email Support: cloudlabs-support@spektrasystems.com

- Live Chat Support: https://cloudlabs.ai/labs-support

Now, click on **Next** from the lower right corner to move on to the next page.

![](./images/infra-app-security-lab1-49.png)

## Happy Learning!!