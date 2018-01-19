# ROLES (RBAC-arm )
This Document will help you to create appropriate role for your environment and decide what all should we include in our role file. This document is more about what we are using in day to day work.
A Role is that one which give the user the permission to read, write, modify etc..
For reference on roles/actions you can go to : https://docs.microsoft.com/en-us/azure/active-directory/role-based-access-control-resource-provider-operations

## Commands related to Roles and Policy
#### Remove an existing policy
Remove-AzureRmPolicyAssignment -Name < policy_name > -Scope < resourcegroup_ID >
#### Defining a new policy
New-AzureRmPolicyDefinition -Name < policy_name > -Description "< enter_your_description >" -Policy "< policy_file_path >" </br>
#### Assigning a defined Policy
New-AzureRMPolicyAssignment -name < policy_name > -Scope < resourcegroup_ID > -PolicyDefinition < assigned_policy_name ></br>
#### Defining new custom role
New-AzureRmRoleDefinition -InputFile < Role_file_path ></br>
####  Assignig New Role
New-AzureRmRoleAssignment -ResourceGroupName < rg_name > -SignInName < signIn_Name > -RoleDefinitionName < role_name-inbuilt role or custom role ></br>

## Microsoft.Compute

Mainly **Microsoft.Compute** include resources like Virtual machines, Virtual machine scale sets, availability sets etc..</br>
We can give full permissions to these resources by adding the following actions in Role file.</br>
__Microsoft.Compute/avalabilitySets/*__ </br>
__Microsoft.Compute/virtualMachines/*__ </br> 
__Microsoft.Compute/virtualMachineScaleSets/*__ </br>
Or else we can give :</br>
__Microsoft.Compute/*__ - This will give full permissions to all resources under Microsoft.Compute</br>
We can further restrict or allow the user by using the following actions actions/operations along with Microsoft.Compute. </br>
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
__Microsoft.Storage/storageAccounts/*__   - This will give permission to all actions under the resource Storage Account. </br>
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
__Microsoft.Networks/publicIPAddress/*__ </br>
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
If the user wants to create Load Balancer,the following actions along with Microsoft.Networks in Rbac file.</br>
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
For full permissions to loadBalancer we can use: __Microsoft.Networks/loadBalancers/*__ .</br></br>

Microsoft.Networks also includes resources like Application Gateways and Local Network Gateways. Resources like this are highly cost consuming. So if it is not needed for the user, then it is better to deny permission create to these resources.We can deny any resources by including that specific resources inside Not Actions[].</br>
Actions/ Operations related to Network Gateways and Application Gateways are:</br>
**/applicationGateways/read**	-Gets an application gateway.</br>
**/applicationGateways/write**	-Creates an application gateway or updates an application gateway.</br>
**/applicationGateways/delete**	-Deletes an application gateway.</br>
**/applicationGateways/backendhealth/action**	-Gets an application gateway backend health.</br>
**/applicationGateways/start/action**	-Starts an application gateway.</br>
**/applicationGateways/stop/action**	-Stops an application gateway.</br>
**/applicationGateways/backendAddressPools/join/action** -	Joins an application gateway backend address pool.</br>




 












