# ROLES (RBAC-arm )
This Document will help you to create appropriate role for your environment and decide what all should we include in our role file. This document is more about what we are using in daya to day work.
A Role is that one which give the user the permission to read, write, modify etc..
For reference on roles/actions you can go to : https://docs.microsoft.com/en-us/azure/active-directory/role-based-access-control-resource-provider-operations

## Commands related to Roles and Policy
#### Remove an existing policy
Remove-AzureRmPolicyAssignment -Name <policy name> -Scope <resource group ID>
#### Defining a new policy
New-AzureRmPolicyDefinition -Name <policy name> -Description "<enter your description>" -Policy "<policy file path>"</br>
#### Assigning a defined Policy
New-AzureRMPolicyAssignment -name <policy name> -Scope <resource group ID> -PolicyDefinition <assigned policy name></br>
#### Defining new custom role
New-AzureRmRoleDefinition -InputFile <path of Role file></br>
####  Assignig New Role
New-AzureRmRoleAssignment -ResourceGroupName <rg name> -SignInName <signIn Name> -RoleDefinitionName <role name-inbuilt role or custom role></br>

## Microsoft.Compute

Mainly **Microsoft.Compute** include resources like Virtual machines, Virtual machine scale sets, availability sets etc..</br>
We can give full permissions to the resource by adding the following actions in Role file.</br>
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
We can give full permissions to  by adding the following actions in Role file.</br>
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









