---
title: 功能切換 (Analytics Platform System)
description: Analytics Platform System AU7 中，會顯示有關導入的兩個功能參數的資訊。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 06/27/2018
ms.author: murshedz
ms.reviewer: martinle
monikerRange: '>= aps-pdw-2016-au7 || = sqlallproducts-allversions'
ms.openlocfilehash: 0d2aadb0e7c0c56c69d89bc94e0ddaacef54e837
ms.sourcegitcommit: 3e1efbe460723f9ca0a8f1d5a0e4a66f031875aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2018
ms.locfileid: "50236904"
---
#<a name="appliance-feature-switches"></a>應用裝置功能參數
**功能切換**頁面會顯示有關功能參數正被採用，Analytics Platform System AU7 及更新版本的資訊。 使用此組態 頁面來更新或啟用/停用功能和 Analytics Platform System 中的設定。 功能參數值的變更需要重新啟動服務。

![DWConig 設備功能切換](media/feature-switch/SQL_Server_PDW_DWConfig_feature_switch.png "DWConig 設備功能參數") 

##<a name="autostatsenabled"></a>AutoStatsEnabled
控制自動統計資料功能。 此功能開關設定為升級到 AU7 之後的預設值為 true。 升級之後所建立的任何資料庫會繼承自動建立與非同步更新統計資料。 對於現有的資料庫，資料庫系統管理員可以啟用自動統計資料[ALTER DATABASE （平行資料倉儲）](../t-sql/statements/alter-database-transact-sql.md?tabs=sqlpdw)。 如需有關統計資料的詳細資訊，請參閱 <<c0> [ 統計資料](../relational-databases/statistics/statistics.md)。

##<a name="maxdopforinsertqueries"></a>MaxDOPForInsertQueries
可讓您挑選大於 1 的插入/選取作業的 maxdop 設定。 這個設定的選項是 0、 1、 2 和 4 中的，預設值是 1。

##<a name="usecatalogqueries"></a>UseCatalogQueries
使用目錄物件，而不是使用 SMO 一些中繼資料呼叫已顯示效能改進。 設為 true，預設會在 CU7.1，此參數可控制該行為。 

##<a name="dmsprocessstopmessagetimeoutinseconds"></a>DmsProcessStopMessageTimeoutInSeconds
控制資料移動服務 (DMS) 來取消涉及移動資料的查詢時，在忙碌的系統同步處理所等待的時間。 更新至 AU7 預設會設定此值為 900 秒 （15 分鐘）。 有效範圍為 0 – 3600 秒。