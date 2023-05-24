---
title: 發行說明 | Adobe Experience Manager Guidesas a Cloud Service，2023年2月發行
description: Adobe Experience Manager Guidesas a Cloud Service版2月版
exl-id: c639b136-11ed-4a8b-a595-4bb5da879747
source-git-commit: ee520ab86ea41df7556a1f40d7bfc5e3617b34ae
workflow-type: tm+mt
source-wordcount: '2178'
ht-degree: 2%

---

# Adobe Experience Manager Guidesas a Cloud Service版2月版

## 升級至2月版

as a Cloud Service升級您目前的Adobe Experience Manager Guides (稍後稱為 *AEM指南as a Cloud Service*)進行設定：
1. 檢視Cloud Services的Git程式碼，並切換到在Cloud Services管道中設定的分支，該分支與您要升級的環境相對應。
2. 更新 `<dox.version>` 中的屬性 `/dox/dox.installer/pom.xml` 將您的Cloud Services Git程式碼檔案改成2023.2.235。
3. 提交變更並執行Cloud Services管道，以升級至AEM Guidesas a Cloud Service的2月版本。

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


## 新增功能和功能改善

AEM Guidesas a Cloud Service在2月版本中提供增強功能和新功能：

### 從網頁編輯器產生報表

AEM Guides的網頁編輯器提供了一項功能，可讓您檢查技術檔案的整體完整性，並為其產生報告。
您可以從以下位置檢視主題清單、管理中繼資料，以及檢視目前地圖的所有參照中所使用的多媒體：
**報表** 索引標籤進行編輯。

**產生主題清單檢視**

您可以產生「主題清單」，提供主題的相關詳細資訊，例如參照型別、檔案狀態和作者。 您也可以產生CSV來下載DITA map中主題的目前快照。

**管理中繼資料並變更檔案狀態**

您可以在個別主題上套用標籤，或使用大量標籤功能，在多個主題、DITA map或子對映上套用多個標籤。 您也可以將所有選取主題的檔案狀態變更為下一個可能的通用檔案狀態。

<img src="assets/web-editor-metadata-panel.png" alt="管理中繼資料" width="600">

**產生多媒體報告**

您可以產生多媒體報告，其中包含有關目前地圖中參照使用的多媒體的詳細資訊。 您可以彈性地篩選和排序報表中列出的多媒體檔案。
您也可以產生CSV來下載DITA map中使用之多媒體的目前快照。

<img src="assets/web-editor-reports-multimedia.png" alt="多媒體報告" width="600">

### 針對稽核功能改版的UX

現在AEM Guides提供改良的UX，可幫助您檢閱共用供檢閱的主題。 在最新的體驗中，稽核功能有下列增強功能：

* 重新整理的使用者介面
* 條件面板，可讓您根據主題中的可用條件反白顯示內容
* 註解面板中的每個註解都會連結到目前主題中的對應文字。 它有助於您識別註解的文字。
* 註解會以檔案中註解文字的順序顯示。
* 稽核工作流程上會顯示稽核任務的名稱。
* 選取審閱工作的根目錄對映，用於解析審閱內容中使用的所有關鍵參考和字彙表術語。
* 可協助您快速反白或刪除線文字的內容工具列
* 「選項」選單可編輯或刪除您自己的註解
* 對於過時的註解，您可以存取並排檢視，這有助於將主題的前一版本與目前的稽核版本進行比較。
* 使用篩選器時，右側面板上的註解會根據選取範圍進行篩選，而左側面板中的註解數量也會據此更新。


   <img alt="評論任務" src="assets/comment-pop-up-panel.png" width="600">



### 翻譯增強功能

現在，翻譯儀表板中提供了更方便使用的增強功能，可幫助您從網頁編輯器輕鬆翻譯檔案。

**將版本標籤傳遞至目標版本**

AEM Guides可讓您將來源檔案的標籤傳遞至目標檔案。 這可協助您輕鬆識別翻譯檔案的來源版本。

<img alt="翻譯標籤" src="assets/translation-pass-source-label.png" width="600">

例如，如果您有一些來源檔案套用了版本標籤1.0版，那麼您也可以將來源標籤（1.0版）傳遞給翻譯的檔案。

**強制同步處理不同步的資產**

如果您對部分資產進行變更，AEM Guides會將其標籤為不同步。 您可以重新翻譯修改的資產，或選擇關閉「不同步」狀態。 例如，如果您進行了一些確實不需要翻譯的次要變更，您可以將其狀態標示為「同步」。

<img src="assets/translation-version-diff.png" alt="翻譯面板" width="600">

**檢視主題或地圖的進行中翻譯專案**

翻譯控制面板上的某些參考可能正在進行中。 現在AEM Guides提供的功能可幫助您檢視包含所選參考的所有進行中翻譯專案的清單（以及目標語言）。


### 從網頁編輯器產生多種格式的輸出

現在您可以從網頁編輯器輕鬆產生主題或DITA map的輸出。 您可以設定各種輸出預設集，例如AEM Site、PDF、HTML5、JSON （Headless輸出格式）和自訂輸出。 然後，您可以使用這些來產生個別輸出。

您可以在DITA主題中定義屬性，然後使用條件預設集在發佈輸出時套用條件。 您也可以使用基準線發佈功能，選擇性地發佈DITA map或主題的特定版本。


### 在地圖層級尋找和取代文字

AEM Guides可讓您在地圖中搜尋包含特定文字的檔案。 搜尋的文字會在檔案中反白顯示。 現在，您也可以在所有檔案中，將搜尋到的字詞或片語取代為其他字詞或片語。 您可以選取 **全部取代** 圖示取代所有檔案中搜尋字詞的所有出現位置。

<img src="assets/map-find-replace.png" alt="地圖尋找取代" width="600">

### 從存放庫面板刪除和複製檔案

現在，您可以輕鬆地從建立檔案的重複或復本 **選項** 儲存庫面板中選取檔案的功能表。 依預設，檔案會以字尾建立(例如 `filename_1.extension`)。

<img src="assets/options-menu-repo-view-file-level.png" alt="檔案選項功能表 " width="500">


### 其他Web Editor增強功能

* 在AEM Guides中，您可以使用快顯選單對影像和媒體檔案執行一些常見操作。 現在您也可以在存放庫中找出選取的影像或媒體，或在Assets UI中檢視檔案預覽。

* 目前資料夾描述檔的名稱會在主工具列中顯示為「使用者偏好設定」圖示的標籤。 這有助於您識別正在處理的資料夾設定檔。

* 在地圖檢視中開啟地圖時，目前地圖的標題會顯示在主工具列的中心。 這有助於讓使用者知道目前開啟的地圖。


### 在氧氣編輯器中檢視標題取代UUID

現在AEM Guides可讓您選擇 **在編輯器和地圖管理員中使用標題** 選項。 如果選取此選項，當在「編輯器」或「DITA地圖管理員」中開啟時，檔案的標題會顯示在檔案的標籤上。 如果您未選取此選項，則檔案的UUID會顯示在檔案的索引標籤上。

### AEM Guidesas a Cloud Service的微服務型發佈

新的發佈微服務可讓您在AEM Guidesas a Cloud Service上同時執行大量發佈工作負載，並利用業界領先的Adobe I/O Runtime無伺服器平台。

對於每個發佈請求，AEM Guidesas a Cloud Service會執行單獨的容器，它會根據使用者請求水平縮放。 這可讓您執行多個發佈請求，並獲得改進的效能。

如需詳細資訊，請參閱 [為AEM Guidesas a Cloud Service設定新的微服務型發佈](https://experienceleague.adobe.com/docs/experience-manager-guides-learn/tutorials/knowledge-base/publishing/configure-microservices.md).

### 原生PDF |在PDF輸出中新增自訂書籤

現在，您可以在最終PDF輸出中的特定內容上新增自訂書籤，以便輕鬆導覽。 這將會新增到從DITA map中的主題或區段標題建立的目錄。

### 原生PDF |在目錄專案和主題內容上套用自訂樣式

AEM Guides提供在目錄專案或PDF輸出中的特定主題上套用自訂樣式的功能。 例如，您可以變更目錄中的文字顏色和主題標題。 您也可以在主題內的整個內容上套用樣式。


### 原生PDF |在註腳元件中設定頁面標籤的樣式

現在，您可以在註腳中設定頁面標籤的樣式。 例如，您可以新增括弧或變更其顏色。 這些樣式可協助使用者輕鬆識別檔案中的頁面標籤。

### 原生PDF |變更列表示目錄中已變更的主題

AEM Guides現在可讓您快速識別PDF輸出目錄。  它會在目錄中已變更的主題左側顯示變更列。 您可以按一下目錄中的主題並檢視詳細變更。

<img src="assets/change-marker-toc.png" alt="在目錄中變更標籤 " width="500">

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
