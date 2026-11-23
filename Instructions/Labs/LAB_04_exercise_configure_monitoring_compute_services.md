---
lab:
  title: Exercise - Configure monitoring for compute services
  module: Guided Project - Deploy and configure Azure Monitor
  description: You configure Azure Monitor for compute services by creating a data collection endpoint and data collection rule for a Windows virtual machine. You add IIS log collection to an existing rule and configure Network Connection Monitor for a Linux virtual machine.
  duration: 15 minutes
  level: 300
  islab: true
  primarytopics:
    - Azure Monitor
    - Data Collection Rules
    - Data Collection Endpoints
    - IIS Logs
    - Network Connection Monitor
    - Network Watcher
---

In this exercise, you’ll configure monitoring for compute services.

This exercise should take approximately **15** minutes to complete. <!-- update with estimated duration -->

## Skilling tasks

- Create a data collection endpoint
- Create a data collection rule
- Add an IIS log collection to an existing data collection rule
- Configure Network Connection Monitor for a Linux IaaS virtual machine

## Exercise instructions

### Create a data collection endpoint

1. In the Azure Portal Search Bar, enter **Monitor** and select **Monitor** from the list of results.
1. In the **Monitor** page, under **Settings**, choose **Data Collection Endpoints**.
1. On the **Data Collection Endpoints** page, choose **Create**.
1. On the Create Data Collection Endpoint page, provide the following settings and then choose Review + Create.

    | Property | Value    |
    |:---------|:---------|
    | Endpoint name  | IaaSVMCollectionEndpoint   |
    | Subscription	| Your subscription  |
    | Resource Group	| rg-alpha  |
    | Region	| East US  |

5. Review the settings and choose **Create**.

### Create a data collection rule

1. In the Azure Portal Search Bar, enter **Monitor** and select **Monitor** from the list of results.
1. In the **Monitor** page, under **Settings**, choose **Data Collection Rules**.
1. On the **Data Collection Rules** page, choose **Create**.
1. On the **Create Data Collection Rule** page, configure the following settings and choose **Next**.

    | Property | Value    |
    |:---------|:---------|
    | Rule name  | WinVMDCR   |
    | Subscription  | Your subscription   |
    | Resource Group	| rg-alpha  |
    | Region	| East US  |
    | Type of telemetry | Agent-based - Windows |
    | Data collection endpoint 	| IaaSVMCollectionEndpoint   |

5. On the **Resources** page, choose **Add Resources**.
1. On the **Select a scope** page, enable the **WS-VM1** checkbox and choose **Apply**.
1. On the **Create Data Collection Rule** page, choose **Next**.
1. On the **Collect and deliver** page, choose **Add new data source** (or **Add new dataflow**, if displayed).
1. On the **Add data source** page, select **Windows Event Logs**. In the **Application** category enable the **Critical** and **Error** categories. In the **Security** category, choose the **Audit Failure** category. In the **System** category, enable the **Critical** and **Error** categories. 
1. Choose **Next**.
1. On the **Destination** page, choose **Add destination** and configure the following settings:

    | Property | Value    |
    |:---------|:---------|
    | Destination type  | Log Analytics Workspaces |
    | Subscription  | Your subscription   |
    | Destination details | LogAnalytics1 |

12. Choose **Apply** to add the destination. Leave the optional transformation unchanged, and choose **Save** to save the data source.
1. Choose **Review + Create** and then choose **Create**.


### Add an IIS log collection to an existing data collection rule

1. In the Azure Portal Search Bar, enter **Monitor** and select **Monitor** from the list of results.
1. In the **Monitor** page, under **Settings**, choose **Data Collection Rules**.
1. Choose the **WinVMDCR** rule in rg-alpha.
1. Under **Configuration**, choose **Data Sources**.
1. On the **Data Sources** page, leave **Use preview** enabled if the toggle is displayed, and choose **Add** to use the new data source editor.
1. On the **Add Data Source** page, select **IIS Logs**.
1. Choose **Next**.
1. On the **Destination** page, choose **Add destination** and configure the following settings:

    | Property | Value    |
    |:---------|:---------|
    | Destination type  | Log Analytics Workspaces |
    | Subscription  | Your subscription   |
    | Destination details | LogAnalytics1 |

9. Choose **Apply** to add the destination. Leave the optional transformation unchanged, and choose **Save** to save the data source.

### Configure Network Connection Monitor for a Linux IaaS virtual machine

1. In the Azure Portal Search Bar, enter **Network Watcher** and select **Network Watcher** from the list of results.
1. Under **Monitoring**, choose **Connection Monitor**.
1. On the **Connection Monitor** page, open **Create** and choose **Manual create**.
1. On the **Basics** page of the **Create Connection Monitor** wizard, provide the following information and choose **Next**.

    | Property | Value    |
    |:---------|:---------|
    | Connection Monitor name  | LinuxVMPubIP   |
    | Subscription  | Your subscription   |
    | Region	| East US 2 |

5. On the **Add test group details** page, enter the name **LinuxIPTest** and choose **Add sources**.
1. On the **Add Sources** page, select **Azure endpoints** and set the type to **Virtual Machines**. Select **Subnet**, expand the subnet containing **Linux-VM**, and select the VM's checkbox. In its **IP** drop-down, select the public IP address shown on the **Linux-VM** resource's **Overview** page. Choose **Add Endpoints** and verify that the source endpoint identifies **Linux-VM**, not the entire subnet.
1. Choose **Add Test Configuration**. 
1. On the **Add Test Configuration** page, enter the name **DefaultHTTP** and then choose **Add Test Configuration**.
1. Choose **Add Destinations**. Select **Azure endpoints** and set the type to **Virtual Machines**. Select **Subnet**, expand the subnet containing **WS-VM1**, and select the VM's checkbox. Select **Add Endpoints** and verify that the destination endpoint identifies **WS-VM1**, not the entire subnet.
1. Choose **Add Test Group**.
1. Select **Next: Workspace**. Select **Custom Workspace** and configure the following settings:

    | Property | Value |
    |:---------|:------|
    | Subscription | Your subscription |
    | Region | East US (the region of LogAnalytics1) |
    | Workspace | LogAnalytics1 |

1. Choose **Review + create**, review the settings, and then choose **Create**.
