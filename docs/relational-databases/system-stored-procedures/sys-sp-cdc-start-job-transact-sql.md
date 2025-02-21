---
title: "sys.sp_cdc_start_job (Transact-SQL)"
description: "sys.sp_cdc_start_job (Transact-SQL)"
author: markingmyname
ms.author: maghan
ms.date: "03/14/2017"
ms.service: sql
ms.subservice: system-objects
ms.topic: "reference"
f1_keywords:
  - "sp_cdc_start_job"
  - "sp_cdc_start_job_TSQL"
  - "sys.sp_cdc_start_job_TSQL"
  - "sys.sp_cdc_start_job"
helpviewer_keywords:
  - "sp_cdc_start_job"
dev_langs:
  - "TSQL"
---
# sys.sp_cdc_start_job (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Starts a change data capture cleanup or capture job for the current database.  
  
 :::image type="icon" source="../../includes/media/topic-link-icon.svg" border="false"::: [Transact-SQL syntax conventions](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## Syntax  
  
```  
  
sys.sp_cdc_start_job [ [ @job_type = ] 'job_type' ]  
```  
  
## Arguments  
`[ [ @job_type = ] 'job_type' ]`
 Type of job to add. *job_type* is **nvarchar(20)** with a default of **capture**. Valid inputs are **capture** and **cleanup**.  
  
## Return Code Values  
 **0** (success) or **1** (failure)  
  
## Result Sets  
 None  
  
## Remarks  
 sys.sp_cdc_start_job can be used by an administrator to explicitly start either the capture job or the cleanup job.  
  
## Permissions  
 Requires membership in the db_owner fixed database role.  
  
## Examples  
  
### A. Starting a capture job  
 The following example starts the capture job for the `AdventureWorks2012` database. Specifying a value for *job_type* is not required because the default job type is **capture**.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sys.sp_cdc_start_job;  
GO  
```  
  
### B. Starting a cleanup job  
 The following example starts a cleanup job for the `AdventureWorks2012` database.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sys.sp_cdc_start_job @job_type = N'cleanup';  
```  
  
## See Also  
 [dbo.cdc_jobs &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md)   
 [sys.sp_cdc_stop_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-stop-job-transact-sql.md)  
  
  
