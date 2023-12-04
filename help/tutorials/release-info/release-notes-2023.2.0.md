---
title: 發行說明 | Adobe Experience Manager Guidesas a Cloud Service，2023年2月發行
description: 2月Adobe Experience Manager Guidesas a Cloud Service版本
source-git-commit: 880cd344ceb65ea339be699ebcad41c0d62e168a
workflow-type: tm+mt
source-wordcount: '870'
ht-degree: 0%

---

# 2023年2月發行的Adobe Experience Manager Guidesas a Cloud Service

本發行說明涵蓋升級指示、相容性矩陣，以及2023年2月版Adobe Experience Manager Guides中修正的問題(以下稱 *AEM Guidesas a Cloud Service*)。

如需新功能和增強功能的詳細資訊，請參閱 [2023年2月版AEM Guidesas a Cloud Service的新增功能](whats-new-2023.2.0.md).

## 升級至2023年2月發行版本

執行下列步驟，升級您目前的AEM Guidesas a Cloud Service設定：
1. 檢視Cloud Service的Git程式碼，並切換到在Cloud Service管線中設定的分支，該分支與您要升級的環境相對應。
2. 更新 `<dox.version>` 中的屬性 `/dox/dox.installer/pom.xml` 將Cloud Service Git程式碼的檔案設為2023.2.235。
3. 提交變更並執行Cloud Service管道，以升級至2023年2月版本的AEM Guidesas a Cloud Service。

## 索引現有內容的步驟(僅限使用9月之前版本的AEM Guidesas a Cloud Service)

執行以下步驟來索引現有內容，並在地圖層級使用新的尋找和取代文字：

* 對伺服器執行POST要求（使用正確的驗證） - `http://<server:port>/bin/guides/map-find/indexing`.
(選用：您可以傳遞地圖的特定路徑來編列索引，預設情況下，所有地圖都會編列索引 ||範例： `https://<Server:port>/bin/guides/map-find/indexing?paths=<map_path_in_repository>`)

* 此API將傳回jobId。 若要檢查作業的狀態，您可以傳送作業識別碼的GET要求至相同的端點 —  `http://<server:port>/bin/guides/map-find/indexing?jobId={jobId}`
(例如： http://&lt;_localhost：8080_>/bin/guides/map-find/indexing？jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678)

* 工作完成後，上述GET要求將回應為成功，並提及是否有任何地圖失敗。 可以從伺服器記錄檔確認已成功編制索引的對應。

## 相容性矩陣

本節列出AEM Guides 2023年2月as a Cloud Service發行版本支援之軟體應用程式的相容性矩陣。

### FrameMaker和FrameMaker Publishing Server

| AEM Guides as a Cloud版本 | FMPS | FrameMaker |
| --- | --- | --- |
| 2023.02.0 | 不相容 | 2022或更高 |
| | | |

*從2020.2開始的FMPS版本支援AEM中建立的基準和條件。

### 氧氣聯結器

| AEM Guides as a Cloud版本 | 氧氣聯結器視窗 | 氧氣聯結器Mac | 在氧氣視窗中編輯 | 在氧氣Mac中編輯 |
| --- | --- | --- | --- | --- |
| 2023.02.0 | 2.8-uuid-8 | 2.8-uuid-8 | 2.3 | 2.3 |
|  |  |  |  |

## 已修正的問題

以下列出各種區域中修正的錯誤：

### 編寫

* 網頁編輯器html中的變更會導致 `<dl>` 和 `<dlentry>`. (11024)
* 有些屬性不會被視為有條件屬性，而會造成問題。 (10895)
* 三個或多個巢狀層級 `<indexterm>` 非巢狀內嵌於原生PDF匯出中。 (10799)
* 從「作者」切換到「來源」檢視時，內容會消失在工作內文中。 (10735)
* 評論在評論任務中被錯誤放置。 (10625)
* **還原** 或 **取消復原** 對部分檔案無法正常運作。 (10373)
* 複製和貼上動作不會保留自訂中繼資料。 (10367)
* XML編輯器中的還原選項會將使用者帶至頁面頂端。 (10091)
* 執行資產的複製和貼上操作後，會移除節點屬性。 (10053)
* mimetype是針對DITA資產建立和更新的硬式編碼。 (8979)
* 對於透過Assets UI上傳的檔案，版本記錄中的版本建立者名稱是&quot;fmdita-serviceuser&quot;。 (8910)
* 雲端上安裝AEM Guides時，無法複製和貼上內容片段。 (11315)
* 使用自訂結構描述載入內容時，瀏覽器（網頁編輯器）會凍結。 (11211)

### 管理

* 複製DITA map資產（從資產UI ）會導致複製的資產中出現錯誤的基準線。 (11218)
* 在檔案上傳超過AEM允許的上限（預設為2 GB）時，不會顯示警告訊息。 (10817)
* 網頁編輯器 — 基準線 |在網頁編輯器內的新基準儀表板中，「最新」欄的行為是不同的。 (10808)
* 翻譯 |由於/libs/fmdita/i18n/ja.json無效，翻譯工作未開始。 (10543)
* 翻譯 |從翻譯控制面板（人工翻譯）建立的範圍設定翻譯專案發生錯誤。 (10526)
* 翻譯 |如果整個語言資料夾的資產位於使用中的翻譯專案中，該資料夾的後處理會被封鎖。 (10332)
* 如果版本在基線編輯器中變更並儲存，則任何資產都會出現多個快顯視窗。 (10399)
* 工作階段洩漏發生於 `com.day.cq.search.impl.builder.QueryBuilderImpl.createResourceResolver(QueryBuilderImpl.java:210)`. (10279)

### 發佈

* 主題重新產生不適用於某些案例。 (10635)
* Publishlistener不會在資訊記錄中顯示要求的資料，而且其中也包含一些垃圾記錄檔。( 10567)
* 原生PDF |使用「新增至資料夾設定檔」選項建立輸出預設集時，PDF產生會因「Null指標」例外而失敗。 (10950)
* 原生PDF |旋轉表格標題時發生問題。 (10555)
* 原生PDF |巢狀 `<indexterm>` 非巢狀內嵌於原生PDF匯出中。 (10521)
* 原生PDF |附錄中的巢狀topicref全部轉換為臨時HTML中的h1。 (10454)
* 使用FrameMaker Publishing Server2020產生的PDF基準發佈失敗。 (10551)
* 原生PDF |新增 `xref` 至影像不會呈現在產生的PDF上。 (11346)
* 原生PDF |影像標籤會將display-inline屬性新增至所有影像。 (10653)
* 原生PDF |預設會在產生的輸出中隱藏草稿註解。 (10560)
* 原生PDF |不會將navtitle授予topichead。 (10509)
