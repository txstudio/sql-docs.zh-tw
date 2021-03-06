---
title: 使用 R 和 SQL Server 機器學習服務的資料庫內分析的教學課程 |Microsoft Docs
description: 了解如何內嵌 R 程式設計語言中 SQL Server 預存程序和 T-SQL 函式的程式碼。
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/29/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 80c4d39e87984b022340079be4d944ed6ad963e3
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/06/2018
ms.locfileid: "51030645"
---
# <a name="tutorial-in-database-r-analytics-for-sql-developers"></a>適用於 SQL 開發人員的教學課程： 在資料庫內 R 分析
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

在本教學課程中的 SQL 程式設計人員，透過建置和部署 R 為基礎的機器學習解決方案使用了解 R 整合[NYCTaxi_sample](demo-data-nyctaxi-in-sql.md)上 SQL Server 資料庫。 

本教學課程會向您介紹的資料模型化工作流程中使用的 R 函數。 步驟包括資料瀏覽、 建置及定型二元分類模型和部署模型。 您會使用從 New York City 計程車和 Limosine 佣金，範例資料，您將建置的模型會預測一趟車程是否可能會造成提示，根據的時間、 歷經一段，距離和上車位置中。 在本教學課程中使用的 R 程式碼的所有包裝在您建立和在 Management Studio 中執行的預存程序。


> [!NOTE]
> 
> 本教學課程適用於 R 和 Python。 Python 版本，請參閱[資料庫內分析適用於 Python 開發人員](../tutorials/sqldev-in-database-python-for-sql-developers.md)。

## <a name="overview"></a>總覽

建置機器學習服務解決方案的程序很複雜，可包含多個工具和專家協調跨數個階段：

+ 取得和清除資料
+ 瀏覽資料及建置適用於模型化功能
+ 定型和微調模型
+ 部署至生產環境

實際的程式碼的開發和測試是最適合執行使用專用的開發環境。 不過，指令碼經過完整測試之後，您可以輕鬆部署到[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]使用[!INCLUDE[tsql](../../includes/tsql-md.md)]預存程序在熟悉的環境中[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]。

您是 SQL 程式設計人員熟悉 R，還是 R 開發人員熟悉 SQL，此多部分的教學課程介紹進行資料庫內分析與 R 和 SQL Server 的一般工作流程。 

- [第 1 課： 探索和視覺化 預存程序呼叫 R 函式的 資料圖形和散發](../tutorials/sqldev-explore-and-visualize-the-data.md)

- [第 2 課： 建立在 T-SQL 函式中使用 R 的資料特徵](sqldev-create-data-features-using-t-sql.md)
  
- [第 3 課： 訓練及儲存使用函式和預存程序的 R 模型](sqldev-train-and-save-a-model-using-t-sql.md)
  
- [第 4 課： 預測潛在的預存程序中使用 R 模型的結果](../tutorials/sqldev-operationalize-the-model.md)

模型儲存到資料庫之後，呼叫從預測模型[!INCLUDE[tsql](../../includes/tsql-md.md)]使用預存程序。

## <a name="prerequisites"></a>先決條件

所有的工作可使用[!INCLUDE[tsql](../../includes/tsql-md.md)]預存程序中的[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]。

本教學課程假設您熟悉基本資料庫作業，例如建立資料庫和資料表、 匯入資料，以及撰寫 SQL 查詢。 它不會假設您知道。因此，提供所有 R 程式碼。 

+ [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md#verify-installation)或[SQL Server 2017 Machine Learning 服務以啟用 R](../install/sql-machine-learning-services-windows-install.md#verify-installation)

+ [R 程式庫](../r/determine-which-packages-are-installed-on-sql-server.md#get-the-r-library-location)

+ [Permissions](../security/user-permission.md)

+ [NYC 計程車示範資料庫](demo-data-nyctaxi-in-sql.md)


## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [將 NYC 計程車資料庫設定](demo-data-nyctaxi-in-sql.md)