---
title: Azure Service Bus SDK for Java
description: Reference for Azure Service Bus SDK for Java
ms.date: 07/09/2025
ms.topic: reference
ms.devlang: java
ms.service: azure-service-bus
---
# Service Bus libraries for Java

## Overview

Service Bus provides highly reliable queues and publish/subscribe topics with deep feature capabilities such as 
ordered delivery, sessions, partitioning, scheduling, complex subscriptions, as well as workflow and transaction handling.

Learn more about Service Bus concepts [in the messaging documentation section](https://docs.microsoft.com/azure/service-bus-messaging/). 

For Java developers, Service Bus provides a Microsoft supported native API and Service Bus can also be used with
AMQP 1.0 compliant libraries such as Apache Qpid Proton's JMS provider.

## Libraries for resource management

Create and manage namespaces, topics, queues, subscriptions and rules using Azure Resource Manager.

**Use the Management API in your project:**
\
[Add a dependency](https://maven.apache.org/guides/getting-started/index.html#How_do_I_use_external_dependencies) to your Maven `pom.xml` file to use the management API in your project.  

| Maven Package | Reference | Samples |
|--------------------------------------|---------------------------------------------------------------|---------------------------------------------------------------|
|    [azure-mgmt-servicebus](http://search.maven.org/#search%7Cga%7C1%7Ca%3A%22azure-mgmt-servicebus%22)    |    [API Reference](https://docs.microsoft.com/java/api/com.microsoft.azure.management.servicebus?view=azure-java-stable&preserve-view=true)    |    [Manage Service Bus queues](https://github.com/Azure-Samples/service-bus-java-manage-queue-with-basic-features), [Create and subscribe to Service Bus topics](https://github.com/Azure-Samples/service-bus-java-manage-publish-subscribe-with-basic-features)    | 

```XML
<dependency>
    <groupId>com.microsoft.azure</groupId>
    <artifactId>azure-mgmt-servicebus</artifactId>
    <version>1.38.0</version>
</dependency>
```

> [!div class="nextstepaction"]
> [Explore the Management APIs](/java/api/overview/azure/servicebus/management)

## Libraries for data access

Use data access libraries to send and receive messages from Service Bus queues, topics and subscriptions. You can also use these libraries to manage queues, topics, subscriptions and rules in a given namespace. There are two libraries available that provide these features at the moment.

[Add a dependency](https://maven.apache.org/guides/getting-started/index.html#How_do_I_use_external_dependencies) to your Maven `pom.xml` file to use the client library in your project. Specify the version as desired.

| Maven Package | Reference | Samples | GitHub |
|--------------------------------------|---------------------------------------------------------------|-------------------------------------------------------------------------------|-------|
|    [azure-messaging-servicebus (latest)](http://search.maven.org/#search%7Cga%7C1%7Ca%3A%22azure-messaging-servicebus%22)    |    [API Reference](https://azuresdkdocs.z19.web.core.windows.net/java/azure-messaging-servicebus/latest/index.html)    |    [Samples](https://docs.microsoft.com/samples/azure/azure-sdk-for-java/servicebus-samples/)    | [Source code for azure-messaging-servicebus](https://github.com/Azure/azure-sdk-for-java/tree/main/sdk/servicebus/azure-messaging-servicebus) | 
|    [microsoft-azure-servicebus (legacy)](http://search.maven.org/#search%7Cga%7C1%7Ca%3A%22azure-servicebus%22)    |    [API Reference](https://docs.microsoft.com/java/api/overview/azure/servicebus/client?view=azure-java-stable&preserve-view=true)    |    [Samples](https://github.com/Azure/azure-service-bus/tree/master/samples/Java)    | [Source code for microsoft-azure-servicebus](https://github.com/Azure/azure-sdk-for-java/tree/main/sdk/servicebus/microsoft-azure-servicebus)

### azure-messaging-servicebus

This is the latest SDK for Azure Service Bus for sending and receiving messages available as of December 2020. To manage queues, topics, subscriptions and rules use the `ServiceBusAdministrationClient` in this package. 

If you are using the older `com.microsoft.azure:azure-servicebus` package, please consider upgrading. Read the [migration guide](https://aka.ms/azsdk/java/migrate/sb) at for more details.

Add dependency in your `pom.xml`.

```XML
<dependency>
    <groupId>com.azure</groupId>
    <artifactId>azure-messaging-servicebus</artifactId>
    <version>7.0.0</version>
</dependency>
```

### microsoft-azure-servicebus

This is the older SDK for Azure Service Bus. Please note, the newer package `com.azure:azure-messaging-servicebus` is available as of December 2020. While the older `com.microsoft.azure:azure-servicebus` package will continue to receive critical bug fixes, we strongly encourage you to upgrade. Read the [migration guide](https://aka.ms/azsdk/java/migrate/sb) at for more details.

Add dependency in your `pom.xml`.

```XML
<dependency>
  <groupId>com.microsoft.azure</groupId>
  <artifactId>azure-servicebus</artifactId>
  <version>3.5.1</version>
</dependency>
```

Explore more [sample Java code for Azure Service Bus](https://azure.microsoft.com/resources/samples/?platform=java&term=bus) you can use in your apps.