---
description: sp_trace_setstatus (Transact-SQL)
title: sp_trace_setstatus (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_trace_setstatus_TSQL
- sp_trace_setstatus
dev_langs:
- TSQL
helpviewer_keywords:
- sp_trace_setstatus
ms.assetid: 29e7a7d7-b9c1-414a-968a-fc247769750d
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 23d74214176d70ef2d71e04b1d758b4e40fac808
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89543016"
---
# <a name="sp_trace_setstatus-transact-sql"></a>sp_trace_setstatus (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  修改指定追蹤的目前狀態。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 請改用擴充事件。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_trace_setstatus [ @traceid = ] trace_id , [ @status = ] status  
```  
  
## <a name="arguments"></a>引數  
`[ @traceid = ] trace_id` 這是要修改的追蹤識別碼。 *trace_id* 是 **int**，沒有預設值。 使用者會使用這個 *trace_id* 值來識別、修改和控制追蹤。 如需有關取出 *trace_id*的詳細資訊，請參閱 [sys. fn_trace_getinfo &#40;transact-sql&#41;](../../relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql.md)。  
  
`[ @status = ] status` 指定要在追蹤上執行的動作。 *狀態* 是 **int**，沒有預設值。  
  
 下表列出可能指定的狀態。  
  
|狀態|描述|  
|------------|-----------------|  
|**0**|停止指定的追蹤。|  
|**1**|啟動指定的追蹤。|  
|**2**|關閉指定的追蹤，並從伺服器中刪除其定義。|  
  
> [!NOTE]  
>  您必須先關閉追蹤，才能將它刪除。 您必須先停止和關閉追蹤，才能檢視它。  
  
## <a name="return-code-values"></a>傳回碼值  
 下表描述在預存程序完成之後，使用者可能得到的代碼值。  
  
|傳回碼|描述|  
|-----------------|-----------------|  
|**0**|沒有錯誤。|  
|**1**|未知的錯誤。|  
|**8**|指定的狀態無效。|  
|**9**|指定的追蹤控制代碼無效。|  
|**13**|記憶體不足。 當沒有足夠的記憶體可以執行指定的動作時，便傳回這個代碼。|  
  
 如果追蹤已在指定的狀態中， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 則會傳回 **0**。  
  
## <a name="remarks"></a>備註  
 所有 SQL 追蹤預存程式 (**sp_trace_xx**) 的參數都是嚴格輸入的。 如果沒有依照引數描述所指定，以正確的輸入參數資料類型來呼叫這些參數，預存程序會傳回錯誤。  
  
 如需使用追蹤預存程序的範例，請參閱[建立追蹤 &#40;Transact-SQL&#41;](../../relational-databases/sql-trace/create-a-trace-transact-sql.md)。  
  
## <a name="permissions"></a>權限  
 使用者必須有 ALTER TRACE 權限。  
  
## <a name="see-also"></a>另請參閱  
 [sys. fn_trace_geteventinfo &#40;Transact-sql&#41;](../../relational-databases/system-functions/sys-fn-trace-geteventinfo-transact-sql.md)   
 [sys.fn_trace_getfilterinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql.md)   
 [sp_trace_generateevent &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [sp_trace_setfilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)   
 [SQL 追蹤](../../relational-databases/sql-trace/sql-trace.md)  
  
  
