---
title: sp_grant_publication_access (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_grant_publication_access_TSQL
- sp_grant_publication_access
helpviewer_keywords:
- sp_grant_publication_access
ms.assetid: 17993952-def6-4a16-b1c1-323ec42967f8
ms.author: vanto
manager: craigg
ms.openlocfilehash: 79367d67503f28c84a1199cfa7c74243e30eadad
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47852046"
---
# <a name="spgrantpublicationaccess-transact-sql"></a>sp_grant_publication_access (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  將登入加入發行集的存取清單中。 這個預存程序執行於發行集資料庫的發行者端。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_grant_publication_access [ @publication = ] 'publication', [ @login = ] 'login'   
    [ , [ @reserved = ] 'reserved' ]  
```  
  
## <a name="arguments"></a>引數  
 [ **@publication**=] **'***發行集***'**  
 這是要存取的發行集名稱。 **'***出版物***'** 是**sysname**，沒有預設值。  
  
 [ **@login**=] **'***登入***'**  
 這是登入識別碼。 **'***登入***'** 是**sysname**，沒有預設值。  
  
 [  **@reserved =**] **'***保留***'**  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="remarks"></a>備註  
 **sp_grant_publication_access**用於快照式、 交易式和合併式複寫。  
  
 這個預存程序可以重複呼叫。  
  
## <a name="permissions"></a>Permissions  
 只有成員**sysadmin**固定的伺服器角色或**db_owner**固定的資料庫角色可以執行**sp_grant_publication_access**。  
  
## <a name="see-also"></a>另請參閱  
 [sp_help_publication_access &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-help-publication-access-transact-sql.md)   
 [sp_revoke_publication_access &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-revoke-publication-access-transact-sql.md)   
 [保護發行者](../../relational-databases/replication/security/secure-the-publisher.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
