# A Static Web App automated with Terraform and Azure Pipelines

## Terraform configuration
Terraform main.tf file defines a storage account and a blob container named $web, which is what is used for static web sites in Azure. 

Other Terraform configuration files include:
- providers.tf - for storing the AzureRM and Random providers config
- variables.tf - for storing the resource group location and resource group prefix
- outputs.tf - for outputing the name of the Storage account and the RG, as well as the Primary Web Endpoint of the site

## Terraform commands to execute

Initialize the config:
`terraform init -upgrade`

Create an execution plan:
`terraform plan -out main.tfplan`

Apply the execution plan:
`terraform apply main.tfplan`

Get the URL to the static web site:
primary_web_host=$(terraform output -raw primary_web_host)

*If you need to clean-up resources:*
`terraform plan -destroy -out main.destroy.tfplan`