# Deploy an Application by Using Azure Kubernetes Service

## Exam Overview

## Understand the scenario

You are an Azure® administrator. You need to deploy a Kubernetes® containerized application by using Azure Kubernetes Service (AKS). First, you will create an AKS cluster. Next, you will connect to the AKS cluster by using Azure Cloud Shell. Finally, you will run an application as a container in the AKS cluster.

## Understand your environment

You will be creating an Azure resource group named **RG-Exam7** that contains no resources.

# Create an AKS cluster by using the Azure portal

- Sign in to the Azure portal as your user account and password.

  Make sure you are signed in to Azure as the administrator.

- Create an Azure Kubernetes Service (AKS) cluster by using the values in the following table. For any property that is not specified, use the default value.

  | Property                     | Value                                       |
  | :--------------------------- | :------------------------------------------ |
  | Resource group               | **RG-Exam7**                                |
  | Cluster preset configuration | **Standard**                                |
  | Kubernetes cluster name      | **aks-[Initials]**                          |
  | Region                       | **(US) East US**                            |
  | Availability zones           | **None**                                    |
  | Node size                    | **Standard DS2_v2** - 2 vcpus, 8 GiB memory |
  | Scale method                 | **Manual**                                  |
  | Node count                   | 1                                           |
  | Container monitoring         | **Disabled**                                |

  >It will take approximately 5–10 minutes to deploy the AKS cluster.

  >[AKS](https://docs.microsoft.com/en-us/azure/aks/intro-kubernetes) creates a fully managed hosting cluster for containerized applications that supports the open source Kubernetes platform.

## Check your work

- [ ] Confirm that you created an AKS cluster named **aks-[Initials]**.

# Connect to the AKS cluster by using Azure Cloud Shell

- Create an Azure Cloud Shell **Bash** session by using the settings in the following table. For any property that is not specified, use the default value.

  | Property           | Value            |
  | :----------------- | :--------------- |
  | Cloud Shell region | **East US**      |
  | Resource group     | **RG-Exam7**     |
  | Storage account    | **cs[Initials]** |
  | File share         | **fs[Initials]** |

- Connect to the **aks-[Initials]** AKS cluster in the **RG-Exam7** resource group by using the [get-credentials](https://docs.microsoft.com/en-us/cli/azure/aks?view=azure-cli-latest#az_aks_get_credentials) command.

  >You can use *Ctrl+Shift+V* to paste into Cloud Shell.

- Display a list of the cluster nodes by using the [kubectl get](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#get) command.

  >There should be only one node in the cluster.

## Check your work

- [ ] Confirm that you connected to the AKS cluster.
- [ ] Confirm that you displayed a list of the cluster nodes.

# Run an application in the AKS cluster

- Create an application deployment named **nginx-[Initials]** that contains an nginx container image from Docker Hub by using the [kubectl create deployment](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#-em-deployment-em-) command.

  >You can get information on the kubectl create syntax by using the kubectl create deployment --help command.

- Display a list of the pods in the AKS cluster by using the kubectl get command.

  > There should be only one pod running on the AKS cluster.

  > The AKS deployment you created contains a [pod](https://docs.microsoft.com/en-us/azure/aks/concepts-clusters-workloads#pods) that is used to run the NGINX web server.

- Expose the pod in the **nginx-[Initials]** deployment to the internet on port 80 by using the [kubectl expose](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#expose) command and the LoadBalancer service type.

- Display the status of the available services by using the kubectl get command.

- Ensure that IP address in the **EXTERNAL-IP** column for **nginx-[Initials]** has changed from **<pending>** to a public IP address, and then record the public IP address in the following **Public IP Address** text box:

  **Public IP Address**

  ```
  
  ```

  >You may need to rerun the kubectl get service command until the public IP address is displayed.

- Open a new browser window, go to the public IP address at http://, and then verify that the browser displays the **Welcome to nginx** page.

## Check your work

- [ ] Confirm that you deployed an application that uses the nginx container image to the AKS cluster.
- [ ] Confirm that you displayed the nginx application in a browser.

# Summary

Congratulations, you have completed the **Deploy an Application by Using Azure Kubernetes Service** Exam.

You have accomplished the following:

- Created an AKS cluster by using the Azure portal.
- Connected to the AKS cluster by using Azure Cloud Shell.
- Deployed an application in the AKS cluster.