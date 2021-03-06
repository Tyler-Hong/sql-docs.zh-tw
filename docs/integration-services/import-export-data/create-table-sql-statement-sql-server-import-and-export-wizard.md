---
description: 建立資料表的 SQL 陳述式 (SQL Server 匯入和匯出精靈)
title: 建立資料表的 SQL 陳述式 (SQL Server 匯入和匯出精靈) | Microsoft Docs
ms.custom: ''
ms.date: 02/16/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.impexpwizard.createtablesql.f1
ms.assetid: 0d6f6b3b-d023-4770-a8a9-65b2977c8d05
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7854a8121c16d263da900ffc3f8475a4fe4dddff
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88484124"
---
# <a name="create-table-sql-statement-sql-server-import-and-export-wizard"></a>建立資料表的 SQL 陳述式 (SQL Server 匯入和匯出精靈)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


如果您選取 [建立目的地資料表] **** ，然後在 [資料行對應] **** 對話方塊中選取 [編輯 SQL] **** ，[ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 匯入和匯出精靈] 會顯示 [建立資料表的 SQL 陳述式] **** 對話方塊。 在此頁面上，您可以檢閱並選擇性地自訂 **CREATE TABLE** 命令，精靈將會執行此命令來建立新的目的地資料表。
  
> [!NOTE]
> 如果您想要尋找 [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE TABLE 陳述式的相關資訊，而不是 [[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 匯入和匯出精靈] 之 [建立資料表的 SQL 陳述式]**** 對話方塊的相關資訊，請參閱 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)。 
  
## <a name="screen-shot-of-the-create-table-sql-statement-page"></a>[建立資料表的 SQL 陳述式] 頁面的螢幕擷取畫面  
 下列螢幕擷取畫面顯示精靈的 [建立資料表的 SQL 陳述式] **** 對話方塊。
 
在此範例中，[SQL 陳述式] **** 方塊會包含精靈所產生的預設 **CREATE TABLE** 陳述式。 此陳述式會建立名為 **Person.AddressNew** 的新目的地資料表，這是 **Person.Address** 來源資料表的複本。 
  
 ![[匯入和匯出精靈] 的 [建立資料表] 頁面](../../integration-services/import-export-data/media/create-table.png "[匯入和匯出精靈] 的 [建立資料表] 頁面")  
  
## <a name="review-or-regenerate-the-create-table-statement"></a>檢視或重新產生 CREATE TABLE 陳述式  
 **SQL 陳述式**  
顯示自動產生的 SQL 陳述式並讓您進行自訂。
 
如果您變更預設 CREATE TABLE 命令，當您返回 [資料行對應]**** 對話方塊時，也可能必須變更關聯的資料行對應。  
  
若要在 SQL 陳述式的文字中包含歸位字元，請按 CTRL+ENTER 鍵。 如果只按 ENTER 鍵，對話方塊就會關閉。  
  
如需 CREATE TABLE 陳述式和語法的詳細資訊，請參閱 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)。   
  
 **自動產生**  
 按一下 [自動產生]****，還原預設 SQL 陳述式 (如果已變更)。  
  
## <a name="create-a-table-that-includes-a-filestream-column"></a>建立包含 FILESTREAM 資料行的資料表  
 [ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 匯入和匯出精靈] 會根據連接的資料來源來產生預設 CREATE TABLE 陳述式。 這個預設 CREATE TABLE 陳述式不會包含 FILESTREAM 屬性，即使來源資料表具有 FILESTREAM 資料行亦然。
 1.  若要使用精靈來複製 FILESTREAM 資料行，請先在目的地資料庫上實作 FILESTREAM 儲存體。
 2.  然後在 [建立資料表的 SQL 陳述式] **** 對話方塊中，將 FILESTREAM 屬性手動加入 CREATE TABLE 陳述式。  

如需語法的詳細資訊，請參閱 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)。 如需 FILESTREAM 的詳細資訊，請參閱[二進位大型物件 &#40;Blob&#41; 資料 &#40;SQL Server&#41;](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md)。  
  
## <a name="whats-next"></a>接下來要做什麼？  
 檢閱並自訂 CREATE TABLE 命令，然後按一下 [確定] **** 之後，[建立資料表的 SQL 陳述式] **** 對話方塊會將您返回 [資料行對應] **** 對話方塊。 如需詳細資訊，請參閱 [資料行對應](../../integration-services/import-export-data/column-mappings-sql-server-import-and-export-wizard.md)。
 
 ## <a name="see-also"></a>另請參閱
[透過匯入和匯出精靈的簡單範例開始使用](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md)


