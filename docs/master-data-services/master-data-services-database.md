---
title: Master Data Services 資料庫
description: Master Data Services 資料庫包含 Master Data Services 系統的所有資訊，而且是 Master Data Services 部署的核心。
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- database [Master Data Services], about the database
- database [Master Data Services]
ms.assetid: 5f590cc1-6ec2-4b8c-a598-03de0f6051a0
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 2c7e24a7d519d787882ec587fc33f624f1eb6472
ms.sourcegitcommit: 6be9a0ff0717f412ece7f8ede07ef01f66ea2061
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85811483"
---
# <a name="master-data-services-database"></a>Master Data Services 資料庫

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  此資料庫包含 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 系統的所有資訊。 它是 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 部署的核心。 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 資料庫：  
  
-   儲存 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 系統所需的設定、資料庫物件和資料。  
  
-   包含用來處理來源系統中資料的臨時資料表。  
  
-   提供用來儲存來源系統中主資料的結構描述和資料庫物件。  
  
-   支援版本控制功能，包括商務規則驗證和電子郵件通知。  
  
-   為需要從資料庫擷取資料的訂閱系統，提供檢視表。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [分葉成員暫存資料表 &#40;Master Data Services&#41;](../master-data-services/leaf-member-staging-table-master-data-services.md)  
  
-   [合併成員暫存資料表 &#40;Master Data Services&#41;](../master-data-services/consolidated-member-staging-table-master-data-services.md)  
  
-   [關聯性暫存資料表 &#40;Master Data Services&#41;](../master-data-services/relationship-staging-table-master-data-services.md)  
  
-   [暫存處理序錯誤 &#40;Master Data Services&#41;](../master-data-services/staging-process-errors-master-data-services.md)  
  
## <a name="see-also"></a>另請參閱  
 [建立 Master Data Services 資料庫](../master-data-services/install-windows/create-a-master-data-services-database.md)   
 [資料庫物件安全性 &#40;Master Data Services&#41;](../master-data-services/database-object-security-master-data-services.md)   
 [資料庫登入、使用者和角色 &#40;Master Data Services&#41;](../master-data-services/database-logins-users-and-roles-master-data-services.md)  
  
  
