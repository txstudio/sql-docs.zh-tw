---
title: 實作轉譯延伸模組 | Microsoft Docs
ms.date: 03/16/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: extensions
ms.topic: reference
helpviewer_keywords:
- rendering extensions [Reporting Services]
- custom rendering extensions [Reporting Services]
- transformations [Reporting Services]
- extensions [Reporting Services], rendering
- rendering extensions [Reporting Services], implementing
ms.assetid: 4a5c64f5-2391-4597-ba3f-81d265b23703
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 56a8294775ccb51cd216c2cd72c955bd9379c004
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47643746"
---
# <a name="implementing-a-rendering-extension"></a>實作轉譯延伸模組
  轉譯延伸模組是報表伺服器的元件或模組，可將報表資料與配置資訊轉換成裝置特定的格式。 SQL Server Reporting Services 包含六個轉譯延伸模組：HTML、Excel、Word、CSV 或 Text、XML、Image 和 PDF。 您可以建立其他轉譯延伸模組，以產生其他格式的報表。  
  
> [!NOTE]  
>  若要決定可以使用哪些轉譯延伸模組，您可以檢視在 RSReportServer.config 檔案中已安裝的延伸模組清單。  
  
## <a name="in-this-section"></a>本節內容  
 [轉譯延伸模組概觀](../../../reporting-services/extensions/rendering-extension/rendering-extensions-overview.md)  
 介紹如何撰寫 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 的自訂轉譯延伸模組。  
  
 [實作 IRenderingExtension 介面](../../../reporting-services/extensions/rendering-extension/implementing-the-irenderingextension-interface.md)  
 描述轉譯延伸模組的屬性。  
  
 [部署轉譯延伸模組](../../../reporting-services/extensions/rendering-extension/deploying-a-rendering-extension.md)  
 描述如何在報表伺服器上部署轉譯延伸模組。  
  
 [移除轉譯延伸模組](../../../reporting-services/extensions/rendering-extension/removing-a-rendering-extension.md)  
 描述如何從報表伺服器移除轉譯延伸模組。  
  
## <a name="see-also"></a>另請參閱  
 [Reporting Services 延伸模組](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Reporting Services 延伸模組程式庫](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
