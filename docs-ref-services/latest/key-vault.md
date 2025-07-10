---
title: Azure Key Vault SDK for Java
description: Reference for Azure Key Vault SDK for Java
ms.date: 07/10/2025
ms.topic: reference
ms.devlang: java
ms.service: keyvault
---
# Azure Key Vault libraries for Java

The Azure Key Vault client libraries for Java offer a convenient interface for making calls to Azure Key Vault. For more information about Azure Key Vault, see [Introduction to Azure Key Vault](/azure/key-vault/general/overview).

## Libraries for data access

The latest version of the Azure Key Vault libraries is version 4.x.x. Microsoft recommends using version 4.x.x for new applications.

If you cannot update existing applications to version 4.x.x, then Microsoft recommends using version 1.x.x.

### Version 4.x.x

The version 4.x.x client libraries for Java are part of the Azure SDK for Java. The source code for the Azure Key Vault client libraries for Java is available on [GitHub](https://github.com/Azure/azure-sdk-for-java/tree/master/sdk/keyvault).

Use the following version 4.x.x libraries to work with certificates, keys, and secrets:

| Library | Reference | Package | Source |
|----------------------------------------|-------------------------------------------------------------|-----------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------|
|    azure-security-keyvault-certificates   |    [Reference](https://azuresdkdocs.z19.web.core.windows.net/java/azure-security-keyvault-certificates/latest/index.html)    |    [Maven](https://search.maven.org/artifact/com.azure/azure-security-keyvault-certificates)    |    [GitHub](https://github.com/Azure/azure-sdk-for-java/tree/master/sdk/keyvault/azure-security-keyvault-certificates) |
|    azure-security-keyvault-keys    |    [Reference](https://azuresdkdocs.z19.web.core.windows.net/java/azure-security-keyvault-keys/latest/index.html)    |    [Maven](https://search.maven.org/artifact/com.azure/azure-security-keyvault-keys)    |    [GitHub](https://github.com/Azure/azure-sdk-for-java/tree/master/sdk/keyvault/azure-security-keyvault-keys)    |
|    azure-security-keyvault-secrets    |    [Reference](https://azuresdkdocs.z19.web.core.windows.net/java/azure-security-keyvault-secrets/latest/index.html)    |    [Maven](https://search.maven.org/artifact/com.azure/azure-security-keyvault-secrets)    |    [GitHub](https://github.com/Azure/azure-sdk-for-java/tree/master/sdk/keyvault/azure-security-keyvault-secrets)    |

### Version 1.x.x

The source code for the Azure Key Vault client libraries for Java is available on [GitHub](https://github.com/Azure/azure-sdk-for-java/tree/master/sdk/keyvault).

Use the following version 1.x.x libraries to work with certificates, keys, and secrets:

| Library | Reference | Package | Source |
|--------------------------------------|---------------------------------------------------------------|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------|
|    microsoft-azure-keyvault-core    |    [Reference](/java/api/com.microsoft.azure.keyvault.core)    |    [Maven](https://mvnrepository.com/artifact/com.microsoft.azure/azure-keyvault-core)    |    [GitHub](https://github.com/Azure/azure-sdk-for-java/tree/master/sdk/keyvault/microsoft-azure-keyvault-core)    |
|    microsoft-azure-keyvault-cryptography    |    [Reference](/java/api/com.microsoft.azure.keyvault.cryptography)    |    [Maven](https://mvnrepository.com/artifact/com.microsoft.azure/azure-keyvault-cryptography)    |    [GitHub](https://github.com/Azure/azure-sdk-for-java/tree/master/sdk/keyvault/microsoft-azure-keyvault-cryptography)    |
|    microsoft-azure-keyvault-extensions   |    [Reference](/java/api/com.microsoft.azure.keyvault.extensions)    |    [Maven](https://mvnrepository.com/artifact/com.microsoft.azure/azure-keyvault-extensions)    |    [GitHub](https://github.com/Azure/azure-sdk-for-java/tree/master/sdk/keyvault/microsoft-azure-keyvault-extensions) |
|    microsoft-azure-keyvault-webkey    |    [Reference](/java/api/com.microsoft.azure.keyvault.webkey)    |    [Maven](https://mvnrepository.com/artifact/com.microsoft.azure/azure-keyvault-webkey)    |    [GitHub](https://github.com/Azure/azure-sdk-for-java/tree/master/sdk/keyvault/microsoft-azure-keyvault-webkey)    |
|    microsoft-azure-keyvault   |    [Reference](/java/api/com.microsoft.azure.keyvault)    |    [Maven](https://mvnrepository.com/artifact/com.microsoft.azure/azure-keyvault)    |    [GitHub](https://github.com/Azure/azure-sdk-for-java/tree/master/sdk/keyvault/microsoft-azure-keyvault) |

## Libraries for resource management

Use the following library to work with the Azure Key Vault resource provider:

|    Library    |    Reference    |    Package    |    Source    |
|------------------------------------------|-------------------------------------------------------------------|-----------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------|
|    azure-resourcemanager-keyvault    |    [Reference](/java/api/com.azure.resourcemanager.keyvault)    |    [Maven](https://mvnrepository.com/artifact/com.azure.resourcemanager/azure-resourcemanager-keyvault)    |    [GitHub](https://github.com/Azure/azure-sdk-for-java/tree/main/sdk/resourcemanager/azure-resourcemanager-keyvault)    |