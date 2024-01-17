//   COMMANDS TO RUN

// To create or edit run the same command 
az stack group create --name "lambda-api-dev" --resource-group "aks-rg1" --template-file ./main.bicep --parameters ../configurations/dev.json --delete-all --deny-settings-mode none

// To delete the entire Stack
az stack group delete --name "lambda-api-dev" --resource-group "aks-rg1" --delete-all --yes

Options available -> 
  --deny-settings-mode denyWriteAndDelete // This disallows deletion or modification of resources post creation
  --deny-setttings-apply-to-child-scopes // applies this setting to the child resources created automatically due to creation of resources via stack
  --deny-settings-excluded-actions ''Microsoft.Compute/virtualMachines/write Microsoft.StorageAccounts/delete' // would prevent deletion and editiing of virtual machines once created
  --deny-settings-excluded-principals "Principals mentioned here can come and delete even whern you had denyWriteAndDelete


Screenshots:
// Creation 
![Alt text](./stack.png)

![Alt text](./rg_details.png)

// Deletion

![Alt text](./deletion.png)




Reference :
https://learn.microsoft.com/en-us/azure/azure-resource-manager/bicep/deployment-stacks?tabs=azure-cli

How to Use for our Purpose

- For individual Stacks -> create seperate Bicep files eg SQLStack.bicep which has everything related to SQL deployments in it 
  - eg SQLContainerName, SQLDB etc

- Run the commands mentioned above to deploy the individual stacks -> This could be part of the scripts in Deploy Cordant environments
  - In some parameters file we could have the name of the deployment stack so that its easier for deletion
  - Just like we had cleanup scripts these can be written in a similar way


Account Info 

[
    {
      "cloudName": "AzureCloud",
      "homeTenantId": "f4d0fd33-e2f5-47ab-bb12-b31e0102c9ab",
      "id": "aa495c4e-4339-495f-9fc1-56659373ec7a",
      "isDefault": true,
      "managedByTenants": [],
      "name": "Free Trial",
      "state": "Enabled",
      "tenantId": "f4d0fd33-e2f5-47ab-bb12-b31e0102c9ab",
      "user": {
        "name": "jashjain21@outlook.com",
        "type": "user"
      }
    }
  ]


//   COMMANDS TO RUN

az stack group create --name "lambda-api-dev" --resource-group "aks-rg1" --template-file ./main.bicep --parameters ../configurations/dev.json --delete-all --deny-settings-mode none
az stack group delete --name "lambda-api-dev" --resource-group "aks-rg1" --delete-all --yes

Options available -> 
  --deny-settings-mode denyWriteAndDelete // This disallows deletion or modification of resources post creation
  --deny-setttings-apply-to-child-scopes // applies this setting to the child resources created automatically due to creation of resources via stack
  --deny-settings-excluded-actions ''Microsoft.Compute/virtualMachines/write Microsoft.StorageAccounts/delete' // would prevent deletion and editiing of virtual machines once created
  --deny-settings-excluded-principals "Principals mentioned here can come and delete even whern you had denyWriteAndDelete