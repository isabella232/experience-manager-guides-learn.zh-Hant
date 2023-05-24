---
title: 發行說明 | Adobe Experience Manager Guidesas a Cloud Service，2023年4月發行
description: 最新版Adobe Experience Manager Guidesas a Cloud Service
exl-id: 3b09f0b3-cfa4-422d-91b7-733ab1c1896c
source-git-commit: cf612da41f79b0bf9da4c4d7454a0e3c86af7a4c
workflow-type: tm+mt
source-wordcount: '852'
ht-degree: 2%

---

# 4月版Adobe Experience Manager Guidesas a Cloud Service

## 升級至最新版本

as a Cloud Service升級您目前的Adobe Experience Manager Guides (稍後稱為 *AEM指南as a Cloud Service*)進行設定：

1. 檢視Cloud Services的Git程式碼，並切換到在Cloud Services管道中設定的分支，該分支與您要升級的環境相對應。
2. 更新 `<dox.version>` 中的屬性 `/dox/dox.installer/pom.xml` 將Cloud Services Git程式碼的檔案設為2023.4.249。
3. 提交變更並執行Cloud Services管道，以升級到最新版AEM Guidesas a Cloud Service。

## 索引現有內容的步驟(僅限使用9月之前版本的AEM Guidesas a Cloud Service)

執行以下步驟，為現有內容編制索引，並在地圖層級使用新的尋找和取代文字：

* 對伺服器執行POST要求（使用正確的驗證） - `http://<server:port>/bin/guides/map-find/indexing`.
(可選：您可以傳遞地圖的特定路徑來為其建立索引，預設情況下，所有地圖都會建立索引 ||範例： `https://<Server:port>/bin/guides/map-find/indexing?paths=<map_path_in_repository>`)

* 此API將傳回jobId。 若要檢查作業的狀態，您可以將具有作業ID的GET要求傳送至相同的端點 —  `http://<server:port>/bin/guides/map-find/indexing?jobId={jobId}`
(例如： http://&lt;
_localhost：8080_>/bin/guides/map-find/indexing？jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678)

* 工作完成後，上述GET要求將回應為成功，並提及是否有任何地圖失敗。 可以從伺服器記錄檔確認已成功建立索引的對應。

## 相容性矩陣

本節列出AEM Guides 2023年4月as a Cloud Service發行版本支援之軟體應用程式的相容性矩陣。

### FrameMaker和FrameMaker Publishing Server

| AEM Guides as a Cloud版本 | FMPS | FrameMaker |
| --- | --- | --- |
| 2023.04.0 | 不相容 | 2022或更高 |
|  |  |  |


### 氧氣聯結器

| AEM Guides as a Cloud版本 | 氧氣聯結器視窗 | 氧氣聯結器Mac | 在氧氣視窗中編輯 | 在氧氣Mac中編輯 |
| --- | --- | --- | --- | --- |
| 2023.04.0 | 2.9-uuid-2 | 2.9-uuid-2 | 2.3 | 2.3 |
|  |  |  |  |


## 新增功能和功能改善

AEM Guidesas a Cloud Service在最新版本中提供增強功能和新功能：

### PDF發佈中的進階中繼資料支援

AEM Guides現在為中繼資料提供進階支援，這些中繼資料會對應到PDF輸出中的中繼資料。 中繼資料選項包括有關檔案及其內容的資訊，例如作者姓名、檔案標題、關鍵字、版權資訊和其他資料欄位。

<img src="assets/pdf-metadata.png" alt=" 原生pdf中繼資料">

您可以匯入XMP檔案，AEM Guides可以從檔案中挑選資訊。 您也可以選擇使用下拉式清單提供中繼資料名稱和值。 您也可以直接在名稱欄位中輸入，以新增自訂中繼資料。


### 增強型大綱檢視面板

AEM Guides提供改良的「大綱檢視」面板，您可以在其中取得檔案中使用之元素的階層檢視。

<img src="assets/select-element-content-outline-view_cs.png" alt=" 原生pdf中繼資料">

「大綱檢視」提供下列增強功能：

* 「檢視選項」下拉式清單會顯示在「大綱檢視」面板上方。 如果元素有ID、屬性和文字，您可以從下拉式清單中選取它們，以便與元素一起顯示。 可以在「大綱檢視」面板中顯示的屬性由管理員在 **編輯器設定**.

* 您可以使用搜尋功能，依名稱、ID、文字或屬性值來搜尋元素。


### AEM Guidesas a Cloud Service的微服務型發佈

AEM Guidesas a Cloud Service提供以微服務式發佈同時執行大量發佈工作負荷的功能，並可運用業界領先的Adobe I/O Runtime無伺服器平台。

現在在4月發行版本中，您可以同時執行多個發佈要求，並使用微服務型原生PDF發佈以非常有效率的方式產生大量PDF輸出。
如需詳細資訊，請參閱 [為AEM Guidesas a Cloud Service設定新的微服務型發佈](../knowledge-base/publishing/configure-microservices.md).


## 已修正的問題

修復了各種區域的錯誤如下所列：

* 原生PDF |如果發佈的內容具有包含brackets()的輸出類別，會導致發佈凍結。 (11596)
* 在移動（拖放）至開啟追蹤變更的現有清單專案時發生問題。 (11570)
* 當作為新清單專案移動（拖放）時會發生問題，且追蹤變更開啟。 (11569)
* 「追蹤變更」開啟時，縮排或減少縮排清單專案無法如預期運作。 (11568)
* 在開啟「追蹤變更」的行上新增內容，然後關閉「追蹤變更」並不會實際將其關閉。 (11567)
* 難以拖放清單專案，文字會移動來取代清單專案。 (11566)
* 完成的檢閱不會在唯讀模式下開啟。 (11387)
* AEM網站搜尋中發生問題（在2-3層級節點以外無法運作）。 (11352)
* 以綠色（追蹤變更）顯示的元素中進行製作時，即使追蹤變更已停用，新內容仍會顯示為追蹤變更。 (7021)

### 有因應措施的已知問題

Adobe已確定2023年4月as a Cloud Service發行的AEM Guides的下列已知問題。

* 原生PDF |在明確開啟輸出預設集之前，不會填入舊中繼資料。
