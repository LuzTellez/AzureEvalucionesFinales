# Configure a Route Table by Using the Azure Portal

## Challenge Overview

## Understand the scenario

You are a system administrator for a company that is deploying virtual networks for Azure workloads. You need to ensure that traffic is routed through an Azure Firewall. In this challenge you will create a route table to manage the traffic for Azure Firewall. Then, you will create an Azure Firewall in a pre-configured virtual network. Finally, you will create a user-defined route to route the resources in your subnet so they can use the Azure Firewall.

## Understand your environment

You are using an Azure resource group that contains two virtual networks in a single region.

You will be creating the following resources.

| Resource        | Name           | Description |
| :-------------- | :------------- | ----------- |
| Resource group  | **RG-Exam10**  |             |
| Virtual Network | **WebAppVnet** | 10.1.0.0/16 |
| Virtual Network | **DBVnet**     | 10.2.0.0/16 |
| Subnet          | **default**    | 10.1.0.0/24 |
| Subnet          | **default**    | 10.2.0.0/24 |

> Important: **do not start** until these resources have been created, you will not be guided through these tasks. 

# Create a route table

- Sign in to the Azure portal as your user account and password.

  Make sure you are signed in to Azure as the administrator.

- Create a route table named **RouteTable[Initials]** in the **RG-Exam10** resource group. Specify **East US** Region as the location for the route table.

## Check your work

- [ ] A route table named **RouteTable[Initials]** exists.

# Create an Azure Firewall

- Create an Azure Firewall in the **RG-Exam10** resource group and **East US** region. Name the firewall instance **AzureFirewall**, set the Firewall tier to **Standard**, and set Firewall management to **Use Firewall rules (classic) to manage this firewall**. Ensure that it is applied to the **WebAppVnet** Virtual network, and create a new Public IP address named **azureFirewalls-ip**.

## Check your work

- [ ] An Azure Firewall named **AzureFirewall** exists in the **WebAppVnet[Initials]** virtual network.

# Add a route to Azure Firewall

- Create a route named **AzureFWRoute** in the routing table. In the routing table entry, add a route for all internet traffic to use the internal IP address of the Azure Firewall (10.1.0.4).

## Check your work

- [ ] A route table named **AzureFWRoute ** exists.

# Summary

Congratulations, you have completed the **Configure a Route Table by Using the Azure Portal** challenge. You have accomplished the following:

- Provisioned a route table.
- Provisioned an Azure Firewall
- Created a user-defined route for an Azure Firewall