---
title: Jet： 日期、 時間和時間戳記常值 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- literals [ODBC], SQL grammar
- SQL grammar [ODBC], literals
- date literals [ODBC]
- timestamp literals [ODBC]
- time literals [ODBC]
ms.assetid: 37db1ae1-ca4e-4cd8-9b47-7f1a38e7fcad
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2325cd7e4a10e91f351aa2107c64c0978b843fa6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47825836"
---
# <a name="jet-date-time-and-timestamp-literals"></a>Jet：日期、時間和時間戳記常值
最大的互通性，應用程式應該傳遞日期常值使用 escape 子句語法的 ODBC 標準格式：  
  
-   日期常值，{d '*值*'}，其中*值*e 的格式 」-yyyy-mm-dd"  
  
-   時間常值，{t '*值*'}，其中*值*e 是形式為"hh: mm: 」  
  
 時間戳記常值 {ts'*值*'}，其中*宣告*e 的格式為"yyyy-mm-dd hh: mm: [.f...]"。
