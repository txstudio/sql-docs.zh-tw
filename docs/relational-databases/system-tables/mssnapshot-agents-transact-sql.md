---
title: MSsnapshot_agents (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSsnapshot_agents
- MSsnapshot_agents_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSsnapshot_agents system table
ms.assetid: aeae0a2e-4c21-4c45-be65-1e426fa52bdd
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a0890b30946f2a2033d43712e62fc031fa8451c8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47836396"
---
# <a name="mssnapshotagents-transact-sql"></a>MSsnapshot_agents (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSsnapshot_agents**資料表包含一個資料列與本機散發者相關聯的每個快照集代理程式。 這份資料表儲存在散發資料庫中。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**id**|**int**|快照集代理程式的識別碼。|  
|**name**|**nvarchar(100)**|快照集代理程式的名稱。|  
|**publisher_id**|**smallint**|發行者的識別碼。|  
|**publisher_db**|**sysname**|發行者資料庫的名稱。|  
|**發行集**|**sysname**|發行集的名稱。|  
|**publication_type**|**int**|發行集類型：<br /><br /> **0** = 交易式。<br /><br /> **1** = 快照集。<br /><br /> **2** = 合併式。|  
|**local_job**|**bit**|指出本機散發者是否有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業。|  
|**job_id**|**binary(16)**|作業識別碼。|  
|**profile_id**|**int**|設定識別碼，從[MSagent_profiles &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-tables/msagent-profiles-transact-sql.md)資料表。|  
|**dynamic_filter_login**|**sysname**|值，用來評估[SUSER_SNAME &#40;TRANSACT-SQL&#41; ](../../t-sql/functions/suser-sname-transact-sql.md)定義資料分割的參數化篩選中的函式。 這個資料行供資料分割快照集使用。|  
|**dynamic_filter_hostname**|**sysname**|值，用來評估[HOST_NAME &#40;TRANSACT-SQL&#41; ](../../t-sql/functions/host-name-transact-sql.md)定義資料分割的參數化篩選中的函式。 這個資料行供資料分割快照集使用。|  
|**publisher_security_mode**|**smallint**|連接到發行者時，代理程式所用的安全性模式，它可以是下列項目之一：<br /><br /> **0**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]驗證<br /><br /> **1**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 驗證。|  
|**publisher_login**|**sysname**|連接到發行者時所用的登入。|  
|**publisher_password**|**nvarchar(524)**|連接到發行者時，所用之密碼的加密值。|  
|**job_step_uid**|**uniqueidentifier**|用來啟動代理程式之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業步驟的唯一識別碼。|  
|**job_login**|**sysname**||  
|**job_password**|**nvarchar(524)**||  
  
## <a name="see-also"></a>另請參閱  
 [複寫資料表&#40;Transact SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [複寫檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
