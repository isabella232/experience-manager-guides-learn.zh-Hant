---
title: 發行說明 | Adobe Experience Manager指南as a Cloud Service,2023年3月發行版本
description: 3月版Adobe Experience Manager指南as a Cloud Service
source-git-commit: d762cccc4a8f89eb91a1a8eb2c1410a7e0358b85
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 2%

---

# 3月版Adobe Experience Manager指南as a Cloud Service

## 升級至3月版

升級您目前的Adobe Experience Manager指南as a Cloud Service(稍後稱為 *AEM指南as a Cloud Service*)，請執行下列步驟：
1. 查看Cloud Services的Git程式碼，並切換至Cloud Services管道中所設定的分支，該管道與您要升級的環境對應。
2. 更新 `<dox.version>` 屬性 `/dox/dox.installer/pom.xml` 檔案的Cloud ServicesGit程式碼。
3. 提交變更並執行Cloud Services管道，以升級至3月版的AEM指南as a Cloud Service。

## 為現有內容建立索引的步驟(僅限使用9月版AEM指南之前的版本時as a Cloud Service)

執行以下步驟來建立現有內容的索引，並在映射級別使用新的查找和替代文字：

* 對伺服器執行POST請求（使用正確的驗證） —  `http://<server:port>/bin/guides/map-find/indexing`.
(可選：您可以傳遞映射的特定路徑來為其建立索引，預設情況下，所有映射都將編製索引 ||範例： `https://<Server:port>/bin/guides/map-find/indexing?paths=<map_path_in_repository>`)

* API會傳回jobId。 要檢查作業的狀態，可以向相同的終點發送具有作業ID的GET請求 —  `http://<server:port>/bin/guides/map-find/indexing?jobId={jobId}`
(例如：http://&lt;
_localhost:8080_>/bin/guides/map-find/indexing?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678)

* 作業完成後，上述GET要求會以成功回應，並在地圖失敗時提及。 可以從伺服器日誌中確認已成功索引的映射。

## 相容性矩陣

本節列出AEM指南as a Cloud Service於2023年3月發行版本所支援軟體應用程式的相容性矩陣。

### FrameMaker和FrameMaker Publishing Server

| AEM雲端版本指南 | FMPS | FrameMaker |
| --- | --- | --- |
| 2023.03.0 | 不相容 | 2022年或更新版本 |
|  |  |  |


### 氧連接器

| AEM雲端版本指南 | 氧連接器窗口 | 氧連接器Mac | 在氧氣窗口中編輯 | 在Oxion Mac中編輯 |
| --- | --- | --- | --- | --- |
| 2023.03.0 | 2.9-uuid-2 | 2.9-uuid-2 | 2.3 | 2.3 |
|  |  |  |  |


## 新增功能和功能改善

AEM指南as a Cloud Service於2023年3月版本中提供增強功能和新功能：

### 在網頁編輯器中開啟並播放視訊或音訊檔案

AEM指南現在提供在網頁編輯器中開啟和播放音訊或視訊檔案的功能。 您可以變更音量或視訊的檢視。 在快捷菜單中，您還可以選擇 **下載**，變更 **播放速度**，或檢視 **子母畫面**.

<img src="assets/video-web-editor.png" alt="播放視訊" width="600">


## 已修正的問題

以下列出各個區域中修正的錯誤：

* 下載PDF程式在網頁編輯器中無法正常運作。 (11496)
* JSON輸出 |將具有屬性值的中繼資料映射為 `"value in spaces and double quotes"` 導致發佈錯誤。 (11438)
* 音訊和視訊多媒體檔案的插入無法在 **插入多媒體** 表徵圖。 (11320)
* 使用具有專用標題元素的模板建立映射時發生驗證錯誤。 (11212)
* 原生PDF |表格標題中出現的腳注會導致PDF輸出中對應頁尾中出現粗體和居中對齊的文字。 (10610)
>[!NOTE]
>
>若要反映原生PDF變更，請刪除位於/content/dam/dita-templates的PDF資料夾，然後升級至最新組建。 (10610)

### 因應措施的已知問題

Adobe已識別下列AEM指南的已知問題(as a Cloud Service2023年3月發行)。

* 使用者無法儲存或建立重複資產的版本。

**因應措施**:對重複資產進行任何變更前，請先從資產UI重新處理該資產。

