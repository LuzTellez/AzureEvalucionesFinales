# Work With Managed Disk Snapshots

## Exam Overview

## Understand the scenario

You are a cloud operations engineer responsible for configuring an Azure® virtual machine that uses a managed disk. You need to create a new test virtual machine that is based on an existing managed disk. First, you will prepare to create a snapshot, and then you will create a snapshot of an existing managed disk. Next, you will create a managed disk from the snapshot. Finally, you will create a virtual machine from the new managed disk.

# Understand your environment

You will be creating Azure environment that contains a resource group named **RG-Exam1**and a virtual machine named **VM1**(Linux (ubuntu 16.04 Standard DS1 v2 East US with NGINX Server and personalized page installed).

> Important: **do not start** until these resources have been created, you will not be guided through these tasks. 

# Prepare to create a managed disk snapshot

- Sign in to the Azure portal as your user account and password.

  Make sure you are signed in to Azure as the administrator.

- Record the **public IP address** of the **VM1** virtual machine in the following **Public IP Address** text box:

  ```
  ```

- Open a new browser window, go to http://<PIP>, verify that the web app displays the text **Auto-scale web application**, and then close the browser window.

  > If you receive a timeout, connection refused, or 502 Bad Gateway error, wait 2–3 minutes, and then refresh the page. Do not continue to the next step until the page displays the text *Auto-scale web application*.

- Stop **VM1**, and then verify that the status is **Stopped (deallocated)**.

  > You can use the command bar on the virtual machine page in the Azure portal or Azure PowerShell® commands to [stop](https://docs.microsoft.com/en-us/powershell/module/servicemanagement/azure.service/stop-azurevm?view=azuresmps-4.0.0), [start](https://docs.microsoft.com/en-us/powershell/module/servicemanagement/azure.service/start-azurevm?view=azuresmps-4.0.0), and [restart](https://docs.microsoft.com/en-us/powershell/module/servicemanagement/azure.service/restart-azurevm?view=azuresmps-4.0.0) a virtual machine.

  > Alert: Do not continue until the status of **VM1** changes to *Stopped (deallocated)*. You may need to refresh the page.

## Check your work

- [ ] Confirm that you displayed the web app on **VM1**.
- [ ] Confirm that you deallocated **VM1**.

# Create a snapshot of an existing managed disk

- Create a managed disk snapshot named snapshot-[initials] in the **rg1lod[initials]** resource group by using **VM1_disk1**.

  > **VM1_OsDisk** is the operating system disk used by the VM1 virtual machine.

  > Do not continue until the snapshot is successfully created.

  > Remember: You can create a snapshot by using the [Azure portal](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/snapshot-copy-managed-disk) or by using the [New-AzSnapshot](https://docs.microsoft.com/en-us/powershell/module/az.compute/new-azsnapshot?view=azps-5.5.0) PowerShell cmdlet.

- Start the **VM1** virtual machine, and then verify that the virtual machine status is **Running**.

## Check your work

- [ ] Confirm that you created a snapshot named **snapshot-[initials]**.
- [ ] Confirm that you verified that the **VM1** status is Running.

# Create a managed disk from a snapshot

- Create a managed disk named VM2_OsDisk_1_[initials] in the **RG-Exam1** resource group by using the **snapshot-[initials]** snapshot.

  > You can create a managed disk by using the Azure portal, Azure PowerShell, or the Azure command-line interface CLI 2.0.

## Check your work

- [ ] Confirm that you created a managed disk named **VM2_OsDisk_1_[initials]** by using **snapshot-[initials]**.

# Create a virtual machine from an unattached disk

- Create a virtual machine that uses **VM2_OsDisk_1_[initials]** as the operating system disk by using the values in the following table. For any property that is not specified, use the default value.

  | Property             | Value                                     |
  | :------------------- | :---------------------------------------- |
  | Resource group       | **RG-Exam1**                              |
  | Virtual machine name | **VM2**                                   |
  | Availability options | **No infrastructure redundancy required** |
  | Size                 | DS1_v2                                    |
  | Public inbound ports | **HTTP**, **SSH (22)**                    |
  | Boot diagnostics     | **Disable**                               |

  > Remember: You can create a virtual machine from an existing disk by using the Azure portal or by using a [Windows PowerShell script](https://docs.microsoft.com/en-us/azure/virtual-machines/scripts/virtual-machines-windows-powershell-sample-create-vm-from-snapshot).

- Restart **VM2** to reload the web app.

- Record the **public IP address** of **VM2** in the following **Public IP Address** text box:

  **Public IP Address**

  ```
  ```

- Open a new browser window, go to http://<PIP2>, and then verify that the web app displays the text **Auto-scale web application**.

- > If you receive a timeout error, connection refused, or 502 Bad Gateway error after restarting the virtual machine, refresh the page. It may take 3–5 minutes for the web server to start responding.

## Check your work

- [ ] Confirm that you created a virtual machine named **VM2** that uses an existing operating system disk named **VM2_OsDisk_1_[initials]**.
- [ ] Confirm that you verified that the web app on **VM2** displays the text Auto-scale web application.

# Summary

Congratulations, you have completed the **Work With Managed Disk Snapshots** **Exam**.

You have accomplished the following:

- Prepared to create a managed disk snapshot.
- Created a snapshot of an existing managed disk.
- Created a new managed disk from the snapshot.
- Created a virtual machine from the new managed disk.