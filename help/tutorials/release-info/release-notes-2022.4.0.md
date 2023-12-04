---
title: 發行說明 | Adobe Experience Manager Guidesas a Cloud Service，2022年4月發行
description: Adobe Experience Manager Guidesas a Cloud Service於4月發行
source-git-commit: 880cd344ceb65ea339be699ebcad41c0d62e168a
workflow-type: tm+mt
source-wordcount: '809'
ht-degree: 0%

---

# Adobe Experience Manager Guidesas a Cloud Service於4月發行

## 升級至4月發行

升級您目前的 [!DNL Adobe Experience Manager Guides] as a Cloud Service(稍後稱為 *[!DNL AEM Guides]as a Cloud Service*)進行設定，請執行以下步驟：
1. 檢視Cloud Service的Git程式碼，並切換到在Cloud Service管線中設定的分支，該分支與您要升級的環境相對應。
1. 更新 `<dox.version>` 中的屬性 `/dox/dox.installer/pom.xml` 將Cloud Service Git程式碼的檔案設為2022.4.133。
1. 提交變更並執行Cloud Service管道，以升級至4月版本的 [!DNL AEM Guides] as a Cloud Service。

## 相容性矩陣

本節列出所支援軟體應用程式的相容性矩陣。 [!DNL AEM Guides] 2022年4月版本as a Cloud Service。

### FrameMaker和FrameMaker Publishing Server

| FMPS | FrameMaker |
| --- | --- |
| 不相容 | 2020 Update 4及更新版本 |
| | |


### 氧氣聯結器

| AEM Guides雲端版 | 氧氣聯結器視窗 | 氧氣聯結器Mac |
| --- | --- | --- |
| 2022.4.0 | 2.5.6 | 2.5.6 |
|  |  |  |

*從2020.2開始的FMPS版本支援AEM中建立的基準和條件。

## 新功能和增強功能

網頁編輯器中新增了許多增強功能和新功能：

### 改善金鑰解析度

DITA內容索引鍵參照會將部分內容從一個主題插入另一個主題。 它會使用索引鍵來尋找內容。 需要解析與DITA主題相關聯的關鍵參照。 選取的根對映解析關鍵參照的優先順序最高。

![使用者偏好設定對話方塊](assets/user-preferences.png)

現在，主要參考會根據根對映集來解析，其優先順序如下：

1. 使用者偏好設定
1. 地圖檢視面板
1. 資料夾設定檔

如需詳細資訊，請參閱 *解析關鍵參考* 區段。

### 在左側面板中新增自訂面板

現在您可以在網頁編輯器的左側面板中新增自訂面板。 您可以將自訂面板用於各種用途，例如提供說明或針對專案進行測試。 如果自訂面板已設定，則它也出現在內的面板清單中 **編輯器設定**. 您可以切換開關，以顯示或隱藏自訂面板。

### 能夠變更DITA map中主題的檔案狀態

現在您可以輕鬆地變更DITA map中選取主題的檔案狀態。 您也可以在DITA map中開啟及編輯所選主題的屬性，其來源為 **更多選項** 選單（位於地圖檢視面板底部）。

![選取的主題屬性](assets/map-view-properties.png)

### 預覽模式中顯示的版本資訊

網頁編輯器可協助您管理版本。 現在您也可以在主題的「預覽」模式中，在主題之檔案標籤的右上角，看到使用中主題或DITA map的版本。

![預覽版本](assets/preview-version.png)

## 已修正的問題

以下列出各種區域中修正的錯誤：

* 新標籤不會自動反映在新增/移除標籤下拉式清單中，而是需要基線重新整理。 (9249)
* 如果基準是由標籤條件所建立，則無法編輯基準標題。 (9171)
* 如果基準線狀態變更為「失敗」，使用基準線的發佈工作會卡在「等待中」狀態。 (9194)
* 移除直接參照上的標籤也會從間接參照中移除標籤。 (9257)
* 當您輸入時進行搜尋，會在「存放庫」檢視中造成不必要的搜尋請求。 (9307)
* 在索引標籤的標題中使用任何關鍵字時會發生問題。 (9318)
* 基線無法新增含有空格的標籤。 (9362)
* AEM網站輸出未正確顯示glosusage元素。 (8936)
* 開啟 **輸出** 索引標籤進行編輯。 (8715)
* 透過Salesforce發佈手動記錄型別時顯示的錯誤訊息不是直覺式的。 (8952)
* 使用條件屬性設定進行驗證不會立即開啟，而是使用者需要重新開啟檔案才能檢視驗證。 (9300)
* 使用中繼資料發佈DITA map後，就無法移除中繼資料。  (9178)
* 即使在Map編輯器中開啟DITA map，也可看到翻譯面板。 (9053)
* 使用者定義的自訂DTD不會優先於內嵌於DITA-OT中的標準DITA DTD。 (9104)
* 在原生PDF功能中，對於非DITA和非影像檔案，範本中的上傳會失敗。 (9070)
* 在某些特殊情況下，授權機制會執行兩個查詢而不是一個查詢。 (9221)
* 使用自訂DTD發佈AEM網站輸出時失敗。 (9243)
* 參考用腳註不會捲動至AEM網站輸出中的腳註區段。 (9234)

## 已知問題

Adobe已在中發現下列已知問題 [!DNL AEM Guides] 4月版本as a Cloud Service。

* 當以相同名稱建立兩個或多個基準線，但兩者有空格或大小寫差異時，Web編輯器不會報告錯誤。 例如，「adobe」和「Adobe」或「Adobe」。
* 執行頻繁登入或登出，或在不同驗證型別之間切換時，氧氣聯結器會斷斷續續地掛起。
