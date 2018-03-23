# AZURE RESOURCE MANAGER POLICIES AND RBACs
# ROLES (RBAC-ARM )
This Document will help you to create appropriate role for your environment and decide what all should we include in our role file. This document is more about what we are using in day to day work.
A Role is that one which give the user the permission to read, write, modify etc..
For reference on roles/actions you can go to : https://docs.microsoft.com/en-us/azure/active-directory/role-based-access-control-resource-provider-operations

## Powershell commands related to Roles 
#### Defining new custom role
````
New-AzureRmRoleDefinition -InputFile < Role_file_path ></br>
````
####  Assignig New Role
````
New-AzureRmRoleAssignment -ResourceGroupName < rg_name > -SignInName < signIn_Name > -RoleDefinitionName < role_name-inbuilt role or custom role ></br>
````
## Microsoft.Compute

Mainly **Microsoft.Compute** include resources like Virtual machines, Virtual machine scale sets, availability sets etc..</br>
We can give full permissions to these resources by adding the following actions in Role file.</br>
__Microsoft.Compute/avalabilitySets/*__ </br>
__Microsoft.Compute/virtualMachines/*__ </br> 
__Microsoft.Compute/virtualMachineScaleSets/*__ </br>
Or else we can give :</br>
__Microsoft.Compute/*__ - This will give full permissions to all resources under Microsoft.Compute</br></br>
We can further restrict or allow the user by using the following actions actions/operations along with Microsoft.Compute. </br></br>
**/availabilitySets/read**	             -        Get the properties of an availability set </br>
**/availabilitySets/write**	             -        Creates a new availability set or updates an existing one </br>
**/availabilitySets/delete**            -       	Deletes the availability set </br>
**/virtualMachines/delete**              -	      Deletes the virtual machine </br>
**/virtualMachines/start/action**        -        Starts the virtual machine </br>
**/virtualMachines/restart/action**	     -        Restarts the virtual machine </br>
**/virtualMachines/deallocate/action**	 -        Powers off the virtual machine and releases the compute resources </br>
**/virtualMachines/vmSizes/read**        -      	Lists available sizes the virtual machine can be updated to</br>
**/virtualMachines/extensions/read**     -       	Get the properties of a virtual machine extension</br>
**/virtualMachines/extensions/write**   -        Creates a new virtual machine extension or updates an existing one</br>
**/virtualMachines/extensions/delete**  -        Deletes the virtual machine extension </br>
**/virtualMachineScaleSets/virtualMachines/read**	  - Retrieves the properties of a Virtual Machine in a VM Scale Set</br>
**/virtualMachineScaleSets/virtualMachines/delete**	- Delete a specific Virtual Machine in a VM Scale Set.</br>
**/virtualMachineScaleSets/virtualMachines/start/action**	   -  Starts a Virtual Machine instance in a VM Scale Set.</br>
**/virtualMachineScaleSets/virtualMachines/powerOff/action** -  Powers Off a Virtual Machine instance in a VM Scale Set.</br>
**/virtualMachineScaleSets/virtualMachines/restart/action**	 -  Restarts a Virtual Machine instance in a VM Scale Set.</br>
**/virtualMachineScaleSets/virtualMachines/deallocate/action**	-  Powers off and releases the compute resources for a Virtual Machine in a VM Scale Set.</br>

## Micrsoft.Storage
We can give full permissions by adding the following actions in Role file.</br>
__Microsoft.Storage/*__ </br>
Or else we can give :</br>
__Microsoft.Storage/storageAccounts/*__   - This will give permission to all actions under the resource Storage Account. </br></br>
We can further restrict or allow the user by using the following actions actions/operations along with Microsoft.Storage. </br>
**/storageAccounts/write**	             -          Creates a storage account with the specified parameters or update the properties or  tags or adds custom domain for the specified storage account.</br>
**/storageAccounts/delete**              -         	Deletes an existing storage account.</br>
**/storageAccounts/listkeys/action**	   -          Returns the access keys for the specified storage account.</br>
**/storageAccounts/regeneratekey/action**-          Regenerates the access keys for the specified storage account.</br>
**/storageAccounts/read**	               -          Returns the list of storage accounts or gets the properties for the specified storage account.</br>

## Microsoft.Networks
We can give full permissions by adding the following actions in Role file.</br>
__Microsoft.Networks/*__ </br>

Microsoft.Networks includes a lot of resources like Virtual Networks, Network Interfaces, Network security groups, Public IP Address, Load Balancers, Local Network Gateways, Application Gateways. </br>
We can further deny or allow this resources more specifically. </br>
For a Virtual machine normally we will be using Virtual Networks, Network Interfaces, Network security groups and Public IP Address.
If we are giving full permissions to these resources then operations in Rbac will look like this.</br>
__Microsoft.Networks/virtualNetworks/*__ </br>
__Microsoft.Networks/networkInterfaces/*__ </br>
__Microsoft.Networks/networkSecurityGroups/*__ </br>
__Microsoft.Networks/publicIPAddress/*__ </br></br>
 We can further deny or restrict using the following commands along with Microsoft.Networks</br>
**/networkSecurityGroups/read**	- Gets a network security group definition.</br>
**/networkSecurityGroups/write**	- Creates a network security group or updates an existing network security group.</br>
**/networkSecurityGroups/delete**	 - Deletes a network security group.</br>
**/networkSecurityGroups/join/action**	- Joins a network security group.</br>
**/networkSecurityGroups/defaultSecurityRules/read**	- Gets a default security rule definition.</br>
**/networkSecurityGroups/securityRules/read**	 - Gets a security rule definition.</br>
**/networkSecurityGroups/securityRules/write**	 - Creates a security rule or updates an existing security rule.</br>
**/networkSecurityGroups/securityRules/delete**  - Deletes a security rule.</br></br>
**/virtualNetworks/read** - Get the virtual network definition.</br>
**/virtualNetworks/write** -	Creates a virtual network or updates an existing virtual network.</br>
**/virtualNetworks/delete** 	-Deletes a virtual network.</br>
**/virtualNetworks/subnets/read**	- Gets a virtual network subnet definition.</br>
**/virtualNetworks/subnets/write**	- Creates a virtual network subnet or updates an existing virtual network subnet.</br>
**/virtualNetworks/subnets/delete**	- Deletes a virtual network subnet.</br>
**/virtualNetworks/subnets/join/action**	- Joins a virtual network.</br>
**/virtualNetworks/subnets/virtualMachines/read**	- Gets references to all the virtual machines in a virtual network subnet.</br>
**/virtualNetworks/virtualMachines/read**	- Gets references to all the virtual machines in a virtual network.</br></br>
**/networkInterfaces/read**	- Gets a network interface definition.</br>
**/networkInterfaces/write**	- Creates a network interface or updates an existing network interface.</br>
**/networkInterfaces/join/action**	- Joins a Virtual Machine to a network interface.</br>
**/networkInterfaces/delete**	- Deletes a network interface.</br>
**/networkInterfaces/loadBalancers/read**	- Gets all the load balancers that the network interface is part of.</br>
**/networkInterfaces/ipconfigurations/read**	- Gets a network interface ip configuration definition.</br></br>
**/publicIPAddresses/read**	- Gets a public ip address definition.</br>
**/publicIPAddresses/write**	- Creates a public Ip address or updates an existing public Ip address.</br>
**/publicIPAddresses/delete**	- Deletes a public Ip address.</br>
**/publicIPAddresses/join/action** - Joins a public ip address.</br></br>
If the user wants to create Load Balancer, use the following actions along with Microsoft.Networks in Rbac file.</br>
**/loadBalancers/read**-	Gets a load balancer definition.</br>
**/loadBalancers/write**-	Creates a load balancer or updates an existing load balancer.</br>
**/loadBalancers/delete**-	Deletes a load balancer.</br>
**/loadBalancers/networkInterfaces/read**	-Gets references to all the network interfaces under a load balancer.</br>
**/loadBalancers/loadBalancingRules/read**	-Gets a load balancer load balancing rule definition.</br>
**/loadBalancers/backendAddressPools/read**	-Gets a load balancer backend address pool definition.</br>
**/loadBalancers/backendAddressPools/join/action**	-Joins a load balancer backend address pool.</br>
**/loadBalancers/probes/read**	-Gets a load balancer probe.</br>
**/loadBalancers/virtualMachines/read**	-Gets references to all the virtual machines under a load balancer.</br>
**/loadBalancers/frontendIPConfigurations/read**	-Gets a load balancer frontend IP configuration definition.</br>
For full permissions to loadBalancer we can use: __Microsoft.Networks/loadBalancers/*__ .</br>

Microsoft.Networks also includes resources like Application Gateways and Local Network Gateways. Resources like this are highly cost consuming. So if it is not needed for the user, then it is better to deny permission create to these resources.We can deny any resources by including that specific resources inside Not Actions[].</br>
Actions/ Operations related to Network Gateways and Application Gateways are:</br>
**/applicationGateways/read**	-Gets an application gateway.</br>
**/applicationGateways/write**	-Creates an application gateway or updates an application gateway.</br>
**/applicationGateways/delete**	-Deletes an application gateway.</br>
**/applicationGateways/backendhealth/action**	-Gets an application gateway backend health.</br>
**/applicationGateways/start/action**	-Starts an application gateway.</br>
**/applicationGateways/stop/action**	-Stops an application gateway.</br>
**/applicationGateways/backendAddressPools/join/action** -	Joins an application gateway backend address pool.</br>

## An Example for Rbac 
Rbac file which permits the user to create a Virtual Machine, Network Security Group, Virtual Network, Public Ip Address and Network Interface card looks like as follows
````
{
  "Name": "Sample Custom Role",
  "Id": "casb4a5a-4e7a-41be-14dv-05cje226739",
  "IsCustom": true,
  "Description": "Azure Resource Manager Custom Role",
  "Actions": [
    "Microsoft.Authorization/*/read",
    "Microsoft.Compute/locations/*",
    "Microsoft.Resources/deployments/*",
    "Microsoft.Resources/subscriptions/resourceGroups/read",
    "Microsoft.Compute/virtualMachines/*",
    "Microsoft.Network/virtualNetworks/*",
    "Microsoft.Network/networkInterfaces/*",
    "Microsoft.Network/publicIpAddresses/*",
    "Microsoft.Network/networkSecurityGroups/*"

  ],
  "NotActions": [
  ],
  "AssignableScopes": [
   ]
}
````
````
Id specified in the rbac file should be unique and you can generate it using a GUID Generator.
````
# ARM Policies
This will help you to create appropriate ARM policies for your environment and decide what all should we include in your policy file. This document is more about what we are using in day to day work.</br>
Azure Policy is a service in Azure that you use to create, assign and, manage policy definitions. Policy definitions enforce different rules and actions over your resources, so those resources stay compliant with your corporate standards and service level agreements. Azure Policy runs an evaluation of your resources, scanning for those not compliant with the policy definitions you have. For example, you can have a policy to allow only certain type of virtual machines. Another requires that all resources have a particular tag. These policies are then evaluated when creating and updating resources.</br>
Resource policy definition used by Azure Policy enables you to establish conventions for resources in your organization by describing when the policy is enforced and what action to take. By defining conventions, you can control costs and more easily manage your resources. For example, you can specify that only certain types of virtual machines are allowed. Or, you can require that all resources have a particular tag. Policies are inherited by all child resources. So, if a policy is applied to a resource group, it is applicable to all the resources in that resource group.</br>
For reference on roles/actions you can go to : https://docs.microsoft.com/en-us/azure/azure-policy/policy-definition#parameters 

## Powershell commands related to ARM Policy
#### Remove an existing policy
````
Remove-AzureRmPolicyAssignment -Name < policy_name > -Scope < resourcegroup_ID ></br>
````
#### Defining a new policy
````
New-AzureRmPolicyDefinition -Name < policy_name > -Description "< enter_your_description >" -Policy "< policy_file_path >" </br>
````
#### Assigning a defined Policy
````
New-AzureRMPolicyAssignment -name < policy_name > -Scope < resourcegroup_ID > -PolicyDefinition < assigned_policy_name ></br>
````
##Aliases
Some of the property aliases to access specific properties for a resource type are specified in this document. Aliases enable you to restrict what values or conditions are permitted for a property on a resource. Each alias maps to paths in different API versions for a given resource type. During policy evaluation, the policy engine gets the property path for that API version.</br>

### Microsoft.Cache/Redis

**Microsoft.Cache/Redis/enableNonSslPort**	- Set whether the non-ssl Redis server port (6379) is enabled.</br>
**Microsoft.Cache/Redis/shardCount**	- Set the number of shards to be created on a Premium Cluster Cache.</br>
**Microsoft.Cache/Redis/sku.capacity**	- Set the size of the Redis cache to deploy.</br>
**Microsoft.Cache/Redis/sku.family**	- Set the SKU family to use.</br>
**Microsoft.Cache/Redis/sku.name**	- Set the type of Redis Cache to deploy.</br>

### Microsoft.Cdn/profiles

**Microsoft.CDN/profiles/sku.name**	- Set the name of the pricing tier.</br>

### Microsoft.Compute/disks

**Microsoft.Compute/imageOffer**	- Set the offer of the platform image or marketplace image used to create the virtual machine.</br>
**Microsoft.Compute/imagePublisher**	- Set the publisher of the platform image or marketplace image used to create the virtual machine.</br>
**Microsoft.Compute/imageSku**	- Set the SKU of the platform image or marketplace image used to create the virtual machine.</br>
**Microsoft.Compute/imageVersion**	- Set the version of the platform image or marketplace image used to create the virtual machine.</br>

### Microsoft.Compute/virtualMachines

**Microsoft.Compute/imageId**	- Set the identifier of the image used to create the virtual machine.</br>
**Microsoft.Compute/imageOffer**	- Set the offer of the platform image or marketplace image used to create the virtual machine.</br>
**Microsoft.Compute/imagePublisher**	- Set the publisher of the platform image or marketplace image used to create the virtual machine.</br>
**Microsoft.Compute/imageSku**	- Set the SKU of the platform image or marketplace image used to create the virtual machine.</br>
**Microsoft.Compute/imageVersion**	- Set the version of the platform image or marketplace image used to create the virtual machine.</br>
**Microsoft.Compute/licenseType**	- Set that the image or disk is licensed on-premises. This value is only used for images that contain the Windows Server operating system.</br>
**Microsoft.Compute/virtualMachines/imageOffer**	- Set the offer of the platform image or marketplace image used to create the virtual machine.</br>
**Microsoft.Compute/virtualMachines/imagePublisher**	- Set the publisher of the platform image or marketplace image used to create the virtual machine.</br>
**Microsoft.Compute/virtualMachines/imageSku**	- Set the SKU of the platform image or marketplace image used to create the virtual machine.</br>
**Microsoft.Compute/virtualMachines/imageVersion**	- Set the version of the platform image or marketplace image used to create the virtual machine.</br>
**Microsoft.Compute/virtualMachines/osDisk.Uri**	- Set the vhd URI.</br>
**Microsoft.Compute/virtualMachines/sku.name**	- Set the size of the virtual machine.</br>
**Microsoft.Compute/virtualMachines/availabilitySet.id**	- Sets the availability set id for the virtual machine.</br>

### Microsoft.Compute/virtualMachines/extensions

**Microsoft.Compute/virtualMachines/extensions/publisher**	- Set the name of the extension’s publisher.</br>
**Microsoft.Compute/virtualMachines/extensions/type**	- Set the type of extension.</br>
**Microsoft.Compute/virtualMachines/extensions/typeHandlerVersion**	- Set the version of the extension.</br>

### Microsoft.Compute/virtualMachineScaleSets

**Microsoft.Compute/imageId** -	Set the identifier of the image used to create the virtual machine.</br>
**Microsoft.Compute/imageOffer** -	Set the offer of the platform image or marketplace image used to create the virtual machine.</br>
**Microsoft.Compute/imagePublisher** -	Set the publisher of the platform image or marketplace image used to create the virtual machine.</br>
**Microsoft.Compute/imageVersion** -	Set the version of the platform image or marketplace image used to create the virtual machine.</br>
**Microsoft.Compute/imageSku** -	Set the SKU of the platform image or marketplace image used to create the virtual machine.</br>
**Microsoft.Compute/imageVersion** -	Set the version of the platform image or marketplace image used to create the virtual machine.</br>
**Microsoft.Compute/licenseType** -	Set that the image or disk is licensed on-premises. This value is only used for images that contain the Windows Server operating system.</br>
**Microsoft.Compute/VirtualMachineScaleSets/computerNamePrefix** -	Set the computer name prefix for all the virtual machines in the scale set.</br>
**Microsoft.Compute/VirtualMachineScaleSets/osdisk.imageUrl** -	Set the blob URI for user image.</br>
**Microsoft.Compute/VirtualMachineScaleSets/osdisk.vhdContainers** -	Set the container URLs that are used to store operating system disks for the scale set.</br>
**Microsoft.Compute/VirtualMachineScaleSets/sku.name** -	Set the size of virtual machines in a scale set.</br>
**Microsoft.Compute/VirtualMachineScaleSets/sku.tier** -	Set the tier of virtual machines in a scale set.</br>

### Microsoft.Network/applicationGateways

**Microsoft.Network/applicationGateways/sku.name** -	Set the size of the gateway.</br>

### Microsoft.Network/virtualNetworkGateways

**Microsoft.Network/virtualNetworkGateways/gatewayType**	- Set the type of this virtual network gateway.</br>
**Microsoft.Network/virtualNetworkGateways/sku.name**	- Set the gateway SKU name.</br>

### Microsoft.Sql/servers

**Microsoft.Sql/servers/version**	- Set the version of the server.</br>

### Microsoft.Sql/databases

**Microsoft.Sql/servers/databases/edition** -	Set the edition of the database.</br>
**Microsoft.Sql/servers/databases/elasticPoolName**	- Set the name of the elastic pool the database is in.</br>
**Microsoft.Sql/servers/databases/requestedServiceObjectiveId**	- Set the configured service level objective ID of the database.</br>
**Microsoft.Sql/servers/databases/requestedServiceObjectiveName**	- Set the name of the configured service level objective of the database.</br>

### Microsoft.Sql/elasticpools

servers/elasticpools	Microsoft.Sql/servers/elasticPools/dtu.</br>
servers/elasticpools	Microsoft.Sql/servers/elasticPools/edition.</br>

### Microsoft.Storage/storageAccounts

**Microsoft.Storage/storageAccounts/accessTier** -	Set the access tier used for billing.</br>
**Microsoft.Storage/storageAccounts/accountType**	- Set the SKU name.</br>
**Microsoft.Storage/storageAccounts/enableBlobEncryption**	- Set whether the service encrypts the data as it is stored in the blob storage service.</br>
**Microsoft.Storage/storageAccounts/enableFileEncryption**	- Set whether the service encrypts the data as it is stored in the file storage service.</br>
**Microsoft.Storage/storageAccounts/sku.name** -	Set the SKU name.</br>
**Microsoft.Storage/storageAccounts/supportsHttpsTrafficOnly** - Set to allow only https traffic to storage service.</br>
**Microsoft.Storage/storageAccounts/networkAcls.virtualNetworkRules[*].id**	- Check whether Virtual Network Service Endpoint is enabled.</br>

## An Example for ARM Policy
Rbac file which permits the user to create a Virtual Machine, Network Security Group, Virtual Network, Public Ip Address and Network Interface card looks like as follows
````
{
    "if": {
        "anyOf": [{
                "allOf": [
                    {
                        "field": "type",
                        "equals": "Microsoft.Storage/storageAccounts"
                    },
                    {
                        "not": {
                            "field": "Microsoft.Storage/storageAccounts/sku.name",
                            "in": [
                                "Standard_LRS"
                            ]
                        }
                    },
                    {
                        "not": {
                            "field": "Microsoft.Storage/storageAccounts/accessTier",
                            "equals": "cool"
                        }
                    }
                ]
            },
            {
                "allOf": [{
                        "field": "type",
                        "equals": "Microsoft.Compute/virtualMachines"
                    },
                    {
                        "not": {
                            "field": "Microsoft.Compute/virtualMachines/sku.name",
                          "equals": "Standard_A2_v2"
                        }
                    }
                ]
            },
            {
                "not": {
                    "anyOf": [{
                            "field": "type",
                            "like": "Microsoft.Resources/*"
                        },
                        {
                            "field": "type",
                            "like": "Microsoft.Compute/*"
                        },
                        {
                            "field": "type",
                            "like": "Microsoft.Storage/*"
                        },
                        {
                            "field": "type",
                            "like": "Microsoft.Network/*"
                        }
                    ]
                }
            },
            {
                "allOf": [{
                        "field": "type",
                        "equals": "Microsoft.Compute/virtualMachines"
                    },
                    {
                        "not": {
                            "allOf": [{
                                    "field": "Microsoft.Compute/virtualMachines/imagePublisher",
                                    "equals": "MicrosoftWindowsServer"
                                },
                                {
                                    "field": "Microsoft.Compute/virtualMachines/imageOffer",
                                    "equals": "WindowsServer"
                                },
                                {
                                    "field": "Microsoft.Compute/virtualMachines/imageSku",
                                    "equals": "2012-R2-Datacenter"
                                }
                            ]
                        }
                    }
                ]
            }
        ]
    },
    "then": {
        "effect": "deny"
    }
}
````


 












