This repository provides a common Azure DevOps pipeline template (`importAcrImage.yml`) that simplifies the process of importing image from the ACR. By using this template, you can easily import images from the registry with your Azure DevOps pipelines.


### Parameters used
| Name  | type | Default | Values | Optional/Required | Comments |
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
| templateDisplayName | string | "Import Image From Previous Registry" | | Required | |
| imageRepository | string | | | Required | |
| azureSubscription | string | | | Required | |
| importImage | string | | | Required | |
| sourceImageTag | string | | | Required | |
| targetContainerRegistry | string | | | Required | |
| sourceContainerRegistry | string | | | Required | |
| sourceRepositary | string | | | Required | |
| imageRepositary | string | | | Required | |
| targetRepositary | string | | | Required | |
| servicePrincipalApplicationId | string | | | Required | |
| servicePrincipalClientAuth | string | | | Required | |
 

### Usage

To use this template, follow these steps:

1. Include the `importAcrImage.yml` file in your Azure DevOps repository.

2. In your Azure DevOps pipeline YAML file, add the following code to reference the template:

```yaml
resources:
  repositories:
    - repository: Templates
      type: github
      name: gitHubServiceConnection
      ref: <respective branch name>
      endpoint: 'gitHubServiceConnection'
steps:
- template: importAcrImage.yml@Template 
  parameters:
    azureSubscription: ${{ parameters.azureSubscriptionNameStaging }}
    imageRepository: ${{ parameters.imageRepository }}
    sourceContainerRegistry: ${{ parameters.sourceContainerRegistry }}
    sourceImageTag: 'latest'
    importImage: true
    targetContainerRegistry: ${{ parameters.targetContainerRegistry }}
    templateDisplayName: 'Promote from dev to staging'
```
