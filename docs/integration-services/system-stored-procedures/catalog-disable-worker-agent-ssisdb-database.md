---
title: catalog.disable_worker_agent (SSISDB 資料庫) | Microsoft Docs
ms.custom: ''
ms.date: 12/16/2016
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3f19dc4c-a000-4318-8fe1-e80d56720e66
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 13e5020ab3f29300e4fd9f6cc81f77a19763f79d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47683326"
---
# <a name="catalogdisableworkeragent-ssisdb-database"></a>catalog.disable_worker_agent (SSISDB 資料庫)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

停用處理此 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 目錄之 Scale Out Master 的 Scale Out Worker。

## <a name="syntax"></a>語法

```sql
catalog.disable_worker_agent [@WorkerAgentId =] WorkerAgentId
```
## <a name="arguments"></a>引數
[@WorkerAgentId =] *WorkerAgentId*：Scale Out Worker 的背景工作代理程式識別碼。 *WorkerAgentId* 是 **uniqueidentifier**。

## <a name="example"></a>範例
這個範例會在 MachineA 上停用 Scale Out Worker。

```sql
SELECT WorkerAgentId, MachineName FROM [catalog].[worker_agents]
GO
-- Result: --
-- WorkerAgentId                           MachineName --
-- 6583054A-E915-4C2A-80E4-C765E79EF61D    MachineA    --

EXEC [catalog].[disable_worker_agent] '6583054A-E915-4C2A-80E4-C765E79EF61D'
GO 
```

## <a name="return-code-value"></a>傳回碼值  
 0 (成功)  
  
## <a name="result-sets"></a>結果集  
 None  

## <a name="permissions"></a>[權限]  
 這個預存程序需要下列其中一個權限：  
  
-   **ssis_admin** 資料庫角色的成員資格  
  
-   **系統管理員**伺服器角色的成員資格 

## <a name="errors-and-warnings"></a>錯誤和警告
如果背景工作代理程式識別碼無效，則預存程序會傳回錯誤。
