# Configure a Virtual Machine by Using a PowerShell DSC Extension

## Exam Overview

## Understand the scenario
You are a cloud operations engineer assigned to create a Windows® virtual machine in Azure®. You need to automate the configuration of a web app on a new server. First, you will create a storage account, and then you will create a Windows virtual machine. Next, you will create the configuration files. Finally, you will apply a PowerShell® Desired State Configuration (DSC) extension, and then you will verify that the web app loads.

## Understand your environment
You will be creating an Azure resource group named **RG-Exam3** with not resources.

# Create a storage account

- Sign in to the Azure portal as your user account and password.

  Make sure you are signed in to Azure as the administrator.
- Create a storage account named **sa[initials]** in the **RG-Exam3** resource group by using the default settings.
- Add a container named scripts to the **sa[initials]** storage account.

## Check your work

- [ ] Confirm that you created a storage account named **sa[initials]**.
- [ ] Confirm that you created a container named scripts in the **sa[initials]** storage account.

# Create a Windows virtual machine

- Create a virtual machine by using the values in the following table. For any property that is not specified, use the default value.

  | Property             | Value                                      |
  | :------------------- | :----------------------------------------- |
  | Resource group       | **RG-Exam3**                               |
  | Virtual machine name | VM1                                        |
  | Image                | **Windows Server 2019 Datacenter – Gen 1** |
  | Size                 | DS1_v2                                     |
  | Username             | azureuser                                  |
  | Password             | f3pMNq0Se8+!Dr                             |
  | Select inbound ports | **HTTP (80)**, **RDP (3389)**              |
  | Boot diagnostics     | **Disable**                                |

  > While it is possible to add the PowerShell DSC extension at the time you create the virtual machine, in this Exam, you will add the extension in the next step.

  > Do not continue until the deployment is complete. This will take approximately 2–4 minutes.

- Record the public IP address of VM1 in the following Public IP Address text box:

  ```
  ```

  > You will use the public IP address in an upcoming task.

## Check your work

- [ ] Confirm that you created a virtual machine named **VM1**.
- [ ] Confirm that you recorded the public IP address of **VM1**.

# Create the configuration files

- Copy the content from the [WebApp.ps1](https://raw.githubusercontent.com/LuzTellez/ChallengeLabs_ArmResources/master/Labs/AIS/WebApp.ps1) Windows PowerShell DSC file, paste the content into a text editor—for example, Notepad—on your local computer, and then save the file on your desktop as WebApp.ps1.

- Create a ZIP file named WebApp.zip that contains only the file **WebApp.ps1**.

  >Make sure you do not add any extra files or folders.

  >Remember: You can use a DSC Script resource to run Windows PowerShell script blocks on target nodes.

- Copy the configuration for the deployment from the [allnodes.psd1](https://raw.githubusercontent.com/LuzTellez/ChallengeLabs_ArmResources/master/Labs/AIS/allnodes.psd1) PowerShell module manifest file, paste the content into a text editor on your local computer, and then save the file on your desktop as allnodes.psd1.

  > You can use the built-in [DSC ConfigurationData parameter](https://docs.microsoft.com/en-us/powershell/scripting/dsc/configurations/configdata?view=powershell-7) to define the data that you will use in a DSC configuration for your environment. You can use a single configuration for multiple environments.environments.

- Upload the **WebApp.zip** and **allnodes.psd1** files to the **scripts** container in the **sa[initials]** storage account.

## Check your work

- [ ] Confirm that you created a file named **WebApp.zip** that contains a single file named **WebApp.ps1**.
- [ ] Confirm that you created a file named **allnodes.psd1**.
- [ ] Confirm that you uploaded the **WebApp.zip** and allnodes.psd1 files to the scripts container in the **sa[initials]** storage account.

# Add a PowerShell DSC extension

- Add a **PowerShell Desired State Configuration** extension for **VM1**, and then configure the extension by using the values in the following table. For any property that is not specified, use the default value.

  | Property                               | Value                                                        |
  | :------------------------------------- | :----------------------------------------------------------- |
  | Configuration Modules or Script        | **WebApp.zip**                                               |
  | Module-qualified Name of Configuration | WebApp.ps1\WebApp                                            |
  | Configuration Data PSD1 File           | **allnodes.psd1**                                            |
  | Version                                | The latest version specified on the [Azure DSC extension version history](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-extension-history) page |

  >Wait until the DSC extension has been provisioned. This will take approximately 3-5 minutes.
  >
  >You may need to refresh the page to see that the extension was provisioned.
  >
  >You can also monitor the success of the provisioning by using the Notifications menu.

  >Periodically, Microsoft will deploy new versions of the Azure DSC extension. For that reason, you may see that the documentation no longer matches the image displayed in the hint. You should always check the documentation to ensure that you are referencing the most recent version available.

- In a new browser window, go to http://<PIP>, and then periodically refresh the browser window until the **Test Web App Deployment** page is displayed.

  > It may take as long as 10 minutes for the virtual machine extension to be created and for the script to finish running, but you can start testing and refreshing the page while the Azure deployment is still in progress. When the deployment is finished, you will see the following webpage: **Test Web App Deployment**
  >
  > Congratulations! You have successfully deployed a simple web application on an Azure virtual machine.

## Check your work

- [ ] Confirm that you added a PowerShell DSC extension to a virtual machine by using the **Install-webApp.ps1** script.
- [ ] Confirm that you displayed the Test Web App Deployment page that was installed by the PowerShell DSC extension.

# Summary

Congratulations, you have completed the **Configure a Virtual Machine by Using a PowerShell DSC Extension** Exam.

In this Exam, you accomplished the following:

- Created a storage account.
- Created a Windows virtual machine in Azure.
- Created a PowerShell DSC extension.
- Added a PowerShell DSC extension to a virtual machine.
