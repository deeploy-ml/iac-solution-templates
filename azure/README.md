# Create Deeploy Stack from Azure template

[![Deploy To Azure](https://raw.githubusercontent.com/Azure/azure-quickstart-templates/master/1-CONTRIBUTION-GUIDE/images/deploytoazure.svg?sanitize=true)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fdeeploy-ml%2Fiac-solution-templates%2Fmain%2Fazure%2Fdeeploy.template.json)

https://raw.githubusercontent.com/deeploy-ml/iac-solution-templates/main/azure/deeploy.template.json

This solution template allows you to deploy the Deeploy Stack on Azure. It creates 2 resource groups:
* Core resource group: a secure 3 node, Single Node Type Service Fabric Cluster running Ubuntu Server on a Standard_D2_v2 Size Virtual Machine Scale set with Azure Diagnostics turned on.
* Storage resource group: a PostgreSQL database server, blob storage account and keyvault.

This template assumes that you already have certificates uploaded to your keyvault. If you want to create a new certificate run the createServiceFabricClusterCertificate.ps1 file in the scripts folder of this sample.
