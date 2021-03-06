---
title: 移除轉譯延伸模組 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- deleting rendering extensions
- removing rendering extensions
- rendering extensions [Reporting Services], removing
ms.assetid: 2abfebfb-065f-45cc-a904-c914394cf900
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 4e9abf2254d9c9710e68df9b488321b4ae4c1b16
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48132958"
---
# <a name="removing-a-rendering-extension"></a>移除轉譯延伸模組
  若要移除[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]轉譯延伸模組，只要移除`Extension`項目，為您的轉譯延伸模組，從 rsreportserver.config 檔案，位於 **%ProgramFiles%\Microsoft SQL server\msrs10_50.<instancename>\reporting。\<執行個體名稱 > services\reportserver**資料夾。 如果您對報表設計工具，以及報表伺服器項目，移除`Extension`項目[RSReportDesigner Configuration File](../../report-server/rsreportdesigner-configuration-file.md)以及。 在移除組態資訊之後，轉譯延伸模組將無法再供元件使用。  
  
## <a name="see-also"></a>另請參閱  
 [Reporting Services 組態檔](../../report-server/reporting-services-configuration-files.md)   
 [實作轉譯延伸模組](implementing-a-rendering-extension.md)   
 [轉譯延伸模組概觀](rendering-extensions-overview.md)   
 [實作 IRenderingExtension 介面](implementing-the-irenderingextension-interface.md)   
 [延伸模組的安全性考量](../security-considerations-for-extensions.md)   
 [部署轉譯延伸模組](deploying-a-rendering-extension.md)  
  
  
