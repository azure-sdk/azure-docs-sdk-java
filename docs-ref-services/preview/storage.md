---
title: Azure Storage SDK for Java
description: Reference for Azure Storage SDK for Java
ms.date: 07/08/2025
ms.topic: reference
ms.devlang: java
ms.service: storage
---
# Azure Storage libraries for Java

The Azure Storage libraries for Java provide classes for working with data in your your Azure storage account, and with the storage account itself. For more information about Azure Storage, see [Introduction to Azure Storage](/azure/storage/storage-introduction).

## Client library for data access

The Azure Storage client library for Java supports Blob storage, Queue storage, Azure Files, and Azure Data Lake Storage Gen2 (preview library).

### Add the package to your project

Add the following dependencies to your Maven `pom.xml` file as appropriate:

```xml
<dependency>
    <groupId>com.azure</groupId>
    <artifactId>azure-storage-blob</artifactId>
    <version>12.4.0</version>
</dependency>

<dependency>
  <groupId>com.azure</groupId>
  <artifactId>azure-storage-queue</artifactId>
  <version>12.3.0</version>
</dependency>

<dependency>
  <groupId>com.azure</groupId>
  <artifactId>azure-storage-file-share</artifactId>
  <version>12.2.0</version>
</dependency>

<dependency>
  <groupId>com.azure</groupId>
  <artifactId>azure-storage-file-datalake</artifactId>
  <version>12.0.0-preview.6</version>
</dependency>
```

For more information about adding a dependency in Java, see [Add a dependency](https://maven.apache.org/guides/getting-started/index.html#How_do_I_use_external_dependencies).

### Example usage

The following example creates a storage container and uploads a local file to the storage container.

```java
String yourSasToken = "<insert-your-sas-token>";
/* Create a new BlobServiceClient with a SAS Token */
BlobServiceClient blobServiceClient = new BlobServiceClientBuilder()
    .endpoint("https://your-storage-account-url.storage.windows.net")
    .sasToken(yourSasToken)
    .buildClient();

/* Create a new container client */
try {
    containerClient = blobServiceClient.createBlobContainer("my-container-name");
} catch (BlobStorageException ex) {
    // The container may already exist, so don't throw an error
    if (!ex.getErrorCode().equals(BlobErrorCode.CONTAINER_ALREADY_EXISTS)) {
        throw ex;
    }
}

/* Upload the file to the container */
BlobClient blobClient = containerClient.getBlobClient("my-remote-file.jpg");
blobClient.uploadFromFile("my-local-file.jpg");
```

For more examples, review the [Client Library README](https://github.com/Azure/azure-sdk-for-java/blob/azure-storage-blob_12.0.0/sdk/storage/azure-storage-blob/README.md).

### Available packages

 The following table describes the recommended versions of the storage client library for Java.

| Library version | Supported services | Maven | Reference / Javadoc | Source, Readme, Examples |
|----------------------|------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Version 12 | Blob, Queue, File, and Data Lake | [Blob](https://search.maven.org/artifact/com.azure/azure-storage-blob/)<br />[Queue](https://search.maven.org/artifact/com.azure/azure-storage-queue/)<br />[File](https://search.maven.org/artifact/com.azure/azure-storage-file-share/)<br />[Data Lake](https://search.maven.org/artifact/com.azure/azure-storage-file-datalake/) | [Blob](https://azuresdkdocs.z19.web.core.windows.net/java/azure-storage-blob/latest/index.html)<br/>[Queue](hhttps://azuresdkdocs.z19.web.core.windows.net/java/azure-storage-queue/latest/index.html)<br />[File](https://azuresdkdocs.z19.web.core.windows.net/java/azure-storage-file-share/latest/index.html)<br />[Data Lake](https://azuresdkdocs.z19.web.core.windows.net/java/azure-storage-file-datalake/latest/index.html)  | [Blob](https://github.com/Azure/azure-sdk-for-java/tree/azure-storage-blob_12.4.0/sdk/storage/azure-storage-blob) ([Quickstart](/azure/storage/blobs/storage-quickstart-blobs-java))<br />[Queue](https://github.com/Azure/azure-sdk-for-java/tree/azure-storage-blob_12.3.0/sdk/storage/azure-storage-queue)<br />[File](https://github.com/Azure/azure-sdk-for-java/tree/azure-storage-file-share_12.2.0/sdk/storage/azure-storage-queue)<br />[Data Lake](https://github.com/Azure/azure-sdk-for-java/tree/azure-storage-blob_12.0.0/sdk/storage/azure-storage-file-datalake) |
| Version 8 | Blob, Queue, File, and Table | [All services](https://mvnrepository.com/artifact/com.microsoft.azure/azure-storage) | [Version 8 reference](https://docs.microsoft.com/java/api/overview/azure/storage/client?view=azure-java-stable) | [All services](https://github.com/azure/azure-storage-java/tree/legacy-master) ([Quickstart](/azure/storage/blobs/storage-quickstart-blobs-java-legacy)) |

Refer to the [Azure SDK Releases page](https://azure.github.io/azure-sdk/) for details on how to install and use the preview packages.

## Client library for resource management

Use the Azure Storage resource provider to manage storage accounts, account keys, access tiers, and more. To use the resource provider library, [add a dependency](https://maven.apache.org/guides/getting-started/index.html#How_do_I_use_external_dependencies) to your Maven `pom.xml` file. The latest version of the resource provider library is available on [Maven](https://mvnrepository.com/artifact/com.microsoft.azure/azure-mgmt-storage).  

For more information about the resource provider library, see the [Management](/java/api/overview/azure/storage/management) reference. The source code for the resource provider library is available in the [Azure Java SDK repository](https://github.com/Azure/azure-sdk-for-java/tree/master/storage/resource-manager).

The following example creates a new storage account in your subscription and retrieves its access keys.

```java
StorageAccount storageAccount = azure.storageAccounts().define(storageAccountName)
        .withRegion(Region.US_EAST)
        .withNewResourceGroup(rgName)
        .create();

// get a list of storage account keys related to the account
List<StorageAccountKey> storageAccountKeys = storageAccount.getKeys();
for(StorageAccountKey key : storageAccountKeys)    {
    System.out.println("Key name: " + key.keyName() + " with value "+ key.value());
}
```