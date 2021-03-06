---
description: sp_refresh_log_shipping_monitor (Transact-SQL)
title: sp_refresh_log_shipping_monitor (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_refresh_log_shipping_monitor
- sp_refresh_log_shipping_monitor_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_refresh_log_shipping_monitor
ms.assetid: edefb912-31c5-4d99-9aba-06629afd0171
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 3ece1b616c1639a7e826f6c5d5cc566ec8cb35b6
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89549556"
---
# <a name="sp_refresh_log_shipping_monitor-transact-sql"></a>sp_refresh_log_shipping_monitor (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  這個預存程序會利用指定記錄傳送代理程式的給定主要或次要伺服器所提供的最新資訊，來重新整理遠端監視器資料表。 這個程序可於主要或次要伺服器上叫用。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_refresh_log_shipping_monitor  
[ @agent_id = ] 'agent_id',  
[ @agent_type = ] 'agent_type'  
[ @database = ] 'database'  
[ @mode ] n  
```  
  
## <a name="arguments"></a>引數  
`[ @agent_id = ] 'agent_id'` 備份的主要識別碼或複製或還原的次要識別碼。 *agent_id* 是 **uniqueidentifier** ，不能是 Null。  
  
`[ @agent_type = ] 'agent_type'` 記錄傳送作業的類型。  
  
 0 = 備份。  
  
 1 = 複製。  
  
 2 = 還原。  
  
 *agent_type* 是 **Tinyint** ，不能是 Null。  
  
`[ @database = ] 'database'` 由備份或還原代理程式記錄所使用的主要或次要資料庫。  
  
`[ @mode ] n` 指定是否要重新整理監視器資料或將其清除。 *M*的資料類型是 Tinyint，支援的值為：  
  
 1 = 重新整理 (這是預設值。)  
  
 2 = 刪除  
  
## <a name="return-code-values"></a>傳回碼值  
 0 (成功) 或 1 (失敗)  
  
## <a name="result-sets"></a>結果集  
 無。  
  
## <a name="remarks"></a>備註  
 **sp_refresh_log_shipping_monitor** 使用尚未傳送的任何會話資訊重新整理 **log_shipping_monitor_primary**、 **log_shipping_monitor_secondary**、 **log_shipping_monitor_history_detail**和 **log_shipping_monitor_error_detail** 資料表。 這可讓您在監視器不同步一段時間之後，將監視伺服器和主要或次要伺服器同步化。 另外，必要的話，它也可讓您清除監視伺服器的監視資訊。  
  
 **sp_refresh_log_shipping_monitor** 必須從主要或次要伺服器上的 **master** 資料庫執行。  
  
## <a name="permissions"></a>權限  
 只有 **系統管理員（sysadmin** ）固定伺服器角色的成員，才能夠執行這個程式。  
  
## <a name="see-also"></a>另請參閱  
 [關於記錄傳送 &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
