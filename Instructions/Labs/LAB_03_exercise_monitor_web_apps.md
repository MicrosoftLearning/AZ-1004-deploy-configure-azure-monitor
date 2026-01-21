---
lab:
    title: 'Exercise - Monitor web apps'
    module: 'Guided Project - Deploy and configure Azure Monitor'
---
In this exercise, you’ll prepare configure Azure Monitor for web apps.

This exercise should take approximately **20** minutes to complete. <!-- update with estimated duration -->

## Skilling tasks

- Enable Application Insights
- Disable logging for .NET core snapshot debugger
- Configure web app HTTP logs to be written to a Log Analytics workspace
- Configure SQL Insights data to be written to a Log Analytics workspace
- Enable file and configuration change tracking for web apps

## Exercise instructions

### Enable Application Insights

1. In the Azure Portal Search Bar, enter **rg-alpha** and select **rg-alpha** from the list of results.
1. From the list of items in the resource group, choose **App Services for the Web App with an SQL Database**.
1. Under **Monitoring** choose **Application Insights**.
1. On the **Application Insights** page, choose **Turn On Application Insights**.
1. On the **Application Insights** page, ensure that **Create a new resource** is selected and that the Log Analytics Workspace is set to **LogAnalytics1** and choose **Apply**.
1. On the **Apply monitoring settings** dialog, choose **Yes**.

### Disable logging for .NET core snapshot debugger

1. In the Azure Portal Search Bar, enter **rg-alpha** and select **rg-alpha** from the list of results.
1. From the list of items in the resource group, choose **App Services for the Web App with an SQL Database**.
1. Under **Monitoring** choose **Application Insights**.
1. Under **Instrument your application**, choose **.NET Core** and then set the Snapshot Debugger setting to **Off**. Choose **Apply**.
1. On the **Apply Monitoring Settings** dialog box, choose **Yes**.

### Configure web app HTTP logs to be written to a Log Analytics workspace

1. In the Azure Portal Search Bar, enter **rg-alpha** and select **rg-alpha** from the list of results.
1. From the list of items in the resource group, choose **App Services for the Web App with an SQL Database**.
1. Under **Monitoring**, choose **Diagnostic settings**.
1. On the **Diagnostic settings** page, select **+ Add diagnostic settings**.
1. On the **Diagnostic settings** page, choose the following and select **Save**.

    | Property | Value    |
    |:---------|:---------|
    | Diagnostic setting name  | httplogs   |
    | Categories	| HTTP logs  |
    | Destination details	| Send to Log Analytics workspace  |
    | Subscription	| Your subscription  |
    | Log Analytics workspace 	| LogAnalytics1   |

### Configure SQL Insights data to be written to a Log Analytics workspace

1. In the Azure Portal Search Bar, enter **rg-alpha** and select **rg-alpha** from the list of results.
1. From the list of items in the resource group, choose the sample SQL database.
1. Under **Monitoring**, choose **Diagnostic settings**.
1. On the **Diagnostic settings** page, choose **Add diagnostic setting**.
1. On the **Diagnostic setting page**, provide the following information and choose **Save**.

    | Property | Value    |
    |:---------|:---------|
    | Diagnostic setting name  | InsightLogAnalytics   |
    | Categories	| SQL Insights  |
    | Destination details	| Send to Log Analytics workspace  |
    | Subscription	| Your subscription  |
    | Log Analytics workspace 	| LogAnalytics1   |
