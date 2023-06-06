---
title: 發行說明 | Adobe Experience Manager Guidesas a Cloud Service，2023年2月發行
description: Adobe Experience Manager Guidesas a Cloud Service版2月版
source-git-commit: 4bb9ce2690a2e76a5b2a93b65db7dd452e15d295
workflow-type: tm+mt
source-wordcount: '1428'
ht-degree: 0%

---


# Adobe Experience Manager Guidesas a Cloud Service版2023年2月的新增功能

本文介紹2023年2月版Adobe Experience Manager Guides中的新功能和增強功能(以下稱為 *AEM指南as a Cloud Service*)。

如需有關升級指示、相容性矩陣，以及此版本中修正問題的詳細資訊，請參閱 [發行說明](release-notes-2023.2.0.md) 文章。


## 從網頁編輯器產生報表

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

## 針對稽核功能改版的UX

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



## 翻譯增強功能

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


## 從網頁編輯器產生多種格式的輸出

現在您可以從網頁編輯器輕鬆產生主題或DITA map的輸出。 您可以設定各種輸出預設集，例如AEM Site、PDF、HTML5、JSON （Headless輸出格式）和自訂輸出。 然後，您可以使用這些來產生個別輸出。

您可以在DITA主題中定義屬性，然後使用條件預設集在發佈輸出時套用條件。 您也可以使用基準線發佈功能，選擇性地發佈DITA map或主題的特定版本。


## 在地圖層級尋找和取代文字

AEM Guides可讓您在地圖中搜尋包含特定文字的檔案。 搜尋的文字會在檔案中反白顯示。 現在，您也可以在所有檔案中，將搜尋到的字詞或片語取代為其他字詞或片語。 您可以選取 **全部取代** 圖示取代所有檔案中搜尋字詞的所有出現位置。

<img src="assets/map-find-replace.png" alt="地圖尋找取代" width="600">

## 從存放庫面板刪除和複製檔案

現在，您可以輕鬆地從建立檔案的重複或復本 **選項** 儲存庫面板中選取檔案的功能表。 依預設，檔案會以字尾建立(例如 `filename_1.extension`)。

<img src="assets/options-menu-repo-view-file-level.png" alt="檔案選項功能表 " width="500">


## 其他Web Editor增強功能

* 在AEM Guides中，您可以使用快顯選單對影像和媒體檔案執行一些常見操作。 現在您也可以在存放庫中找出選取的影像或媒體，或在Assets UI中檢視檔案預覽。

* 目前資料夾描述檔的名稱會在主工具列中顯示為「使用者偏好設定」圖示的標籤。 這有助於您識別正在處理的資料夾設定檔。

* 在地圖檢視中開啟地圖時，目前地圖的標題會顯示在主工具列的中心。 這有助於讓使用者知道目前開啟的地圖。


## 在氧氣編輯器中檢視標題取代UUID

現在AEM Guides可讓您選擇 **在編輯器和地圖管理員中使用標題** 選項。 如果選取此選項，當在「編輯器」或「DITA地圖管理員」中開啟時，檔案的標題會顯示在檔案的標籤上。 如果您未選取此選項，則檔案的UUID會顯示在檔案的索引標籤上。

## AEM Guidesas a Cloud Service的微服務型發佈

新的發佈微服務可讓您在AEM Guidesas a Cloud Service上同時執行大量發佈工作負載，並利用業界領先的Adobe I/O Runtime無伺服器平台。

對於每個發佈請求，AEM Guidesas a Cloud Service會執行單獨的容器，它會根據使用者請求水平縮放。 這可讓您執行多個發佈請求，並獲得改進的效能。

如需詳細資訊，請參閱 [為AEM Guidesas a Cloud Service設定新的微服務型發佈](https://experienceleague.adobe.com/docs/experience-manager-guides-learn/tutorials/knowledge-base/publishing/configure-microservices.md).

## 原生PDF |在PDF輸出中新增自訂書籤

現在，您可以在最終PDF輸出中的特定內容上新增自訂書籤，以便輕鬆導覽。 這將會新增到從DITA map中的主題或區段標題建立的目錄。

## 原生PDF |在目錄專案和主題內容上套用自訂樣式

AEM Guides提供在目錄專案或PDF輸出中的特定主題上套用自訂樣式的功能。 例如，您可以變更目錄中的文字顏色和主題標題。 您也可以在主題內的整個內容上套用樣式。


## 原生PDF |在註腳元件中設定頁面標籤的樣式

現在，您可以在註腳中設定頁面標籤的樣式。 例如，您可以新增括弧或變更其顏色。 這些樣式可協助使用者輕鬆識別檔案中的頁面標籤。

## 原生PDF |變更列表示目錄中已變更的主題

AEM Guides現在可讓您快速識別PDF輸出目錄。  它會在目錄中已變更的主題左側顯示變更列。 您可以按一下目錄中的主題並檢視詳細變更。

<img src="assets/change-marker-toc.png" alt="在目錄中變更標籤 " width="500">

