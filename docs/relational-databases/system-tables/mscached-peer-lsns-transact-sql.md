---
description: MScached_peer_lsns (Transact-SQL)
title: MScached_peer_lsns (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MScached_peer_lsns_TSQL
- MScached_peer_lsns
dev_langs:
- TSQL
helpviewer_keywords:
- MScached_peer_lsns system table
ms.assetid: f8b6089a-0230-45f9-8c34-9fe0d2a3a74e
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 23d4339d7a907cd755934df4803e38f5ba769b5e
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89550994"
---
# <a name="mscached_peer_lsns-transact-sql"></a>MScached_peer_lsns (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  **MScached_peer_lsns**資料表是用來追蹤交易記錄中的 LSN 值，這些值可用來判斷哪些命令要在點對點複寫中傳回給指定的訂閱者。 這份資料表儲存在散發資料庫中。  
  
## <a name="definition"></a>定義  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**agent_id**|**int**|散發代理程式的識別碼。|  
|**鼻祖**|**sysname**|原始發行者名稱。|  
|**originator_db**|**sysname**|原始發行集資料庫的名稱。|  
|**originator_publication_id**|**int**|識別原始發行集。|  
|**originator_db_version**|**int**|識別來源資料庫的版本號碼。|  
|**originator_lsn**|**varbinary(16)**|原始交易的 LSN。|  
  
## <a name="remarks"></a>備註  
 LSN 值只會在插入之後立即使用，它們在系統中並沒有長久的意義。  
  
## <a name="see-also"></a>另請參閱  
 [複寫資料表 &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [複寫檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
