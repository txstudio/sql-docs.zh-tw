---
title: catalog.restore_project (SSISDB 資料庫) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 8adee525-579b-4d2f-b807-e2ecc07fb2e9
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 65c51839f1a2204f7b5b105c637112c3ca23378c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47680396"
---
# <a name="catalogrestoreproject-ssisdb-database"></a>catalog.restore_project (SSISDB 資料庫)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  將 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 目錄中的專案還原到舊版。  
  
## <a name="syntax"></a>語法  
  
```sql  
catalog.restore_project [ @folder_name = ] folder_name  
    , [ @project_name = ] project _name  
    , [ @object_version_lsn = ] object_version_lsn  
  
```  
  
## <a name="arguments"></a>引數  
 [ @folder_name = ] *folder_name*  
 包含專案之資料夾的名稱。 *folder_name* 是 **nvarchar(128)**。  
  
 [ @project _name = ] *project_name*  
 專案的名稱。 *project_name* 是 **nvarchar(128)**。  
  
 [ @object_version_lsn = ] *object_version_lsn*  
 專案的版本。 *object_version_lsn* 是 **bigint**。  
  
## <a name="return-code-value"></a>傳回碼值  
 0 (成功)  
  
## <a name="result-sets"></a>結果集  
 如果找不到 *project_name*，專案詳細資料會以 **varbinary(MAX)** 的方式傳回，當作結果集的一部分。  
  
 如果專案無法還原到指定的資料夾，就會傳回 **NO RESULT SET**。  
  
## <a name="permissions"></a>[權限]  
 這個預存程序需要下列其中一個權限：  
  
-   專案的 READ 和 MODIFY 權限  
  
-   **ssis_admin** 資料庫角色的成員資格  
  
-   **系統管理員**伺服器角色的成員資格  
  
## <a name="errors-and-warnings"></a>錯誤和警告  
 下列清單將描述可能會引發錯誤或警告的某些條件：  
  
-   專案版本不存在或不符合專案名稱  
  
-   專案不存在  
  
-   使用者未具備適當的權限  
  
## <a name="remarks"></a>Remarks  
 還原專案時，會為所有參數會指定預設值，而且所有環境參考都會維持不變。 目錄中保留的專案版本最大數目取決於目錄屬性 **MAX_VERSIONS_PER_PROJECT**，如同 [catalog_property](../../integration-services/system-views/catalog-catalog-properties-ssisdb-database.md) 檢視中所示。  
  
> [!WARNING]  
>  還原專案之後，環境參考可能不再有效。  
  
  
