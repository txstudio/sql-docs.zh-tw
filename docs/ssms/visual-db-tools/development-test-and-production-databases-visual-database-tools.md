---
title: 開發、測試和生產資料庫 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- production databases [SQL Server]
- testing databases
- database testing [SQL Server]
ms.assetid: cb403330-8cbe-41c6-bd23-bc432d50f173
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 214c70d9c71053b81e81b9228bca5b42167eabc5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47684209"
---
# <a name="development-test-and-production-databases-visual-database-tools"></a>開發、測試和生產資料庫 (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
如果您有兩個結構完全相同的資料庫，您可以變更其中一個資料庫，然後再將這些變更傳播到另一個資料庫。 例如，如果您具備個人開發資料庫和群組測試資料庫，您可以修改開發資料庫，然後將這些變更傳播到測試資料庫。  
  
若要完成此工作，請在單一工作階段中對開發資料庫執行所有的修改，建立工作階段的變更指令碼 (Change Script)，然後在測試資料庫中執行此指令碼。  
  
## <a name="see-also"></a>另請參閱  
[多使用者環境 &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/multiuser-environments-visual-database-tools.md)  
  
