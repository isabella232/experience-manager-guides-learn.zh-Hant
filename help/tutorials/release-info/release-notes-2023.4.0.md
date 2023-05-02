---
title: 發行說明 | Adobe Experience Manager指南as a Cloud Service,2023年4月發行版本
description: 最新版Adobe Experience Manager指南as a Cloud Service
exl-id: 3b09f0b3-cfa4-422d-91b7-733ab1c1896c
source-git-commit: cf612da41f79b0bf9da4c4d7454a0e3c86af7a4c
workflow-type: tm+mt
source-wordcount: '852'
ht-degree: 2%

---

# 4月發行的Adobe Experience Manager指南as a Cloud Service

## 升級至最新版本

升級您目前的Adobe Experience Manager指南as a Cloud Service(稍後稱為 *AEM指南as a Cloud Service*)，請執行下列步驟：

1. 查看Cloud Services的Git程式碼，並切換至Cloud Services管道中所設定的分支，該管道與您要升級的環境對應。
2. 更新 `<dox.version>` 屬性 `/dox/dox.installer/pom.xml` 檔案的Cloud ServicesGit程式碼。
3. 提交變更並執行Cloud Services管道，以升級至最新版本的AEM指南as a Cloud Service。

## 為現有內容建立索引的步驟(僅限使用9月版AEM指南之前的版本時as a Cloud Service)

執行以下步驟來建立現有內容的索引，並在映射級別使用新的查找和替代文字：

* 對伺服器執行POST請求（使用正確的驗證） —  `http://<server:port>/bin/guides/map-find/indexing`.
(可選：您可以傳遞映射的特定路徑來為其建立索引，預設情況下，所有映射都將編製索引 ||範例： `https://<Server:port>/bin/guides/map-find/indexing?paths=<map_path_in_repository>`)

* API會傳回jobId。 要檢查作業的狀態，可以向相同的終點發送具有作業ID的GET請求 —  `http://<server:port>/bin/guides/map-find/indexing?jobId={jobId}`
(例如：http://&lt;
_localhost:8080_>/bin/guides/map-find/indexing?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678)

* 作業完成後，上述GET要求會以成功回應，並在地圖失敗時提及。 可以從伺服器日誌中確認已成功索引的映射。

## 相容性矩陣

本節列出AEM指南as a Cloud Service於2023年4月發行版本所支援軟體應用程式的相容性矩陣。

### FrameMaker和FrameMaker Publishing Server

| AEM雲端版本指南 | FMPS | FrameMaker |
| --- | --- | --- |
| 2023.04.0 | 不相容 | 2022年或更新版本 |
|  |  |  |


### 氧連接器

| AEM雲端版本指南 | 氧連接器窗口 | 氧連接器Mac | 在氧氣窗口中編輯 | 在Oxion Mac中編輯 |
| --- | --- | --- | --- | --- |
| 2023.04.0 | 2.9-uuid-2 | 2.9-uuid-2 | 2.3 | 2.3 |
|  |  |  |  |


## 新增功能和功能改善

AEM指南as a Cloud Service提供最新版本的增強功能和新功能：

### PDF發佈中的進階中繼資料支援

AEM指南現在提供對應至PDF輸出中中繼資料的中繼資料的進階支援。 元資料選項包括關於文檔及其內容的資訊，如作者的名稱、文檔標題、關鍵字、版權資訊和其他資料欄位。

<img src="assets/pdf-metadata.png" alt=" 原生pdf中繼資料">

您可以匯入XMP檔案，AEM參考線可從檔案中挑選資訊。 您也可以選擇使用下拉式清單提供中繼資料名稱和值。 您也可以直接在名稱欄位中輸入，以新增自訂中繼資料。


### 增強的大綱視圖面板

AEM指南提供了一個改進的「大綱視圖」面板，在該面板中可以獲取文檔中使用的元素的分層視圖。

<img src="assets/select-element-content-outline-view_cs.png" alt=" 原生pdf中繼資料">

「大綱視圖」提供了以下增強功能：

* 「查看選項」下拉清單顯示在「大綱視圖」面板的頂部。 如果元素有ID、屬性和文字，您可以從下拉式清單中選取它們，以連同元素一起顯示。 可在「大綱視圖」面板中顯示的屬性由管理員在 **編輯器設定**.

* 使用搜尋功能，您可以依元素名稱、ID、文字或屬性值來搜尋元素。


### AEM指南的微服務發佈as a Cloud Service

AEM指南as a Cloud Service提供與微服務發佈功能同時執行大型發佈工作負載，並運用領先業界的Adobe I/O Runtime無伺服器平台。

現在，在4月的版本中，您可以使用微服務型原生PDF發佈，同時執行多個發佈請求，並高效產生大量PDF輸出。
如需詳細資訊，請參閱 [為AEM參考線設定全新的Microservice發佈as a Cloud Service](../knowledge-base/publishing/configure-microservices.md).


## 已修正的問題

以下列出各個區域中修正的錯誤：

* 原生PDF |若發佈內容含有帶括弧()的輸出類別，會導致發佈凍結。 (11596)
* 移動（拖放）以取代已開啟「追蹤變更」的現有清單項目時發生問題。 (11570)
* 將新清單項目移動（拖放）時發生問題，並開啟追蹤變更。 (11569)
* 在開啟「跟蹤更改」時，縮進或縮進清單項無法如預期工作。 (11568)
* 在開啟「追蹤變更」的行上新增內容，然後關閉「追蹤變更」實際上並不會關閉。 (11567)
* 拖放清單項目時遇到困難，文字會移動以取代清單項目。 (11566)
* 已完成的審核未以只讀模式開啟。 (11387)
* AEM網站搜尋發生問題（無法運作超過2-3級節點）。 (11352)
* 在以綠色顯示的元素中編寫時（追蹤變更），即使已停用追蹤變更，新內容仍會顯示為追蹤變更。 (7021)

### 因應措施的已知問題

Adobe已識別下列AEM指南的已知問題(as a Cloud Service2023年4月發行)。

* 原生PDF |在明確開啟輸出預設集之前，不會填入舊的中繼資料。
