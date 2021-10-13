# Azure Guardian FAQ #

* 1. Why is Global Reader access is required on the AOE Automation Account Service Principal?

Other than Cost Optimization recommendation, Azure Optimization Engine also provides Security     recommendations on Azure environment both at AAD and subscription level.

Global Reader access is required to access existing Application registrations\ Service Principals for which no expiration is setup or is expired or about to expire.

This helps to setup an overarching Security governance on Azure environment and helps to get insights on security misconfigurations.

* 2. Why Insight PAL Service Principal needs Contributor access on subscription?

 A Service Principal is a non-interactive service account and will be used for PAL registration and is a record in AAD tenant that shows Microsoft that Insight as Microsoft Partner has delivered the service and is helping customer (PSC) on Azure cloud adoption.  
  
 The service principal need Contributor access to subscriptions to be able to recognized by Microsoft.
  
 The service principal need to logon once to associate the service principal with Insight partner id.  That linkage between service principal and Insight partner id is on the service principal account level.
  
 Once the registration is complete, PSC can delete the password\ secret for the Service Principal and generate a new secret and store it in the Azure Key Vault. Can Customer can create Service Principal and perform Insight PAL association by themselves. This way Insight doesn't need to know the SP credentials.
  
 One tenant can have other service principal id for other partners, the partner association with Insight does not prevent any additional partner association being created in the same tenant.
  
 Also service principal does not need continuous logon to tenant.

* 3. Why do we need 2 Service Principal for Azure Guardian deployment?

 To make Insight PAL enablement and Guardian AOE code deployment process independent of each other we need 2 service principals to be provisioned into the customer environment.

 First Service Principal is used to enable Insight PAL into the customer's Azure environment. This service principal need Contributor access to subscriptions to be able to recognized by Microsoft. It is a record in customer's AAD  that shows Microsoft that Insight as Microsoft Partner has delivered the service and is helping customer on Azure cloud adoption.

 Second Service Principal is created during the deployment of Azure Guardian AOE code deployment. As an Azure automation account is provisioned and registered with the AAD. This automation account Service Principal needs Reader access on all the customer managed Azure subscriptions to provide recommendation. This service principal also needs Global Reader permission on AAD to provide security recommendations on existing AAD registered Service principals.

* 4. What happen when customer is not comfortable in assigning Global Reader permission to Azure Guardian AOE Service Principal?

 Azure Guardian Optimization Engine also provide Security recommendations along with Cost optimization recommendations.

 When AAD Global Reader access is assigned to the Azure Guardian AOE Service Principal, it then assesses existing Service Principals registered with customer's AAD and provide security recommendations aligned with Azure Best Practises. In absence of Global Reader permission Azure Guardian AOE won't be able to provide the below mentioned recommendations:

 • The maximum number of years for a Service Principal credential/certificate is valid. It defaults to 2 years with an option to set the customer defined acceptable default timeframe.
 • The minimum number of days left for a Service Principal credential/certificate before it expires. It defaults to 30 days with an option to set the customer defined notification threshold.
