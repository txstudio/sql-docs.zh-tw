---
title: 如何將資料內嵌到 SQL Server 資料集區使用 TRANSACT-SQL |Microsoft Docs
description: 本教學課程會示範如何將資料內嵌到具有 sp_data_pool_table_insert_data 預存程序的 SQL Server 2019 巨量資料叢集 （預覽） 的資料集區。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 11/06/2018
ms.topic: tutorial
ms.prod: sql
ms.openlocfilehash: 1f585a354175ff893869cef7f2f47b12fe244634
ms.sourcegitcommit: cb73d60db8df15bf929ca17c1576cf1c4dca1780
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2018
ms.locfileid: "51221694"
---
# <a name="tutorial-ingest-data-into-a-sql-server-data-pool-with-transact-sql"></a>教學課程： 將資料內嵌至 SQL Server 資料集區使用 TRANSACT-SQL

本教學課程示範如何使用 TRANSACT-SQL，將資料載入[資料集區](concept-data-pool.md)的 SQL Server 2019 巨量資料叢集 （預覽）。 使用 SQL Server 的巨量資料叢集，從各種來源的資料可以擷取並分散到資料集區執行個體。

在本教學課程中，您將了解如何：

> [!div class="checklist"]
> * 建立外部資料表的資料集區中。
> * 插入的資料集區資料表中的範例 web 點選流資料。
> * 加入本機資料表的資料集區資料表中的資料。

> [!TIP]
> 如果您想，您可以下載並執行命令的指令碼，在本教學課程。 如需相關指示，請參閱 <<c0> [ 資料集區範例](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/data-pool)GitHub 上。

## <a id="prereqs"></a> 必要條件

* [將巨量資料叢集的 Kubernetes 上部署](deployment-guidance.md)。
* [安裝 Azure Data Studio 和 SQL Server 2019 副檔名](deploy-big-data-tools.md)。
* [將範例資料載入叢集](#sampledata)。

[!INCLUDE [Load sample data](../includes/big-data-cluster-load-sample-data.md)]

## <a name="create-an-external-table-in-the-data-pool"></a>建立資料集區中的外部資料表

下列步驟會建立外部資料表名為資料集區內**web_clickstream_clicks_data_pool**。 本表然後可用做為位置擷取資料到巨量資料叢集。

1. 在 Azure Data Studio，連接到您的巨量資料叢集的 SQL Server 主要執行個體。 如需詳細資訊，請參閱 <<c0> [ 連接到 SQL Server 的主要執行個體](deploy-big-data-tools.md#master)。

1. 在連線 中按兩下**伺服器**視窗以顯示 SQL Server 的主要執行個體的伺服器儀表板。 選取 **新的查詢**。

   ![SQL Server 的主要執行個體查詢](./media/tutorial-data-pool-ingest-sql/sql-server-master-instance-query.png)

1. 執行下列 TRANSACT-SQL 命令，以將內容變更為**銷售**主要執行個體中的資料庫。

   ```sql
   USE Sales
   GO
   ```

1. 建立名為外部資料表**web_clickstream_clicks_data_pool**資料集區中。 `SqlDataPool`資料來源是可從任何巨量資料叢集的主要執行個體的特殊的資料來源類型。

   ```sql
   IF NOT EXISTS(SELECT * FROM sys.external_tables WHERE name = 'web_clickstream_clicks_data_pool')
      CREATE EXTERNAL TABLE [web_clickstream_clicks_data_pool]
      ("wcs_user_sk" BIGINT , "i_category_id" BIGINT , "clicks" BIGINT)
      WITH
      (
         DATA_SOURCE = SqlDataPool,
         DISTRIBUTION = ROUND_ROBIN
      );
   ```
  
1. 在 CTP 2.1 中，建立資料集區是非同步的但沒有任何方式可判斷當尚未完成。 等候兩分鐘，以確定資料集區建立後再繼續。

## <a name="load-data"></a>載入資料

下列步驟會將範例 web 點選流資料嵌入使用先前步驟中建立外部資料表的資料集區。

1. 定義您想要將資料插入的資料集區使用之查詢的變數。 然後使用**模型...sp_data_pool_table_insert_data**預存程序，從查詢中插入的資料集區的結果 ( **web_clickstream_clicks_data_pool**外部資料表)。

   ```sql
   DECLARE @db_name SYSNAME = 'Sales'
   DECLARE @schema_name SYSNAME = 'dbo'
   DECLARE @table_name SYSNAME = 'web_clickstream_clicks_data_pool'
   DECLARE @query NVARCHAR(MAX) = '
   SELECT wcs_user_sk, i_category_id, COUNT_BIG(*) as clicks
   FROM sales.dbo.web_clickstreams
   INNER JOIN sales.dbo.item it ON (wcs_item_sk = i_item_sk
      AND wcs_user_sk IS NOT NULL)
   GROUP BY wcs_user_sk, i_category_id
   HAVING COUNT_BIG(*) > 100;'

   EXEC model..sp_data_pool_table_insert_data @db_name, @schema_name, @table_name, @query
   ```

1. 檢查兩個選取的查詢與插入的資料。

   ```sql
   SELECT count(*) FROM [dbo].[web_clickstream_clicks_data_pool]
   SELECT TOP 10 * FROM [dbo].[web_clickstream_clicks_data_pool]  
   ```

## <a name="query-the-data"></a>查詢資料

加入資料集區中的查詢中的本機資料的預存的結果**銷售**資料表。

```sql
SELECT TOP (100)
   w.wcs_user_sk,
   SUM( CASE WHEN i.i_category = 'Books' THEN 1 ELSE 0 END) AS book_category_clicks,
   SUM( CASE WHEN w.i_category_id = 1 THEN 1 ELSE 0 END) AS [Home & Kitchen],
   SUM( CASE WHEN w.i_category_id = 2 THEN 1 ELSE 0 END) AS [Music],
   SUM( CASE WHEN w.i_category_id = 3 THEN 1 ELSE 0 END) AS [Books],
   SUM( CASE WHEN w.i_category_id = 4 THEN 1 ELSE 0 END) AS [Clothing & Accessories],
   SUM( CASE WHEN w.i_category_id = 5 THEN 1 ELSE 0 END) AS [Electronics],
   SUM( CASE WHEN w.i_category_id = 6 THEN 1 ELSE 0 END) AS [Tools & Home Improvement],
   SUM( CASE WHEN w.i_category_id = 7 THEN 1 ELSE 0 END) AS [Toys & Games],
   SUM( CASE WHEN w.i_category_id = 8 THEN 1 ELSE 0 END) AS [Movies & TV],
   SUM( CASE WHEN w.i_category_id = 9 THEN 1 ELSE 0 END) AS [Sports & Outdoors]
FROM [dbo].[web_clickstream_clicks_data_pool] as w
INNER JOIN (SELECT DISTINCT i_category_id, i_category FROM item) as i
   ON i.i_category_id = w.i_category_id
GROUP BY w.wcs_user_sk;
```

## <a name="clean-up"></a>清除

您可以使用下列命令，移除在本教學課程中建立的資料庫物件。

```sql
DROP EXTERNAL TABLE [dbo].[web_clickstream_clicks_data_pool];
```

## <a name="next-steps"></a>後續步驟

深入了解如何將資料內嵌到 Spark 作業的資料集區：
> [!div class="nextstepaction"]
> [擷取與 Spark 作業的資料](tutorial-data-pool-ingest-spark.md)
