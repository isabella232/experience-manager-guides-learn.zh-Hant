---
title: 發行說明 | Adobe Experience Manager Guidesas a Cloud Service，2022年4月發行
description: 4月版Adobe Experience Manager Guidesas a Cloud Service
exl-id: c735ba24-a803-454b-8723-57dacf90061b
source-git-commit: 67ba514616a0bf4449aeda035161d1caae0c3f50
workflow-type: tm+mt
source-wordcount: '799'
ht-degree: 3%

---

# 4月版Adobe Experience Manager Guidesas a Cloud Service

## 升級至4月發行

升級您目前的 [!DNL Adobe Experience Manager Guides] as a Cloud Service(稍後稱為 *[!DNL AEM Guides]as a Cloud Service*)進行設定：
1. 檢視Cloud Services的Git程式碼，並切換到在Cloud Services管道中設定的分支，該分支與您要升級的環境相對應。
1. 更新 `<dox.version>` 中的屬性 `/dox/dox.installer/pom.xml` 將您的Cloud Services Git程式碼檔案改成2022.4.133。
1. 提交變更並執行Cloud Services管道，以升級至4月版的 [!DNL AEM Guides] as a Cloud Service。

## 相容性矩陣

本節列出所支援軟體應用程式的相容性矩陣。 [!DNL AEM Guides] 2022年4月發行版本as a Cloud Service。

### FrameMaker和FrameMaker Publishing Server

| FMPS | FrameMaker |
| --- | --- |
| 不相容 | 2020 Update 4及更高版本 |
|  |  |


### 氧氣聯結器

| AEM Guides雲端版 | 氧氣聯結器視窗 | 氧氣聯結器Mac |
| --- | --- | --- |
| 2022.4.0 | 2.5.6 | 2.5.6 |
|  |  |  |

*自2020.2開始的FMPS版本支援AEM中建立的基準和條件。

## 新增功能和功能改善

Web編輯器中新增了許多增強功能和新功能：

### 改善金鑰解析度

DITA內容索引鍵參照會將部分內容從一個主題插入另一個主題。 它會使用索引鍵來尋找內容。 需要解析與DITA主題相關聯的關鍵參考。 選取的根對映擁有最高優先權可解析索引鍵參考。

![使用者偏好設定對話方塊](assets/user-preferences.png)

現在，主要參考會根據根對映集來解析，其優先順序如下：

1. 使用者偏好設定
1. 地圖檢視面板
1. 資料夾設定檔

如需詳細資訊，請參閱 *解析索引鍵參考* 區段。

### 在左側面板中新增自訂面板

現在您可以在網頁編輯器的左側面板中新增自訂面板。 您可以將自訂面板用於各種用途，例如提供說明或為專案進行測試。 如果已設定自訂面板，則它也會出現在內的面板清單中 **編輯器設定**. 您可以切換開關以顯示或隱藏自訂面板。

### 能夠變更DITA map中主題的檔案狀態

現在您可以輕鬆地變更DITA map中選取主題的檔案狀態。 您也可以從「 」開啟和編輯DITA map中選取主題的屬性。 **更多選項** 選單（位於地圖檢視面板底部）。

![選取的主題屬性](assets/map-view-properties.png)

### 預覽模式中顯示的版本資訊

網頁編輯器可協助您管理版本。 現在您也可以在主題的「預覽」模式中，在主題之檔案索引標籤的右上角，看到使用中主題或DITA map的版本。

![預覽版本](assets/preview-version.png)

## 已修正的問題

修復了各種區域的錯誤如下所列：

* 新標籤不會自動反映在新增/移除標籤下拉式清單中，而是需要基線重新整理。 (9249)
* 如果基準線是由標籤條件建立，則無法編輯基準線標題。 (9171)
* 如果基準線狀態變更為「失敗」，使用基準線發佈工作會卡在「等待中」狀態。 (9194)
* 移除直接參照上的標籤也會從間接參照中移除標籤。 (9257)
* 鍵入時進行搜尋會在「存放庫」檢視中造成不想要的搜尋請求。 (9307)
* 在索引標籤的標題中使用任何關鍵字時會發生問題。 (9318)
* 基線無法新增含有空格的標籤。 (9362)
* AEM網站輸出未正確顯示glosusage元素。 (8936)
* 開啟「 」時出現主控台錯誤 **輸出** 索引標籤進行編輯。 (8715)
* 透過Salesforce發佈手動記錄型別時顯示的錯誤訊息不是直覺式的。 (8952)
* 使用條件屬性驗證設定不會立即開啟，而是使用者需要重新開啟檔案才能檢視驗證。 (9300)
* 使用中繼資料發佈DITA map後，無法移除中繼資料。  (9178)
* 即使在「地圖編輯器」中開啟DITA map，也可看到翻譯面板。 (9053)
* 使用者定義的自訂DTD不會優先於內嵌於DITA-OT中的標準DITA DTD。 (9104)
* 在原生PDF功能中，上傳範本中的非DITA和非影像檔案會失敗。 (9070)
* 授權機制在某些特殊情況下會執行兩個查詢，而不是一個。 (9221)
* 使用自訂DTD發佈AEM網站輸出時失敗。 (9243)
* 參考使用註腳不會捲動至AEM網站輸出中的註腳區段。 (9234)

## 已知問題

Adobe已在中發現下列已知問題 [!DNL AEM Guides] 4月版本as a Cloud Service。

* 當以相同名稱建立兩個或多個基準線，但兩者有空格或大小寫差異時，Web編輯器不會報告錯誤。 例如，「adobe」和「Adobe」或「Adobe」。
* 執行頻繁登入或登出或在不同驗證型別之間切換時，氧氣聯結器會間歇性地掛起。
