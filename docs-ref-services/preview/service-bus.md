---
title: Azure Service Bus SDK for Java
description: Reference for Azure Service Bus SDK for Java
ms.date: 07/08/2025
ms.topic: reference
ms.devlang: java
ms.service: azure-service-bus
keywords: Azure, Java, SDK, API, messaging, amqp, qpid, JMS, pubsub, pub-sub, message broker
manager: douge
---
# Service Bus libraries for Java

## Overview

Service Bus is an enterprise-class, transactional messaging platform service that provides highly reliable queues 
and publish/subscribe topics with deep feature capabilities such as ordered delivery, sessions, partitioning, 
scheduling, complex subscriptions, as well as workflow and transaction handling.

The Service Bus feature capabilities are comparable and often exceed those of high-end, on-premises legacy message 
brokers. The Service Bus features are available via standards-based protocols like AMQP 1.0 and HTTPS and all 
protocol gestures are fully documented, allowing for broad interoperability. 

Focusing on highly available and reliable durable messaging, the Service Bus Premium provides competitive throughput 
performance even with substantial local datacenter deployments, but without hardware selection and acquisition 
processes, deployment planning and execution, and endless performance optimization sessions. 

Service Bus Premium is a fully managed offering with dedicated capacity reserved for each tenant that yields 
predictable performance with a simple, capacity-oriented pricing model and at extremely lower overall cost than 
commercial on-premises brokers. For many customers, Service Bus Premium can replace dedicated on-premises messaging 
clusters today, even if the attached workloads do not run in the cloud. 

Learn more about Service Bus concepts [in the messaging documentation section](https://docs.microsoft.com/azure/service-bus-messaging/) 

For Java developers, Service Bus provides a Microsoft supported native API and Service Bus can also be used with
AMQP 1.0 compliant libraries such as Apache Qpid Proton's JMS provider.

## Client library

The official Service Bus client is available in [source code form on GitHub](https://github.com/Azure/azure-sdk-for-java/tree/master/sdk/servicebus/) and
binaries and packaged sources [are available on Maven Central](http://search.maven.org/#search%7Cga%7C1%7Ca%3A%22azure-servicebus%22).

**The [sample code repository](https://github.com/Azure/azure-service-bus/blob/master/samples/Java/) contains samples for:**
* How to use the [QueueClient](https://github.com/Azure/azure-service-bus/blob/master/samples/Java/azure-servicebus/QueuesGettingStarted/src/main/java/com/microsoft/azure/servicebus/samples/queuesgettingstarted/QueuesGettingStarted.java)
* How to use the [TopicClient and SubscriptionClient](https://github.com/Azure/azure-service-bus/tree/master/samples/Java/azure-servicebus/TopicsGettingStarted/src/main/java/com/microsoft/azure/servicebus/samples/topicsgettingstarted)

[Add a dependency](https://maven.apache.org/guides/getting-started/index.html#How_do_I_use_external_dependencies) to your Maven `pom.xml` file to use the client library in your project. Specify the version as desired.

```XML
<dependency>
    <groupId>com.microsoft.azure</groupId>
    <artifactId>azure-servicebus</artifactId>
    <version>1.0.0</version>
</dependency>
```

```java
public class BasicSendReceiveWithQueueClient {
    // Connection String for the namespace can be obtained from the Azure portal under the
    // 'Shared Access policies' section.
    private static final String connectionString = "{connection string}";
    private static final String queueName = "{queue name}";
    private static IQueueClient queueClient;
    private static int totalSend = 100;
    private static int totalReceived = 0;

    public static void main(String[] args) throws Exception {

        Log.log("Starting BasicSendReceiveWithQueueClient sample");

        // create client
        Log.log("Create queue client.");
        queueClient = new QueueClient(new ConnectionStringBuilder(connectionString, queueName), ReceiveMode.PeekLock);

        // send and receive
        queueClient.registerMessageHandler(new MessageHandler(queueClient), new MessageHandlerOptions(1, false, Duration.ofMinutes(1)));
        for (int i = 0; i < totalSend; i++) {
            int j = i;
            Log.log("Sending message #%d.", j);
            queueClient.sendAsync(new Message("" + i)).thenRunAsync(() -> { Log.log("Sent message #%d.", j);});
        }

        while(totalReceived != totalSend) {
            Thread.sleep(1000);
        }

        Log.log("Received all messages, exiting the sample.");
        Log.log("Closing queue client.");
        queueClient.close();
    }

    static class MessageHandler implements IMessageHandler {
        private IQueueClient client;

        public MessageHandler(IQueueClient client) {
            this.client = client;
        }

        @Override
        public CompletableFuture<Void> onMessageAsync(IMessage iMessage) {
            Log.log("Received message with sq#: %d and lock token: %s.", iMessage.getSequenceNumber(), iMessage.getLockToken());
            return this.client.completeAsync(iMessage.getLockToken()).thenRunAsync(() -> {
                Log.log("Completed message sq#: %d and locktoken: %s", iMessage.getSequenceNumber(), iMessage.getLockToken());
                totalReceived++;
            });
        }

        @Override
        public void notifyException(Throwable throwable, ExceptionPhase exceptionPhase) {
            Log.log(exceptionPhase + "-" + throwable.getMessage());
        }
    }
}
```

> [!div class="nextstepaction"]
> [Explore the Client APIs](/java/api/overview/azure/servicebus/client)
> [Find more examples here (See also above for more details)](https://github.com/Azure/azure-service-bus/blob/master/samples/Java/)

## Management API

Create and manage namespaces, topics, queues, and subscriptions with the management API.

**Please find some examples here:**
* [Manage Service Bus queues](https://github.com/Azure-Samples/service-bus-java-manage-queue-with-basic-features)
* [Create and subscribe to Service Bus topics](https://github.com/Azure-Samples/service-bus-java-manage-publish-subscribe-with-basic-features)

**Use the Management API in your project:**
\
[Add a dependency](https://maven.apache.org/guides/getting-started/index.html#How_do_I_use_external_dependencies) to your Maven `pom.xml` file to use the management API in your project.  

```XML
<dependency>
    <groupId>com.microsoft.azure</groupId>
    <artifactId>azure-mgmt-servicebus</artifactId>
    <version>1.3.0</version>
</dependency>
```

> [!div class="nextstepaction"]
> [Explore the Management APIs](/java/api/overview/azure/servicebus/management)

Explore more [sample Java code for Azure Service Bus](https://azure.microsoft.com/resources/samples/?platform=java&term=bus) you can use in your apps.