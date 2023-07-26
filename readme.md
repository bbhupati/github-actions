groupId=$(az group show \
  --name githuactions \
  --query id --output tsv)

az ad sp create-for-rbac \
  --scope $groupId \
  --role Contributor \
  --sdk-auth

registryId=$(az acr show \
  --name bhupathigithu \
  --resource-group githuactions \
  --query id --output tsv)

az role assignment create \
  --assignee "48033113-8f19-4f9a-9948-d510833739d3" \
  --scope $registryId \
  --role AcrPush


{
  "clientId": "48033113-8f19-4f9a-9948-d510833739d3",
  "clientSecret": "ELa8Q~pJYrg7UAMm8etSe5iTphDz9Y7ZJD5xDdAo",
  "subscriptionId": "5bb83c93-b635-45a4-b4b5-f6a6edc9f6fd",
  "tenantId": "0170852e-b5ea-4028-93fb-631b8b09bf11",
  "activeDirectoryEndpointUrl": "https://login.microsoftonline.com",
  "resourceManagerEndpointUrl": "https://management.azure.com/",
  "activeDirectoryGraphResourceId": "https://graph.windows.net/",
  "sqlManagementEndpointUrl": "https://management.core.windows.net:8443/",
  "galleryEndpointUrl": "https://gallery.azure.com/",
  "managementEndpointUrl": "https://management.core.windows.net/"
}