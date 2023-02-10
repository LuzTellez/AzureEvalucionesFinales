# Configure a Virtual Machine by Using a Custom Script Extension

## Exam Overview

## Understand the scenario

You are a cloud operations engineer assigned to create a Windows® virtual machine in Azure®. You need to automate the configuration of a web app on a new server. First, you will create an Azure storage account, and then you will create a Windows virtual machine. Next, you will create a custom Windows PowerShell® script, and then you will upload the script to the Azure storage account. Finally, you will install the web app in the virtual machine by using a custom script extension.

## Understand your environment

You will be creating an Azure resource group named **RG-Exam2** with not resources.

# Create a storage account

- Sign in to the Azure portal as your user account and password.

  Make sure you are signed in to Azure as the administrator.
- Create a storage account named **sa[Initials]** in the **RG-Exam2** resource group by using the default settings.
- Add a container named scripts to the **sa[Initials]** storage account.

## Check your work

- [ ] Confirm that you created a storage account named **sa[Initials]**.
- [ ] Confirm that you created a container named scripts in the **sa[Initials]** storage account.

# Create an Azure virtual machine

- Create a virtual machine by using the values in the following table. For any property that is not specified, use the default value.

  | Property             | Value                                     |
  | :------------------- | :---------------------------------------- |
  | Resource group       | **RG-Exam2**                              |
  | Virtual machine name | **VM1**                                   |
  | Image                | **Windows Server 2019 Datacenter - Gen1** |
  | Size                 | DS1_v2                                    |
  | Username             | azureuser                                 |
  | Password             | dn2BPSb87+r$kH                            |
  | Select inbound ports | **HTTP (80)**, **RDP (3389)**             |
  | Boot diagnostics     | **Disable**                               |

  > While it is possible to add the custom script extension at the time that you create the virtual machine, in this Exam, you will add the extension in the next task.

  > You can use [Azure Hybrid Benefit for Windows Server](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/hybrid-use-benefit-licensing) to significantly reduce the costs associated with running your workloads in the cloud.

  > Do not continue until the deployment is complete. This may take a few minutes.

- Record the **public IP address** of **VM1** in the following **Public IP Address** text box:

  **Public IP Address**
  
  ```
  ```
  
  You will use the public IP address in an upcoming task.

## Check your work

- [ ] Confirm that you created a virtual machine named **VM1**.
- [ ] Confirm that you recorded the public IP address of **VM1**.

# Create a custom PowerShell script

- Copy the content from the [Windows PowerShell configuration script](https://raw.githubusercontent.com/LuzTellez/ChallengeLabs_ArmResources/master/Labs/AIS/Install-WebApp.ps1), paste the content into a text editor—for example, Notepad—on your local computer, and then save the file on your desktop as Install-WebApp.ps1.
- Upload the **Install-WebApp.ps1** file to the **scripts** container in the **sa[Initials]** storage account.

## Check your work

- [ ] Confirm that you created a script file named Install-webApp.ps1 on your local computer.
- [ ] Confirm that you uploaded the Install-WebApp.ps1 file to the scripts container in the **sa[Initials]** storage account.

# Add a custom script extension

- Add a custom script extension for the **VM1** virtual machine by using the **Install-webApp.ps1** script file in the **sa[Initials]** storage account.

  > Wait until the custom script extension has been provisioned.
  >
  > This will take approximately 3-5 minutes.

  >It may take as long as 10 minutes for the virtual machine extension to be created and for the script to finish running, but you can start testing and refreshing the page while the Azure deployment is still in progress. When the deployment is finished, you will see the following web page:
  >
  >**Test Web App Delployment**
  >
  >Congratulations! You have successfully deployed a simple web application on an Azure virtual machine.

  > You can use a [custom script extension](https://docs.microsoft.com/en-us/azure/virtual-machines/extensions/custom-script-windows) to implement post-deployment configuration of an Azure virtual machine.

## Check your work

- [ ] Confirm that you added a custom script extension to VM1 by using the Install-webApp.ps1 script.
- [ ] Confirm that you displayed the Test Web App Deployment page that was installed by the custom script extension.

# Summary

Congratulations, you have completed the **Configure a Virtual Machine by Using a Custom Script Extension** Exam.

You have accomplished the following:

- Created a storage account.
- Created an Azure virtual machine.
- Created a custom PowerShell script.
- Added a custom script extension to a virtual machine.