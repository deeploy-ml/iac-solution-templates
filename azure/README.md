# Create Deeploy Stack from Azure template

[![Deploy To Azure](https://raw.githubusercontent.com/Azure/azure-quickstart-templates/master/1-CONTRIBUTION-GUIDE/images/deploytoazure.svg?sanitize=true)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fdeeploy-ml%2Fiac-solution-templates%2Fmain%2Fazure%2Fdeeploy.mainTemplate.json)

This solution template allows you to deploy the Deeploy Stack on Azure. It creates 2 resource groups:
* Core resource group: a Maneged AKS Cluster running Ubuntu Server on a Standard_D2_v2 Size Virtual Machine Scale set.
* Storage resource group: a PostgreSQL database server, blob storage account and Key Vault.

Run (parameter values are defaults):

```
az deployment sub create \
--name Deeploy \
--location westeurope \
--template-file "./azure/deeploy.mainTemplate.json" \
--parameters coreResourceGroupName=deeployCoreResourceGroup \
storageResourceGroupName=deeployStorageResourceGroup \
clusterName=deeploytest \
servicePrincipalClientId="<your-sp-client-id>" \
servicePrincipalObjectId="<your-sp-object-id>" \
servicePrincipalSecret="<your-sp-principal-secret>" \
dnsPrefix=deeploy \
osDiskSizeGB=0 \
minAgentCount=1 \
maxAgentCount=5 \
desiredAgentCount=3 \
agentVMSize=Standard_DS2_v2 \
linuxAdminUsername=deeploy \
sshRSAPublicKey="<your-public-key>" \
dbName=deeploytest \
dbAdministratorLogin=deeploy \
dbAdministratorLoginPassword=<your-db-password> \
dbTypeName=B_Gen5_1 \
dbTier=Basic \
dbCapacity=1 \
dbSizeMB=51200 \
dbFamily=Gen5 \
keyVaultName=deeploy \
saName=deeploy \
saType=Standard_LRS
```
