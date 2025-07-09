---
title: Azure Event Grid SDK for Java
description: Reference for Azure Event Grid SDK for Java
ms.date: 07/09/2025
ms.topic: reference
ms.devlang: java
ms.service: azure-event-grid
---
# Azure Event Grid libraries for Java

## Overview

Build event-driven applications that listen and react to events from Azure services and custom sources using simple HTTP-based event handling with Azure Event Grid.

[Learn more](/azure/event-grid/overview) about Azure Event Grid and get started with the [Azure Blob storage event tutorial](/azure/storage/blobs/storage-blob-event-quickstart). 

## Libraries for data access

The latest version of the Azure EventGrid libraries is version 4.x.x. Microsoft recommends using version 4.x.x for new applications.

If you cannot update existing applications to version 4.x.x, then Microsoft recommends using version 1.x.x.

### Version 4.x.x

The version 4.x.x client libraries for Java are part of the Azure SDK for Java. The source code for the Azure Key Vault client libraries for Java is available on [GitHub](https://github.com/Azure/azure-sdk-for-java/tree/master/sdk/eventgrid/azure-messaging-eventgrid).

[Add a dependency](https://maven.apache.org/guides/getting-started/index.html#How_do_I_use_external_dependencies) to your Maven `pom.xml` file to use the client library in your project. Specify the version as desired.

| Maven Package | Reference | Samples |
|--------------------------------------|---------------------------------------------------------------|-------------------------------------------------------------------------------|
|    [azure-messaging-eventgrid](https://mvnrepository.com/artifact/com.azure/azure-messaging-eventgrid)    |    [API Reference](https://docs.microsoft.com/java/api/overview/azure/eventgrid/client)    |    [Samples](https://github.com/Azure/azure-sdk-for-java/tree/master/sdk/eventgrid/azure-messaging-eventgrid/src/samples/java)    |


> [!div class="nextstepaction"]
> [Explore the Event Grid Client APIs](/java/api/overview/azure/eventgrid/client)

### Version 1.x.x
The Maven package for the EventGrid legacy SDK is [azure-eventgrid](https://mvnrepository.com/artifact/com.microsoft.azure/azure-eventgrid). 


The source code for the Azure EventGrid client libraries for Java 1.x.x is available on [GitHub](https://github.com/Azure/azure-sdk-for-java/tree/master/sdk/eventgrid/microsoft-azure-eventgrid).

The following code authenticates with Azure and publishes a `List` of  `EventGridEvent` events of a custom type (in this example, `Contoso.Items.ItemsReceived` ) to a topic. The topic key and endpoint address used in the sample can be retrieved from the Azure CLI:

```azurecli-interactive
az eventgrid topic show -g gridResourceGroup -n topicName
az eventgrid topic key list -g gridResourceGroup -n topicName
```

```java
// Create an event grid client.
TopicCredentials topicCredentials = new TopicCredentials(System.getenv("EVENTGRID_TOPIC_KEY"));
EventGridClient client = new EventGridClientImpl(topicCredentials);

// Publish custom events to the EventGrid.
System.out.println("Publish custom events to the EventGrid");
List<EventGridEvent> eventsList = new ArrayList<>();
for (int i = 0; i < 5; i++) {
    eventsList.add(new EventGridEvent(
        UUID.randomUUID().toString(),
        String.format("Door%d", i),
        new ContosoItemReceivedEventData("Contoso Item SKU #1"),
        "Contoso.Items.ItemReceived",
        DateTime.now(),
        "2.0"
    ));
}

String eventGridEndpoint = String.format("https://%s/", new URI(System.getenv("EVENTGRID_TOPIC_ENDPOINT")).getHost());

client.publishEvents(eventGridEndpoint, eventsList);
```

> [!div class="nextstepaction"]
> [Explore the Event Grid Client APIs](/java/api/overview/azure/eventgrid/client)

## Libraries for resource management

Create, update, or delete Event Grid instances, topics, and subscriptions with the Event Grid management SDK.

[Add a dependency](https://maven.apache.org/guides/getting-started/index.html#How_do_I_use_external_dependencies) to your Maven `pom.xml` file to use the client library in your project.

```XML
<dependency>
    <groupId>com.microsoft.azure</groupId>
    <artifactId>azure</artifactId>
    <version>1.16.0</version>
</dependency>
```   

The following example creates an Event Grid subscription, taken from the [EventGrid Java samples](https://github.com/Azure-Samples/event-grid-java-publish-consume-events)

```java
// Create an event grid subscription.
//
System.out.println("Creating an Azure EventGrid Subscription");

EventSubscription eventSubscription = eventGridManager.eventSubscriptions().define(eventSubscriptionName)
    .withScope(eventGridTopic.id())
    .withDestination(new EventHubEventSubscriptionDestination()
        .withResourceId(eventHub.id()))
    .withFilter(new EventSubscriptionFilter()
        .withIsSubjectCaseSensitive(false)
        .withSubjectBeginsWith("")
        .withSubjectEndsWith(""))
    .create();
```

> [!div class="nextstepaction"]
> [Explore the management APIs](/java/api/overview/azure/eventgrid/management)