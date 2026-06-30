# Implement Agent 365 to observe, govern, and secure Al apps, Copilot & Agents

### Overall Estimated Duration: 8 Hours

## Overview

In this hands-on lab, you will learn about the end-to-end security, governance, and monitoring of AI agents across a corporate environment. By assuming various personas—such as Administration, Security Operations, and you will deploy custom Copilot Studio agents, establish identity governance, apply Zero Trust conditional access policies, govern data sharing, and proactively hunt for security risks using Microsoft's suite of security and compliance tools. 

## Objective

The primary objective of these labs is to establish a comprehensive security and governance framework for AI agents. You will learn how to:
- Provision and manage AI agents and their underlying Entra identities. 
- Extend Zero Trust controls to AI agents using Custom Security Attributes and Conditional Access.
- Protect sensitive corporate data from AI oversharing via Microsoft Purview Sensitivity Labels and Data Loss Prevention (DLP) policies.
- Surface and investigate misconfigured or risky agents using Microsoft Defender XDR and Advanced Hunting.
- Assess data risks and remediate oversharing using Data Security Posture Management (DSPM).
- Fulfill compliance obligations by managing audit logs, retention policies, and analyzing events using Security Copilot.

## Prerequisites

- A Microsoft 365 tenant equipped with administrative access and applicable licensing for Microsoft Copilot Studio, Microsoft Entra ID, Microsoft Purview, and Microsoft Defender XDR.
- Access to the designated lab personas: **ODL User** (Setup/Admin), **Patti Fernandes** (SOC Analyst/Security Admin), and **Adele Vance** (End User).
- **Lab 00 must be completed first**, as it sets up the foundational environment. It creates the required SharePoint sites (HR and Operations), the Entra ID security groups (`copilotagentsecurity`), and the three primary Zava Copilot Studio agents (HR Assistant, Finance Agent, and IT Support Agent) that act as the governance targets for all subsequent labs.

## Explanation of Components

- **Microsoft Copilot Studio:** Used to create, manage, and deploy custom AI agents.
- **Microsoft Entra ID:** Manages identities, group memberships, and enforces Zero Trust via Conditional Access policies for AI agents.
- **Microsoft Purview:** Provides Data Loss Prevention (DLP) policies and Sensitivity Labels to govern data sharing and prevent overexposure.
- **Microsoft Defender XDR & Defender for Cloud Apps:** Utilized for Advanced Hunting and discovering unauthenticated or misconfigured agents.
- **Microsoft Security Copilot:** Assists in analyzing audit events, logs, and interaction data to fulfill compliance obligations.
- **Microsoft 365 Admin Center (Agent Registry):** Used to discover, inspect, and manage the lifecycle of custom AI agents across the tenant.

## Getting Started with the lab

Welcome to your workshop. Let's begin by making the most of this experience:

## Accessing Your Lab Environment

Once you're ready to dive in, your virtual machine and **Guide** will be right at your fingertips within your web browser.

![Access Your VM and Lab Guide](./media/gs0.png)

## Lab Guide Zoom In/Zoom Out

To adjust the zoom level for the environment page, click the **A↕ : 100%** icon located next to the timer in the lab environment.

![](./media/gs1.png)

## Virtual Machine & Lab Guide

Your virtual machine is your workhorse throughout the workshop. The lab guide is your roadmap to success.

## Exploring Your Lab Resources

To get a better understanding of your lab resources and credentials, navigate to the **Environment** tab.

![Explore Lab Resources](./media/gs1.1.png)
## Utilizing the Split Window Feature

For convenience, you can open the lab guide in a separate window by selecting the **Split Window** button from the Top right corner.

![Use the Split Window Feature](./media/gs1.2.png)

## Managing Your Virtual Machine

Feel free to **Start, Stop, or Restart (2)** your virtual machine as needed from the **Resources (1)** tab. Your experience is in your hands!

![Manage Your Virtual Machine](./media/VMSS.png)

## Let's Get Started with Azure Portal

1. On your virtual machine, click on the Azure Portal icon.

    ![](media/GettingStarted-07.png)

2. You'll see the **Sign into Microsoft Azure** tab. Here, enter your credentials:

   - **Email/Username:** <inject key="AzureAdUserEmail"></inject>

     ![Enter Your Username](./media/odlusr.png)

3. Next, provide your password:

   - **Password:** <inject key="AzureAdUserPassword"></inject>

     ![Enter Your Password](./media/password.png)

4. If **Action required** pop-up window appears, click on **Ask later**.
5. If prompted to **stay signed in**, you can click **No**.
6. If a **Welcome to Microsoft Azure** pop-up window appears, simply click **"Cancel"** to skip the tour.

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
1. If prompted to stay signed in, you can click "No."

1. If a **Welcome to Microsoft Azure** pop-up window appears, simply click "Maybe Later" to skip the tour.

## Support Contact

The CloudLabs support team is available 24/7, 365 days a year, via email and live chat to ensure seamless assistance at any time. We offer dedicated support channels tailored specifically for both learners and instructors, ensuring that all your needs are promptly and efficiently addressed.

Learner Support Contacts:

- Email Support: [cloudlabs-support@spektrasystems.com](mailto:cloudlabs-support@spektrasystems.com)
- Live Chat Support: https://cloudlabs.ai/labs-support

Click **Next** from the bottom right corner to embark on your Lab journey!

![Start Your Azure Journey](./media/PageNo.png)

Now you're all set to explore the powerful world of technology. Feel free to reach out if you have any questions along the way. Enjoy your workshop!
