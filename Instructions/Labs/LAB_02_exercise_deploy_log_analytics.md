---
lab:
    title: 'Exercise - Deploy Log Analytics'
    module: 'Guided Project - Deploy and configure Azure Monitor'
---

## Skilling tasks

- Create a Log Analytics workspace
- Configure Log Analytics data retention and archive policies
- Enable access to a Log Analytics workspace

## Exercise instructions

### Create a Log Analytics workspace

1. In the Azure Portal Search Bar, enter **Log Analytics** and select **Log Analytics workspaces** from the list of results.
1. On the **Log Analytics workspaces** page, choose **Create**.
1. On the **Basics** page of the Create Log Analytics workspace wizard, provide the following information and choose **Review + Create**.
   
    | Property | Value    |
    |:---------|:---------|
    | Subscription  | Your subscription   |
    | Resource Group	| rg-alpha  |
    | Name	| LogAnalytics1  |
    | Region	| East US  |

4. Review the information and choose **Create**.

### Install and configure the Log Analytics agent on Linux-VM2

1. In the Azure Portal Search Bar, enter **Virtual Machines** and select **Virtual Machines** from the list of results.
1. On the **Virtual Machines** page, select **Linux-VM2**.
1. On the **Linux-VM2** page, choose **Extensions + Applications** under **Settings**.
1. Choose **Add** and select the **Log Analytics agent for Linux** (also known as OmsAgentForLinux). Choose **Next**.
1. For the Workspace ID and Workspace Key, navigate to **LogAnalytics1 > Settings > Agents** in a separate browser tab or window.
1. Copy the **Workspace ID** and **Primary Key** from the LogAnalytics1 workspace.
1. Return to the Linux-VM2 extension installation page and paste the Workspace ID and Workspace Key. Choose **Review and Create**, and then choose **Create**.
1. After the installation completes, on the **Linux-VM2 Extensions + Applications** page, select the **AzureNetworkWatcherExtension**.
1. On the extension details page, ensure that **Enable automatic upgrade** is set to **Yes**. If not, enable it and choose **Save**.
1. Return to the **Extensions + Applications** page and select the **OmsAgentForLinux** extension.
1. On the extension details page, ensure that **Enable automatic upgrade** is set to **Yes**. If not, enable it and choose **Save**.

### Configure Log Analytics data retention and archive policies

1. In the Azure Portal Search Bar, enter **Log Analytics** and select **Log Analytics workspaces** from the list of results.
1. On the **Log Analytics workspaces** page, choose **LogAnalytics1**.
1. On the **Log Analytics workspace** page for LogAnalytics1, choose **Usage and estimated costs**.
1. Select **Data Retention** and set the slider to 60 days. Choose **OK**.
1. On the **Log Analytics workspace** page for LogAnalytics1, choose **Usage and estimated costs**.
1. Select **Daily cap**. Choose **On**. Set the daily cap to 10 GB and choose **OK**.

### Enable access to a Log Analytics workspace

1. In the Azure Portal Search Bar, enter **Log Analytics** and select **Log Analytics workspaces** from the list of results.
1. On the **Log Analytics workspaces** page, choose **LogAnalytics1**.
1. Select **Access control (IAM)**.
1. Choose **Add** and then choose **Add role assignment**.
1. On the list of roles, select **Log Analytics Reader** and choose **Next**.
1. On the **Members** page, choose **Select Members** and choose the App Log Examiners security group. **Choose Select**.
1. On the **Members** space, choose **Review + Assign**.
