---
title: 啟用 PowerPivot 功能整合在管理中心為網站集合 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 62a27e53-446a-42d7-b5db-c009e02d4904
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e22c18ef92fbc82401bb9f8294e42971fcdb41c1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48141678"
---
# <a name="activate-powerpivot-feature-integration-for-site-collections-in-central-administration"></a>在管理中心為網站集合啟用 PowerPivot 功能整合
  如果您使用 [現有的伺服陣列] 安裝選項來安裝 SQL Server PowerPivot for SharePoint，就需要為特定的網站集合啟用 PowerPivot 功能整合。 如果您已使用 [新的伺服器] 選項來安裝 PowerPivot for SharePoint，您可以略過這項工作，因為 SQL Server 安裝程式已經在設定部署時，針對根網站集合啟用 PowerPivot 功能整合。  
  
 網站集合層級的功能啟用對於將應用程式頁面和範本提供給網站使用 (包括排程資料重新整理的組態頁面，以及 PowerPivot 圖庫和資料摘要文件庫的應用程式頁面) 是必要的。  
  
 您必須為每個支援 PowerPivot 查詢處理的網站集合啟用 PowerPivot 整合。  
  
## <a name="prerequisites"></a>先決條件  
 您必須是網站集合管理員。  
  
## <a name="activate-powerpivot-features"></a>啟用 PowerPivot 功能  
  
1.  按一下 SharePoint 網站上的 [網站動作]。  
  
     根據預設，SharePoint Web 應用程式會經由通訊埠 80 進行存取。 這表示您通常可以存取 SharePoint 網站中輸入 http://\<電腦名稱 > 以開啟根網站集合。  
  
2.  按一下 **[站台設定]**。  
  
3.  按一下 [網站集合管理] 中的 [網站集合功能]。  
  
4.  捲動頁面，直到您找到**PowerPivot 整合網站集合功能**。  
  
5.  按一下 **[啟用]**。  
  
6.  開啟每個網站並按一下 [網站動作]，為其他網站集合重複執行。  
  
## <a name="see-also"></a>另請參閱  
 [管理中心的 PowerPivot 伺服器管理和組態](power-pivot-server-administration-and-configuration-in-central-administration.md)   
 [初始設定&#40;PowerPivot for SharePoint&#41;](../../sql-server/install/initial-configuration-powerpivot-for-sharepoint.md)   
 [PowerPivot for SharePoint 2010 安裝](../../sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
