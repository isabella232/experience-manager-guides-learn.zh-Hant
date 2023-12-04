---
title: 發行說明 | Adobe Experience Manager Guidesas a Cloud Service，2022年10月發行
description: Adobe Experience Manager Guidesas a Cloud Service10月版
source-git-commit: 880cd344ceb65ea339be699ebcad41c0d62e168a
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 1%

---

# Adobe Experience Manager Guidesas a Cloud Service10月版

## 升級至10月版

as a Cloud Service升級您目前的Adobe Experience Manager Guides (稍後稱為 *AEM Guidesas a Cloud Service*)進行設定，請執行以下步驟：
1. 檢視Cloud Service的Git程式碼，並切換到在Cloud Service管線中設定的分支，該分支與您要升級的環境相對應。
1. 更新 `<dox.version>` 中的屬性 `/dox/dox.installer/pom.xml` 將您的Cloud Service Git程式碼檔案設為2022.10.183。
1. 提交變更並執行Cloud Service管道，以升級至AEM Guides的10月版本as a Cloud Service。

## 相容性矩陣

本節列出AEM Guides 2022年10月as a Cloud Service發行版本支援之軟體應用程式的相容性矩陣。

### FrameMaker和FrameMaker Publishing Server

| FMPS | FrameMaker |
| --- | --- |
| 不相容 | 2020 Update 4及更新版本 |
| | |

*從2020.2開始的FMPS版本支援AEM中建立的基準和條件。

### 氧氣聯結器

| AEM Guides as a Cloud版本 | 氧氣聯結器視窗 | 氧氣聯結器Mac | 在氧氣視窗中編輯 | 在氧氣Mac中編輯 |
| --- | --- | --- | --- | --- |
| 2022.10.0 | 2.7.13 | 2.7.13 | 2.3 | 2.3 |
|  |  |  |  |


## 新功能和增強功能

AEM Guidesas a Cloud Service在10月版本中提供了增強功能和新功能：


### 快速產生面板

現在AEM Guides提供 **快速產生** 面板，可協助您快速產生並檢視針對DITA map建立的預設集輸出。

![「快速產生」圖示](assets/quick-generate-icon.png)

在 **快速產生** 面板中，您可以看到為DITA map建立的所有輸出預設集清單。

![快速產生面板](assets/quick-generate-panel.png)

選取一或多個預設集並快速產生輸出。 您也可以快速檢視針對預設集產生的輸出。 成功訊息會顯示在產生的輸出上。 如果輸出產生失敗，會顯示錯誤訊息。 您也可以檢視錯誤記錄，以檢視產生程式中所發生錯誤的詳細資料。


## 已修正的問題

以下列出各種區域中修正的錯誤：

* 原生PDF |從PDF輸出移除僅限資源的主題時發生錯誤。 (10554)
* 原生PDF |PDF輸出中出現空白的Keyref。 (10553)
* 原生PDF | `navtitle` 的 `topichead` 不接受。 (10509)
* 原生PDF |支援amd64 JDK風格。 (10465)
* 原生PDF |無法從目錄隱藏重要主題。 (10355)
* 原生PDF |重新啟動章節配置中的頁碼會從上一個章節的結尾開始隨機編號。 (10154)
* Chrome瀏覽器 |從UI拖放任何元素時，畫面會變成空白。 例如，從「條件」面板拖曳條件時。 (10524)
* 資產執行複製貼上操作後，節點屬性會被移除。 (10053)
* 按一下  **關閉** 系統已將使用者重新導向至資產 — 已修正體驗，將使用者帶至AEM首頁。 (9654)
