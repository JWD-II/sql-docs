---
title: "sp_helptrigger (Transact-SQL)"
description: "sp_helptrigger (Transact-SQL)"
author: markingmyname
ms.author: maghan
ms.date: "03/14/2017"
ms.service: sql
ms.subservice: system-objects
ms.topic: "reference"
f1_keywords:
  - "sp_helptrigger"
  - "sp_helptrigger_TSQL"
helpviewer_keywords:
  - "sp_helptrigger"
dev_langs:
  - "TSQL"
monikerRange: "=azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current"
---
# sp_helptrigger (Transact-SQL)
[!INCLUDE [SQL Server Azure SQL Database Azure SQL Managed Instance](../../includes/applies-to-version/sql-asdb-asdbmi.md)]

  Returns the type or types of DML triggers defined on the specified table for the current database. sp_helptrigger cannot be used with DDL triggers. Query the [system stored procedures](../../relational-databases/system-catalog-views/sys-triggers-transact-sql.md) catalog view instead.  
  
 :::image type="icon" source="../../includes/media/topic-link-icon.svg" border="false"::: [Transact-SQL syntax conventions](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## Syntax  
  
```  
  
sp_helptrigger [ @tabname = ] 'table'   
     [ , [ @triggertype = ] 'type' ]  
```  
  
## Arguments  
`[ @tabname = ] 'table'`
 Is the name of the table in the current database for which to return trigger information. *table* is **nvarchar(776)**, with no default.  
  
`[ @triggertype = ] 'type'`
 Is the type of DML trigger to return information about. *type* is **char(6)**, with a default of NULL, and can be one of these values.  
  
|Value|Description|  
|-----------|-----------------|  
|**DELETE**|Returns DELETE trigger information.|  
|**INSERT**|Returns INSERT trigger information.|  
|**UPDATE**|Returns UPDATE trigger information.|  
  
## Return Code Values  
 0 (success) or 1 (failure)  
  
## Result Sets  
 The following table shows the information that is contained in the result set.  
  
|Column name|Data type|Description|  
|-----------------|---------------|-----------------|  
|**trigger_name**|**sysname**|Name of the trigger.|  
|**trigger_owner**|**sysname**|Name of the owner of the table on which the trigger is defined.|  
|**isupdate**|**int**|1=UPDATE trigger<br /><br /> 0=Not an UPDATE trigger|  
|**isdelete**|**int**|1=DELETE trigger<br /><br /> 0=Not a DELETE trigger|  
|**isinsert**|**int**|1=INSERT trigger<br /><br /> 0=Not an INSERT trigger|  
|**isafter**|**int**|1=AFTER trigger<br /><br /> 0=Not an AFTER trigger|  
|**isinsteadof**|**int**|1=INSTEAD OF trigger<br /><br /> 0=Not an INSTEAD OF trigger|  
|**trigger_schema**|**sysname**|Name of the schema to which the trigger belongs.|  
  
## Permissions  
 Requires [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md) permission on the table.  
  
## Examples  
 The following example executes `sp_helptrigger` to produce information about the trigger(s) on the `Person.Person` table.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_helptrigger 'Person.Person';  
```  
  
## See Also  
 [Database Engine Stored Procedures &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [ALTER TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/alter-trigger-transact-sql.md)   
 [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)   
 [DROP TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/drop-trigger-transact-sql.md)   
 [System Stored Procedures &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
