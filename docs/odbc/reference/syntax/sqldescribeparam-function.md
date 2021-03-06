---
description: SQLDescribeParam 函數
title: SQLDescribeParam 函式 |Microsoft Docs
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLDescribeParam
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLDescribeParam
helpviewer_keywords:
- SQLDescribeParam function [ODBC]
ms.assetid: 1f5b63c4-2f3e-44da-b155-876405302281
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0e6209f4e3145e55dfd94a9ff1375013ae5c7a85
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88491311"
---
# <a name="sqldescribeparam-function"></a>SQLDescribeParam 函數
**一致性**  
 引進的版本： ODBC 1.0 標準合規性： ODBC  
  
 **總結**  
 **SQLDescribeParam** 會傳回與備妥的 SQL 語句相關聯之參數標記的描述。 這項資訊也可在 IPD 的欄位中取得。  
  
## <a name="syntax"></a>語法  
  
```cpp  
  
SQLRETURN SQLDescribeParam(  
      SQLHSTMT        StatementHandle,  
      SQLUSMALLINT    ParameterNumber,  
      SQLSMALLINT *   DataTypePtr,  
      SQLULEN *       ParameterSizePtr,  
      SQLSMALLINT *   DecimalDigitsPtr,  
      SQLSMALLINT *   NullablePtr);  
```  
  
## <a name="arguments"></a>引數  
 *StatementHandle*  
 輸出語句控制碼。  
  
 *ParameterNumber*  
 輸出以遞增的參數順序順序排序的參數標記編號，從1開始。  
  
 *DataTypePtr*  
 出緩衝區的指標，此緩衝區會傳回參數的 SQL 資料類型。 此值是從 IPD 的 SQL_DESC_CONCISE_TYPE 記錄欄位讀取。 這會是 [附錄 D：資料類型] 的 [ [SQL 資料類型](../../../odbc/reference/appendixes/sql-data-types.md) ] 區段中的其中一個值，或是驅動程式特定的 sql 資料類型。  
  
 在 ODBC 3 中。*x*、SQL_TYPE_DATE、SQL_TYPE_TIME 或 SQL_TYPE_TIMESTAMP 將分別在* \* DataTypePtr*中傳回日期、時間或時間戳記資料，在 ODBC 2 中傳回。*x*將會傳回 x、SQL_DATE、SQL_TIME 或 SQL_TIMESTAMP。 當 ODBC 2 時，驅動程式管理員會執行必要的對應。*x* 應用程式正在使用 ODBC 3。*x* 驅動程式或 ODBC 3。*x* 應用程式正在使用 ODBC 2。*x* 驅動程式。  
  
 當書簽資料行) 的*ColumnNumber*等於 0 (時，會在* \* DataTypePtr*中傳回可變長度書簽的 SQL_BINARY。 如果 ODBC 3 使用書簽，則會傳回 (SQL_INTEGER。使用 ODBC 2 的*x* 應用程式。*x* 驅動程式或 ODBC 2。使用 ODBC 3 的*x* 應用程式。*x* 驅動程式。 )   
  
 如需詳細資訊，請參閱附錄 D：資料類型中的 [SQL 資料類型](../../../odbc/reference/appendixes/sql-data-types.md) 。 如需有關驅動程式特定的 SQL 資料類型的詳細資訊，請參閱驅動程式的檔。  
  
 *ParameterSizePtr*  
 出緩衝區的指標，傳回資料來源所定義之對應參數標記的資料行或運算式大小（以字元為單位）。 如需資料行大小的詳細資訊，請參閱資料 [行大小、小數位數、傳輸八位長度和顯示大小](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)。  
  
 *DecimalDigitsPtr*  
 出緩衝區的指標，此緩衝區會傳回資料來源所定義之對應參數的資料行或運算式的小數位數。 如需十進位數的詳細資訊，請參閱資料 [行大小、小數位數、傳輸八位長度和顯示大小](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)。  
  
 *NullablePtr*  
 出緩衝區的指標，此緩衝區會傳回指出參數是否允許 Null 值的值。 此值是從 IPD 的 SQL_DESC_NullABLE 欄位讀取。 下列其中之一：  
  
-   SQL_NO_NullS：參數不允許 Null 值 (這是預設值) 。  
  
-   SQL_NullABLE：參數允許 Null 值。  
  
-   SQL_NullABLE_UNKNOWN：驅動程式無法判斷參數是否允許 Null 值。  
  
## <a name="returns"></a>傳回  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_STILL_EXECUTING、SQL_ERROR 或 SQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診斷  
 當**SQLDescribeParam**傳回 SQL_ERROR 或 SQL_SUCCESS_WITH_INFO 時，可以藉由呼叫**SQLGetDiagRec**和*HandleType* （SQL_HANDLE_STMT）和*StatementHandle*的*控制碼*來取得相關聯的 SQLSTATE 值。 下表列出 **SQLDescribeParam** 通常會傳回的 SQLSTATE 值，並在此函式的內容中說明每一個值;「 (DM) 」標記法優先于驅動程式管理員所傳回的 SQLSTATEs 描述。 除非另有說明，否則會 SQL_ERROR 與每個 SQLSTATE 值相關聯的傳回碼。  
  
|SQLSTATE|錯誤|描述|  
|--------------|-----------|-----------------|  
|01000|一般警告|驅動程式特定的告知性訊息。  (函數會傳回 SQL_SUCCESS_WITH_INFO。 ) |  
|07009|描述元索引無效| (DM) 引數 *ParameterNumber* 指定的值小於1。<br /><br /> 針對引數 *ParameterNumber* 指定的值大於相關聯 SQL 語句中的參數數目。<br /><br /> 參數標記是非 DML 語句的一部分。<br /><br /> 參數標記是 **選取** 清單的一部分。|  
|08S01|通訊連結失敗|在函式完成處理之前，驅動程式與連接驅動程式的資料來源之間的通訊連結失敗。|  
|21S01|插入值清單與資料行清單不相符|**INSERT**語句中的參數數目不符合語句中所指定資料表中的資料行數目。|  
|HY000|一般錯誤|發生未定義特定 SQLSTATE 的錯誤，且未定義任何執行特定的 SQLSTATE。 **SQLGetDiagRec**在* \* MessageText*緩衝區中傳回的錯誤訊息會描述錯誤及其原因。|  
|HY001|記憶體配置錯誤|驅動程式無法配置支援執行或完成函式所需的記憶體。|  
|HY008|已取消作業|*StatementHandle*已啟用非同步處理。 呼叫函式，並在完成執行之前，在*StatementHandle*上呼叫**SQLCancel**或**SQLCancelHandle** 。 然後在 *StatementHandle*上再次呼叫該函式。<br /><br /> 呼叫函式，並在完成執行之前，從多執行緒應用程式中的不同執行緒在*StatementHandle*上呼叫**SQLCancel**或**SQLCancelHandle** 。|  
|HY010|函數順序錯誤| (DM) 在呼叫*StatementHandle*的**SQLPrepare**或**SQLExecDirect**之前，會呼叫此函數。<br /><br />  (DM) 以非同步方式執行的函式，是與 *StatementHandle*相關聯的連接控制碼所呼叫。 呼叫 **SQLDescribeParam** 函式時，仍在執行此非同步函式。<br /><br />  (DM) 以非同步方式執行的函式 (不是針對 *StatementHandle* 呼叫這個) ，而且在呼叫此函式時仍在執行。<br /><br /> 針對*StatementHandle*呼叫 (DM) **SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**或**SQLSetPos** ，並傳回 SQL_NEED_DATA。 在傳送所有資料執行中參數或資料行的資料之前，會呼叫此函數。|  
|HY013|記憶體管理錯誤|無法處理函式呼叫，因為無法存取基礎記憶體物件，可能是因為記憶體不足的情況。|  
|HY117|由於未知的交易狀態，連接已暫止。 只允許中斷連接和唯讀功能。| (DM) 如需暫停狀態的詳細資訊，請參閱 [SQLEndTran 函數](../../../odbc/reference/syntax/sqlendtran-function.md)。|  
|HYT01|連接逾時已過期|連接逾時期間已在資料來源回應要求之前過期。 連接逾時期間是透過 **SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT 設定。|  
|IM001|驅動程式不支援此功能| (DM) 與 *StatementHandle* 相關聯的驅動程式不支援此功能。|  
|IM017|非同步通知模式中的輪詢已停用|每當使用通知模型時，就會停用輪詢。|  
|IM018|尚未呼叫**SQLCompleteAsync**來完成這個控制碼上先前的非同步作業。|如果控制碼上先前的函式呼叫傳回 SQL_STILL_EXECUTING，而且如果啟用了通知模式，則必須在控制碼上呼叫 **SQLCompleteAsync** ，以進行後置處理，並完成作業。|  
  
## <a name="comments"></a>註解  
 參數標記會以遞增的參數順序編號，從1開始，依照它們出現在 SQL 語句中的順序。  
  
 **SQLDescribeParam** 不會傳回 SQL 語句中參數 (輸入、輸入/輸出或輸出) 的型別。 除了在程式的呼叫中，SQL 語句中的所有參數都是輸入參數。 若要在呼叫程式時判斷每個參數的類型，應用程式會呼叫 **SQLProcedureColumns**。  
  
 如需詳細資訊，請參閱 [描述參數](../../../odbc/reference/develop-app/describing-parameters.md)。  
  
## <a name="code-example"></a>程式碼範例  
 下列範例會提示使用者輸入 SQL 語句，然後準備該語句。 接下來，它會呼叫 **SQLNumParams** 來判斷語句是否包含任何參數。 如果語句包含參數，它會呼叫 **SQLDescribeParam** 來描述這些參數和 **SQLBindParameter** 來系結它們。 最後，它會提示使用者輸入任何參數的值，然後執行語句。  
  
```cpp  
SQLCHAR       Statement[100];  
SQLSMALLINT   NumParams, i, DataType, DecimalDigits, Nullable;  
SQLUINTEGER   ParamSize;  
SQLHSTMT      hstmt;  
  
// Prompt the user for an SQL statement and prepare it.  
GetSQLStatement(Statement);  
SQLPrepare(hstmt, Statement, SQL_NTS);  
  
// Check to see if there are any parameters. If so, process them.  
SQLNumParams(hstmt, &NumParams);  
if (NumParams) {  
   // Allocate memory for three arrays. The first holds pointers to buffers in which  
   // each parameter value will be stored in character form. The second contains the  
   // length of each buffer. The third contains the length/indicator value for each  
   // parameter.  
   SQLPOINTER * PtrArray = (SQLPOINTER *) malloc(NumParams * sizeof(SQLPOINTER));  
   SQLINTEGER * BufferLenArray = (SQLINTEGER *) malloc(NumParams * sizeof(SQLINTEGER));  
   SQLINTEGER * LenOrIndArray = (SQLINTEGER *) malloc(NumParams * sizeof(SQLINTEGER));  
  
   for (i = 0; i < NumParams; i++) {  
   // Describe the parameter.  
   SQLDescribeParam(hstmt, i + 1, &DataType, &ParamSize, &DecimalDigits, &Nullable);  
  
   // Call a helper function to allocate a buffer in which to store the parameter  
   // value in character form. The function determines the size of the buffer from  
   // the SQL data type and parameter size returned by SQLDescribeParam and returns  
   // a pointer to the buffer and the length of the buffer.  
   AllocParamBuffer(DataType, ParamSize, &PtrArray[i], &BufferLenArray[i]);  
  
   // Bind the memory to the parameter. Assume that we only have input parameters.  
   SQLBindParameter(hstmt, i + 1, SQL_PARAM_INPUT, SQL_C_CHAR, DataType, ParamSize,  
         DecimalDigits, PtrArray[i], BufferLenArray[i],  
         &LenOrIndArray[i]);  
  
   // Prompt the user for the value of the parameter and store it in the memory  
   // allocated earlier. For simplicity, this function does not check the value  
   // against the information returned by SQLDescribeParam. Instead, the driver does  
   // this when the statement is executed.  
   GetParamValue(PtrArray[i], BufferLenArray[i], &LenOrIndArray[i]);  
   }  
}  
  
// Execute the statement.  
SQLExecute(hstmt);  
  
// Process the statement further, such as retrieving results (if any) and closing the  
// cursor (if any). Code not shown.  
  
// Free the memory allocated for each parameter and the memory allocated for the arrays  
// of pointers, buffer lengths, and length/indicator values.  
for (i = 0; i < NumParams; i++) free(PtrArray[i]);  
free(PtrArray);  
free(BufferLenArray);  
free(LenOrIndArray);  
```  
  
## <a name="related-functions"></a>相關函數  
  
|如需下列資訊|請參閱|  
|---------------------------|---------|  
|將緩衝區系結至參數|[SQLBindParameter 函式](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|取消語句處理|[SQLCancel 函式](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|執行已備妥的 SQL 語句|[SQLExecute 函式](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|準備要執行的語句|[SQLPrepare 函式](../../../odbc/reference/syntax/sqlprepare-function.md)|  
  
## <a name="see-also"></a>另請參閱  
 [ODBC API 參考](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC 標頭檔](../../../odbc/reference/install/odbc-header-files.md)
