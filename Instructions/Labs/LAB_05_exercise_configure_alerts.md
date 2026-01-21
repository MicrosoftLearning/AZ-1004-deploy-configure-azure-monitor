---
lab:
    title: 'Exercise - Configure alerts'
    module: 'Guided Project - Deploy and configure Azure Monitor'
---
In this exercise, you’ll configure alerts and actions.

This exercise should take approximately **10** minutes to complete. <!-- update with estimated duration -->

## Skilling tasks

- Create an action group to send an email
- Create an alert for virtual machine CPU utilization

## Exercise instructions

### Create an action group to send an email

1. In the Azure Portal Search Bar, enter **Monitor** and select **Monitor** from the list of results.
1. Select **Alerts** in the navigation menu.
1. Choose **Action Groups**.
1. On the **Action Groups** page, choose **Create**.
1. On the **Basics** page of the Create Action Group wizard, configure the following settings and choose **Next**.

    | Property | Value    |
    |:---------|:---------|
    | Subscription  | Your subscription   |
    | Resource Group  | rg-alpha   |
    | Region	| Global  |
    | Action group name	| NotifyCPU  |
    | Display Name	| NotifyCPU  |

6. On the **Notifications** page, set the notification type to **Email/SMS message/Push/Voice** and the Name to **NotificationEmail**. Choose the **Edit** (pencil) icon.
1. On the Email/SMS message/Push/Voice enable the **email** checkbox and enter the address **prime@fabrikam.com**. Choose **OK**. 
1. Choose **Review and Create**. Choose **Create**.


### Create an alert for virtual machine CPU utilization

1. In the Azure Portal Search Bar, enter **rg-alpha** and select **rg-alpha** from the list of results.
1. From the list of items in the resource group, choose **Linux-VM2**.
1. On the **Linux-VM2 properties** page, choose **Alerts** under **Monitoring**.
1. On the **Alerts** page, choose **Create** and then choose **Alert rule**.
1. On the **Condition** page of the Create an Alert Rule wizard, set the Signal name to **Percentage CPU**. Use the default settings and choose **Next**.
1. On the **Actions** page, choose **Select Action Group**.
1. On the **Select Action Groups** page, choose **NotifyCPU** and choose **Select**.
1. On the **Details** page enter the Alert rule name **HighCPU**. Choose **Review and Create** and then choose **Create**.

## Clean up subscription

To clean up the subscription, delete resource group **rg-alpha** and delete the **App Log Examiners** security group.
