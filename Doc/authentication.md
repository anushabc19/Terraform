## Terraform Authentication

## Azure Authentication

We need to create a service principal for azure authentication 

* Refer below link for creating service principal
  https://learn.microsoft.com/en-us/entra/identity-platform/howto-create-service-principal-portal

## Terrform code to set up  authentication
  
### sp keys
```
export ARM_CLIENT_ID="00000000-0000-0000-0000-000000000000"
export ARM_CLIENT_SECRET="12345678-0000-0000-0000-000000000000"
export ARM_TENANT_ID="10000000-0000-0000-0000-000000000000"
export ARM_SUBSCRIPTION_ID="20000000-0000-0000-0000-000000000000"
```

### Terraform code

```
terraform {
  required_providers {
    azurerm = {
      source = "hashicorp/azurerm"
      version = "~>2.0"
    }
  }
}

provider "azurerm" {
  features {}

  subscription_id   = "<azure_subscription_id>"
  tenant_id         = "<azure_subscription_tenant_id>"
  client_id         = "<service_principal_appid>"
  client_secret     = "<service_principal_password>"
}

# Your code goes here
resource "azurerm_resource_group" "testrg" {
name = "testrg"
location= "East us"
}
```
