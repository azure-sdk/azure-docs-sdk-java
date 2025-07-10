---
title: Azure Resources SDK for Java
description: Reference for Azure Resources SDK for Java
ms.date: 07/10/2025
ms.topic: reference
ms.devlang: java
ms.service: azure-resource-manager
---
# Azure Resource Manager libraries for Java

## Overview

Deploy, monitor, and manage resources in groups with [Azure Resource Manager](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview).

## Management API

Use the management API to create resource groups and deploy resources from templates.

[Add a dependency](https://maven.apache.org/guides/getting-started/index.html#How_do_I_use_external_dependencies) to your Maven `pom.xml` file to use the management API in your project.


```XML
<dependency>
    <groupId>com.microsoft.azure</groupId>
    <artifactId>azure-mgmt-resources</artifactId>
    <version>1.3.0</version>
</dependency>
```

## Example

Create a new resource group in the Azure Eastern US region.

```java
ResourceGroup resourceGroup = azure.resourceGroups().define("myResourceGroup")
            .withRegion(Region.US_EAST)
            .create();
```

> [!div class="nextstepaction"]
> [Explore the Management APIs](/java/api/overview/azure/resources/management)

## Samples

[Manage Azure Resource Groups with Java][1] 
[Deploy resources using an ARM template][2]

[1]: https://github.com/Azure-Samples/resources-java-manage-resource-group
[2]: https://github.com/Azure-Samples/resources-java-deploy-using-arm-template

View the [complete list](https://azure.microsoft.com/resources/samples/?platform=java&term=resource) of Azure Resource Manager samples.