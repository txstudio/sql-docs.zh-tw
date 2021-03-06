---
title: 在 Linux 上的 SQL Server 的安全性限制 |Microsoft Docs
description: 本文說明 SQL Server 上 Linux 的限制。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 01/30/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 64da74cc-14bf-4636-a55e-8cc1fce2aaff
ms.openlocfilehash: 9c58592568ca841df270190970fb76fefe43d96d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47711716"
---
# <a name="security-limitations-for-sql-server-on-linux"></a>在 Linux 上的 SQL Server 的安全性限制

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

在 Linux 上的 SQL Server 目前有下列限制：

* 提供標準的密碼原則。 MUST_CHANGE 是唯一的選項，您可以設定。  
* 不支援可延伸金鑰管理。 
* 不支援使用 Azure Key Vault 中儲存的金鑰。
* SQL Server 會產生自己的自我簽署的憑證，加密連線。 SQL Server 可以設定為使用 TLS 提供憑證的使用者。 

如需有關 SQL Server 中可用的安全性功能的詳細資訊，請參閱 < [SQL Server Database Engine 和 Azure SQL Database 的資訊安全中心](../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)。

## <a name="next-steps"></a>後續步驟

如需常見安全性工作，請參閱[開始使用 Linux 上的 SQL Server 的安全性功能](sql-server-linux-security-get-started.md)。 如需指令碼來變更 TCP 連接埠號碼，SQL Server 目錄中，並設定追蹤旗標或定序，請參閱[設定 SQL Server on Linux 使用 mssql-conf](sql-server-linux-configure-mssql-conf.md)。
