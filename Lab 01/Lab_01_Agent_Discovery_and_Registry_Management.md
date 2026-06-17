# Lab 01: Agent Discovery and Registry Management

### Estimated time: 20 Minutes

## Introduction

Zava's CISO has asked the security team to confirm that all deployed AI agents are visible, governed, and accounted for before any security policy work begins. Patti Fernandes, Zava's Security Admin and SOC Analyst, will use the Agent Registry in Microsoft Entra ID to inspect the three Zava agents, test lifecycle controls, and identify any governance gaps. The Defender XDR workspace and Defender for Cloud Apps connector will also be initialised so that agent activity data begins flowing before moving further in the security journey.

This lab introduces the Microsoft 365 Admin Center Agent Registry as the primary tool for agent discovery, lifecycle management, and governance. Patti will explore the registry, review agent metadata, take lifecycle actions, identify ownerless agents, and complete the prerequisite configuration tasks required for Day 2 security labs - including Purview Audit verification, Defender XDR provisioning, and Defender for Cloud Apps initialisation.

## Objectives

- Explore the Agent 365 Overview dashboard and interpret key metrics.
- Inspect all three Zava agents in the Agent Registry and review their metadata.
- Block and unblock the Zava HR Assistant to validate lifecycle controls.
- Export the agent inventory to confirm audit trail capability.
- Identify ownerless agents using the registry dashboard filter.
- Verify that Purview Audit is active and run a baseline audit log search.
- Provision Microsoft Defender XDR by signing in to the Defender portal.
- Configure Defender for Cloud Apps organisation details and connect the Microsoft 365 app connector.

## Exercise 1: Explore the Agent 365 Overview and Agent Registry

### Task 1: Access the Agent 365 Overview Page

1. Open a browser and navigate to **Microsoft 365 admin center** and Sign in with **ODL User** credentials if prompted.

    ```
	https://admin.cloud.microsoft/
	```

	- **Email/Username:** <inject key="AzureAdUserEmail"></inject>

	- **Password:** <inject key="AzureAdUserPassword"></inject>

2. In the left navigation pane, expand **Agents**, and then select **Overview**.

	![](./media/secure1.png)

3. On the **Agent Overview** page, locate the following metrics and note their current values:

   - **Agent Registry** - total count of agents in the tenant.
   - **Active users in Copilot** - unique users who interacted with an agent in the last 30 days.
   - **Pending requests for agents** - open requests to add specific agents.
   - **Agents without owners** - agents whose owner has left the company.
   - **Agent analytics** - agents by creators, top platforms used to build agents, and active users in Copilot over time.

		![](./media/secure2.png)

      >**Note:** In a freshly configured environment, active user counts and agents without owners may show zero. This is expected. The metrics will populate as agents are used throughout the course.



### Task 2: Inspect and Approve the Zava Agents in the Agent Registry

1. In the left navigation pane, select **Agents**. Select **All agents**. Then select the **Requests** tab.

	![](./media/l01-t2-s1.png)

2. In the agent list, locate **Zava IT Support Agent** and select the vertical **...** next to the name.

3. From the two options, you can either **Reject submission** or **Publish to store**. For now, select **Publish to store**.

	![](./media/l01-t2-s2.png)

4. On the **Publish new agent** flow, under **Select users or groups who can install the agent**, select **All users**.

	![](./media/l01-e1-t2-s4.png)

5. Under **Select users or groups who will have the agent pre-installed (optional)**, select **Specific users/groups**.

	![](./media/l01-e1-t2-s5.png)

6. In the **Specific users/groups** search box, search for `Patti Fernandes` and select her from the dropdown.

	![](./media/l01-e1-t2-s7.png)

9. Then, select **Next**.

	![](./media/l01-e1-t2-s8.png)

10. On **Apply template**, select **Next**.

	![](./media/l01-e1-t2-s9.png)

11. On **Review permissions**, select **Next**.

	![](./media/l01-e1-t2-s10.png)

12. Click on **Publish** to publish the Zava IT Support Agent.

	![](./media/l01-e1-t2-s11.png)

13. Select **Done**.
    
	![](./media/l01-e1-t2-s12.png)

1. Repeat the above steps 1 to step 12 for **Zava HR Agent**


### Task 3: Approve an Agent in Teams Admin Center

1. Open a new browser tab and navigate to **Teams Admin Center** using the below URL and log in using the ODL User credentials.

    ```
	https://admin.teams.microsoft.com/
	```

	- **Email/Username:** <inject key="AzureAdUserEmail"></inject>
	- **Password:** <inject key="AzureAdUserPassword"></inject>

2. From the left navigation under **Teams apps**, select **Manage apps (1)**. In the search bar, search for `Zava` and select **Zava HR Assistant (2)**.

	![](./media/secure3.png)

      >**Note:** Make sure to select the one with the M365 apps as the selected **Supported on** coloumn.

4. Verify if **Zava HR Assistant** is published.

	![](./media/secure4.png)

      >**Note:** If not, click on **Publish** and click on it again on the pop-up confirmation.

	  ![](./media/secure17.png)

      ![](./media/secure18.png)

### Task 4: Block and Unblock the Zava HR Assistant

1. Navigate back to Microsoft 365 admin center.

    ```
	https://admin.cloud.microsoft/
	```

2. Expand **Agents** from the left navigation pane, select **All agents (1)**, select the **Registry** tab, then search for and select **Zava HR Assistant (2)** in the agent list.

	![](./media/secure5.png)

3. On the Details panel, click **Block** to prevent users from accessing the **Zava HR Assistant** app while keeping the app installed and available for future use if needed.
	![](./media/secure6.png)

4. On the **Block agent** pane, review the message confirming that blocking will prevent all users in the organisation from accessing the agent. Check the box next to **Block agent (1)**. Select **Save (2)**.

	![](./media/secure7.png)

5. Confirm that **Zava HR Assistant** now displays a **Blocked** status.

	![](./media/l01-e1-t4-s5.png)

6. On the Details panel, click **Unblock** to restore user access to the **Zava HR Assistant** app and make it available again across the organization.

	![](./media/secure8.png)

7. On the **Unblock agent** pane, select the **Unblock agent** checkbox. Select **Save**. Close the details panel.

    ![](./media/l1t4s7.png)

8. In the agent list, confirm that **Zava HR Assistant** now displays an **Available** status.

9. Close the tab.


### Task 5: Export the Agent Inventory

1. On the **Registry** tab, select **Export** on the toolbar above the agent list.

	![](./media/secure9.png)

   > **Note:** If an **Export** button is not visible in the toolbar, select the ellipsis (**...**) menu in the toolbar to locate the export option.

2. Confirm the download in the confirmation dialog. Wait for the export file to be generated and downloaded to your lab VM.

	![](./media/image25.png)

   > **Note:** If the above pop-up doesn't appear like the above image, select **All agents (1)** and click on **Continue (2)**.

	 ![](./media/secure10.png)

3. Open the downloaded CSV file.

4. Confirm that the file contains rows for **Zava HR Assistant**, **Zava Finance Agent**, and **Zava IT Support Agent**.

5. Confirm that the following columns are present: agent name, publisher, creator, creation date, host products, and availability status.

	![](./media/l01-e1-t5-s5.png)

6. Close the CSV file.



### Task 6: Identify Ownerless Agents

1. On the **Registry** tab, select the **Agents without Owners** card.

	![](./media/l01-e1-t6-s1.png)

2. Review the list of agents that are displayed.

	![](./media/l01-e1-t6-s2.png)

3. Note whether any of the three Zava agents appear in this filtered list.

   > **Note:** In a lab environment where agents were created by ODL User, the agents may or may not appear as ownerless depending on how ownership is propagated from Copilot Studio. If no agents appear, this confirms that ownership was correctly assigned during creation. If agents appear, this represents a governance gap that would be addressed by reassigning ownership.

4. Select **Clear filter** or reset the filters to return to the full agent list.

	![](./media/l01-e1-t6-s4.png)

## Exercise 2: Prepare Purview Audit for Day 2

### Task 1: Verify Purview Audit Is Active

1. Open a new browser tab and enter the following URL to navigate to the **Microsoft Purview**. 

    ```
	https://purview.microsoft.com
	```

1. Sign in with following  credentials:

	- **Email/Username:** **<inject key="AzureAdUserEmail"></inject>**

	- **Password:** **<inject key="AzureAdUserPassword"></inject>**

1. When prompted to **Welcome to the new Microsoft Purview portal!**, click  **Get started** to proceed with new Purview portal.

	![](./media/l01-e2-t1-s1.png)

1. In the Microsoft Purview portal, select **Solutions** **(1)** from the left navigation pane, and then choose **Audit** **(2)** to access auditing capabilities.

	![](./media/l01-e2-t1-s2.png)

3. On the **Audit** page, check whether a banner appears prompting you to start recording user and admin activity.

   - If a banner is displayed, select **Start recording user and admin activity** to enable auditing.

		![](./media/l01-e2-t1-s3.png)

   - If no banner is displayed, auditing is already enabled. Proceed to the next step.

1. Configure the search with the following values:

   - **Start date (1):** Select today's date minus 3 days.

   - **End date (2):** Select today's date.

   - Then click **Search** **(3)** to retrieve the corresponding audit logs.

	 ![](./media/l01-e2-t1-s5.png)

6. Wait for the search job to complete.

	![](./media/l1n3.png)

7. Review the results to confirm that audit records are being returned.

   > **Note:** If the search returns no results, this may indicate that no audited activities have occurred yet in the tenant, or that audit log ingestion requires additional time after initial provisioning. This is expected in a new lab environment. Audit records generated throughout this and subsequent labs will be searchable from Day 2 onwards.

## Exercise 3: Initialise Microsoft Defender XDR and Defender for Cloud Apps

### Task 1: Provision Microsoft Defender XDR

1. Open a new browser tab and enter the following URL to navigate to the **Microsoft Defender** portal. 

    ```
	https://security.microsoft.com
	```

1. If prompted to Sign in, enter the following credentials:

	- **Email/Username:** **<inject key="AzureAdUserEmail"></inject>**

	- **Password:** **<inject key="AzureAdUserPassword"></inject>**

2. On the **Microsoft Defender** portal welcome screen, review the provisioning message if displayed.

   > **Note:** Microsoft Defender XDR provisions automatically when an eligible admin visits the portal for the first time. If provisioning is in progress, a message will indicate the data centre location being used and an estimated completion time. Wait for provisioning to complete before continuing.

3. Once the portal has loaded completely, select **Home** to confirm the Defender XDR home dashboard loads without errors.

	![](./media/secure11.png)

### Task 2: Configure Defender for Cloud Apps Organisation Details

1. Click **Show navigation** **(1)** to show all menu items, select **Settings** **(2)** under the **System** section, and then choose **Cloud Apps** **(3)** to configure Microsoft Defender for Cloud Apps settings.

	![](./media/secure12.png)

1. Under System, select **Organisation details (1)** and enter the following details and click on **Save (5)**:

	- On the **Organisation details** page, in the **Organisation display name** field, replace the existing name with `Zava Corporation` **(2)**.

	- In the **Environment name** field, enter **DevOne-<inject key="Deployment ID" enableCopy="false"></inject>** **(3)**.

	- In the **Managed domains** field, keep it default

	  ![](./media/l1e3t2s2.png)

8. Confirm that a success notification appears confirming that the settings were saved.

### Task 3: Enable File Monitoring in Defender for Cloud Apps

1. From the left navigation pane, under **Information Protection**, select **Files (1)**. On the **Files** page, select the **Enable file monitoring (2)** checkbox and click **Save (3)**.

	 ![](./media/secure14.png)

1. Confirm that a success notification appears confirming that file monitoring was enabled.

### Task 4: Connect the Microsoft 365 App Connector

1. From the left navigation pane, under **Connected apps**, select **App Connectors (1)**. On the **App Connectors** page, select **+ Connect an app (2)**. In the app list, select **Microsoft 365 (3)**.

	 ![](./media/secure15.png)

1. On the **Select Microsoft 365 components** page, confirm that all components are selected by default. If any component is deselected, select it to enable it and click **Connect Microsoft 365**.

	![](./media/secure16.png)

1. Wait for the connection to complete. Then click **Done**.

	![](./media/l01-e3-t4-s8.png)

1. On the **App Connectors** page, select the **Microsoft 365** app connector **(1)** and from the toolbar select **+ icon (2)** to **Connect Microsoft Azure Instance**.

	![](./media/l01-e3-t4-s10.png)

1. Click **Connect Microsoft Azure** to authenticate with your Azure administrator account and establish the connection between Microsoft Defender for Cloud Apps and Microsoft Azure. 

	![](./media/l01-e3-t4-s11.png)

1. Wait for the connection to complete and click on **Done**.

    > **Note:** After connecting, Defender for Cloud Apps begins scanning Microsoft 365 activity. Initial data from the past week will appear in the portal. The first full scan may take several hours depending on tenant size. This connector is required for activity monitoring, DLP policy enforcement, and alert generation in Day 2 and Day 3 labs.

## Summary

In this lab, you explored the Agent 365 Overview dashboard and reviewed key governance metrics for the Zava tenant. You inspected all three Zava agents in the Agent Registry, reviewing their metadata, host products, and knowledge sources. You approved the Zava IT Support Agent submission, published the Zava HR Assistant through Teams Admin Center, then blocked and unblocked the Zava HR Assistant to verify that lifecycle controls function correctly. You exported the agent inventory to a CSV file to confirm audit trail capability, and used the ownerless agent filter to check for governance gaps in agent ownership.

You then prepared the Day 2 monitoring infrastructure by verifying that Purview Audit is active and running a baseline audit log search. You provisioned Microsoft Defender XDR, configured Defender for Cloud Apps with Zava Corporation organisation details and managed domain, connected the Microsoft 365 app connector to begin activity data ingestion, and enabled file monitoring.

The Zava agent environment is now fully visible, governed, and ready for security policy configuration in Day 2.
