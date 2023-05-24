---
title: 發行說明 | Adobe Experience Manager Guidesas a Cloud Service，2023年3月發行
description: Adobe Experience Manager Guidesas a Cloud Service三月版
exl-id: b3fe7cc8-1654-467a-ab18-6e6912855ecc
source-git-commit: 8073716bccacbe8d6a158b44d5106b083e3a5dcd
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 2%

---

# Adobe Experience Manager Guidesas a Cloud Service三月版

## 升級至3月版

as a Cloud Service升級您目前的Adobe Experience Manager Guides (稍後稱為 *AEM指南as a Cloud Service*)進行設定：
1. 檢視Cloud Services的Git程式碼，並切換到在Cloud Services管道中設定的分支，該分支與您要升級的環境相對應。
2. 更新 `<dox.version>` 中的屬性 `/dox/dox.installer/pom.xml` 將Cloud Services Git程式碼的檔案設為2023.3.242。
3. 提交變更並執行Cloud Services管道，以升級至AEM Guidesas a Cloud Service的3月版本。

## 索引現有內容的步驟(僅限使用9月之前版本的AEM Guidesas a Cloud Service)

執行以下步驟，為現有內容編制索引，並在地圖層級使用新的尋找和取代文字：

* 對伺服器執行POST要求（使用正確的驗證） - `http://<server:port>/bin/guides/map-find/indexing`.
(可選：您可以傳遞地圖的特定路徑來為其建立索引，預設情況下，所有地圖都會建立索引 ||範例： `https://<Server:port>/bin/guides/map-find/indexing?paths=<map_path_in_repository>`)

* 此API將傳回jobId。 若要檢查作業的狀態，您可以將具有作業ID的GET要求傳送至相同的端點 —  `http://<server:port>/bin/guides/map-find/indexing?jobId={jobId}`
(例如： http://&lt;
_localhost：8080_>/bin/guides/map-find/indexing？jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678)

* 工作完成後，上述GET要求將回應為成功，並提及是否有任何地圖失敗。 可以從伺服器記錄檔確認已成功建立索引的對應。

## 相容性矩陣

本節列出AEM Guides 2023年3月as a Cloud Service發行版本支援之軟體應用程式的相容性矩陣。

### FrameMaker和FrameMaker Publishing Server

| AEM Guides as a Cloud版本 | FMPS | FrameMaker |
| --- | --- | --- |
| 2023.03.0 | 不相容 | 2022或更高 |
|  |  |  |


### 氧氣聯結器

| AEM Guides as a Cloud版本 | 氧氣聯結器視窗 | 氧氣聯結器Mac | 在氧氣視窗中編輯 | 在氧氣Mac中編輯 |
| --- | --- | --- | --- | --- |
| 2023.03.0 | 2.9-uuid-2 | 2.9-uuid-2 | 2.3 | 2.3 |
|  |  |  |  |


## 新增功能和功能改善

AEM Guidesas a Cloud Service在2023年3月版本中提供增強功能和新功能：

### 在網頁編輯器中開啟並播放視訊或音訊檔案

AEM Guides現在提供在網頁編輯器中開啟和播放音訊或視訊檔案的功能。 您可以變更音量或視訊檢視。 在快捷選單中，您也有 **下載**，變更 **播放速度**，或檢視 **子母畫面**.

<img src="assets/video-web-editor.png" alt="播放視訊" width="600">


## 已修正的問題

修復了各種區域的錯誤如下所列：

* 下載PDF程式在網頁編輯器中無法正常運作。 (11496)
* JSON輸出 |屬性值為「 」的中繼資料對應 `"value in spaces and double quotes"` 導致發佈錯誤。 (11438)
* 音訊和視訊多媒體檔案的插入失敗，因為YouTube格式位於 **插入多媒體** 圖示。 (11320)
* 使用具有專門化標題元素的範本建立對應時，會發生驗證錯誤。 (11212)
* 原生PDF |表格頁首中的註腳會在PDF輸出的對應頁尾中，指向粗體和居中對齊文字。 (10610)
>[!NOTE]
>
>若要反映原生PDF變更，請刪除位於/content/dam/dita-templates的PDF資料夾，然後升級至最新版本。 (10610)

### 有因應措施的已知問題

Adobe已確認2023年3月AEM Guidesas a Cloud Service版本的下列已知問題。

* 使用者無法儲存或建立重複資產的版本。

**因應措施**：對重複資產進行任何變更之前，請先從Assets UI重新處理該資產。
