---
title: 使用者定義成員屬性 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- custom member properties [MDX]
ms.assetid: b64cc581-e784-42c4-bec8-932abd687423
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 97f7a61772b93c78173f3eca8ad38fca1ade671a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48114308"
---
# <a name="user-defined-member-properties-mdx"></a>使用者自訂成員屬性 (MDX)
  使用者自訂成員屬性可以做為屬性關聯性，增加到維度中的特定具名層級。 使用者自訂成員屬性無法加入`(All)`層級的階層或階層本身。  
  
## <a name="creating-user-defined-member-properties"></a>建立使用者自訂成員屬性  
 您可以透過使用者介面或以程式設計的方式，將使用者自訂成員屬性增加到伺服器維度或 Cube：  
  
-   若要透過使用者介面加入使用者定義成員屬性，您可以使用 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]中的維度設計師。 如需詳細資訊，請參閱 [定義屬性關聯性](../attribute-relationships-define.md)。  
  
-   若要以程式設計方式加入使用者定義的成員屬性，您的應用程式可以使用分析管理物件 (AMO)，或 XML for Analysis (XMLA) 及 Analysis Services 指令碼語言 (ASSL) 的組合。 如需詳細資訊，請參閱 [屬性關聯性](../../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)。  
  
## <a name="retrieving-user-defined-member-properties"></a>擷取使用者自訂成員屬性  
 您可以擷取使用的使用者自訂成員屬性`PROPERTIES`關鍵字或[屬性](/sql/mdx/properties-mdx)函式。  
  
### <a name="using-the-properties-keyword-to-retrieve-user-defined-member-properties"></a>使用 PROPERTIES 關鍵字擷取使用者自訂成員屬性  
 擷取使用者自訂成員屬性的語法，跟用以擷取內建層級成員屬性的語法類似，如以下語法所示：  
  
 `DIMENSION PROPERTIES [Dimension.]Level.<Custom_Member_Property>`  
  
 `PROPERTIES`關鍵字會在座標軸規格的集合運算式後面出現。 例如，下列 MDX 查詢`PROPERTIES`關鍵字來擷取`List Price`和`Dealer Price`使用者自訂成員屬性及集合運算式，可識別產品銷售年 1 月之後顯示：  
  
```  
SELECT   
   CROSSJOIN([Ship Date].[Calendar].[Calendar Year].Members,   
             [Measures].[Sales Amount]) ON COLUMNS,  
   NON EMPTY Product.Product.MEMBERS  
   DIMENSION PROPERTIES   
              Product.Product.[List Price],  
              Product.Product.[Dealer Price]  ON ROWS  
FROM [Adventure Works]  
WHERE ([Date].[Month of Year].[January])   
```  
  
### <a name="using-the-properties-function-to-retrieve-user-defined-member-properties"></a>使用 Properties 函數擷取使用者自訂成員屬性  
 或者，您可以使用 `Properties` 函數來存取自訂成員屬性。 例如，下列 MDX 查詢會使用`WITH`關鍵字來建立導出的成員組成`List Price`成員屬性：  
  
```  
WITH   
   MEMBER [Measures].[Product List Price] AS  
   [Product].[Product].CurrentMember.Properties("List Price")  
SELECT   
   [Measures].[Product List Price] on COLUMNS,  
   [Product].[Product].MEMBERS  ON Rows  
FROM [Adventure Works]  
```  
  
 如需建立導出成員的詳細資訊，請參閱[在 MDX 中建立導出成員 &#40;MDX&#41;](mdx-calculated-members-building-calculated-members.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用成員屬性&#40;MDX&#41;](mdx-member-properties.md)   
 [屬性&#40;MDX&#41;](/sql/mdx/properties-mdx)  
  
  
