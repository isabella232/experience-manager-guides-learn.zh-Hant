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

下列將提供地圖控制面板主要功能的概觀。

>[!VIDEO](https://video.tv.adobe.com/v/339040?quality=12&learn=on)

## 在地圖儀表板中開啟地圖

1. 在「存放庫檢視」中，選取地圖上的省略符號圖示以開啟「選項」功能表，然後開啟「地圖控制面板」。
   ![images/ellipsis-map-dashboard.png](images/ellipsis-map-dashboard.png)

   「對映圖示板」會在另一個標籤中開啟。

## 地圖儀表板的元件

地圖儀表板包含許多標籤，包括輸出預設集、輸出結果、使用的主題、基線等。

### 輸出預設集

「輸出預設集」索引標籤會顯示各種輸出型別的預設預設集：「AEM網站」、「PDF」、「HTML5」、「ePub」和「自訂」。

![images/output-presets.png](images/output-presets.png)

您可以選取輸出預設集來檢視其設定的詳細資訊，包括轉換名稱、目的地路徑、基準線和套用的條件。

### 輸出

「輸出」標籤會顯示所有先前產生和目前產生的輸出。

![images/generated-outputs.png](images/generated-outputs.png)

「產生設定」欄下方的綠色圓圈表示已成功產生輸出。 此欄中的文字會作為作用中的超連結，您可以選取它們以開啟產生的輸出。 「型別」欄下的專案表示輸出型別。
其他輸出產生資訊也會顯示在這裡，包括產生輸出的使用者名稱、產生日期和時間，以及產生所需的時間。 如果產生期間發生錯誤，您可以在「產生時間」欄下選取產生日期和時間，以開啟並檢閱錯誤記錄。

### 主題

「主題」標籤會顯示地圖中所有主題的清單。

![images/topics.png](images/topics.png)

選取主題的核取方塊可讓您執行其他動作。 您可以編輯它、重新產生它，以及顯示、套用或隱藏它的標籤。

### 條件預設集

「條件預設集」索引標籤會顯示要包含或排除的特定條件內容的設定。

![images/condition-presets.png](images/condition-presets.png)

在此處，選取Writer Only版本的核取方塊將會產生輸出，排除具有「設計者」標籤之「audience」屬性的所有內容，並包括具有「writers」標籤的所有內容。

### 基準線

基準線標籤可讓您檢視基準線。

![images/baselines.png](images/baselines.png)

基準線會即時當作快照，並讓您建立主題和資產的版本以供發佈。 例如，擷取特定日期和時間內容的基準線，可以根據其當時的個別版本，使用一個主題的1.3版和另一個主題的1.0版。
如果沒有指定基準線，則會以所有內容的最新版本產生輸出。

### 報告

「報表」標籤會顯示主題資訊的摘要，包括使用中的主題總數、這些主題中缺少的元素以及檔案狀態。

![images/reports.png](images/reports.png)

如果主題缺少元素，您可以選取列中最右側的箭頭，以展開專案並檢視有關錯誤的詳細資訊。
