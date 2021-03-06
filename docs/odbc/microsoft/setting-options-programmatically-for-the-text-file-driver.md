---
description: 以程式設計方式設定文字檔驅動程式的選項
title: 以程式設計方式設定文字檔驅動程式的選項 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- text file driver [ODBC], setting options programmatically
- ODBC desktop database drivers [ODBC], text file driver
- desktop database drivers [ODBC], text file driver
- Jet-based ODBC drivers [ODBC], text file driver
ms.assetid: cbde2ca1-5d4e-4444-a371-a72f3ac4d92a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fdc130904266dcdaedf84e826d4812aa6cfbb607
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483451"
---
# <a name="setting-options-programmatically-for-the-text-file-driver"></a>以程式設計方式設定文字檔驅動程式的選項

|選項|描述|方法|  
|------------|-----------------|------------|  
|資料來源名稱|識別資料來源的名稱，例如薪資或人員。|若要動態設定此選項，請在[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md)的呼叫中使用**DSN**關鍵字。|  
|定義格式|顯示 [ **定義文字格式** ] 對話方塊，可讓您指定資料來源目錄中個別資料表的架構。|呼叫 [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md)時，無法動態設定這個選項。|  
|描述|資料來源中資料的選擇性描述;例如，「雇用日期、薪資歷程記錄和目前的員工評論」。|若要動態設定這個選項，請在[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md)的呼叫中使用**DESCRIPTION**關鍵字。|  
|目錄|選取目標目錄。|若要動態設定這個選項，請在[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md)的呼叫中使用**DEFAULTDIR**關鍵字。|  
|延伸模組清單|列出資料來源上文字檔的副檔名。 使用文字驅動程式時，當使用沒有副檔名的名稱執行 CREATE TABLE 語句時，就會建立不含副檔名的檔案。 其他驅動程式會在未提供任何擴充功能時，建立具有預設副檔名的檔案。 若要建立副檔名為 .txt 的檔案，此副檔名必須包含在名稱中。 若要在 [ **定義文字格式** ] 對話方塊中顯示沒有副檔名的檔案，請指定 "*"。 必須加入延伸模組清單中。|若要動態設定這個選項，請在[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md)的呼叫中使用**EXTENSIONS**關鍵字。|  
|唯讀|將資料庫指定為唯讀。|若要動態設定這個選項，請在[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md)的呼叫中使用**READONLY**關鍵字。|  
|要掃描的資料列|要掃描的資料列數目，以決定每個資料行的資料類型。 資料類型會根據找到的資料類型數目上限來決定。 如果遇到的資料與資料行猜測的資料類型不相符，則資料類型會以 Null 值傳回。<br /><br /> 針對文字驅動程式，您可以輸入從1到32767的數位，以掃描的資料列數目;不過，此值一律會預設為25。  (超出限制的數位將會傳回錯誤。 ) |若要動態設定這個選項，請在[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md)的呼叫中使用**MAXSCANROWS**關鍵字。|  
|選取目錄|顯示對話方塊，您可以在其中選取包含要存取之檔案的目錄。<br /><br /> 定義資料來源目錄時，請指定您最常使用的檔案所在的目錄。 ODBC 驅動程式會使用此目錄作為預設目錄。 如果經常使用檔案，請將其他檔案複製到此目錄。 或者，您可以在 SELECT 語句中使用目錄名稱來限定檔案名： `SELECT * FROM C:\MYDIR\EMP`<br /><br /> 或者，您可以使用 **SQLSetConnectOption** 函數搭配 SQL_CURRENT_QUALIFIER 選項，以指定新的預設目錄。|若要動態設定這個選項，請在[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md)的呼叫中使用**DEFAULTDIR**關鍵字。|
