---
title: 發行說明 | Adobe Experience Manager Guidesas a Cloud Service，2023年2月發行
description: Adobe Experience Manager Guidesas a Cloud Service版2月版
exl-id: c639b136-11ed-4a8b-a595-4bb5da879747
source-git-commit: 99ca14a816630f5f0ec1dc72ba77994ffa71dff6
workflow-type: tm+mt
source-wordcount: '854'
ht-degree: 4%

---

# 2023年2月發行的Adobe Experience Manager Guidesas a Cloud Service

此發行說明涵蓋升級指示、相容性矩陣，以及2023年2月版Adobe Experience Manager Guides中修正的問題(後稱為 *AEM指南as a Cloud Service*)。

如需新功能和增強功能的詳細資訊，請參閱 [AEM Guidesas a Cloud Service版2023年2月的新增功能](whats-new-2023.2.0.md).

## 升級至2023年2月發行版本

請執行以下步驟，升級您目前的AEM Guidesas a Cloud Service設定：
1. 檢視Cloud Services的Git程式碼，並切換到在Cloud Services管道中設定的分支，該分支與您要升級的環境相對應。
2. 更新 `<dox.version>` 中的屬性 `/dox/dox.installer/pom.xml` 將您的Cloud Services Git程式碼檔案改成2023.2.235。
3. 確認變更並執行Cloud Services管道，以升級至2023年2月版的AEM Guidesas a Cloud Service。

## 索引現有內容的步驟(僅限使用9月之前版本的AEM Guidesas a Cloud Service)

執行以下步驟來索引現有內容，並在地圖層級使用新的尋找和取代文字：

* 對伺服器執行POST要求（使用正確的驗證） - `http://<server:port>/bin/guides/map-find/indexing`.
(可選：您可以傳遞地圖的特定路徑來為其建立索引，預設情況下，所有地圖都會建立索引 ||範例： `https://<Server:port>/bin/guides/map-find/indexing?paths=<map_path_in_repository>`)

* 此API將傳回jobId。 若要檢查作業的狀態，您可以將具有作業ID的GET要求傳送至相同的端點 —  `http://<server:port>/bin/guides/map-find/indexing?jobId={jobId}`
(例如： http://&lt;
_localhost：8080_>/bin/guides/map-find/indexing？jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678)

* 工作完成後，上述GET要求將回應為成功，並提及是否有任何地圖失敗。 可以從伺服器記錄檔確認已成功建立索引的對應。

## 相容性矩陣

本節列出AEM Guides 2023年2月as a Cloud Service發行版本支援之軟體應用程式的相容性矩陣。

### FrameMaker和FrameMaker Publishing Server

| AEM Guides as a Cloud版本 | FMPS | FrameMaker |
| --- | --- | --- |
| 2023.02.0 | 不相容 | 2022或更高 |
|  |  |  |

*自2020.2開始的FMPS版本支援AEM中建立的基準和條件。

### 氧氣聯結器

| AEM Guides as a Cloud版本 | 氧氣聯結器視窗 | 氧氣聯結器Mac | 在氧氣視窗中編輯 | 在氧氣Mac中編輯 |
| --- | --- | --- | --- | --- |
| 2023.02.0 | 2.8-uuid-8 | 2.8-uuid-8 | 2.3 | 2.3 |
|  |  |  |  |

## 已修正的問題

修復了各種區域的錯誤如下所列：

### 編寫

* 網頁編輯器html中的變更導致下列專案發生問題： `<dl>` 和 `<dlentry>`. (11024)
* 有些屬性不會被視為有條件屬性而造成問題。 (10895)
* 三個層級或更多巢狀 `<indexterm>` 未巢狀化至原生PDF匯出中。 (10799)
* 從「作者」切換到「來源」檢視時，內容會消失在任務的內文中。 (10735)
* 評論在評論任務中被錯誤放置。 (10625)
* **還原** 或 **取消復原** 某些檔案無法正常運作。 (10373)
* 複製和貼上動作未保留自訂中繼資料。 (10367)
* XML編輯器中的還原選項會將使用者帶至頁面頂端。 (10091)
* 在資產的複製和貼上操作後，節點屬性會被移除。 (10053)
* mimeType是為DITA資產建立和更新而以硬式編碼。 (8979)
* 對於透過Assets UI上傳的檔案，版本歷史記錄中的版本建立者名稱是&quot;fmdita-serviceuser&quot;。 (8910)
* 雲端上安裝AEM Guides時，無法複製和貼上內容片段。 (11315)
* 使用自訂結構描述載入內容時，瀏覽器（網頁編輯器）會凍結。 (11211)

### 管理

* 複製DITA map資產（從資產UI ）會導致複製的資產中出現錯誤的基準線。 (11218)
* 上傳大於AEM所允許限制（預設為2 GB）的檔案時，不會顯示警告訊息。 (10817)
* 網頁編輯器 — 基準線 |在網頁編輯器內的新基準線控制面板中，「最新」欄的行為不同。 (10808)
* 翻譯 |由於/libs/fmdita/i18n/ja.json無效，翻譯工作未開始。 (10543)
* 翻譯 |從翻譯控制面板（人工翻譯）建立的範圍設定翻譯專案中發生錯誤。 (10526)
* 翻譯 |資產存在於使用中翻譯專案的整個語言資料夾都會封鎖後續處理。 (10332)
* 如果版本變更並儲存在「基準線」編輯器上，則任何資產都會出現多個快顯視窗。 (10399)
* 工作階段洩漏發生於 `com.day.cq.search.impl.builder.QueryBuilderImpl.createResourceResolver(QueryBuilderImpl.java:210)`. (10279)

### 發佈

* 主題重新產生不適用於某些情況。 (10635)
* Publishlistener不會在資訊記錄中顯示要求的資料，而且其中也包含一些垃圾記錄檔。( 10567)
* 原生PDF |使用「新增至資料夾設定檔」選項建立輸出預設集時，PDF產生失敗並出現Null指標例外狀況。 (10950)
* 原生PDF |旋轉表格標題時發生問題。 (10555)
* 原生PDF |巢狀 `<indexterm>` 未巢狀化至原生PDF匯出中。 (10521)
* 原生PDF |附錄中的巢狀topicref全部轉換為臨時HTML中的h1。 (10454)
* 使用FrameMaker Publishing Server 2020產生的PDF基準線發佈失敗。 (10551)
* 原生PDF |新增 `xref` 「 to a Image 」不會轉譯產生PDF上的影像。 (11346)
* 原生PDF |影像標籤會將display-inline屬性新增至所有影像。 (10653)
* 原生PDF |預設會在產生的輸出中隱藏草稿註解。 (10560)
* 原生PDF | navtitle不適用於topichead。 (10509)
