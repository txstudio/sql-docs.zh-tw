---
title: 備份組 (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- backupset
- backupset_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- backupset system table
- backup media [SQL Server], backupset system table
- backup sets [SQL Server]
ms.assetid: 6ff79bbf-4acf-4f75-926f-38637ca8a943
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7b5bf5ce20678845111a1f410739674c50c7bb61
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47596157"
---
# <a name="backupset-transact-sql"></a>backupset (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  每個備份組各含一個資料列。 「備份組」包含單次成功備份作業的備份。 RESTORE、RESTORE FILELISTONLY、RESTORE HEADERONLY 和 RESTORE VERIFYONLY 陳述式會在位於指定之單一或多重備份裝置上媒體集內單一備份組上操作。  
  
 這份資料表儲存在**msdb**資料庫。  

  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**backup_set_id**|**int**|用來識別備份組的唯一備份組識別碼。 識別，主索引鍵。|  
|**backup_set_uuid**|**uniqueidentifier**|用來識別備份組的唯一備份組識別碼。|  
|**media_set_id**|**int**|用來識別備份組所在媒體集的唯一媒體集識別碼。 參考**backupmediaset （media_set_id)**。|  
|**first_family_number**|**tinyint**|備份組啟動時所在之媒體的家族號碼。 可以是 NULL。|  
|**first_media_number**|**smallint**|備份組啟動時所在之媒體的媒體號碼。 可以是 NULL。|  
|**last_family_number**|**tinyint**|備份組結束時所在之媒體的家族號碼。 可以是 NULL。|  
|**last_media_number**|**smallint**|備份組結束時所在之媒體的媒體號碼。 可以是 NULL。|  
|**catalog_family_number**|**tinyint**|備份組目錄起點所在之媒體的家族號碼。 可以是 NULL。|  
|**catalog_media_number**|**smallint**|備份組目錄起點所在之媒體的媒體號碼。 可以是 NULL。|  
|**位置**|**int**|還原作業用來尋找適當備份組和檔案的備份組位置。 可以是 NULL。 如需詳細資訊，請參閱中的檔案[BACKUP &#40;TRANSACT-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)。|  
|**expiration_date**|**datetime**|備份組到期的日期和時間。 可以是 NULL。|  
|**software_vendor_id**|**int**|寫入備份媒體標頭的軟體供應商識別碼。 可以是 NULL。|  
|**name**|**nvarchar(128)**|備份組的名稱。 可以是 NULL。|  
|**description**|**nvarchar(255)**|備份組的描述。 可以是 NULL。|  
|**user_name**|**nvarchar(128)**|執行備份作業的使用者名稱。 可以是 NULL。|  
|**software_major_version**|**tinyint**|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 主要版本號碼。 可以是 NULL。|  
|**software_minor_version**|**tinyint**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 次要版本號碼。 可以是 NULL。|  
|**software_build_version**|**smallint**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組建編號。 可以是 NULL。|  
|**time_zone**|**smallint**|本機時間 (備份作業所在位置) 和國際標準時間 (UTC) 的時差，間隔是 15 分鐘。 值可以是 -48 至 +48，頭尾包括在內。 127 值表示未知。 例如，-20 是美東標準時間 (EST) 或 UTC 之後 5 小時。 可以是 NULL。|  
|**mtf_minor_version**|**tinyint**|[!INCLUDE[msCoName](../../includes/msconame-md.md)] Tape Format 次要版本號碼。 可以是 NULL。|  
|**first_lsn**|**numeric(25,0)**|備份組中第一個或最舊記錄檔記錄的記錄序號。 可以是 NULL。|  
|**last_lsn**|**numeric(25,0)**|備份組之後下一個記錄檔記錄的記錄序號。 可以是 NULL。|  
|**checkpoint_lsn**|**numeric(25,0)**|必須啟動重做的記錄之記錄序號。 可以是 NULL。|  
|**database_backup_lsn**|**numeric(25,0)**|最近的完整資料庫備份之記錄序號。 可以是 NULL。<br /><br /> **database_backup_lsn**是 「 檢查點的 「 備份啟動時觸發。 將會符合這個 LSN **first_lsn**如果在進行備份時資料庫處於閒置狀態，且沒有設定任何複寫。|  
|**database_creation_date**|**datetime**|最初建立資料庫的日期和時間。 可以是 NULL。|  
|**backup_start_date**|**datetime**|備份作業開始的日期和時間。 可以是 NULL。|  
|**backup_finish_date**|**datetime**|備份作業完成的日期和時間。 可以是 NULL。|  
|**type**|**char(1)**|這是備份類型， 可為以下項目：<br /><br /> D = 資料庫<br /><br /> I = 差異資料庫<br /><br /> L = 記錄<br /><br /> F = 檔案或檔案群組<br /><br /> G = 差異檔案<br /><br /> P = 部分<br /><br /> Q = 差異部分<br /><br /> 可以是 NULL。|  
|**sort_order**|**smallint**|執行備份作業的伺服器排序順序。 可以是 NULL。 如需有關排序次序和定序的詳細資訊，請參閱 < [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md)。|  
|**字碼頁**|**smallint**|執行備份作業的伺服器字碼頁。 可以是 NULL。 如需字碼頁的詳細資訊，請參閱[Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md)。|  
|**compatibility_level**|**tinyint**|這是資料庫的相容性層級設定， 可為以下項目：<br /><br /> 90 = [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]<br /><br /> 100 = [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]<br /><br /> 110 = [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]<br /><br /> 120 = [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]<br /><br /> 可以是 NULL。<br /><br /> 如需相容性層級的詳細資訊，請參閱 [ALTER DATABASE 相容性層級 &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)。|  
|**database_version**|**int**|資料庫版本號碼。 可以是 NULL。|  
|**backup_size**|**numeric(20,0)**|備份組的大小 (以位元組為單位)。 可以是 NULL。 VSS 的備份，backupset 會是估計的值。|  
|**database_name**|**nvarchar(128)**|執行備份所涉及的資料庫名稱。 可以是 NULL。|  
|**server_name**|**nvarchar(128)**|執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 備份作業的伺服器名稱。 可以是 NULL。|  
|**machine_name**|**nvarchar(128)**|執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的電腦名稱。 可以是 NULL。|  
|**flags**|**int**|在  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，則**旗標**資料行已被取代，取代下列的位元資料行：<br /><br /> **has_bulk_logged_data** <br /> **is_snapshot** <br /> **is_readonly** <br /> **is_single_user** <br /> **has_backup_checksums** <br /> **is_damaged** <br /> **begins_log_chain** <br /> **has_incomplete_metadata** <br /> **is_force_offline** <br /> **is_copy_only**<br /><br /> 可以是 NULL。<br /><br /> 在較早 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本的備份組中，旗標位元的狀況如下：<br />1 = 備份包含記錄最少的資料。 <br />2 = 使用 WITH SNAPSHOT。 <br />4 = 當備份時，資料庫是唯讀的。<br />8 = 當備份時，資料庫在單一使用者模式中。|  
|**unicode_locale**|**int**|Unicode 地區設定。 可以是 NULL。|  
|**unicode_compare_style**|**int**|Unicode 比較樣式。 可以是 NULL。|  
|**collation_name**|**nvarchar(128)**|定序名稱。 可以是 NULL。|  
|**Is_password_protected**|**bit**|備份組<br /><br /> 是否有密碼保護：<br /><br /> 0 = 無保護<br /><br /> 1 = 保護|  
|**recovery_model**|**nvarchar(60)**|資料庫的復原模式：<br /><br /> FULL<br /><br /> BULK-LOGGED<br /><br /> SIMPLE|  
|**has_bulk_logged_data**|**bit**|1 = 備份包含大量記錄資料。|  
|**is_snapshot**|**bit**|1 = 備份是利用 SNAPSHOT 選項所取得。|  
|**is_readonly**|**bit**|1 = 當備份時，資料庫是唯讀的。|  
|**is_single_user**|**bit**|1 = 當備份時，資料庫是單一使用者。|  
|**has_backup_checksums**|**bit**|1 = 備份包含備份總和檢查碼。|  
|**is_damaged**|**bit**|1 = 建立這個備份時，偵測到資料庫損毀。 要求備份作業忽略錯誤，繼續作業。|  
|**begins_log_chain**|**bit**|1 = 這是連續記錄備份鏈結中的第一個記錄備份。 記錄鏈結的開頭是建立資料庫之後，或從簡單復原模式切換到完整或大量記錄復原模式之後，所取出的第一個記錄備份。|  
|**has_incomplete_metadata**|**bit**|1 = 包含不完整中繼資料的結尾記錄備份。 如需詳細資訊，請參閱[結尾記錄備份 &#40;SQL Server&#41;](../../relational-databases/backup-restore/tail-log-backups-sql-server.md)。|  
|**is_force_offline**|**bit**|1 = 當取得備份時，利用 NORECOVERY 選項使資料庫離線。|  
|**is_copy_only**|**bit**|1 = 僅限複製的備份。 如需詳細資訊，請參閱[只複製備份 &#40;SQL Server&#41;](../../relational-databases/backup-restore/copy-only-backups-sql-server.md)。|  
|**first_recovery_fork_guid**|**uniqueidentifier**|起始復原分岔的識別碼。 這會對應至**FirstRecoveryForkID** RESTORE HEADERONLY。<br /><br /> 備份資料，如**first_recovery_fork_guid** equals **last_recovery_fork_guid**。|  
|**last_recovery_fork_guid**|**uniqueidentifier**|結尾復原分岔的識別碼。 這會對應至**RecoveryForkID** RESTORE HEADERONLY。<br /><br /> 備份資料，如**first_recovery_fork_guid** equals **last_recovery_fork_guid**。|  
|**fork_point_lsn**|**numeric(25,0)**|如果**first_recovery_fork_guid**不等於**last_recovery_fork_guid**，這就是分岔點的記錄序號。 否則，這個值是 NULL。|  
|**database_guid**|**uniqueidentifier**|資料庫的唯一識別碼。 這會對應至**BindingID** RESTORE HEADERONLY。 當還原資料庫時，會指派一個新值。|  
|**family_guid**|**uniqueidentifier**|建立時原始資料庫的唯一識別碼。 當還原資料庫時，即使還原成不同的名稱，這個值也會維持不變。|  
|**differential_base_lsn**|**numeric(25,0)**|差異備份的基底 LSN。 單一的差異備份;變更 lsn 大於或等於**differential_base_lsn**併入差異備份中。<br /><br /> 對於基底差異備份，這個值會是 NULL，且基底 LSN 必須取決於檔案層級 (請參閱[backupfile &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/backupfile-transact-sql.md))。<br /><br /> 如果是非差異備份類型，這個值永遠是 NULL。|  
|**differential_base_guid**|**uniqueidentifier**|如果是單一基底差異備份，這個值就是差異基底的唯一識別碼。<br /><br /> 如果是多重基底差異備份，這個值就是 NULL，差異基底必須取決於檔案層級。<br /><br /> 如果是非差異備份類型，這個值就是 NULL。|  
|**compressed_backup_size**|**Numeric(20,0)**|儲存於磁碟上之備份的總位元組數。<br /><br /> 若要計算壓縮比，請使用**backup_size**並**backupset**。<br /><br /> 期間**msdb**升級時，此值設定為 NULL。 這表示非壓縮的備份。|  
|**key_algorithm**|**nvarchar(32)**|用於加密備份的加密演算法。 NO_Encryption 值表示備份未加密。|  
|**encryptor_thumbprint**|**varbinary(20)**|加密程式指模，可用來尋找資料庫中的憑證或非對稱金鑰。 在備份未加密的情況下，這個值是 NULL。|  
|**encryptor_type**|**nvarchar(32)**|使用的加密程式類型：憑證或非對稱金鑰。 . 在備份未加密的情況下，這個值是 NULL。|  
  
## <a name="remarks"></a>備註  
 RESTORE VERIFYONLY FROM *backup_device* WITH LOADHISTORY 會的資料行**backupmediaset**媒體集標頭的適當值的資料表。  
  
 若要減少此資料表和其他備份和記錄資料表中的資料列數目，請執行[sp_delete_backuphistory](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md)預存程序。  
  
## <a name="see-also"></a>另請參閱  
 [備份與還原資料表&#40;Transact SQL&#41;](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)   
 [backupfile &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupfile-transact-sql.md)   
 [backupfilegroup &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupfilegroup-transact-sql.md)   
 [backupmediafamily &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupmediafamily-transact-sql.md)   
 [backupmediaset &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupmediaset-transact-sql.md)   
 [備份和還原期間可能發生的媒體錯誤 &#40;SQL Server&#41;](../../relational-databases/backup-restore/possible-media-errors-during-backup-and-restore-sql-server.md)   
 [媒體集、媒體家族與備份組 &#40;SQL Server&#41;](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md)   
 [復原模式 &#40;SQL Server&#41;](../../relational-databases/backup-restore/recovery-models-sql-server.md)   
 [RESTORE HEADERONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-headeronly-transact-sql.md)   
 [備份與還原資料表&#40;Transact SQL&#41;](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)  
  
  
