# Monitor an Azure Virtual Machine

## Exam Overview

## Understand the scenario

You are an Azure® developer for a company that is migrating its primary web app from its on-premises datacenter to Azure. You need to create an Azure virtual machine that you will use to verify your monitoring strategy. First, you will create a virtual machine that has boot diagnostics enabled. Next, you will monitor the startup metrics by using boot diagnostics, and then you will monitor selected metrics on the virtual machine. Finally, you will perform guest-level monitoring, and then you will create an alert rule.

## Understand your environment

You will be creating an Azure resource group named **RG-Exam8** that initially contains no resources.

# Create an Azure virtual machine that has boot diagnostics enabled

- Sign in to the Azure portal as your user account and password.

  Make sure you are signed in to Azure as the administrator.

- Create an Azure virtual machine by using the values in the following table. For any property that is not specified, use the default value.

  | Property                    | Value                                     |
  | :-------------------------- | :---------------------------------------- |
  | Resource group              | **RG-Exam8**                              |
  | Virtual machine name        | **VM1**                                   |
  | Image                       | **Windows Server 2019 Datacenter - Gen2** |
  | Size                        | **Standard_B2s - 2 vcpus 4 GiB memory**   |
  | Username                    | AzureAdmin                                |
  | Password                    | P455wrd.rd1234                            |
  | OS disk type                | **Standard HDD**                          |
  | Boot diagnostics            | **Enable with custom storage account**    |
  | Enable OS guest diagnostics | **Cleared**                               |

  > You can ignore any warnings about RDP ports as this virtual machine is being used for testing only.

  > The deployment will take approximately 3–5 minutes. Wait for the deployment to complete before moving on to the next task.

- Connect to the virtual machine by using **RDP**, and then sign in as AzureAdmin using P455wrd.rd1234 as the password.

  > You can safely ignore the error **Port prerequisite not met** on the Connect page. This does not affect VM connectivity during this Exam.

  > Minimize the RDP session window so that you can view the Azure portal for the next task.

## Check your work

- [ ] Confirm that you created a virtual machine named VM1 that runs Windows Server 2019 Datacenter.
- [ ] Confirm that you connected to VM1 by using RDP.

# Monitor boot diagnostics and metrics for a virtual machine

- Display the blobs in the boot diagnostics container in the **sacorpdiag[Initials]** storage account.

  > The **sacorpdiag[Initials]** storage account was created to hold diagnostic data when you enabled boot diagnostics with a custom storage account.

- Download each of the blob files, open each file, and then review the boot diagnostics screenshot and the serial console log for **VM1**.

  > You can use [boot diagnostics](https://docs.microsoft.com/en-us/azure/virtual-machines/boot-diagnostics) to observe an Azure virtual machine during startup by capturing the serial log and screenshots.

- Create a chart that displays the Percentage CPU metric for **VM1** and a time range of the **last 30 minutes**, and then create new charts for the Network In Total metric and the OS Disk Read Operations/sec metric.

  > [Azure Monitor Metrics](https://docs.microsoft.com/en-us/azure/azure-monitor/platform/data-platform-metrics) automatically captures numerical system data for Azure resources. You can use the Azure Metrics Explorer to analyze the data and produce reports based on a selected timeframe.

## Check your work

- [ ] Confirm that you downloaded and reviewed the blobs in the boot diagnostics container in the **sacorpdiag[Initials]** storage account.
- [ ] Confirm that you created charts to display selected metrics for VM1.

# Enable guest-level monitoring

- Enable guest-level monitoring for **VM1**.

  > The operation will take approximately 1-2 minutes. Wait for the operation to complete before moving on to the next step.

  > When you enable guest-level monitoring, the [Windows Azure diagnostics extension](https://docs.microsoft.com/en-us/azure/azure-monitor/platform/diagnostics-extension-windows-install) (WAD) is installed as an agent running on the virtual machine. The agent collects performance counters and logs from the guest operating system on the virtual machine. You can use these metrics for monitoring.

- Create a chart that displays the \LogicalDisk(_Total)\Disk Bytes/sec **Guest (classic)** metric for **VM1** and a time range of the **last 30 minutes**, and then create a new chart for the \Memory\Page Faults/sec **Guest (classic)** metric.

- Pin the chart for the **\Memory\Page Faults/sec** metric to the dashboard.

  > When pinning the chart to the dashboard, you may need to select Shared, and then select Private again to get My Dashboard to appear in the Dashboard drop-down list.

## Check your work

- [ ] Confirm that you enabled guest-level monitoring for the **VM1** virtual machine.
- [ ] Confirm that you created charts to display selected Guest (classic) metrics for **VM1**.
- [ ] Confirm that you pinned a chart for the \Memory\Page Faults/sec metric to the dashboard.

# Create an alert rule

- Create an alert rule named Percentage CPU above 80 for **VM1**, and then create a condition by using the values in the following table. For any setting that is not specified, use the default value.

  | Setting                          | Value            |
  | :------------------------------- | :--------------- |
  | Signal name                      | Percentage CPU   |
  | Operator                         | **Greater than** |
  | Threshold value                  | 80               |
  | Aggregation granularity (period) | **15 minutes**   |

- Add a new action group for the alert rule by using the values in the following table. For any setting that is not specified, use the default value.

  | Setting           | Value                                      |
  | :---------------- | :----------------------------------------- |
  | Action group name | **ag-[Initials]**                          |
  | Notification type | **Email/SMS message/Push/Voice**           |
  | Name              | AlertEmail                                 |
  | Email             | Taylor-28665502@cloudslice.onmicrosoft.com |

  > The alert will take up to 10 minutes activate. You do not have to wait for the activation to complete.

  > You can use [Azure alerts](https://docs.microsoft.com/en-us/azure/azure-monitor/platform/alerts-overview) to send notifications and perform actions based on predefined conditions—for example, a condition that is triggered when a metric passes a specified threshold. You can create alerts that fire proactively, giving you advance notice of a potential issue.

## Check your work

- [ ] Confirm that you created an alert rule named Percentage CPU above 80 for VM1.
- [ ] Confirm that you added a new action group named **ag-[Initials]** for the alert rule.

# Summary

Congratulations, you have completed the **Monitor an Azure Virtual Machine** Exam.

You have accomplished the following:

- Created a virtual machine that has boot diagnostics enabled.
- Monitored boot diagnostics and metrics on a virtual machine.
- Enabled and performed guest-level monitoring.
- Created an alert rule.



