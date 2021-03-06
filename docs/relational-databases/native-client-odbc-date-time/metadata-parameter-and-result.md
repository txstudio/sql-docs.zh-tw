---
title: 參數和結果中繼資料 |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- metadata [ODBC]
ms.assetid: 1518e6e5-a6a8-4489-b779-064c5624df53
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9ab95e9c60f0bd8e30f26ecd807fe7ee960c5b85
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2018
ms.locfileid: "51675257"
---
# <a name="metadata---parameter-and-result"></a>中繼資料 - 參數和結果
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  本主題將描述在日期和時間資料類型之實作參數描述項 (IPD) 與實作資料列描述項 (IRD) 欄位中傳回的資訊。  
  
## <a name="information-returned-in-ipd-fields"></a>在 IPD 欄位中傳回的資訊  
 下列資訊會在 IPD 欄位中傳回：  
  
|參數類型|日期|time|smalldatetime|DATETIME|datetime2|datetimeoffset|  
|--------------------|----------|----------|-------------------|--------------|---------------|--------------------|  
|SQL_DESC_CASE_SENSITIVE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_CONCISE_TYPE|SQL_TYPE_DATE|SQL_SS_TIME2|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_SS_TIMESTAMPOFFSET|  
|SQL_DESC_DATETIME_INTERVAL_CODE|SQL_CODE_DATE|0|SQL_CODE_TIMESTAMP|SQL_CODE_TIMESTAMP|SQL_CODE_TIMESTAMP|0|  
|SQL_DESC_DATETIME_INTERVAL_PRECISION|10|8,10..16|16|23|19, 21..27|26, 28..34|  
|SQL_DESC_FIXED_PREC_SCALE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_LENGTH|10|8,10..16|16|23|19, 21..27|26, 28..34|  
|SQL_DESC_OCTET_LENGTH|6|12|4|8|16|20|  
|SQL_DESC_PRECISION|0|0..7|0|3|0..7|0..7|  
|SQL_DESC_SCALE|0|0..7|0|3|0..7|0..7|  
|SQL_DESC_TYPE|SQL_TYPE_DATE|SQL_SS_TYPE_TIME2|SQL_DATETIME|SQL_DATETIME|SQL_DATETIME|SQL_SS_TIMESTAMPOFFSET|  
|SQL_DESC_TYPE_NAME|**date**|**time**|**smalldatetime**在 IRD **datetime2** IPD 中|**日期時間**在 IRD **datetime2** IPD 中|**datetime2**|datetimeoffset|  
|SQL_CA_SS_VARIANT_TYPE|SQL_C_TYPE_DATE|SQL_C_TYPE_BINARY|SQL_C_TYPE_TIMESTAMP|SQL_C_TYPE_TIMESTAMP|SQL_C_TYPE_TIMESTAMP|SQL_C_TYPE_BINARY|  
|SQL_CA_SS_VARIANT_SQL_TYPE|SQL_TYPE_DATE|SQL_SS_TIME2|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_SS_TIMESTAMPOFFSET|  
|SQL_CA_SS_SERVER_TYPE|不適用|不適用|SQL_SS_TYPE_SMALLDATETIME|SQL_SS_TYPE_DATETIME|SQL_SS_TYPE_DEFAULT|不適用|  
  
 有時候，數值範圍會存在不連續的情況。 例如，8,10..16 中便遺漏了 9。 這是當小數有效位數大於零時增加的小數點所導致。  
  
 **datetime2**傳回的型別名稱作為**smalldatetime**並**datetime**因為驅動程式會用它做為一般類型來傳輸所有**SQL_TYPE_TIMESTAMP**到伺服器的值。  
  
 SQL_CA_SS_VARIANT_SQL_TYPE 是新的描述項欄位。 這個欄位會加入至 IRD 和 IPD，讓應用程式指定相關聯的實值型別**sqlvariant** (SQL_SSVARIANT) 資料行和參數  
  
 SQL_CA_SS_SERVER_TYPE 是新的僅限 IPD 欄位，可讓應用程式控制繫結成 SQL_TYPE_TYPETIMESTAMP (或繫結成具有 SQL_C_TYPE_TIMESTAMP 之 C 類型的 SQL_SS_VARIANT) 的參數值如何傳送至伺服器。 如果 SQL_DESC_CONCISE_TYPE 是 SQL_TYPE_TIMESTAMP （或 sql_ss_variant 而且 C 類型 SQL_C_TYPE_TIMESTAMP） 呼叫 SQLExecute 或 SQLExecDirect 時，SQL_CA_SS_SERVER_TYPE 的值會決定表格式資料流 (TDS) 類型的參數值，如下所示：  
  
|SQL_CA_SS_SERVER_TYPE 的值|SQL_DESC_PRECISION 的有效值|SQL_DESC_LENGTH 的有效值|TDS 類型|  
|----------------------------------------|-------------------------------------------|----------------------------------------|--------------|  
|SQL_SS_TYPE_DEFAULT|0..7|19, 21..27|**datetime2**|  
|SQL_SS_TYPE_SMALLDATETIME|0|19|**smalldatetime**|  
|SQL_SS_TYPE_DATETIME|3|23|**datetime**|  
  
 SQL_CA_SS_SERVER_TYPE 的預設設定為 SQL_SS_TYPE_DEFAULT。 SQL_DESC_PRECISION 和 SQL_DESC_LENGTH 的設定會使用 SQL_CA_SS_SERVER_TYPE 的設定進行驗證，如上表所述。 如果這項驗證失敗，系統就會傳回 SQL_ERROR 並且使用 SQLState 07006 和訊息「限制的資料類型屬性違規」來記錄診斷記錄。 如果 SQL_CA_SS_SERVER_TYPE 設定為 SQL_SS_TYPE DEFAULT 以外的值，而且 DESC_CONCISE_TYPE 不是 SQL_TYPE_TIMESTAMP，系統也會傳回這個錯誤。 這些驗證會在發生描述項一致性違規時執行，例如：  
  
-   當 SQL_DESC_DATA_PTR 已變更時。  
  
-   在準備或執行階段 (呼叫 SQLExecute、SQLExecDirect、SQLSetPos 或 SQLBulkOperations 時) 中。  
  
-   藉由呼叫 SQLPrepare 與非延遲準備應用程式強制延遲時準備停用，或藉由呼叫 SQLNumResultCols，SQLDescribeCol 或 SQLDescribeParam 但未備妥的陳述式執行。  
  
 當 SQL_CA_SS_SERVER_TYPE 設定 SQLSetDescField 呼叫時，其值必須是 SQL_SS_TYPE_DEFAULT、 SQL_SS_TYPE_SMALLDATETIME 或 SQL_SS_TYPE_DATETIME。 否則，系統就會傳回 SQL_ERROR 並且使用 SQLState HY092 和訊息「屬性/選項識別碼無效」來記錄診斷記錄。  
  
 SQL_CA_SS_SERVER_TYPE 屬性可用的應用程式，取決於所支援的功能**datetime**並**smalldatetime**，而非**datetime2**。 例如， **datetime2**需要使用**dateadd**並**datediif**函數，而**datetime**和**smalldatetime**也允許使用算術運算子。 大部分應用程式都不需要使用這個屬性，而且應該避免使用這個屬性。  
  
## <a name="information-returned-in-ird-fields"></a>在 IRD 欄位中傳回的資訊  
 下列資訊會在 IRD 欄位中傳回：  
  
|資料行類型|日期|time|smalldatetime|DATETIME|datetime2|datetimeoffset|  
|-----------------|----------|----------|-------------------|--------------|---------------|--------------------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_CASE_SENSITIVE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_CONCISE_TYPE|SQL_TYPE_DATE|SQL_SS_TIME2|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_SS_TIMESTAMPOFFSET|  
|SQL_DESC_DATETIME_INTERVAL_CODE|SQL_CODE_DATE|0|SQL_CODE_TIMESTAMP|SQL_CODE_TIMESTAMP|SQL_CODE_TIMESTAMP|0|  
|SQL_DESC_DATETIME_INTERVAL_PRECISION|10|8,10..16|16|23|19, 21..27|26, 28..34|  
|SQL_DESC_DISPLAY_SIZE|10|8,10..16|16|23|19, 21..27|26, 28..34|  
|SQL_DESC_FIXED_PREC_SCALE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_LENGTH|10|8,10..16|16|2|19, 21..27|26, 28..34|  
|SQL_DESC_LITERAL_PREFIX|‘|‘|‘|‘|‘|‘|  
|SQL_DESC_LITERAL_SUFFIX|‘|‘|‘|‘|‘|‘|  
|SQL_DESC_LOCAL_TYPE_NAME|**date**|**time**|**smalldatetime**|**datetime**|**datetime2**|datetimeoffset|  
|SQL_DESC_OCTET_LENGTH|6|12|4|8|16|20|  
|SQL_DESC_PRECISION|0|0..7|0|3|0..7|0..7|  
|SQL_DESC_SCALE|0|0..7|0|3|0..7|0..7|  
|SQL_DESC_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|  
|SQL_DESC_TYPE|SQL_DATETIME|SQL_SS_TIME2|SQL_DATETIME|SQL_DATETIME|SQL_DATETIME|SQL_SS_TIMESTAMPOFFSET|  
|SQL_DESC_TYPE_NAME|**date**|**time**|**smalldatetime**|**datetime**|**datetime2**|datetimeoffset|  
|SQL_DESC_UNSIGNED|SQL_TRUE|SQL_TRUE|SQL_TRUE|SQL_TRUE|SQL_TRUE|SQL_TRUE|  
  
## <a name="see-also"></a>另請參閱  
 [中繼資料&#40;ODBC&#41;](https://msdn.microsoft.com/library/99133efc-b1f2-46e9-8203-d90c324a8e4c)  
  
  
