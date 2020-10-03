# Azure-EndToEnd-CICD
Udacity Azure DevOps - Ensuring Quality Releases


### Terraform in Azure

1. Configure the storage account and state backend using the `configtfbackend.sh` script.

Replace the values below in terraform/main.tf with the output from script:

* storage_account_name
* container_name
* access_keys

2. Create a Service Principal for Terraform: `az ad sp create-for-rbac --role="Contributor" --scopes="/subscriptions/SUBSCRIPTION_ID"`

This will output the following:

```
{
  "appId": "00000000-0000-0000-0000-000000000000",
  "displayName": "azure-cli-2020-10-02-11-31-24",
  "name": "http://azure-cli-2020-10-02-11-31-24",
  "password": "00000000-0000-0000-0000-000000000000",
  "tenant": "00000000-0000-0000-0000-000000000000"
}
```

Test this by logging in: `az login --service-principal -u CLIENT_ID -p CLIENT_SECRET --tenant TENANT_ID`

These values map to the Terraform variables in terraform.tfvars like so:

* **appId** is the `client_id` defined above.
* **password** is the `client_secret` defined above.
* **tenant** is the `tenant_id` defined above.

### Azure DevOps

1. Import the two files azure-pipelines.yaml and StarterAPIs.json into Azure DevOps.
2. Create a new Azure Pipeline from the azure-pipelines.yaml file. See [here](https://docs.microsoft.com/en-us/azure/devops/pipelines/create-first-pipeline?view=azure-devops&tabs=java%2Cyaml%2Ctfs-2018-2%2Cbrowser)