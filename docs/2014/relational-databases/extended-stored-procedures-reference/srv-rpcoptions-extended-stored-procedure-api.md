---
title: srv_rpcoptions (擴充預存程序 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
api_name:
- srv_rpcoptions
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcoptions
ms.assetid: dbcce5d1-d5a1-4379-9597-04e43af5923d
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 97a30b223df8420ba67aef21d9b7837b2d4e5557
ms.sourcegitcommit: 110e5e09ab3f301c530c3f6363013239febf0ce5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/10/2018
ms.locfileid: "48905909"
---
# <a name="srvrpcoptions-extended-stored-procedure-api"></a>srv_rpcoptions (擴充預存程序 API)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] 請改用 CLR 整合。  
  
 傳回目前遠端預存程序的執行階段選項。  
  
## <a name="syntax"></a>語法  
  
```  
  
DBUSMALLINT srv_rpcoptions ( SRV_PROC *  
srvproc   
);  
  
```  
  
## <a name="arguments"></a>引數  
 *srvproc*  
 是 SRV_PROC 結構的指標，也是特定用戶端連接的控制代碼 (在這個狀況之下，該控制代碼會收到遠端預存程序)。 擴充預存程序 API 程式庫會使用該結構所包含的資訊來管理應用程式與用戶端之間的通訊和資料。  
  
## <a name="returns"></a>傳回值  
 是點陣圖，包含聯結在目前遠端預存程序的邏輯 OR 之執行階段旗標。 如果沒有目前遠端預存程序，則會傳回 0 ，並且產生訊息。  
  
## <a name="remarks"></a>備註  
 下表描述每個執行階段旗標。  
  
|執行階段旗標|描述|  
|--------------------|-----------------|  
|SRV_NOMETADATA|用戶端已要求不含中繼資料資訊的結果。 只有在用戶端與 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體通訊時，才會使用這個旗標。 擴充預存程序 API 應用程式無法省略中繼資料資訊。|  
|SRV_RECOMPILE|用戶端已經要求先重新編譯遠端預存程序，再執行它。 這個旗標可能無法套用至擴充預存程序 API 應用程式。|  
  
> [!IMPORTANT]  
>  您應該徹底檢閱擴充預存程序的原始程式碼，您也應該先測試編譯過的 DLL，才能將它們安裝在實際執行伺服器上。 如需安全性檢閱和測試的資訊，請參閱此 [Microsoft 網站](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/)。  
  
  
