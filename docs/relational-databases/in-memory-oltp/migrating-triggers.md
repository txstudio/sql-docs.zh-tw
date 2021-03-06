---
title: 移轉觸發程序 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: ad5385c5-5a50-40ca-a319-97d5606b8511
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 0e2a8619c9fbd92ba294ab3ebdade64da5eff7d7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47613719"
---
# <a name="migrating-triggers"></a>移轉觸發程序
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  本主題討論 DDL 觸發程序以及記憶體最佳化的資料表。  
  
 DML 觸發程序支援記憶體最佳化資料表，但是只能搭配 FOR | AFTER 觸發程序事件使用。 如需範例，請參閱 [實作 UPDATE 和 FROM 或子查詢](../../relational-databases/in-memory-oltp/implementing-update-with-from-or-subqueries.md)。 
  
 LOGON 觸發程序是定義成發生 LOGON 事件時引發。 LOGON 觸發程序不會影響記憶體最佳化的資料表。  
  
## <a name="ddl-triggers"></a>DDL 觸發程序  
 DDL 觸發程序是定義成對其定義所在的資料庫或伺服器執行 CREATE、ALTER、DROP、GRANT、DENY、REVOKE 或 UPDATE STATISTICS 陳述式時引發的觸發程序。  
  
 如果資料庫或伺服器有一個或多個 DDL 觸發程序定義於 CREATE_TABLE 或包含該等觸發程序的任何事件群組，您便無法建立記憶體最佳化的資料表。 如果資料庫或伺服器有一個或多個 DDL 觸發程序定義於 DROP_TABLE 或包含該等觸發程序的任何事件群組，您便無法卸除記憶體最佳化的資料表。  
  
 如果有一個或多個 DDL 觸發程序位於 CREATE_PROCEDURE、DROP_PROCEDURE 或包含這些事件的任何事件群組，您便無法建立原生編譯預存程序。  
  
## <a name="see-also"></a>另請參閱  
 [移轉至 In-Memory OLTP](../../relational-databases/in-memory-oltp/migrating-to-in-memory-oltp.md)  
  
  
