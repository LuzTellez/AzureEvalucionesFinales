# Configure an Application Security Group

## Exam Overview

## Understand the scenario

You are an Azure administrator. You need to create an Azure virtual machine that uses an application security group. First, you will create a virtual network. Next, you will create an application security group, and then you will create a network security group. Finally, you will create an Azure virtual machine to be used as a web server, and then you will test the security configuration.

## Understand your environment

You will be creating an Azure resource group named **RG-Exam5** that contains no resources.

# Create a virtual network

- Sign in to the Azure portal as your user account and password.

  Make sure you are signed in to Azure as the administrator.

- Create a virtual network in the Azure portal by using the values in the following table. For any property that is not specified, use the default value.

  | Property             | Value        |
  | :------------------- | :----------- |
  | Resource group       | **RG-Exam5** |
  | Name                 | webVNET      |
  | IPv4 address space   | 10.10.0.0/16 |
  | Subnet name          | web          |
  | Subnet address range | 10.10.0.0/25 |

  > You will use this virtual network for the web tier.

  > You can use an [Azure virtual network](https://docs.microsoft.com/en-us/azure/virtual-network/concepts-and-best-practices) to create a network address space in the cloud that you will use to host resources—for example, virtual machines, load balancers, and application gateways—for secure access from on-premises networks and other virtual networks.

## Check your work

- [ ] Confirm that you created a virtual network named **webVNET**.
- [ ] Confirm that you created a subnet named web in the **webVNET** virtual network.

# Create an application security group and an associated network security group

- Create an application security group named webASG in the **RG-Exam5** resource group.

  > You can continue without waiting for the deployment to finish.

- Create a network security group named webNSG in the **RG-Exam5** resource group.

- Add an inbound security rule to **webNSG** to allow HTTP and HTTPS traffic by using the values in the following table. For any property that is not specified, use the default value.

  | Setting                                 | Value                          |
  | :-------------------------------------- | :----------------------------- |
  | Destination                             | **Application security group** |
  | Destination application security groups | **webASG**                     |
  | Destination port ranges                 | 80,443                         |
  | Name                                    | AllowAllweb                    |

  >Wait for the new inbound security rule to be created. This will take approximately 1–2 minutes.

- Add a second inbound security rule to **webNSG** to allow RDP traffic by using the values in the following table. For any property that is not specified, use the default value.

  | Property                                | Value                          |
  | :-------------------------------------- | :----------------------------- |
  | Destination                             | **Application security group** |
  | Destination application security groups | **webASG**                     |
  | Destination port ranges                 | 3389                           |
  | Name                                    | AllowAllRDP                    |

  >Wait for the new inbound security rule to be created.

- Associate the network security group to the **web** subnet in **webVNET**.

  > Wait for the **webNSG** to be associated with the web subnet. This will take approximately 1–2 minutes.

## Check your work

- [ ] Confirm that you created an application security group named **webASG**.
- [ ] Confirm that you created a network security group named **webNSG**.
- [ ] Confirm that you created inbound security rules that allow RDP, HTTP, and HTTPS traffic to flow to **webASG**.
- [ ] Confirm that you associated the web subnet with the **webNSG** network security group.

# Create an Azure virtual machine

- Create an Azure virtual machine by using the values in the following table. For any property that is not specified, use the default value.

  | Property                   | Value                                     |
  | :------------------------- | :---------------------------------------- |
  | Resource group             | **RG-Exam5**                              |
  | Virtual machine name       | VM1                                       |
  | Image                      | **Windows Server 2019 Datacenter - Gen1** |
  | Size                       | **Standard_B2s - 2 vcpus 4 GiB memory**   |
  | Username                   | AzureAdmin                                |
  | Password                   | Az!28664361!                              |
  | Public inbound ports       | **None**                                  |
  | Virtual network            | **webVNET**                               |
  | Subnet                     | **web (10.10.0.0/25)**                    |
  | NIC network security group | **None**                                  |
  | Boot diagnostics           | **Disable**                               |

  > Ignore any warnings about RDP ports as this virtual machine is only being used for testing.

  > The deployment will take approximately 3–5 minutes.

- Record the public IP address of VM1 in the following **VM1 Public IP Address** text box:

  **VM1 Public IP Address**

  ```

- Connect to VM1 through **RDP** by using the values in the following table. For any property that is not specified, use the default value.

  | Property   | Value                 |
  | :--------- | :-------------------- |
  | IP address | **Public IP address** |
  | Username   | AzureAdmin            |
  | Password   | Az!28664361!          |

  >Resize the RDP session window so that you can view the instructions for the Exam at the same time.

- On **VM1**, run the following command in **Windows PowerShell®** to install Internet Information Services (IIS):

  ```
  Install-WindowsFeature -name web-Server -IncludeManagementTools
  ```

- Open a new browser window, and then go to the public IP address of VM1 at http://<PublicIP> .

  > You should see the default Internet Information Services (IIS) webpage. This will verify that web traffic has been routed correctly by using an application security group and a network security group.

## Check your work

- [ ] Confirm that you created an Azure virtual machine named VM1.
- [ ] Confirm that you associated the webASG application security group with the virtual machine NIC.
- [ ] Confirm that you installed IIS on the virtual machine via RDP.
- [ ] Confirm that you verified that web traffic has been routed correctly.

# Summary

Congratulations, you have completed the **Configure an Application Security Group** Exam.

You have accomplished the following:

- Created a virtual network for a web server tier.
- Created an application security group and associated network security group.
- Created an Azure virtual machine and tested application security.