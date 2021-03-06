---
title: 模型方法 - 報表伺服器 Web 服務 | Microsoft Docs
description: 了解可在報表伺服器 Web 服務中用來管理模型的方法。
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service
ms.topic: reference
ms.assetid: d3e658c9-bb22-480b-a3d5-bcde8f537ab2
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 73d4a0ee4c5db4059dfe5ceac908b92d41ab8a45
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/29/2020
ms.locfileid: "79198235"
---
# <a name="model-methods---report-server-web-service"></a>模型方法 - 報表伺服器 Web 服務
  您可以使用這些方法來管理模型。  
  
|方法|動作|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.GenerateModel%2A>|以共用資料來源為基礎產生預設模型。|  
|<xref:ReportService2010.ReportingService2010.GetModelItemPermissions%2A>|擷取與模型項目關聯的使用者權限。|  
|<xref:ReportService2010.ReportingService2010.GetModelItemPolicies%2A>|擷取與模型項目關聯的原則。|  
|<xref:ReportService2010.ReportingService2010.GetUserModel%2A>|為目前使用者傳回模型的語意部分。|  
|<xref:ReportService2010.ReportingService2010.InheritModelItemParentSecurity%2A>|刪除與模型項目關聯的原則，並讓模型項目繼承其父項的原則。|  
|<xref:ReportService2010.ReportingService2010.ListModelDrillthroughReports%2A>|列出與模型中實體關聯的鑽研報表。|  
|<xref:ReportService2010.ReportingService2010.ListModelItemChildren%2A>|傳回模型項目子元素的陣列。|  
|<xref:ReportService2010.ReportingService2010.ListModelItemTypes%2A>|傳回支援的模型項目類型清單。|  
|<xref:ReportService2010.ReportingService2010.ListModelPerspectives%2A>|列出使用者可使用的模型和檢視方塊。|  
|<xref:ReportService2010.ReportingService2010.RegenerateModel%2A>|根據資料來源結構描述的變更，更新現有的模型。|  
|<xref:ReportService2010.ReportingService2010.RemoveAllModelItemPolicies%2A>|刪除指定模型中與模型項目關聯的所有原則。|  
|<xref:ReportService2010.ReportingService2010.SetModelDrillthroughReports%2A>|將一組鑽研報告與模型產生關聯。|  
|<xref:ReportService2010.ReportingService2010.SetModelItemPolicies%2A>|在模型項目上設定安全性原則。|  
  
## <a name="see-also"></a>另請參閱  
 [使用 Web 服務和 .NET Framework 建置應用程式](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [報表伺服器 Web 服務](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [報表伺服器 Web 服務方法](../../../reporting-services/report-server-web-service/methods/report-server-web-service-methods.md)   
 [技術參考 &#40;SSRS&#41;](../../../reporting-services/technical-reference-ssrs.md)  
  
  
