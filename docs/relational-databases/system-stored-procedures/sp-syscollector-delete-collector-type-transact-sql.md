---
title: "sp_syscollector_delete_collector_type (Transact-SQL)"
description: "sp_syscollector_delete_collector_type (Transact-SQL)"
author: markingmyname
ms.author: maghan
ms.date: "03/14/2017"
ms.service: sql
ms.subservice: system-objects
ms.topic: "reference"
f1_keywords:
  - "sp_syscollector_delete_collector_type"
  - "sp_syscollector_delete_collector_type_TSQL"
helpviewer_keywords:
  - "data collector [SQL Server], stored procedures"
  - "sp_syscollector_delete_collector_type"
dev_langs:
  - "TSQL"
---
# sp_syscollector_delete_collector_type (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Deletes the definition of a collector type.  
  
 :::image type="icon" source="../../includes/media/topic-link-icon.svg" border="false"::: [Transact-SQL syntax conventions](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## Syntax  
  
```  
  
sp_syscollector_delete_collector_type [[ @collector_type_uid = ] 'collector_type_uid' ]  
          , [[ @name = ] 'name' ]  
```  
  
## Arguments  
`[ @collector_type_uid = ] 'collector_type_uid'`
 Is the GUID for the collector type. *collector_type_uid* is **uniqueidentifier** and must have a value if *name* is NULL.  
  
`[ @name = ] 'name'`
 Is the name of the collector type. *name* is **sysname** and must have a value if *collector_type_uid* is NULL.  
  
## Return Code Values  
 **0** (success) or **1** (failure)  
  
## Remarks  
 Either *collector_type_uid* or *name* must have a value, both cannot be NULL.  
  
 This procedure will throw an error if collection items of this collection type exist.  
  
## Permissions  
 Requires membership in the **dc_admin** (with EXECUTE permission) fixed database role to execute this procedure.  
  
## Example  
 This example deletes the Generic T-SQL Query collector type.  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_delete_collector_type @collector_type_uid = '302E93D1-3424-4be7-AA8E-84813ECF2419';  
```  
  
## See Also  
 [System Stored Procedures &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Data Collection](../../relational-databases/data-collection/data-collection.md)  
  
  
