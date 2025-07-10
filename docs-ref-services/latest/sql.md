---
title: Azure SQL SDK for Java
description: Reference for Azure SQL SDK for Java
ms.date: 07/10/2025
ms.topic: reference
ms.devlang: java
ms.service: mysql
---
# Azure SQL Database libraries for Java

## Overview

[Azure SQL Database](/azure/sql-database/sql-database-technical-overview) is a relational database service using the Microsoft SQL Server engine that supports table, JSON, spatial, and XML data. 

To get started with Azure SQL Database, see [Azure SQL Database: Use Java to connect and query data](/azure/sql-database/sql-database-connect-query-java).

## Client JDBC driver

Connect to Azure SQL Database from your applications using the [SQL Database JDBC driver](/sql/connect/jdbc/microsoft-jdbc-driver-for-sql-server). You can use the [Java JDBC API](https://docs.oracle.com/javase/8/docs/technotes/guides/jdbc/) to directly connect with the database or use data access frameworks that interact with the database through JDBC such as [Hibernate](http://hibernate.org/).

[Add a dependency](https://maven.apache.org/guides/getting-started/index.html#How_do_I_use_external_dependencies) to your Maven `pom.xml` file to use the client JDBC driver in your project.


```XML
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>6.2.1.jre8</version>
</dependency>
```   

### Example

Connect to SQL database and select all records in a table using JDBC.

```java
String connectionString = "jdbc:sqlserver://fabrikam.database.windows.net:1433;database=fiber;user=raisa;password=testpass;encrypt=true;hostNameInCertificate=*.database.windows.net;loginTimeout=30;";
try {
    Connection conn = DriverManager.getConnection(connectionString);
    Statement statement = conn.createStatement();
    ResultSet resultSet = statement.executeQuery("SELECT * FROM SALES");
}  
```

## Resource Management

Create and manage Azure SQL Database resources in your subscription with the Java resource management libraries.   

[Add a dependency](https://maven.apache.org/guides/getting-started/index.html#How_do_I_use_external_dependencies) to your Maven `pom.xml` file to use the resource management libraries in your project.

```XML
<dependency>
   <groupId>com.azure.resourcemanager</groupId>
   <artifactId>azure-resourcemanager</artifactId>
   <version>2.1.0</version>
</dependency>
```

For detailed information on how to use the Java resource management libraries, please refer to [this doc](https://aka.ms/azsdk/java/mgmt)

> [!div class="nextstepaction"]
> [Explore the Management APIs](/java/api/overview/azure/sql/management)

### Example

Create a SQL Database resource and restrict access to a range of IP addresses using a firewall rule.

```java
SqlServer server = azureResourceManager.sqlServers().define(sqlDbName)
        .withRegion(Region.US_EAST)
        .withNewResourceGroup(resourceGroupName)
        .withAdministratorLogin(adminLogin)
        .withAdministratorPassword(adminPass)
        .defineFirewallRule(firewallRuleName)
        .withIpAddressRange("172.16.0.0", "172.31.255.255")
        .attach()
        .create();
```

## Samples

[!INCLUDE [java-sql-samples](../../docs-ref-conceptual/includes/sql.md)]

Explore more [sample Java code for Azure SQL Database](https://azure.microsoft.com/resources/samples/?platform=java&term=SQL) you can use in your apps.