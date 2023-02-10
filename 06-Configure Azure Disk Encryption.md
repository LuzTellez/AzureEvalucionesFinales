# Configure Azure Disk Encryption

## Exam Overview

## Understand the scenario

You are an Azure® developer. You need to enable Azure Disk Encryption on an Azure virtual machine. First, you will create a virtual machine. Next, you will add a data disk to the virtual machine. Finally, you will enable Azure Disk Encryption.

## Understand your environment

You will be creating an Azure resource group named **RG-Exam6** that contains no resources.

# Create an Azure virtual machine

- Sign in to the Azure portal as your user account and password.

  Make sure you are signed in to Azure as the administrator.

- Create an Azure virtual machine by using the values in the following table. For any property that is not specified, use the default value.

  | Property             | Value                                     |
  | :------------------- | :---------------------------------------- |
  | Resource group       | **RG-Exam6**                              |
  | Virtual machine name | webVM1                                    |
  | Image                | **Windows Server 2019 Datacenter - Gen2** |
  | Size                 | **Standard_B2ms**                         |
  | Username             | AzureAdmin                                |
  | Password             | Az!28664533!                              |
  | Public inbound ports | **Allow selected ports**                  |
  | Select inbound ports | **RDP (3389)**                            |
  | OS disk type         | **Standard HDD**                          |
  | Boot diagnostics     | **Disable**                               |

  > Ignore any warnings about RDP ports as this virtual machine is being used for testing only.

  > The deployment will take approximately 3–5 minutes. Wait for the deployment to complete before moving on to the next step.

- Verify that **webVM1** contains one OS disk that uses **SSE with PMK** encryption, and that there are no data disks.

  > You may need to scroll to the right to see the encryption setting.

  > [Server-side encryption](https://docs.microsoft.com/en-us/azure/virtual-machines/disk-encryption) (SSE) of Azure Disk Storage is enabled by default and encrypts disks at the storage server level by using a platform-managed key (PMK). The encryption key is managed automatically by the platform, in this case Azure, including protection and regular rotation. You can use server-side encryption with a customer-managed key (SSE with CMK) to manage the encryption key manually for compliance reasons. You can combine SSE with Azure Disk Encryption (ADE), which additionally encrypts the disk at the OS level by using technologies such as BitLocker (Windows) or DM-Crypt (Linux), for what is called *double encryption at rest* high security requirements.

## Check your work

- [ ] Confirm that you created an Azure virtual machine named **webVM1**.
- [ ] Confirm that you verified the current disk specifications.

# Add a new data disk to the Azure virtual machine

- Create a new disk named **DataFiles** that is attached to **webVM1**, and then configure the disk by using the **Standard HDD** OS disk type and a size of 128 GiB.

  > The update will take approximately 1–2 minutes. Wait for the update to complete before moving on to the next step.

- Connect to **webVM1** by using **RDP**, and then when prompted, sign in as AzureAdmin using Az!28664533! as the password.

  > Resize the RDP session window so that you can view the instructions for the Exam at the same time.

- Initialize the new disk as a simple volume by using the drive letter **F**, the **NTFS** file system, and a volume label of DataFiles.

- Close the **Remote Desktop Connection** window.

  > If prompted by a *Your remote session will be disconnected* message, select **OK**.

## Check your work

- [ ] Confirm that you added a new data disk named **DataFiles** to the virtual machine.
- [ ] Confirm that you connected to **webVM1** by using RDP.
- [ ] Confirm that you created a new simple volume named **DataFiles** that uses NTFS and the drive letter F.

# Enable Azure Disk Encryption

- Create an Azure key vault by using the values in the following table. For any property that is not specified, use the default value.

  | Property                                    | Value            |
  | :------------------------------------------ | :--------------- |
  | Resource group                              | **RG-Exam6**     |
  | Key vault name                              | **KV[Initials]** |
  | Pricing tier                                | **Standard**     |
  | Azure Disk Encryption for volume encryption | **Selected**     |

  > The deployment will take approximately 1–2 minutes.

- Launch an Azure **Cloud Shell** **PowerShell** session by using the values in the following table. For any property that is not specified, use the default value.

  | Property        | Value            |
  | :-------------- | :--------------- |
  | Resource group  | **RG-Exam6**     |
  | Storage account | **cs[Initials]** |
  | File share      | **cloudshell**   |

- Retrieve the properties of the **KV[Initials]** key vault in the **RG-Exam6** resource group by using the [Get-AzKeyVault](https://docs.microsoft.com/en-us/powershell/module/az.keyvault/get-azkeyvault) cmdlet, and then store the results in a local variable named $KeyVault.

  >Cloud Shell does not support the keyboard shortcut Ctrl+V for paste. Instead, select the command prompt, and then use **Ctrl+Shift+V** to paste.

- Enable Azure Disk Encryption for **webVM1** by using the [Set-AzVMDiskEncryptionExtension](https://docs.microsoft.com/en-us/powershell/module/az.compute/set-azvmdiskencryptionextension) cmdlet and the **RG-Exam6** resource group.

  > The command will take approximately 2–3 minutes to complete.

- Verify that the encryption for **webVM1** succeeded by using the [Get-AzVmDiskEncryptionStatus](https://docs.microsoft.com/en-us/powershell/module/az.compute/get-azvmdiskencryptionstatus) cmdlet and the **RG-Exam6** resource group.

- The encryption for both the OS and data disks should be verified.

  ![](img/06-01.jpg)

- Close the **Cloud Shell** window.

- In the Azure portal, verify that the updated disk specifications use Azure Disk Encryption.

  >The updated disk specifications should show there is now an OS disk and a data disk that both use **SSE with PMK & ADE**.

## Check your work

- [ ] Confirm that you created a key vault by using the Azure portal.
- [ ] Confirm that you enabled Azure Disk Encryption.
- [ ] Confirm that you verified Azure Disk Encryption.

# Summary

Congratulations, you have completed the **Configure Azure Disk Encryption** Exam.

You have accomplished the following:

- Created an Azure virtual machine.
- Added a new data disk to the Azure virtual machine.
- Enabled Azure Disk Encryption.





