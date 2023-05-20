---
title: 地圖儀表板簡介
description: 地圖儀表板簡介
exl-id: c2efa073-15e7-42a0-aaa8-04859b0fdf62
source-git-commit: 1c4d278a05f2612bc55ce277efb5da2e6a0fa9a9
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 0%

---

# 地圖儀表板簡介

以下內容將概述地圖操控板的主要功能。

>[!VIDEO](https://video.tv.adobe.com/v/339040?quality=12&learn=on)

## 在「映射面板」中開啟映射

1. 在儲存庫視圖中，選擇映射上的省略號表徵圖以開啟「選項」菜單，然後選擇開啟映射儀表板。
   ![images/ellipsis-map-dashboard.png](images/ellipsis-map-dashboard.png)

   「映射儀表板」(Map Dashboard)將在另一個頁籤中開啟。

## 映射儀表板的元件

「映射儀表板」包含許多頁籤，包括輸出預設、輸出結果、使用的主題、基線等。

### 輸出預設

「輸出預設」頁籤顯示不同類型輸出的預設預設：站AEM點、PDF、HTML5、ePub和自定義。

![images/output-presets.png](images/output-presets.png)

您可以選擇輸出預設來查看其設定的詳細資訊，包括轉換名稱、目標路徑、基線和應用條件。

### 輸出

「輸出」(Outputs)頁籤顯示所有先前生成的輸出和當前生成的輸出。

![images/generated-outputs.png](images/generated-outputs.png)

「層代設定」(Generation Settings)列下的綠色圓圈表示已成功生成輸出。 此列中的文本充當活動超連結，您可以選擇它們以開啟生成的輸出。 「類型」(Type)列下的條目指示輸出類型。
此處還顯示其他輸出生成資訊，包括生成輸出的用戶名、生成日期和時間以及生成所花費的時間。 如果在生成過程中出錯，則可以在「生成時間」列下選擇生成日期和時間以開啟並查看錯誤日誌。

### 主題

「主題」頁籤顯示映射中所有主題的清單。

![images/topics.png](images/topics.png)

選中主題的複選框可以執行其他操作。 您可以編輯它、重新生成它，並顯示、應用或隱藏其標籤。

### 條件預設

「條件預設」頁籤顯示要包括或排除的特定條件內容的設定。

![images/condition-presets.png](images/condition-presets.png)

在此處，選中僅Writer版的複選框將生成一個輸出，該輸出將排除具有「設計者」標籤的「受眾」屬性的所有內容，並包含具有「writers」標籤的所有內容。

### 基線

「基線」(Baselines)頁籤允許您查看基線。

![images/baselines.png](images/baselines.png)

基線可以作為即時快照，並允許您建立主題和資產的版本以供發佈。 例如，在特定日期和時間捕獲內容的基線可以使用某個主題的1.3版和另一個主題的1.0版，這取決於當時各自的版本。
如果未指定基線，則使用所有內容的最新版本生成輸出。

### 報告

「報告」頁籤顯示主題資訊的摘要，包括正在使用的主題總數、這些主題中缺少的元素以及文檔狀態。

![images/reports.png](images/reports.png)

如果主題缺少元素，則可以選擇行中最右箭頭以展開條目並查看有關錯誤的詳細資訊。
