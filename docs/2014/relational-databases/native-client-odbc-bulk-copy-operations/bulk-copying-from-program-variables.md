---
title: 從程式變數大量複製 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC], program variables
- bcp_bind function
- mapping data types [ODBC]
- SQL Server Native Client ODBC driver, bulk copy
- data types [ODBC], bulk copying
- ODBC, bulk copy operations
- program variables [ODBC]
ms.assetid: e4284a1b-7534-4b34-8488-b8d05ed67b8c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 55b1df99038e95f1e3a9a1c609caf1fe8ce982e4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48080594"
---
# <a name="bulk-copying-from-program-variables"></a>從程式變數中大量複製
  您可以直接從程式變數大量複製。 在配置變數來保存的資料列的資料及呼叫之後[bcp_init](../native-client-odbc-extensions-bulk-copy-functions/bcp-init.md)若要開始大量複製，呼叫[bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)每個資料行指定的位置與相關聯之程式變數的格式與資料行。 填滿每個變數的資料，然後呼叫[bcp_sendrow](../native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md)將一個資料列的資料傳送至伺服器。 重複填入變數及呼叫的程序**bcp_sendrow**之前的所有資料列已傳送至伺服器，然後呼叫[bcp_done](../native-client-odbc-extensions-bulk-copy-functions/bcp-done.md)來指定作業已完成。  
  
 **Bcp_bind * * * pData*參數包含繫結至資料行之變數的位址。 每一個資料行的資料都可以透過以下兩種方式的其中一種來儲存：  
  
-   配置一個變數來保存資料。  
  
-   配置指標變數，後面緊接著資料變數。  
  
 此指標變數指出變動長度資料行之資料的長度，也會在此資料行允許 NULL 時指出 NULL 值。 如果只使用資料變數時，則此變數的位址儲存在 **bcp_bind * * * pData*參數。 如果使用了指標變數，則要將這個指標變數的位址儲存在 **bcp_bind * * * pData*參數。 大量複製函數會計算此資料變數的位置加入 **bcp_bind * * * cbIndicator*並*pData*參數。  
  
 **bcp_bind** 可支援用來處理變動長度資料的三個方法：  
  
-   只搭配資料變數使用 *cbData* 。 將資料的長度放在 *cbData*中。 若要將大量資料的長度複製變更，每次呼叫[bcp_collen](../native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md)重設*cbData*。 如果使用了其他兩個方法的其中一種，請針對 *cbData*指定 SQL_VARLEN_DATA。 如果為資料行提供的所有資料值都是 NULL，請針對 *cbData*指定 SQL_NULL_DATA。  
  
-   使用指標變數。 當每一個新的資料值移到資料變數內時，請將該值的長度儲存在指標變數中。 如果使用了其他兩個方法的其中一種，請針對 *cbIndicator*指定 0。  
  
-   使用結束字元指標。 負載 **bcp_bind * * * pTerm*結束資料之位元模式的位址參數。 如果使用了其他兩個方法的其中一種，請針對 *pTerm*指定 NULL。  
  
 這三種方法全都可以在相同的 **bcp_bind** 呼叫上使用，在此情況下會使用產生最少量複製資料的規格。  
  
 **Bcp_bind * * * 類型*參數會使用 Db-library 資料類型識別碼，而不是 ODBC 資料類型識別碼。 DB-Library 資料類型識別碼定義在 sqlncli.h 中，可搭配 ODBC **bcp_bind** 函數使用。  
  
 大量複製函數並非所有 ODBC C 資料類型都有支援。 例如，大量複製函數不支援 ODBC SQL_C_TYPE_TIMESTAMP 結構，因此請使用[SQLBindCol](../native-client-odbc-api/sqlbindcol.md)或是[SQLGetData](../native-client-odbc-api/sqlgetdata.md)將 ODBC SQL_TYPE_TIMESTAMP 資料轉換成 SQL_C_CHAR 變數。 如果您稍後使用**bcp_bind**與*型別*參數來繫結的變數，以搭配 SQLCHARACTER 的[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **datetime**  欄中，大量複製函數轉換在適當的日期時間格式字元變數中的時間戳記逸出子句。  
  
 下表列出建議的資料類型對應至 ODBC SQL 資料類型中使用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]資料型別。  
  
|ODBC SQL 資料類型|ODBC C 資料類型|bcp_bind *type* 參數|SQL Server 資料類型|  
|-----------------------|----------------------|--------------------------------|--------------------------|  
|SQL_CHAR|SQL_C_CHAR|SQLCHARACTER|**character**<br /><br /> **char**|  
|SQL_VARCHAR|SQL_C_CHAR|SQLCHARACTER|**varchar**<br /><br /> **可變長度字元**<br /><br /> **char varying**<br /><br /> **sysname**|  
|SQL_LONGVARCHAR|SQL_C_CHAR|SQLCHARACTER|**text**|  
|SQL_WCHAR|SQL_C_WCHAR|SQLNCHAR|**nchar**|  
|SQL_WVARCHAR|SQL_C_WCHAR|SQLNVARCHAR|**nvarchar**|  
|SQL_WLONGVARCHAR|SQL_C_WCHAR|SQLNTEXT|**ntext**|  
|SQL_DECIMAL|SQL_C_CHAR|SQLCHARACTER|**decimal**<br /><br /> **dec**<br /><br /> **money**<br /><br /> **smallmoney**|  
|SQL_NUMERIC|SQL_C_NUMERIC|SQLNUMERICN|**numeric**|  
|SQL_BIT|SQL_C_BIT|SQLBIT|**bit**|  
|SQL_TINYINT (帶正負號)|SQL_C_SSHORT|SQLINT2|**smallint**|  
|SQL_TINYINT (不帶正負號)|SQL_C_UTINYINT|SQLINT1|**tinyint**|  
|SQL_SMALL_INT (帶正負號)|SQL_C_SSHORT|SQLINT2|**smallint**|  
|SQL_SMALL_INT (不帶正負號)|SQL_C_SLONG|SQLINT4|**int**<br /><br /> **integer**|  
|SQL_INTEGER (帶正負號)|SQL_C_SLONG|SQLINT4|**int**<br /><br /> **integer**|  
|SQL_INTEGER (不帶正負號)|SQL_C_CHAR|SQLCHARACTER|**decimal**<br /><br /> **dec**|  
|SQL_BIGINT (帶正負號和不帶正負號)|SQL_C_CHAR|SQLCHARACTER|**bigint**|  
|SQL_REAL|SQL_C_FLOAT|SQLFLT4|**real**|  
|SQL_FLOAT|SQL_C_DOUBLE|SQLFLT8|**float**|  
|SQL_DOUBLE|SQL_C_DOUBLE|SQLFLT8|**float**|  
|SQL_BINARY|SQL_C_BINARY|SQLBINARY|**binary**<br /><br /> **timestamp**|  
|SQL_VARBINARY|SQL_C_BINARY|SQLBINARY|**varbinary**<br /><br /> **設定不同的二進位**|  
|SQL_LONGVARBINARY|SQL_C_BINARY|SQLBINARY|**image**|  
|SQL_TYPE_DATE|SQL_C_CHAR|SQLCHARACTER|**datetime**<br /><br /> **smalldatetime**|  
|SQL_TYPE_TIME|SQL_C_CHAR|SQLCHARACTER|**datetime**<br /><br /> **smalldatetime**|  
|SQL_TYPE_TIMESTAMP|SQL_C_CHAR|SQLCHARACTER|**datetime**<br /><br /> **smalldatetime**|  
|SQL_GUID|SQL_C_GUID|SQLUNIQUEID|**uniqueidentifier**|  
|SQL_INTERVAL_|SQL_C_CHAR|SQLCHARACTER|**char**|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不會不會有簽署**tinyint**不帶正負號**smallint**，或不帶正負號**int**資料型別。 若要移轉這些資料類型時，請避免遺失資料的值，建立[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]下一步 的最大整數資料類型的資料表。 若要避免使用者之後加入原始資料類型所允許之範圍以外的值，請將規則套用到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料行，將可允許的值限制為原始來源中受到該資料類型所支援的範圍：  
  
```  
CREATE TABLE Sample_Ints(STinyIntCol   SMALLINT,  
USmallIntCol INT)  
GO  
CREATE RULE STinyInt_Rule  
AS   
@range >= -128 AND @range <= 127  
GO  
CREATE RULE USmallInt_Rule  
AS   
@range >= 0 AND @range <= 65535  
GO  
sp_bindrule STinyInt_Rule, 'Sample_Ints.STinyIntCol'  
GO  
sp_bindrule USmallInt_Rule, 'Sample_Ints.USmallIntCol'  
GO  
```  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不直接支援間隔資料類型。 應用程式可以不過，儲存間隔逸出序列當做字元字串中[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]字元資料行。 應用程式可以讀取它們供日後使用，但是它們不能在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式中使用。  
  
 大量複製函數可用來快速將資料載入[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]讀取從 ODBC 資料來源。 使用  [SQLBindCol](../native-client-odbc-api/sqlbindcol.md)繫結結果集至程式變數的資料行，然後使用**bcp_bind**至相同的程式變數繫結至大量複製作業。 呼叫[SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md)或是**SQLFetch**然後會從 ODBC 資料來源的資料列擷取到程式變數，並呼叫[bcp_sendrow](../native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md)將資料大量複製從程式變數到[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。  
  
 應用程式可以使用[bcp_colptr](../native-client-odbc-extensions-bulk-copy-functions/bcp-colptr.md)函式，每當程式需要變更原本在所指定的資料變數的位址**bcp_bind** *pData*參數。 應用程式可以使用[bcp_collen](../native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md)函式，每當程式需要變更原本指定的資料長度 **bcp_bind * * * cbData*參數。  
  
 您無法讀取來自資料[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]到程式變數使用大量複製，並沒有類似"bcp_readrow"函數。 您只能將應用程式中的資料傳送到伺服器。  
  
## <a name="see-also"></a>另請參閱  
 [執行大量複製作業&#40;ODBC&#41;](performing-bulk-copy-operations-odbc.md)  
  
  
