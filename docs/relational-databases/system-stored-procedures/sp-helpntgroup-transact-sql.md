---
description: sp_helpntgroup (Transact-SQL)
title: sp_helpntgroup (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpntgroup
- sp_helpntgroup_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpntgroup
ms.assetid: 02b4f7c1-480a-436c-8bae-7a2488be45d2
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 1a88caee8d332a4802f4281360f93392ae29aa2c
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89535163"
---
# <a name="sp_helpntgroup-transact-sql"></a>sp_helpntgroup (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  報告目前資料庫中 Windows 群組和帳戶的相關資訊。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_helpntgroup [ [ @ntname= ] 'name' ]   
```  
  
## <a name="arguments"></a>引數  
`[ @ntname = ] 'name'` 這是 Windows 群組的名稱。 *名稱* 是 **sysname**，預設值是 Null。 *名稱* 必須是有效的 Windows 群組，而且具有目前資料庫的存取權。 如果未指定 *name* ，則輸出中會包含目前資料庫存取權的所有 Windows 群組。  
  
## <a name="return-code-values"></a>傳回碼值  
 0 (成功) 或 1 (失敗)  
  
## <a name="result-sets"></a>結果集  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**NTGroupName**|**sysname**|Windows 群組的名稱。|  
|**NTGroupId**|**smallint**|群組識別碼 (ID)。|  
|**SID**|**varbinary(85)**|**.Ntgroupname**的安全識別碼 (SID) 。|  
|**HasDbAccess**|**int**|1 = Windows 群組具有資料庫的存取權限。|  
  
## <a name="remarks"></a>備註  
 若要查看 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 目前資料庫中的角色清單，請使用 **sp_helprole**。  
  
## <a name="permissions"></a>權限  
 需要 **public** 角色的成員資格。  
  
## <a name="examples"></a>範例  
 下列範例會印出具有目前資料庫存取權的 Windows 群組清單。  
  
```  
EXEC sp_helpntgroup;  
```  
  
## <a name="see-also"></a>另請參閱  
 [安全性預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_grantdbaccess &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantdbaccess-transact-sql.md)   
 [sp_helprole &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-helprole-transact-sql.md)   
 [sp_revokedbaccess &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revokedbaccess-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
