---
title: 發行說明 | Adobe Experience Manager指南as a Cloud Service,2023年2月發行版本
description: 2月發行的Adobe Experience Manager指南as a Cloud Service
exl-id: c639b136-11ed-4a8b-a595-4bb5da879747
source-git-commit: ee520ab86ea41df7556a1f40d7bfc5e3617b34ae
workflow-type: tm+mt
source-wordcount: '2178'
ht-degree: 2%

---

# 2月發行的Adobe Experience Manager指南as a Cloud Service

## 升級至2月版

升級您目前的Adobe Experience Manager指南as a Cloud Service(稍後稱為 *AEM指南as a Cloud Service*)，請執行下列步驟：
1. 查看Cloud Services的Git程式碼，並切換至Cloud Services管道中所設定的分支，該管道與您要升級的環境對應。
2. 更新 `<dox.version>` 屬性 `/dox/dox.installer/pom.xml` 檔案的Cloud ServicesGit程式碼。
3. 提交變更並執行Cloud Services管道，以升級至2月版的AEM指南as a Cloud Service。

## 為現有內容建立索引的步驟(僅限使用9月版AEM指南之前的版本時as a Cloud Service)

執行以下步驟來建立現有內容的索引，並在映射級別使用新的查找和替代文字：

* 對伺服器執行POST請求（使用正確的驗證） —  `http://<server:port>/bin/guides/map-find/indexing`.
(可選：您可以傳遞映射的特定路徑來為其建立索引，預設情況下，所有映射都將編製索引 ||範例： `https://<Server:port>/bin/guides/map-find/indexing?paths=<map_path_in_repository>`)

* API會傳回jobId。 要檢查作業的狀態，可以向相同的終點發送具有作業ID的GET請求 —  `http://<server:port>/bin/guides/map-find/indexing?jobId={jobId}`
(例如：http://&lt;
_localhost:8080_>/bin/guides/map-find/indexing?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678)

* 作業完成後，上述GET要求會以成功回應，並在地圖失敗時提及。 可以從伺服器日誌中確認已成功索引的映射。

## 相容性矩陣

本節列出AEM指南as a Cloud Service於2023年2月發行的軟體應用程式的相容性矩陣。

### FrameMaker和FrameMaker Publishing Server

| AEM雲端版本指南 | FMPS | FrameMaker |
| --- | --- | --- |
| 2023.02.0 | 不相容 | 2022年或更新版本 |
|  |  |  |

*從2020.2開始的FMPS版本支援在AEM中建立的基線和條件。

### 氧連接器

| AEM雲端版本指南 | 氧連接器窗口 | 氧連接器Mac | 在氧氣窗口中編輯 | 在Oxion Mac中編輯 |
| --- | --- | --- | --- | --- |
| 2023.02.0 | 2.8-uuid-8 | 2.8-uuid-8 | 2.3 | 2.3 |
|  |  |  |  |


## 新增功能和功能改善

AEM指南as a Cloud Service提供2月版中的增強功能和新功能：

### 從網頁編輯器產生報表

AEM指南隨附於網頁編輯器中的功能，可讓您檢查技術檔案的整體完整性，並為其產生報表。
您可以檢視主題清單、管理中繼資料，以及從
**報表** 頁簽。

**生成主題清單視圖**

您可以生成主題清單，該清單提供有關主題的詳細資訊，如參考類型、文檔狀態和作者。 您也可以產生CSV來下載DITA映射中主題的目前快照。

**管理元資料和更改文檔狀態**

您可以對個別主題套用標籤，或使用大量標籤功能，對多個主題、DITA映射或子映射套用多個標籤。 您也可以將所有所選主題的文檔狀態更改為下一個可能的共同文檔狀態。

<img src="assets/web-editor-metadata-panel.png" alt="管理中繼資料" width="600">

**產生多媒體報表**

您可以生成多媒體報告，其中包含有關當前地圖中參考中使用的多媒體的詳細資訊。 您可以彈性地篩選及排序報表中列出的多媒體檔案。
您也可以產生CSV來下載DITA映射中所用多媒體的目前快照。

<img src="assets/web-editor-reports-multimedia.png" alt="多媒體報告" width="600">

### 經過改寫的UX，提供審核功能

現在AEM指南提供改良的UX，可協助您檢閱共用供檢閱的主題。 在最新體驗中，檢閱功能有下列增強功能：

* 重新整理的使用者介面
* 條件面板，可讓您根據主題中的可用條件反白標示內容
* 註解面板中的每個註解都連結至目前主題中的對應文字。 可協助您識別留言的文字。
* 注釋按文檔中注釋文本的順序顯示。
* 審閱任務的名稱將顯示在審閱工作流上。
* 選擇用於解析審閱內容中使用的所有關鍵引用和術語的審閱任務的rootmap。
* 內容工具列，可協助您快速反白標示或刪除文字
* 可編輯或刪除您自己的注釋的選項菜單
* 若是過時的留言，您可以存取並排檢視，以協助您比較主題的舊版本與目前的審核版本。
* 使用篩選時，會根據選取項目篩選右面板的註解，並據此更新左面板的註解數。


   <img alt="審核任務" src="assets/comment-pop-up-panel.png" width="600">



### 翻譯增強功能

現在，翻譯控制面板中有更方便使用的增強功能，可協助您從網頁編輯器輕鬆翻譯檔案。

**將版本標籤傳遞至目標版本**

AEM指南可讓您將來源檔案的標籤傳遞至目標檔案。 這有助於您輕鬆識別翻譯檔案的來源版本。

<img alt="翻譯標籤" src="assets/translation-pass-source-label.png" width="600">

例如，如果某些源檔案已應用版本標籤Release 1.0，則您也可以將源標籤(Release 1.0)傳遞到翻譯的檔案。

**強制同步資產不同步**

如果您在某些資產中進行變更，AEM參考線會將其標示為不同步。 您可以重新轉譯已修改的資產，或選擇關閉「不同步」狀態。 例如，如果您做了一些非常不需要翻譯的小更改，則可以將其狀態標籤為「同步」。

<img src="assets/translation-version-diff.png" alt="翻譯板" width="600">

**查看主題或地圖的正在進行翻譯項目**

您的翻譯控制面板上的某些參考可能正在進行中。 現在「AEM指南」提供一項功能，可協助您檢視包含所選參考的所有進行中翻譯專案（連同目標語言）的清單。


### 從Web編輯器生成各種格式的輸出

現在，您可以從Web編輯器輕鬆產生主題或DITA映射的輸出。 您可以設定各種輸出預設集，例如AEM Site、PDF、HTML5、JSON（無頭輸出格式）和自訂輸出。 然後，您可以使用這些來產生個別輸出。

您可以在DITA主題中定義屬性，然後使用條件預設集在發佈輸出時套用條件。 您也可以使用基線發佈功能，選擇性地發佈特定版本的DITA映射或主題。


### 在地圖層級尋找並取代文字

AEM指南可讓您在地圖中搜尋包含特定文字的檔案。 在檔案中會反白顯示搜尋的文字。 現在，您也可以在所有檔案中將搜索到的單詞或短語替換為另一個單詞或短語。 您可以選取 **全部替換** 圖示取代所有檔案中所有出現的搜尋詞。

<img src="assets/map-find-replace.png" alt="地圖查找替換" width="600">

### 從儲存庫面板刪除和複製檔案

現在，您可以輕鬆從 **選項** 儲存庫面板中選定檔案的菜單。 依預設，檔案會以尾碼建立(如 `filename_1.extension`)。

<img src="assets/options-menu-repo-view-file-level.png" alt="檔案選項菜單 " width="500">


### 其他網頁編輯器增強功能

* 在AEM指南中，您可以使用內容功能表對影像和媒體檔案執行一些常見操作。 現在，您也可以在存放庫中找到選取的影像或媒體，或在資產UI中檢視檔案的預覽。

* 當前「資料夾配置檔案」的名稱將作為主工具欄中「用戶首選項」表徵圖的標籤顯示。 這可協助您識別目前使用的資料夾設定檔。

* 在地圖檢視中開啟地圖時，目前地圖的標題會顯示在主工具列的中央。 這有助於讓使用者知道目前開啟的地圖。


### 在Oxo編輯器中檢視標題，取代UUID

現在，AEM指南可讓您選擇 **在編輯器和地圖管理器中使用標題** 選項。 如果選擇此選項，則在編輯器或DITA映射管理器中開啟時，檔案的標題將顯示在檔案的頁簽上。 如果未選取此選項，則檔案的UUID會顯示在檔案的索引標籤上。

### AEM指南的微服務發佈as a Cloud Service

新的發佈微服務可讓您在AEM指南as a Cloud Service上同時執行大型發佈工作負載，並運用業界領先的Adobe I/O Runtime無伺服器平台。

對於每個發佈請求，AEM指南會as a Cloud Service執行個別的容器，該容器會根據使用者請求水準縮放。 這可讓您執行多個發佈請求，並獲得改善的效能。

如需詳細資訊，請參閱 [為AEM參考線設定全新的Microservice發佈as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-guides-learn/tutorials/knowledge-base/publishing/configure-microservices.md).

### 原生PDF |在PDF輸出中新增自訂書籤

現在，您可以在最終PDF輸出中的特定內容上新增自訂書籤，以方便導覽。 這會新增至TOC，此TOC是從DITA映射中的主題或區段標題建立。

### 原生PDF |對目錄項目和主題內容套用自訂樣式

AEM指南提供可在目錄項目或PDF輸出中的特定主題上套用自訂樣式的功能。 例如，您可以變更目錄和主題標題中文字的顏色。 您也可以對主題內的整個內容套用樣式。


### 原生PDF |在腳注元件中設定頁面標籤的樣式

現在，您可以在腳注中設定頁面標籤樣式。 例如，您可以新增括弧或變更其顏色。 這些樣式可幫助用戶輕鬆識別文檔中的頁面標籤。

### 原生PDF |更改欄，以指示目錄中更改的主題

AEM指南現在可讓您快速識別PDF輸出目錄中已變更的主題。  它會在目錄中變更的主題左側顯示變更列。 您可以按一下目錄中的主題，並檢視詳細的變更。

<img src="assets/change-marker-toc.png" alt="在目錄中變更標籤 " width="500">

## 已修正的問題

以下列出各個區域中修正的錯誤：

### 製作

* Web編輯器html中的變更會導致 `<dl>` 和 `<dlentry>`. (11024)
* 有些屬性沒有視為條件屬性，且會造成問題。 (10895)
* 三個或更多嵌套層 `<indexterm>` 不會巢狀內嵌於原生PDF匯出中。 (10799)
* 內容會在從「作者」切換至「來源」檢視的任務內文中消失。 (10735)
* 審核評論在審核任務中錯放。 (10625)
* **還原** 或 **取消復原** 在某些檔案上無法正常運作。 (10373)
* 複製和貼上動作時不會保留自訂中繼資料。 (10367)
* 「XML編輯器」中的「撤消」選項將用戶帶到頁面頂部。 (10091)
* 複製和貼上資產後，節點屬性會遭到移除。 (10053)
* MIMEType會以硬式編碼撰寫，以建立和更新DITA資產。 (8979)
* 對於透過資產UI上傳的檔案，版本記錄中的版本建立者名稱為「fmdita-serviceuser」。 (8910)
* 雲端安裝AEM參考線時，無法複製和貼上內容片段。 (11315)
* 使用自訂結構載入內容時，瀏覽器（網頁編輯器）會凍結。 (11211)

### 管理

* 複製DITA對應資產（從資產UI）會造成複製的資產中出現錯誤的基線。 (11218)
* 大於AEM允許限制（預設為2 GB）的檔案上傳時不會顯示警告訊息。 (10817)
* Web編輯器基線 |在Web編輯器的新基線控制面板中，「最新」欄的行為不同。 (10808)
* 翻譯 |由於/libs/fmdita/i18n/ja.json無效，翻譯工作未開始。 (10543)
* 翻譯 |從翻譯控制面板（人工翻譯）建立的範圍翻譯專案中發生錯誤。 (10526)
* 翻譯 |如果活動翻譯專案中有資產，則會封鎖整個語言資料夾的後續處理作業。 (10332)
* 如果版本已變更，並儲存在基線編輯器上，則任何資產都會出現多個快顯視窗。 (10399)
* 工作階段洩漏發生在 `com.day.cq.search.impl.builder.QueryBuilderImpl.createResourceResolver(QueryBuilderImpl.java:210)`. (10279)

### 發佈

* 某些案例無法重新產生主題。 (10635)
* Publishlistener不會在資訊記錄中顯示請求的資料，它也包含一些無用日誌。( 10567)
* 原生PDF |使用「新增至資料夾描述檔」選項建立輸出預設集時，PDF產生會因Null指標例外狀況而失敗。 (10950)
* 原生PDF |旋轉表格標題時發生問題。 (10555)
* 原生PDF |嵌套 `<indexterm>` 不會巢狀內嵌於原生PDF匯出中。 (10521)
* 原生PDF |附錄中的嵌套topicref全部轉換為臨時HTML中的h1。 (10454)
* 使用FrameMaker Publishing Server 2020產生的PDF無法發佈基線。 (10551)
* 原生PDF |添加 `xref` 影像不會在產生的PDF上轉譯影像。 (11346)
* 原生PDF |影像標籤將display-inline屬性添加到所有影像。 (10653)
* 原生PDF |預設情況下，草稿注釋會隱藏在生成的輸出中。 (10560)
* 原生PDF | topichead不接受navtitle。 (10509)
