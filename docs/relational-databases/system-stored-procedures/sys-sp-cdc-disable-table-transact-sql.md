---
description: sys.sp_cdc_disable_table (Transact-SQL)
title: sys. sp_cdc_disable_table (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sp_cdc_disable_table
- sp_cdc_disable_table
- sys.sp_cdc_disable_table_TSQL
- sp_cdc_disable_table_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cdc_disable_table
- sys.sp_cdc_disable_table
- change data capture [SQL Server], disabling tables
ms.assetid: da2156c0-504e-4d76-b9a0-4448becf9bda
author: markingmyname
ms.author: maghan
ms.openlocfilehash: f0819c156cdc3e836028915d89a8d9100eef17c6
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89541130"
---
# <a name="syssp_cdc_disable_table-transact-sql"></a>sys.sp_cdc_disable_table (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  針對目前資料庫中指定的來源資料表和擷取執行個體，停用異動資料擷取。 並非每個 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]版本中都無法異動資料擷取。 如需 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]版本支援的功能清單，請參閱 [SQL Server 2016 版本支援的功能](~/sql-server/editions-and-supported-features-for-sql-server-2016.md)。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sys.sp_cdc_disable_table   
  [ @source_schema = ] 'source_schema' ,   
  [ @source_name = ] 'source_name'  
  [ , [ @capture_instance = ] 'capture_instance' | 'all' ]  
```  
  
## <a name="arguments"></a>引數  
`[ @source_schema = ] 'source\_schema'` 這是包含來源資料表之架構的名稱。 *source_schema* 是 **sysname**，沒有預設值，而且不能是 Null。  
  
 *source_schema* 必須存在於目前的資料庫中。  
  
`[ @source_name = ] 'source\_name'` 這是要停用變更資料捕捉的來源資料表名稱。 *source_name* 是 **sysname**，沒有預設值，而且不能是 Null。  
  
 *source_name* 必須存在於目前的資料庫中。  
  
`[ @capture_instance = ] 'capture\_instance' | 'all'` 這是要針對指定的來源資料表停用的捕獲實例名稱。 *capture_instance* 為 **sysname** ，而且不可以是 Null。  
  
 當指定 ' all ' 時，會停用針對 *source_name* 所定義的所有捕獲實例。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** (成功) 或 **1** (失敗)   
  
## <a name="result-sets"></a>結果集  
 None  
  
## <a name="remarks"></a>備註  
 **sys. sp_cdc_disable_table** 會卸載與指定之來源資料表和 capture 實例相關聯的變更資料捕獲變更資料表和系統函數。 它會從變更資料捕獲系統資料表刪除與指定之 capture 實例相關聯的任何資料列，並將[sys. 資料表](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md)目錄檢視中資料表專案的**is_tracked_by_cdc**資料行設定為0。  
  
## <a name="permissions"></a>權限  
 需要 **db_owner** 固定資料庫角色中的成員資格。  
  
## <a name="examples"></a>範例  
 下列範例會停用 `HumanResources.Employee` 資料表的異動資料擷取。  
  
```  
USE AdventureWorks2012;  
GO  
EXECUTE sys.sp_cdc_disable_table   
    @source_schema = N'HumanResources',   
    @source_name = N'Employee',  
    @capture_instance = N'HumanResources_Employee';  
```  
  
## <a name="see-also"></a>另請參閱  
 [sys. sp_cdc_enable_table &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-table-transact-sql.md)  
  
  
