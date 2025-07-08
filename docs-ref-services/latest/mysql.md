---
title: Azure MySQL SDK for Java
description: Reference for Azure MySQL SDK for Java
ms.date: 07/08/2025
ms.topic: reference
ms.devlang: java
ms.service: mysql
---
# Azure Database for MySQL libraries for Java

## Overview

[Azure Database for MySQL](/azure/sql-database/sql-database-technical-overview) is a relational database service based on the open source [MySQL](https://www.mysql.com/) Server engine. 

To get started with Azure Database for MySQL, see [Use Java to connect and query data](/azure/mysql/connect-java).

## Client JBDC driver

Connect to Azure Database for MySQL from your applications using the open-source [MySQL JDBC driver](https://dev.mysql.com/downloads/connector/j/). You can use the [Java JDBC API](https://docs.oracle.com/javase/8/docs/technotes/guides/jdbc/) to directly connect to the database or use data access frameworks that interact with the database through JDBC such as [Hibernate](http://hibernate.org/).

[Add a dependency](https://maven.apache.org/guides/getting-started/index.html#How_do_I_use_external_dependencies) to your Maven `pom.xml` file to use the client JDBC driver in your project.  

```XML
<dependency>
    <groupId>mysql</groupId>
    <artifactId>mysql-connector-java</artifactId>
    <version>5.1.42</version>
</dependency>
```   

## Example

Connect to Azure Database for MySQL using JDBC and select all records in the sales table. You can get the JDBC connection string for the database from the Azure Portal.

```java
String url = String.format("jdbc:mysql://[your-database-hostname].mysql.database.azure.com:3306/[your-database-name]?verifyServerCertificate=true&useSSL=true&requireSSL=[true|false]&user=[your-username]&password=[your-password]");
try {
    Connection conn = DriverManager.getConnection(url, "USERNAME", "PASSWORD");
    String selectSql = "SELECT * FROM SALES";
    Statement statement = conn.createStatement();
    ResultSet resultSet = statement.executeQuery(selectSql);
}
```

## Samples

[Build a Java and MySQL web app](/azure/app-service-web/app-service-web-tutorial-java-mysql)   
[Design a MySQL database using the Azure CLI](/azure/mysql/tutorial-design-database-using-cli)   

Explore more [sample Java code for Azure Database for MySQL](https://azure.microsoft.com/resources/samples/?platform=java&term=mysql) you can use in your apps.