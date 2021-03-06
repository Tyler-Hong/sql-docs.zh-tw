---
description: ExecuteComplete 事件 (ADO)
title: ExecuteComplete 事件 (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection::ExecuteComplete
- ExecuteComplete
helpviewer_keywords:
- ExecuteComplete event [ADO]
ms.assetid: 62470d42-e511-494c-bec4-ad4591734b7b
author: rothja
ms.author: jroth
ms.openlocfilehash: 36e27f8a86fce348dbf2061a1c7be91f43be9adc
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2020
ms.locfileid: "88973389"
---
# <a name="executecomplete-event-ado"></a>ExecuteComplete 事件 (ADO)
當命令完成執行之後，就會呼叫 **ExecuteComplete** 事件。  
  
## <a name="syntax"></a>語法  
  
```  
  
ExecuteComplete RecordsAffected, pError, adStatus, pCommand, pRecordset, pConnection  
```  
  
#### <a name="parameters"></a>參數  
 *RecordsAffected*  
 **長**數值，指出受命令影響的記錄數目。  
  
 *pError*  
 [Error](../../../ado/reference/ado-api/error-object.md)物件。 描述 **adStatus** 的值為 **adStatusErrorsOccurred**時所發生的錯誤;否則未設定。  
  
 *adStatus*  
 [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md)狀態值。 當呼叫這個事件時，如果造成事件的作業成功，這個參數會設定為 **adStatusOK** ，如果作業失敗，則為 **adStatusErrorsOccurred** 。  
  
 在此事件傳回之前，請將此參數設定為 **adStatusUnwantedEvent** ，以防止後續的通知。  
  
 *pCommand*  
 已執行的 [命令](../../../ado/reference/ado-api/command-object-ado.md) 物件。 包含 **命令** 物件，即使在呼叫 **Connection.Exe刻意** 或 **記錄集** 時也一樣。開啟時不明確建立 **命令**，在這種情況下，會由 ADO 在內部建立 **命令** 物件。  
  
 *pRecordset*  
 執行的命令結果的 [記錄集](../../../ado/reference/ado-api/recordset-object-ado.md) 物件。 此 **記錄集** 可能是空的。 您永遠不應該從這個事件處理常式中終結此記錄集物件。 這樣做會在 ADO 嘗試存取不再存在的物件時，導致存取違規。  
  
 *pConnection*  
 [連接](../../../ado/reference/ado-api/connection-object-ado.md)物件。 執行作業的連接。  
  
## <a name="remarks"></a>備註  
 **ExecuteComplete**事件可能會因為連接而發生 **。**[執行](../../../ado/reference/ado-api/execute-method-ado-connection.md)，**命令。**[Execute](../../../ado/reference/ado-api/execute-method-ado-command.md)，**記錄集。**[開啟](../../../ado/reference/ado-api/open-method-ado-recordset.md)、**記錄集。** 重新[查詢](../../../ado/reference/ado-api/requery-method.md)或**記錄集。**[NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)方法。  
  
## <a name="see-also"></a>另請參閱  
 [ADO 事件模型範例 (VC + +) ](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [ADO 事件處理常式摘要](../../../ado/guide/data/ado-event-handler-summary.md)
