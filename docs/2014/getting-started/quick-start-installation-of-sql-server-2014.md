---
title: 快速入門的 SQL Server 2014 安裝 |Microsoft Docs
ms.custom: ''
ms.date: 05/25/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- data-quality-services
- database-engine
- integration-services
- master-data-services
- replication
- reporting-services-native
- reporting-services-sharepoint
ms.topic: conceptual
helpviewer_keywords:
- quick start installation [SQL Server]
- installation [SQL Server]
- installing SQL Server, quick start installations
ms.assetid: 672afac9-364d-4946-ad5d-8a2d89cf8d81
author: mightypen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c682b29a4265b9c6955b440dc45e4920ca87d081
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48223378"
---
# <a name="quick-start-installation-of-sql-server-2014"></a>SQL Server 2014 快速入門安裝
    
## <a name="introduction"></a>簡介  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 安裝精靈是以 Windows Installer 為基礎。 它提供了安裝下列 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 元件的單一功能樹狀目錄：  
  
-   [!INCLUDE[ssDE](../includes/ssde-md.md)]  
  
-   [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]  
  
-   [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]  
  
-   [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]  
  
-   [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)]  
  
-   管理工具  
  
-   連接元件  
  
 您可以個別安裝每個元件，也可以選取上面所列出元件的組合。 在中提供版本及元件之間最好的選擇[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]，請參閱 < [Edition 和 SQL Server 2014 元件](../sql-server/editions-and-components-of-sql-server-2016.md)。  
  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 有 32 位元和 64 位元兩種版本。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 安裝程式支援下列安裝選項：  
  
-   **安裝精靈**  
  
     請參閱[從安裝精靈安裝 SQL Server 2014&#40;安裝&#41;](../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)如需安裝程序性資訊[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]使用安裝精靈。  
  
-   **命令提示字元**  
  
     請參閱[從命令提示字元安裝 SQL Server 2014](../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)執行自動的安裝的範例語法和安裝參數。  
  
-   **組態檔**  
  
     請參閱[安裝 SQL Server 2014 使用組態檔](../database-engine/install-windows/install-sql-server-using-a-configuration-file.md)透過組態檔執行安裝程式的範例語法及安裝參數。  
  
-   **SysPrep**  
  
     請參閱[SysPrep 安裝 SQL Server 2014 使用](../database-engine/install-windows/install-sql-server-using-sysprep.md)如需安裝程序性資訊[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]使用 SysPrep。  
  
-   **Server Core 安裝**  
  
     請參閱[在 Server Core 上安裝 SQL Server 2014](../database-engine/install-windows/install-sql-server-on-server-core.md)如需安裝程序性資訊[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]在 Windows Server Core 上。  
  
-   **[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] BI 功能安裝**  
  
     請參閱[安裝 SQL Server 2014 BI 功能](../sql-server/install/install-sql-server-business-intelligence-features.md)有關如何安裝屬於 Microsoft BI 平台的功能，包括[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]， [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]， [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]， [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]，和數個用來建立或處理分析資料的用戶端應用程式。  
  
-   **容錯移轉叢集安裝**  
  
     請參閱[SQL Server 容錯移轉叢集安裝](../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md)如需安裝程序性資訊[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]上[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]容錯移轉叢集。  
  
 根據預設， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 安裝程序中不會安裝範例資料庫和範例程式碼。 若要針對非 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Express Edition 安裝範例資料庫和範例程式碼，請參閱 [CodePlex 網站](http://go.microsoft.com/fwlink/?LinkId=87843)。 如需查閱 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 之 [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]範例資料庫及範例程式碼的支援資訊，請參閱＜ [資料庫及範例概觀](http://go.microsoft.com/fwlink/?LinkId=110391)＞。  
  
## <a name="includessnoversionincludesssnoversion-mdmd-installation"></a>[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 安裝  
 不論您是使用 [[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 安裝精靈] 或命令提示字元安裝 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]，安裝程式都包含下列一個或多個步驟：  
  
-   檢閱 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 安裝的安裝需求、系統組態檢查與安全性考量。  如需詳細資訊，請參閱 [Planning a SQL Server Installation](quick-start-installation-of-sql-server-2014.md#BKMK_BeforeYouInstall)。  
  
-   執行 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 安裝程式，將現有的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 版本升級至 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]。 如需詳細資訊，請參閱 <<c0> [ 升級至 SQL Server 2014](#BKMK_Upgrading)。  
  
-   執行 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 安裝程式，以安裝新的 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 執行個體。 如需詳細資訊，請參閱 <<c0> [ 安裝 SQL Server 2014](#BKMK_Install)。  
  
-   完成 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 安裝後，下一個主要的步驟是 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 及其元件的設定。 使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 公用程式來設定 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]。 如需詳細資訊，請參閱 <<c0> [ 設定 SQL Server 2014](#BKMK_Configure)。  
  
 在下一節中，您可以找到這些工作的詳細說明。  
  
## <a name="related-tasks"></a>相關工作  
  
###  <a name="BKMK_BeforeYouInstall"></a> 規劃[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]安裝  
 在安裝 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 之前，您必須檢閱硬體和軟體需求、網路和網際網路考量，以及安全考量，才能安裝並執行 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]。 如需詳細資訊，請參閱 <<c0> [ 規劃 SQL Server 安裝](../../2014/sql-server/install/planning-a-sql-server-installation.md)和下列主題：  
  
|工作描述|主題|  
|----------------------|-----------|  
|請檢閱硬體及軟體需求、作業系統支援、網路及網際網路考量，以及硬碟空間需求。|[安裝的必要條件](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)|  
|檢閱 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 安裝的安全性考量。|[安全性考量](../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)|  
|請檢閱由不同版本 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 所支援功能的詳細資料。|[功能和版本](features-supported-by-the-editions-of-sql-server-2014.md)|  
|請判斷 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 中可用版本及元件之間最好的選擇。|[SQL Server 2014 的版本和元件](../sql-server/editions-and-components-of-sql-server-2016.md)|  
|請檢閱硬體組態，並學習如何準備 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 容錯移轉叢集安裝。|[安裝容錯移轉叢集之前](../sql-server/failover-clusters/install/before-installing-failover-clustering.md)|  
  
###  <a name="BKMK_Upgrading"></a> 升級至 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]  
 您可以將 [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]、[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]、[!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 或 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 的現有執行個體升級至 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]。 如需詳細資訊，請參閱 <<c0> [ 升級至 SQL Server 2014](../database-engine/install-windows/upgrade-sql-server.md)。 在執行 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 安裝程式升級至 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 之前，請先檢閱下列升級程序的主題：  
  
|描述|主題|  
|-----------------|-----------|  
|支援 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 升級路徑的文件。|[支援的升級](../database-engine/install-windows/supported-version-and-edition-upgrades.md)|  
|描述 Upgrade Advisor，這是用於分析 [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]、[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]、[!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 和 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 執行個體以識別已知升級問題的工具。|[使用 Upgrade Advisor 來準備升級](../../2014/sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md)|  
|描述 Distributed Replay Utility，一種可使用多個元件重新執行追蹤資料，並模擬關鍵任務工作負載的工具。 在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 升級前後於測試伺服器上進行重新執行作業，可讓您衡量效能差異，並找出應用程式在升級後可能會發生的不相容情況。|[使用 Distributed Replay Utility 來準備升級](../../2014/sql-server/install/use-the-distributed-replay-utility-to-prepare-for-upgrades.md)|  
|列出當您升級到 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 之後會影響應用程式的一些重大變更。|[回溯相容性](backward-compatibility.md)|  
|將 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的獨立執行個體升級到 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 的程序主題。|[升級為 SQL Server 2014 使用安裝精靈&#40;安裝程式&#41;](../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)|  
|將 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 的版本升級至另一個版本的程序主題。 如需支援版本升級方式的詳細資訊，請參閱 [支援的版本與版本升級](../database-engine/install-windows/supported-version-and-edition-upgrades.md)。|[升級至不同的 SQL Server 2014 版本&#40;安裝程式&#41;](../database-engine/install-windows/upgrade-to-a-different-edition-of-sql-server-setup.md)|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 支援在所有容錯移轉叢集節點上，將 [!INCLUDE[ssDE](../includes/ssde-md.md)] 及 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 分別從 [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]、[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]、[!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 或 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 升級至 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 容錯移轉叢集。 如需詳細資訊，請檢閱本主題。|[升級 SQL Server 容錯移轉叢集](../sql-server/failover-clusters/windows/upgrade-a-sql-server-failover-cluster-instance.md)|  
  
###  <a name="BKMK_Install"></a> 安裝 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]  
 如需不同 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 安裝案例的詳細資訊，請檢閱下列主題。  
  
|描述|主題|  
|-----------------|-----------|  
|提供主題的連結以安裝 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 的多個元件，以及提供程序主題以安裝 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]。|[安裝 SQL Server 2014](../database-engine/install-windows/install-sql-server.md)|  
|檢閱本主題了解如何在 Windows Server Core 上安裝 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]。|[在 Server Core 上安裝 SQL Server 2014](../database-engine/install-windows/install-sql-server-on-server-core.md)|  
|請檢閱本主題以將個別功能加入現有 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 的執行個體。|[將功能加入至 SQL Server 2014 執行個體的&#40;安裝程式&#41;](../database-engine/install-windows/add-features-to-an-instance-of-sql-server-setup.md)|  
|請檢閱本主題以建立新的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 容錯移轉叢集執行個體。|[建立新的 SQL Server 容錯移轉叢集 &#40;安裝程式&#41;](../sql-server/failover-clusters/install/create-a-new-sql-server-failover-cluster-setup.md)|  
|您可以使用本主題管理現有 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 容錯移轉叢集執行個體中的節點。|[在 SQL Server 容錯移轉叢集中加入或移除節點 &#40;安裝程式&#41;](../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)|  
|您可以使用本主題在容錯移轉叢集上安裝 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 用戶端工具。|[在 SQL Server 容錯移轉叢集上安裝用戶端工具](../sql-server/failover-clusters/install/install-client-tools-on-a-sql-server-failover-cluster.md)|  
|檢閱 SQL 探索報告的使用狀況，以驗證電腦上所安裝之 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的版本與 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 功能。|[驗證 SQL Server 安裝](../database-engine/install-windows/validate-a-sql-server-installation.md)|  
|提供如何從安裝精靈、從命令提示字元、使用組態檔及使用 SysPrep 安裝 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 的程序性主題連結。|[安裝的使用說明主題](../../2014/sql-server/install/installation-how-to-topics.md)|  
  
## <a name="related-content"></a>相關內容  
 本節提供設定及解除安裝 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的詳細資訊。  
  
###  <a name="BKMK_Configure"></a> 設定 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]  
 在您安裝 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 之後，可以使用圖形化公用程式和命令提示字元公用程式來進一步設定 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]。 請參閱下列主題以進行第一次的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 設定：  
  
|描述|主題|  
|-----------------|-----------|  
|使用本主題中的資訊可判斷是否需要在防火牆中解除封鎖通訊埠，以允許存取 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 或 PowerPivot for SharePoint。 您可以遵循本主題所提供的步驟，設定通訊埠以及防火牆。|[設定 Windows 防火牆以允許 Analysis Services 存取](../analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)|  
|本主題會提供防火牆組態的概觀，並且摘要列出 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 管理員感興趣的資訊。|[設定 Windows 防火牆以允許 SQL Server 存取](../../2014/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)|  
|此主題描述如何設定 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 和具有進階安全性的 Windows 防火牆，以便在多重主目錄環境中提供給 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體的網路連接。|[設定多重主目錄電腦進行 SQL Server 存取](../../2014/sql-server/install/configure-a-multi-homed-computer-for-sql-server-access.md)|  
  
###  <a name="BKMK_Uninstalling"></a> 解除安裝 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]  
 下列主題描述如何手動解除安裝 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的獨立執行個體及容錯移轉叢集執行個體：  
  
|描述|主題|  
|-----------------|-----------|  
|此主題描述如何手動解除安裝 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的獨立執行個體。|[解除安裝 SQL Server 2014](../sql-server/install/uninstall-sql-server.md)|  
|此主題描述如何解除安裝 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 容錯移轉叢集執行個體。|[移除 SQL Server 容錯移轉叢集執行個體 &#40;安裝程式&#41;](../sql-server/failover-clusters/install/remove-a-sql-server-failover-cluster-instance-setup.md)|  
|本主題提供有關在解除安裝 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] 或只解除安裝 DQS 伺服器之後，手動移除 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (DQS) 物件的資訊。|[移除 Data Quality Server 物件](../../2014/sql-server/install/remove-data-quality-server-objects.md)|  
  
## <a name="see-also"></a>另請參閱  
 [適用於 SQL Server 2014 的產品規格](sql-server-2014-product-specifications.md)   
 [開始使用適用於 SQL Server 的產品文件](../2014-toc/books-online-for-sql-server-2014.md)[回溯相容性](backward-compatibility.md)  
  
  
