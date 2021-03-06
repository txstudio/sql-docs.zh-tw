---
title: 瀏覽預測模型 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, browsing
- forecasting [data mining]
- mining models, viewing
- mining model, time series
- time series [data mining]
ms.assetid: ad35a528-1949-4048-8678-3b9760c1c88c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5176d4e40f0f99810a14ad5ce4298e3a7167d770
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48223198"
---
# <a name="browsing-a-forecasting-model"></a>瀏覽預測模型
  當您開啟預測模型 using**瀏覽**，會顯示此模型中的互動式檢視器，類似於時間序列模型檢視器中[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]。 此檢視器可協助您探索趨勢、比較序列、建立預測，以及取得有關模型和基礎資料的資訊。  
  
##  <a name="bkmk_Top"></a> 瀏覽模型  
 **瀏覽**適用於預測模型的檢視器提供圖表檢視中，會顯示經過一段時間的趨勢，並可讓您建立預測，並以決策樹或迴歸樹狀結構表示時間序列模型檢視。  
  
-   [圖表檢視](#bkmk_charts)  
  
-   [模型檢視](#bkmk_Model)  
  
 若要試驗預測模型，您可以使用範例資料活頁簿中，[預測] 索引標籤上的範例資料，並建置時間序列模型使用[預測精靈&#40;適用於 Excel 的資料採礦增益集&#41;](forecast-wizard-data-mining-add-ins-for-excel.md) 中**資料採礦**功能區中，或是[預測&#40;適用於 Excel 的資料表分析工具&#41;](forecast-table-analysis-tools-for-excel.md)中**分析**功能區。  
  
###  <a name="bkmk_charts"></a> 圖表  
 **圖表** 索引標籤會顯示趨勢資料數列中的一段時間，以及預測值。 圖表的垂直軸代表序列的值，而水平軸代表時間。  
  
##### <a name="explore-the-forecasting-chart"></a>探索預測圖表  
  
1.  此模型包含多個時間序列，不過為了簡化圖表，您可以顯示一個序列，或只顯示幾個相關序列。  
  
     ![預測模型中的歷程記錄預測](media/dm13-forecast-chart-historicpredictions.gif "預測模型中的歷程記錄預測")  
  
     使用核取方塊只選取北美洲的銷售量預測。  
  
2.  按一下 **預測步驟**和新的值，以控制多少未來時間值，您想要查看圖表中的類型。  
  
     預設值為 5。  
  
3.  按一下 在一行中，歷程記錄或未來，以查看該點的確切值的時間，顯示在任何時間點**採礦圖例**。  
  
4.  圖表會顯示記錄資料和未來的資料。 注意套用陰影效果背景的虛線。 這些值是根據模型的未來預測。  
  
     圖表左側顯示用來建立模型的記錄資料。  
  
5.  選取 **顯示記錄預測**選項，以了解時間序列的穩定性。  
  
     ![在模型中單一數列的預測](media/dm13-forecast-chart-singleseries.gif "模型中單一數列的預測")  
  
     記錄預測是根據該點的序列所預測的值，會與實際記錄值進行比較。 如果虛線 (預測值) 與實心線條 (實際值) 相差很多，表示序列的第一部分可能無法正確地預測稍後的值。 您可能需要更多資料，這也可能只是指出循環的變動性。  
  
6.  選取 **顯示偏差**選項來顯示圖表中的誤差線上方。  
  
     誤差線可讓您以視覺化方式評估預測的變化性。 預測的品質視您的來源資料而有所不同，但是隨著您增加預測步驟的數目，您應該會看到偏差穩定地增加。  
  
 **祕訣**  
  
-   若要切換的顯示**採礦圖例**，以滑鼠右鍵按一下圖表中的任何時間點。  
  
     您可以按一下圖表，在圖表上拖曳時間選取範圍，然後再按一下圖表在選取的範圍上放大，以檢視特定的時間範圍。  
  
-   若要取得目前圖表的複本，請按一下**複製至 Excel**，然後按一下 Excel 工作表。 即會使用您已設定的所有選項 (包括圖例) 將圖表插入工作表。  
  
     不過，此圖表是靜態的您就無法編輯圖例或檢視基礎資料，如果您需要更具互動性的圖表檢視時，使用[Visio viewer](viewing-data-mining-models-in-visio-data-mining-add-ins.md)。  
  
-   按一下  **Abs**絕對與相對曲線之間切換檢視器功能表列中。  
  
     如果圖表包含多個模型，但每一個模型的資料比例差異很大，則此選項會很有用。  
  
     例如，如果太平洋地區商店是新開的商店但銷售量很低，此時若使用絕對值，顯示太平洋地區銷售量的線條可能會很扁平，而難以查看實際變更，至於其他模型則以較為正常的比例顯示。  
  
     藉由將檢視切換為使用相對值，您可以標準化不同模型的比例，並將差異顯示為變動百分比。 當變動與每個模型相關時，則可以在相同的圖表中顯示，而不會大幅失真。  
  
 [瀏覽模型](#bkmk_Top)  
  
###  <a name="bkmk_Model"></a> 模型  
 預測模型也可以決策樹來表示，如果序列大部分呈線性，則可以迴歸模型來表示。  
  
 例如，在此模型中，根據特定條件迴歸公式含有差異，因此會將樹狀結構分成兩個分支，每個分支使用不同的迴歸公式。  
  
 ![預測模型中篩選單一數列](media/dm13-forecast-model-northamerica.gif "預測模型中篩選單一數列")  
  
##### <a name="explore-the-forecasting-model-as-a-tree"></a>探索樹狀結構的預測模型  
  
1.  按一下 **樹狀結構**下拉式清單，然後選擇要顯示的模型。  
  
     每個可預測的屬性會顯示不同的樹狀結構或迴歸節點。 例如，如果您的資料包含歐洲、北美洲和太平洋地區的銷售量，則會有三個模型，每個模型各代表一個資料數列。  
  
2.  拖曳**顯示層級**滑桿來篩選出較高層級的樹狀目錄中，並專注於最重要的分割。  
  
3.  按一下每個節點，檢視中的一些描述性統計資料**採礦圖例**。  
  
     當您將滑鼠暫停在某個節點上方時，[工具提示] 也會顯示相同的統計資料，以及描述該節點的完整公式。  
  
4.  如果您想要複製中的資訊**採礦圖例**，以滑鼠右鍵按一下**採礦圖例**，選取**複製**，並在您的 Excel 工作表內按一下。 **複製至 Excel**選項複製圖表，而不是統計資料。  
  
 [瀏覽模型](#bkmk_Top)  
  
## <a name="see-also"></a>另請參閱  
 [瀏覽模型，在 Excel 中的&#40;SQL Server 資料採礦增益集&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
