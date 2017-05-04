---
title: "移除聯結 (Visual Database Tools) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- removing joins
- joins [SQL Server], removing
- deleting joins
ms.assetid: ccc212a1-fd13-48d6-85e5-5ff310c34bbd
caps.latest.revision: 3
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 6c7c9503f8b2edd9dce534e2c7a4caed659add86
ms.lasthandoff: 04/11/2017

---
# <a name="remove-joins-visual-database-tools"></a>移除聯結 (Visual Database Tools)
如果不要使用內部聯結或外部聯結來聯結資料表，則可以移除其間的聯結。 例如，您可以移除 [查詢和檢視設計工具](../../ssms/visual-db-tools/query-and-view-designer-tools-visual-database-tools.md) 自動在兩個資料表間建立的聯結。  
  
> [!NOTE]  
> 移除查詢中的聯結，並不會改變資料庫的基礎關聯性。  
  
如果兩個聯結的資料表是查詢的一部份，並且移除其間的所有聯結條件，則產生的查詢會成為兩個資料表相乘，亦即成為 CROSS JOIN。  
  
### <a name="to-remove-a-join"></a>若要移除聯結  
  
-   在 [圖表窗格] [](../../ssms/visual-db-tools/diagram-pane-visual-database-tools.md)中，選取要移除之聯結的聯結線，然後按 DELETE 鍵。 可以一次選取和刪除多重聯結線。  
  
查詢和檢視設計工具會移除聯結線，並隨即變更 [SQL 窗格] [](../../ssms/visual-db-tools/sql-pane-visual-database-tools.md)中的陳述式。  
  
## <a name="see-also"></a>另請參閱  
[自動聯結資料表 &amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/join-tables-automatically-visual-database-tools.md)  
[手動聯結資料表 &amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/join-tables-manually-visual-database-tools.md)  
[使用聯結查詢 &amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/query-with-joins-visual-database-tools.md)  
  
