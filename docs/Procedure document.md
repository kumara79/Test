#This is a test procedure document
1.1.2	Partner Association
1.1.2.1	Partner Association Service Principal
Purpose
The service principal is a record in AAD tenant that shows Microsoft Insight as Microsoft Partner has delivered the service and is helping customer(DET) on Azure cloud adoption.  
The service principal need Contributor access to subscriptions to be able to recognized by Microsoft.
The service principal need to logon once to associate the service principal with Insight partner id.  That linkage between service principal and Insight partner id is on the service principal account level.
One tenant can have other service principal id for other partners, the partner association with Insight does not prevent any additional partner association being created in the same tenant.
The service principal does not need continuous logon to tenant.
 
Steps
There are different ways to create the partner association as detailed on Microsoft website: https://docs.microsoft.com/en-us/azure/cost-management-billing/manage/link-partner-id.
To create the service principal, the steps are:
1.	Create service principal(e.g. az ad sp create-for-rbac --name ServicePrincipalName)
2.	Grant service principal Contributor from tenant root.
3.	Logon to tenant as the new created service principal
4.	After logon as the new service principal, run commands to update partner id
5.	Logout as the new service principal

Pipeline code example in Azure DevOps:
Pre-req: 
1.	Create service principal(e.g. az ad sp create-for-rbac --name ServicePrincipalName)
2.	Grant service principal Contributor from tenant root.
3.	Setup service connection in azdo with the new service principal id/secret.
Note in below pipeline code 1158331 is insight partner id.
