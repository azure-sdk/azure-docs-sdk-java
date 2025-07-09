---
title: Azure IoT SDK for Java
description: Reference for Azure IoT SDK for Java
ms.date: 07/09/2025
ms.topic: reference
ms.devlang: java
ms.service: iot
---
# Azure IoT libraries for Java

Connect, monitor, and control Internet of Things assets with [Azure IoT Hub](https://docs.microsoft.com/azure/iot-hub/iot-hub-what-is-iot-hub).

To get started with Azure IoT Hub, see [Connect your device to your IoT hub using Java](/azure/iot-hub/iot-hub-java-java-getstarted).

## IoT Service library

Register devices and send messages from the cloud to registered devices using the IoT Service library.

[Add a dependency](https://maven.apache.org/guides/getting-started/index.html#How_do_I_use_external_dependencies) to your Maven `pom.xml` file to use the client library in your project.  

```XML
<dependency>
    <groupId>com.microsoft.azure.sdk.iot</groupId>
    <artifactId>iot-service-client</artifactId>
    <version>1.6.23</version>
</dependency>
```   

## Iot Device library

Send messages to the cloud and receive messages on devices using the IoT Device library.

[Add a dependency](https://maven.apache.org/guides/getting-started/index.html#How_do_I_use_external_dependencies) to your Maven `pom.xml` file to use the client library in your project.  

```XML
<dependency>
    <groupId>com.microsoft.azure.sdk.iot</groupId>
    <artifactId>iot-device-client</artifactId>
    <version>1.3.31</version>
</dependency>
```

> [!div class="nextstepaction"]
> [Explore the Client APIs](/java/api/overview/azure/iot/client)   

## Example

Send a message from Azure IoT Hub to a device.

```java
Message messageToSend = new Message(messageText);
messageToSend.setDeliveryAcknowledgement(DeliveryAcknowledgement.Full);
messageToSend.setMessageId(java.util.UUID.randomUUID().toString());

// set message properties
Map<String, String> propertiesToSend = new HashMap<String, String>();
propertiesToSend.put(messagePropertyKey,messagePropertyKey);
messageToSend.setProperties(propertiesToSend);

CompletableFuture<Void> future = serviceClient.sendAsync(deviceId, messageToSend);
try {
    future.get();
}
catch (ExecutionException e) {
    System.out.println("Exception : " + e.getMessage());
}
```


## Samples

[IoT Device samples](https://github.com/Azure/azure-iot-sdk-java/tree/master/device/iot-device-samples)     
[IoT Service samples](https://github.com/Azure/azure-iot-sdk-java/tree/master/service/iot-service-samples)

Explore more [sample Java code for Azure IoT](https://azure.microsoft.com/resources/samples/?platform=java&term=iot) you can use in your apps.