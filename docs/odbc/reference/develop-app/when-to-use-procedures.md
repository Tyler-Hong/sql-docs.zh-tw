---
description: 程序的使用時機
title: 使用程式的時機 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], procedures
- procedures [ODBC], about procedures
ms.assetid: 7dc9e327-dd54-4b10-9f66-9ef5c074f122
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7268e8650b0de17edab8776eaaf644ece60100bf
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421372"
---
# <a name="when-to-use-procedures"></a>程序的使用時機
使用程式有許多優點，全部都是根據使用程式將 SQL 語句從應用程式移至資料來源的事實。 應用程式中剩下的是可互通的程序呼叫。 這些優點包括：  
  
-   **效能** 程式通常是執行 SQL 語句的最快速方式。 如同備妥的執行，語句會以兩個不同的步驟進行編譯和執行。 不同于備妥的執行，程式只會在執行時間執行。 它們會在不同的時間進行編譯。  
  
-   **商務規則***商務規則*是公司經營商務方式的規則。 例如，只有具備職稱 Sales Person 的人員才能加入新的銷售訂單。 將這些規則放入程式，可讓個別公司藉由重寫應用程式所呼叫的程式，而不需要修改應用程式程式碼，以自訂垂直應用程式。 例如，訂單輸入應用程式可能會使用固定的參數數目來呼叫程式 **InsertOrder** ;實際執行 **InsertOrder** 的方式可能會因公司而異。  
  
-   **可取代性** 與在程式中放置商務規則密切相關的是，可以在不重新編譯應用程式的情況下更換程式。 如果商務規則在公司購買並安裝應用程式之後變更，公司可以變更包含該規則的程式。 從應用程式的觀點來看，沒有任何變更;它仍會呼叫特定程式來完成特定工作。  
  
-   **DBMS 特定的 SQL** 程式提供一種方法，讓應用程式利用 DBMS 特定的 SQL，但仍保持互通。 例如，在 SQL 中支援流程式控制制語句的 DBMS 程式可能會在錯誤中攔截和復原，而 DBMS 上不支援流程式控制制語句的程式則可能只會傳回錯誤。  
  
-   **程式存活交易** 在某些資料來源上，在認可或回復交易時，會刪除連接上所有備妥語句的存取計畫。 藉由將 SQL 語句放在永久儲存在資料來源中的程式，語句就會存留于交易中。 在備妥、部分備妥或未準備的狀態下，程式是否存留于 DBMS 特定的狀態。  
  
-   **獨立開發** 程式可與應用程式的其餘部分分開開發。 在大型公司中，這可能會提供一種方法來進一步利用高度特製化程式設計人員的技巧。 換句話說，應用程式程式設計師可以撰寫使用者介面程式碼，而資料庫程式設計人員可以撰寫程式。  
  
 程式通常是由垂直和自訂應用程式所使用。 這些應用程式通常會執行固定的工作，而且可以硬式編碼程序呼叫。 例如，訂單輸入應用程式可能會呼叫程式 **InsertOrder**、 **DeleteOrder**、 **UpdateOrder**和 **GetOrders**。  
  
 從一般應用程式呼叫程式有很多原因。 程式通常會撰寫成在特定應用程式的內容中執行工作，因此不會使用泛型應用程式。 例如，試算表沒有理由呼叫剛才提及的 **InsertOrder** 程式。 此外，一般應用程式不應該在執行時間建立程式，以提供更快速的語句執行;這種情況不僅可能比準備或直接執行慢，也需要 DBMS 特定的 SQL 語句。  
  
 這種情況的例外是應用程式開發環境，通常會提供方法讓程式設計人員建立執行程式的 SQL 語句，並可為程式設計人員提供測試程式的方法。 這類環境會呼叫 **SQLProcedures** 來列出可用的程式和 **SQLProcedureColumns** ，以列出輸入、輸入/輸出和輸出參數、程式傳回值，以及程式所建立之任何結果集的資料行。 不過，這類程式必須在每個資料來源上事先開發;這麼做需要 DBMS 特定的 SQL 語句。  
  
 使用程式有三個主要缺點。 首先，必須針對要執行應用程式的每個 DBMS 撰寫和編譯器。 雖然這不是自訂應用程式的問題，但它可能會大幅增加針對以許多 Dbms 執行而設計的垂直應用程式的開發和維護時間。  
  
 第二個缺點是許多 Dbms 不支援程式。 同樣地，這很可能是針對以一些 Dbms 執行而設計的垂直應用程式問題。 為了判斷是否支援程式，應用程式會使用 SQL_PROCEDURES 選項來呼叫 **SQLGetInfo** 。  
  
 第三個缺點（特別適用于應用程式開發環境）是 ODBC 不會定義建立程式的標準文法。 也就是說，雖然應用程式可以呼叫程式 interoperably，但無法建立它們 interoperably。
