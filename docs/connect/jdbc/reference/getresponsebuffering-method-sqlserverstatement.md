---
title: "getResponseBuffering Method (SQLServerStatement)"
description: "getResponseBuffering Method (SQLServerStatement)"
author: David-Engel
ms.author: v-davidengel
ms.date: "01/19/2017"
ms.prod: sql
ms.technology: connectivity
ms.topic: reference
apilocation: "SQLServerStatement.getResponseBuffering()"
apiname: "SQLServerStatement.getResponseBuffering()"
apitype: "Assembly"
---
# getResponseBuffering Method (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retrieves the response buffering mode for this [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) object.  
  
## Syntax  
  
```  
  
public final java.lang.String getResponseBuffering()  
```  
  
## Return Value  
 A **String** that contains a lower-case **full** or **adaptive**.  
  
## Remarks  
 **adaptive** specifies buffering the minimum possible data when necessary.  
  
 **full** specifies reading the entire result from the server at run time.  
  
 **adaptive** is the default value in JDBC Driver version 2.0 and 3.0. **full** was the default prior to JDBC Driver version 2.0.  
  
 For more information about using the response buffering mode, see [Using Adaptive Buffering](../../../connect/jdbc/using-adaptive-buffering.md).  
  
## See Also  
 [setResponseBuffering Method &#40;SQLServerStatement&#41;](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)   
 [SQLServerStatement Members](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement Class](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
