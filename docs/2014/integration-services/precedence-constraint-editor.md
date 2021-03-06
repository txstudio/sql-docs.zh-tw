---
title: 優先順序條件約束編輯器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.precedenceconstraint.f1
helpviewer_keywords:
- Precedence Constraint Editor dialog box
ms.assetid: b10d4330-6e35-4037-b309-ef56efcd60c5
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c321d7a3850cf91b996262265492b88a6773f446
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48217298"
---
# <a name="precedence-constraint-editor"></a>優先順序條件約束編輯器
  使用 **[優先順序條件約束編輯器]** 對話方塊，即可設定優先順序條件約束。  
  
## <a name="options"></a>選項。  
 **評估作業**  
 指定優先順序條件約束所使用的評估作業。 這些作業有： **[條件約束]**、 **[運算式]**、 **[運算式與條件約束]**，以及 **[運算式或條件約束]**。  
  
 **值**  
 指定下列條件約束值：[成功]、[失敗] 或 [完成]。  
  
> [!NOTE]  
>  優先順序條件約束線條若是綠色代表 [成功]，反白顯示代表 [失敗]，而藍色代表 [完成]。  
  
 **運算式**  
 如果使用 [運算式]、[運算式與條件約束] 或 [運算式或條件約束] 作業，請輸入運算式或啟動運算式產生器以建立運算式。 運算式必須評估為布林。  
  
 **測試**  
 驗證運算式。  
  
 **邏輯 AND**  
 選取即可指定同一個可執行檔上的多個優先順序條件約束必須一起評估。 所有條件約束必須評估為`True`。  
  
> [!NOTE]  
>  此種類型的優先順序條件約束會顯示為綠色、反白顯示或藍色的實線。  
  
 **邏輯 OR**  
 選取即可指定同一個可執行檔上的多個優先順序條件約束必須一起評估。 至少一個條件約束必須評估為`True`。  
  
> [!NOTE]  
>  此種類型的優先順序條件約束會顯示為綠色、反白顯示或藍色的虛線。  
  
## <a name="see-also"></a>另請參閱  
 [優先順序條件約束](control-flow/precedence-constraints.md)   
 [Integration Services 工作](control-flow/integration-services-tasks.md)   
 [Integration Services 容器](control-flow/integration-services-containers.md)   
 [Integration Services &#40;SSIS&#41; 運算式](expressions/integration-services-ssis-expressions.md)  
  
  
