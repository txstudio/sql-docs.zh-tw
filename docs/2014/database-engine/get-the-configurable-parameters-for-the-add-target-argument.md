---
title: 取得 ADD TARGET 引數的可設定的參數 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- extended events [SQL Server], ADD TARGET argument
- xe
ms.assetid: 08454543-c5c8-4ca3-9af9-f1d82264471c
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 368f019453fe0c8f5fcbef245db3f4b50769a210
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48223148"
---
# <a name="get-the-configurable-parameters-for-the-add-target-argument"></a>取得 ADD TARGET 引數的可設定參數
  完成此工作涉及在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中使用查詢編輯器。  
  
 當此程序中的陳述式完成之後，查詢編輯器的 **[結果]** 索引標籤會顯示以下資料行：  
  
-   package_name  
  
-   target_name  
  
-   parameter_name  
  
-   parameter_type  
  
-   required  
  
##  <a name="BeforeYouBegin"></a> 開始之前  
 在您建立 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 擴充的事件工作階段之前，當您在 CREATE EVENT SESSION 或 ALTER EVENT SESSION 中使用 ADD TARGET 引數時，尋找您可以設定的參數會非常有用。  
  
### <a name="to-get-the-configurable-parameters-for-the-add-target-argument-using-query-editor"></a>使用查詢編輯器取得 ADD TARGET 引數的可設定參數  
  
-   在查詢編輯器中，發出下列陳述式。  
  
    ```  
    SELECT p.name package_name, o.name target_name, c.name parameter_name,   
    c.type_name parameter_type, CASE c.capabilities_desc WHEN 'mandatory' THEN 'yes' ELSE 'no' END   
    required   
    FROM sys.dm_xe_objects o JOIN sys.dm_xe_packages p ON o.package_guid = p.guid   
    JOIN sys.dm_xe_object_columns c ON o.name = c.object_name AND c.column_type = 'customizable'  
    WHERE o.object_type = 'target'   
    ORDER BY package_name, target_name, required DESC  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql)   
 [ALTER EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-event-session-transact-sql)   
 [sys.dm_xe_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql)   
 [sys.dm_xe_packages &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-packages-transact-sql)  
  
  
