# Configure Virtual Network Connectivity by Using Peering

## Exam Overview

## Understand the scenario

You are an Azure® administrator. You need to configure secure bidirectional communication between Azure virtual networks. First, you will create an Azure virtual network by using the Azure portal. Next, you will create an Azure virtual network by using Azure Cloud Shell. Finally, you will configure virtual network peering connections for secure bidirectional communication.

## Understand your environment
You will be creating an Azure resource group named **RG-Exam4** with not resources.

# Create a virtual network by using the Azure portal

- Sign in to the Azure portal as your user account and password.

  Make sure you are signed in to Azure as the administrator.

- Create a virtual network in the Azure portal by using the values in the following table. For any property that is not specified, use the default value.

  | Property             | Value        |
  | :------------------- | :----------- |
  | Resource group       | **RG-Exam4** |
  | Name                 | **webVNET**  |
  | IPv4 address space   | 10.10.0.0/16 |
  | Subnet name          | web          |
  | Subnet address range | 10.10.0.0/25 |

  > You will use this virtual network for the web tier.

  > You can use an [Azure virtual network](https://docs.microsoft.com/en-us/azure/virtual-network/concepts-and-best-practices) to create a network address space in the cloud that you will use to host resources—for example, virtual machines, load balancers, and application gateways—for secure access from on-premises networks and other virtual networks.

## Check your work

- [ ] Confirm that you created a virtual network named **webVNET**.
- [ ] Confirm that you created a subnet named web in the **webVNET** virtual network.

# Create a virtual network by using Azure Cloud Shell

- Launch an Azure Cloud Shell **Bash** session by using the values in the following table. For any property that is not specified, use the default value.

  | Property        | Value            |
  | :-------------- | :--------------- |
  | Resource group  | **RG-Exam4**     |
  | Storage account | **cs[Initials]** |
  | File share      | cloudshell       |

  > The Cloud Shell should take approximately 1–2 minutes to initialize.

  > You will use this virtual network for the application tier.

  > You can use [Azure Cloud Shell](https://docs.microsoft.com/en-us/azure/cloud-shell/overview) to execute commands and scripts directly from the browser without having to pre-install the Azure command-line interface (CLI) or PowerShell® on a client computer. Cloud Shell uses a storage account for its implementation so that you can switch between remote devices while maintaining your scripts and files in the cloud.

- Create a virtual network by using the [az network vnet create](https://docs.microsoft.com/en-us/cli/azure/network/vnet?view=azure-cli-latest) Azure CLI command and the values in the following table. For any property that is not specified, use the default value.

  | Property       | Value        |
  | :------------- | :----------- |
  | name           | appVNET      |
  | resource-group | **RG-Exam4** |
  | address-prefix | 10.20.0.0/16 |
  | subnet-name    | app          |
  | subnet-prefix  | 10.20.0.0/25 |

  > Cloud Shell does not support the keyboard shortcut Ctrl+V for paste. Instead, select the command prompt, and then use **Ctrl+Shift+V** to paste.

  > The [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/what-is-azure-cli) is a command set that you can use to create and manage Azure resources from the command line. It is cross-platform alternative to PowerShell. Azure CLI is pre-installed in the Azure Cloud Shell, but you can also download and install it on a client computer.

- Verify that you created a virtual network named appVNET that contains a subnet named app by using the az network vnet show command.

  > To get help, run the ```az network vnet show --help ``` command.

- Close the **Cloud Shell** window.

## Check your work

- [ ] Confirm that you created a virtual network named **appVNET**.
- [ ] Confirm that you created a subnet named app in the **appVNET** virtual network.

# Configure peering connections between the virtual networks

- Create virtual network peering connections from **webVNET** to **appVNET** by using the values in the following table. For any property that is not specified, use the default value.

  | Property                                   | Value                  |
  | :----------------------------------------- | :--------------------- |
  | This virtual network - Peering link name   | **webVNET-to-appVNET** |
  | Remote virtual network - Peering link name | **appVNET-to-webVNET** |
  | Virtual network                            | **appVNET**            |

  >You can use virtual network peering to connect multiple virtual networks by using private internal connections that are hosted on the Azure internal network, without using the public network. This provides improved performance and security.

- Verify that the **webVNET-to-appVNET** peering connection status is **Connected**.

- Verify that the **appVNET-to-webVNET** peering connection status is **Connected**.

## Check your work

- [ ] Confirm that you created a bidirectional virtual network peering connection between the **webVNET** and **appVNET** virtual networks.
- [ ] Confirm that you verified that both the **webVNET-to-appVNET** peering connection and the a**ppVNET-to-webVNE**T peering connection are connected.

# Summary

Congratulations, you have completed the **Configure Virtual Network Connectivity by Using Peering** Exam.

You have accomplished the following:

- Created a virtual network for a web server tier by using the Azure portal.
- Created a virtual network for an application server tier by using Azure CLI commands in Azure Cloud Shell.
- Configured virtual network peering connections for secure bidirectional communication.



