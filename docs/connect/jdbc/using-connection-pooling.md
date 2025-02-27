---
title: "Using connection pooling"
description: "Learn how the JDBC Driver for SQL Server provides JDBC compliant interfaces to support connection pooling in Java."
author: David-Engel
ms.author: v-davidengel
ms.date: "08/12/2019"
ms.prod: sql
ms.technology: connectivity
ms.topic: conceptual
---
# Using connection pooling

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

The [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] provides support for Java Platform, Enterprise Edition (Java EE) connection pooling. The JDBC driver implements the JDBC 3.0 required interfaces to enable the driver to participate in any connection-pooling implementation that is provided by middleware vendors and is JDBC 3.0-compliant. Middleware such as Java EE application servers frequently provides compliant connection-pooling facilities. The JDBC driver will participate in pooled connections in these environments.  
  
> [!NOTE]  
> Although the JDBC driver supports Java EE connection pooling, it does not provide its own pooling implementation. The driver relies on third-party Java Application Servers to manage the connections.  
  
## Remarks

The classes for the connection pooling implementation are as follows.  
  
| Class                                                           | Implements                                                    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| --------------------------------------------------------------- | ------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| com.microsoft.sqlserver.jdbc. SQLServerXADataSource             | javax.sql.ConnectionPoolDataSource and javax.sql.XADataSource | We recommend that you use the [SQLServerXADataSource](../../connect/jdbc/reference/sqlserverxadatasource-class.md) class for all your Java EE server needs, because it implements all the JDBC 3.0 pooling and XA interfaces.                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| com.microsoft.sqlserver.jdbc. SQLServerConnectionPoolDataSource | javax.sql.ConnectionPoolDataSource                            | This class is a connection factory that enables the Java EE application server to populate its connection pool with physical connections. If the configuration of your Java EE vendor requires a class that implements javax.sql.ConnectionPoolDataSource, specify the class name as [SQLServerConnectionPoolDataSource](../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md). We generally recommend that you use the [SQLServerXADataSource](../../connect/jdbc/reference/sqlserverxadatasource-class.md) class instead, because it implements both pooling and XA interfaces, and has been verified in more Java EE server configurations. |
  
 JDBC application code should always close connections explicitly to derive the most benefit from pooling. When the application explicitly closes a connection, the pooling implementation can reuse the connection immediately. If the connection is not closed, other applications cannot reuse it. Applications can use the `finally` construct to make sure that pooled connections are closed even if an exception occurs.  
  
> [!NOTE]  
> Not all third-party Java connection pooling libraries implement the above JDBC APIs for connection pooling. Those libraries must implement their own methods to return connections back to their original states when they're returned to the connection pool.  
  
## See also

[Connecting to SQL Server with the JDBC driver](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)  
