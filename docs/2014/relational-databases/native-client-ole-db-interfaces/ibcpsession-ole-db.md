---
title: IBCPSession (OLE DB) |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- IBCPSession interface
ms.assetid: 00d0311f-8b71-4ad6-824d-0e89119347a3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 142f6ac339e437877c485588333fabb04e0bd66b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48212318"
---
# <a name="ibcpsession-ole-db"></a>IBCPSession (OLE DB)
  **IBCPSession** 介面會公開以 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 檔案為基礎之大量複製作業的支援。 **IBCPSession**介面會公開在[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者在相同的層級下與工作階段。 在  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者，資料來源物件是工作階段物件的 factory，而且大量複製作業指定於連接屬性 ssprop_enablebulkcopy。 此外，SSPROP_ENABLEFASTLOAD 屬性應該要設定為 true。  
  
 然後，呼叫 **IDBCreateSession::CreateSession** 方法將會導致建立 **BulkCopySession** 物件。 所有透過 **IBCPSession** 物件公開之以檔案為基礎的大量複製方法會變成可在這個 **IBCPSession** 物件的 **IBCPSession** 介面上使用幾乎相同的簽章進行呼叫。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者支援透過以記憶體為基礎的大量複製作業[IRowsetFastLoad](irowsetfastload-ole-db.md)介面。  
  
 如需使用詳細資訊[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者大量複製作業，請參閱[執行大量複製作業](../native-client/features/performing-bulk-copy-operations.md)。  
  
 如需示範如何使用範例**IBCPSession**介面，請參閱[IBCPSession::BCPDone &#40;OLE DB&#41;](ibcpsession-bcpdone-ole-db.md)。  
  
## <a name="in-this-section"></a>本節內容  
  
|方法|描述|  
|------------|-----------------|  
|[Ibcpsession:: Bcpcolfmt &#40;OLE DB&#41;](ibcpsession-bcpcolfmt-ole-db.md)|在程式變數與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料行之間建立繫結。|  
|[Ibcpsession:: Bcpcolumns &#40;OLE DB&#41;](ibcpsession-bcpcolumns-ole-db.md)|設定要繫結至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表中之資料行的欄位數目。|  
|[Ibcpsession:: Bcpcontrol &#40;OLE DB&#41;](ibcpsession-bcpcontrol-ole-db.md)|設定大量複製作業的選項。|  
|[IBCPSession::BCPDone &#40;OLE DB&#41;](ibcpsession-bcpdone-ole-db.md)|認可要傳送至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的其餘資料列。|  
|[Bcpexec &#40;OLE DB&#41;](ibcpsession-bcpexec-ole-db.md)|執行大量複製作業。|  
|[Ibcpsession:: Bcpinit &#40;OLE DB&#41;](ibcpsession-bcpinit-ole-db.md)|初始化大量複製結構、執行一些錯誤檢查、確認資料和格式檔案名稱正確無誤，然後開啟這些項目。|  
|[Ibcpsession:: Bcpreadfmt &#40;OLE DB&#41;](ibcpsession-bcpreadfmt-ole-db.md)|從格式檔案中讀取每個資料行的格式資訊。|  
|[Ibcpsession:: Bcpwritefmt &#40;OLE DB&#41;](ibcpsession-bcpwritefmt-ole-db.md)|將每個資料行的格式資訊寫入格式檔案。|  
  
## <a name="see-also"></a>另請參閱  
 [介面&#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md)  
  
  
