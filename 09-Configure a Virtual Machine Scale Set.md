# Configure a Virtual Machine Scale Set

## Exam Overview

## Understand the scenario

You are a cloud operations engineer for a company that has highly elastic demand requirements for a critical, client-facing application. You need to configure an Azure® virtual machine scale set. First, you will create a scale set that uses load balancing and a common Linux operating system disk image. Next, you will increase the number of virtual machines in the scale set. Finally, you will stop and deallocate a virtual machine instance.

# Understand your environment

You will be creating Azure environment that contains a resource group named **RG-Exam9** and a storage account named **sacs[Initials]**.

# Create a virtual machine scale set

- Sign in to the Azure portal as your user account and password.

  Make sure you are signed in to Azure as the administrator.

- Create a virtual machine scale set by using the values in the following table. For any property that is not specified, use the default value.

  | Property                       | Value                                        |
  | :----------------------------- | :------------------------------------------- |
  | Resource group                 | **RG-Exam9**                                 |
  | Virtual machine scale set name | **webappscaleset**                           |
  | Image                          | CentOS-based *latest version* **- x64 Gen1** |
  | Size                           | DS1_v2                                       |
  | Authentication type            | **Password**                                 |
  | Username                       | azureuser                                    |
  | Password                       | P455Wrd.rd1234                               |
  | Public IP address              | **Enabled**                                  |
  | Use a load balancer            | **Selected**                                 |

  >You can create a [virtual machine scale set](https://docs.microsoft.com/en-us/azure/virtual-machine-scale-sets/overview) by using the [Azure portal](https://docs.microsoft.com/en-us/azure/virtual-machine-scale-sets/quick-create-portal), [Azure PowerShell](https://docs.microsoft.com/en-us/azure/virtual-machine-scale-sets/quick-create-powershell)®, the Azure command-line interface [CLI 2.0](https://docs.microsoft.com/en-us/azure/virtual-machine-scale-sets/quick-create-cli), or an [ARM template](https://docs.microsoft.com/en-us/azure/virtual-machine-scale-sets/quick-create-template-linux).
  >
  >You can use a scale set to scale an application tier horizontally to meet demand while minimizing costs.

  >The deployment will take 2–3 minutes to complete.

- Verify that there are two virtual machine instances running in the **webappscaleset** scale set.

  > By default, there are two virtual machine instances in a scale set, but you can change that number during the initial creation process or at any time after creation.

## Check your work

- [ ] Confirm that you created a scale set that contains two virtual machine instances.

# Increase the number of virtual machine instances in a scale set

- Configure an Azure Cloud Shell **Bash** session by using the existing **RG-Exam9** resource group, an existing storage account named **sacs[Initials]** in the **East US** region, and a new file share named cloud-shell-share.

- Increase the number of virtual machine instances to 3 in the **webappscaleset** scale set that is located in the **RG-Exam9** resource group by using the [az vmss scale](https://docs.microsoft.com/en-us/cli/azure/vmss?view=azure-cli-latest#az_vmss_scale) command.
- Close the **Cloud Shell** window.
- Verify that there are three virtual machine instances running in the **webappscaleset** scale set.

## Check your work

- [ ] Confirm that you created a Bash session in Cloud Shell.
- [ ] Confirm that you increased the number of virtual machine instances in the **webappscaleset** scale set to three.

# Deallocate a virtual machine instance in a scale set

- Deallocate the **webappscaleset_0** virtual machine instance in the **webappscaleset** scale set.

  > You can deallocate virtual machine instances in a scale set by using the Azure portal or by using the [az vmss deallocate](https://docs.microsoft.com/en-us/cli/azure/vmss?view=azure-cli-latest#az_vmss_deallocate) command.

- Refresh the **Instances** page, and then verify that the status of the **webappscaleset_0** instance is **Stopped (deallocated)**.

  > You can create [autoscale rules](https://docs.microsoft.com/en-us/azure/virtual-machine-scale-sets/tutorial-autoscale-cli#define-an-autoscale-profile) based on the average CPU load in your scale set by using the [az monitor autoscale rule create](https://docs.microsoft.com/en-us/cli/azure/monitor/autoscale/rule?view=azure-cli-latest) command, and then you can generate CPU load to test autoscale rules by using the [az vmss list-instance-connection-info](https://docs.microsoft.com/en-us/cli/azure/vmss?view=azure-cli-latest#az_vmss_list_instance_connection_info) command.

## Check your work

- [ ] Confirm that you deallocated a virtual machine instance in the **webappscaleset** scale set.

# Summary

Congratulations, you have completed the **Configure a Virtual Machine Scale Set** Exam.

You have accomplished the following:

- Created an Azure virtual machine scale set.
- Increased the number of virtual machine instances in a scale set.
- Deallocated a virtual machine instance in a scale set.