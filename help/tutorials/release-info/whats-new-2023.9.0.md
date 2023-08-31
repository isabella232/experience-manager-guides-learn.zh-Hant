---
title: 發行說明 | Adobe Experience Manager Guides的新增功能（2023年9月發行）
description: 在2023年9月發行的Adobe Experience Manager Guidesas a Cloud Service中瞭解新功能和增強功能
source-git-commit: 9d59fbbc88c3effe0b1c8438d9f3af55ffb8da27
workflow-type: tm+mt
source-wordcount: '1678'
ht-degree: 0%

---

# 2023年9月版Adobe Experience Manager Guides的as a Cloud Service新增功能

本文介紹2023年9月版Adobe Experience Manager Guides中的新功能和增強功能(以下稱為 *AEM Guidesas a Cloud Service*)。

如需有關升級指示、相容性矩陣，以及此版本中修正問題的詳細資訊，請參閱 [發行說明](release-notes-2023.9.0.md).

## 連線至資料來源並插入主題

AEM Guides提供現成的聯結器，可協助您連線資料來源，讓AEM Guides成為真正的內容中樞。 這可讓您節省原本用於手動新增或複製資料的時間和精力。

除了現有的現成可用聯結器(例如JIRA和SQL (MySQL、PostgreSQL、SQL Server、SQLite)，您的管理員還可以為MariaDB、H2DB、AdobeCommerce和Elasticsearch資料庫設定聯結器。 它們也可以藉由擴充預設介面來新增其他聯結器。

您可以在「 」下方檢視已設定的聯結器 **資料來源** 網頁編輯器中的面板。

<img src="assets/data-sources.png" alt="面板中的資料來源清單" width="300">

*檢視連線的資料來源。*

您現在也可以從連線的資料來源建立主題。 主題可以包含各種格式的資料，例如表格、清單和段落。 它也可讓您為所有主題建立DITA map。 從資料來源提取時，您可以將中繼資料與主題建立關聯。

如需詳細資訊，請檢視 [使用來自您的資料來源的資料](../user-guide/web-editor-content-snippet.md).

## 將引文新增至您的內容

引文是新增至內容之資訊來源的參考。 引文可協助您建立信譽並防止剽竊。 引文可協助讀者找到來源並驗證文字中顯示的資訊。

在AEM Guides中，您可以新增引文或匯入引文，並將其套用至您的內容。 您可以從任何書籍、網站和分錄來源新增這些引文。

將您的引文插入主題後，您可以在網頁編輯器中預覽它們。 您也可以使用原生PDF來發佈引文內容。

![面板中列出的引文](assets/citation-panel.png){width="300" align="left"}

*在「引文」面板中檢視引文清單。*

如需詳細資訊，請檢視 [新增和管理內容中的引文](../user-guide/web-editor-apply-citations.md).


## 發佈至內容片段

內容片段是AEM中的分散式內容片段。 它們是以內容模型為基礎的結構化內容。 內容片段是純內容，沒有設計或版面配置資訊。 它們可以獨立於AEM支援的管道之外進行編寫和管理。 內容片段的模組化和可重複使用性可帶來更大的彈性、一致性、效率，以及更簡單的管理。

現在，AEM Guides提供了將主題或主題內的元素發佈到內容片段的方法。 您可以在主題和內容片段模型之間建立JSON型對應。 使用此對應將主題內部分或全部元素中存在的內容發佈到內容片段。

充分運用AEM Guides和內容片段的強大功能，並在任何AEM網站中使用內容片段。 您也可以透過內容片段支援的API擷取詳細資料。

![發佈內容片段的選項](assets/content-fragment-publish.png){width="550" align="left"}

*發佈主題至內容片段。*

如需詳細資訊，請檢視 [發佈至內容片段](../user-guide//publish-content-fragment.md).

## 檢閱增強功能

AEM Guides現已提供改良的檢閱功能，其功能如下：

### 搜尋稽核主題

進行檢閱是AEM Guides的重要功能。 它有助於稽核者稽核指派給他們的檔案。
現在，您可以在檢閱面板的主題檢視的搜尋列中，輸入標題或檔案路徑的部分文字，以搜尋主題。 您也可以選擇檢視所有主題或檢視含有註解的主題。 依預設，您可以檢視稽核任務中存在的所有主題。 如需詳細資訊，請檢視 [檢閱主題](../user-guide/review-topics.md).

![在評論主題面板中搜尋](assets/review-search-topic.png){width="800" align="left"}

*在稽核面板中搜尋稽核主題。*



## Guides擴充功能框架

在AEM Guides上建立自訂套件，以使用AEM Guides Extension Framework提供擴充功能。 這些套件對開發人員和顧問很有用，且可延伸至編輯器中的元件。 他們可以鎖定按鈕、對話方塊和下拉選單，並新增自訂JavaScript，以便與AEM Guides UI輕鬆互操作。



## 原生PDF增強功能

下列原生PDF增強功能已在2023年9月版本中完成，讓AEM Guides成為更強大的產品：



### 在PDF輸出中排序頁面

您可以在PDF中顯示或隱藏以下區段，也可以排列它們在最終PDF輸出中的顯示順序：

* 目錄
* 章節與主題
* 圖表清單
* 表格清單
* 索引
* 字彙表
* 引用
* 頁面配置

如果不想在PDF輸出中顯示特定截面，可以關閉切換開關來隱藏它。

如需詳細資訊，請檢視 [頁面順序](../native-pdf/components-pdf-template.md#page-order).

### 合併頁面

依預設，在原生PDF輸出中，所有區段都會從新頁面開始。 現在，您可以將區段合併至其上一頁或下一頁。 這會以在PDF輸出中選取的頁面連續發佈區段，且中間沒有分頁符號。

如需詳細資訊，請檢視 **合併頁面** 中的功能說明 [頁面順序](../native-pdf/components-pdf-template.md#page-order) 區段。

### 從目前頁面開始任何章節

您可以設定從奇數或偶數頁開始章節的基本組態設定、目錄結構，以及定義目錄專案的導線格式。

現在您也可以從目前頁面開始章節。 如果您選擇這麼做，所有章節都會連續發佈，而不會出現任何分頁符號。 例如，如果章節結束於第15頁的中間，則下一個章節也會從第15頁本身開始。

如需詳細資訊，請檢視 **一般** 中的索引標籤說明  [進階PDF設定](../native-pdf/components-pdf-template.md#advanced-pdf-settings-advanced-pdf-settings).

### 靜態頁面

您也可以建立自訂頁面配置，並在PDF輸出中發佈為靜態頁面。 這可協助您新增任何靜態內容，例如備註或空白頁面。

如需詳細資訊，請檢視 **靜態頁面** 中的功能說明 [頁面順序](../native-pdf/components-pdf-template.md#page-order) 區段。


### 交叉引用中的變數

您可以使用變數來定義互動參照。 使用變數時，系統會從屬性中挑選變數值。

現在您也可以使用 {figure} 和 {table}.
使用 {figure}以新增圖形編號的互動參照。 它會從您為圖形定義的自動編號樣式中挑選圖形編號。

使用 {table} 以新增表格編號的互動參照。 它會從您為註解定義的自動編號樣式中挑選表格編號。

如需詳細資訊，請檢視 [交叉引用](../native-pdf/components-pdf-template.md##cross-references).



### 重新設計CSS編輯器

現在，CSS編輯器經過重新設計，以更好的使用者體驗選取器和樣式屬性。

#### 增強新增樣式對話方塊

您現在可以使用自訂選取器來新增複雜樣式。 新的「選取器」欄位可協助您新增類別、標籤和虛擬類別組合以外的自訂選取器。 例如，您可以建立 `table a.link` 表格內所有超連結的樣式。

![在原生pdf範本中新增樣式](assets/add-styles-native-pdf.png){width="300" align="left"}

*新增新樣式的詳細資訊。*

#### 自訂樣式的屬性

現在，AEM Guides將向您介紹樣式預覽區段下的全新屬性面板。 您可以從「屬性」面板更有效率且快速地編輯樣式的屬性。


## 支援單一分項清單定義中的多個主旨定義

您現在可以在一個對應中定義一或多個主旨定義，並在另一個對應中定義列舉定義，然後新增對應參照。 主旨 — 列舉參照是在相同對應或參照的對應中進行解析。

您現在也可以定義條件，並將其套用至主題中的某些特定元素。  條件僅對這些特定元素可見，而不會對所有其他元素可見。

如需處理主旨定義與分項清單之階層定義的詳細資訊，請檢視 [左側面板](../user-guide/web-editor-features.md#id2051EA0M0HS) 區段。





## 選取地圖集合中的所有預設集

您不僅可以啟用個別預設集和所有資料夾設定檔預設集，也可以一次啟用DITA map的所有預設集。
![編輯地圖集合](assets/edit-map-collection-cs.png){width="800" align="left"}\
*選取地圖集合中的所有預設集。*

如需詳細資訊，請檢視 [使用地圖集合產生輸出](../user-guide/generate-output-use-map-collection-output-generation.md).


## 大量發佈儀表板中的原生PDF支援


透過AEM Guides的大量啟用功能，您可以輕鬆快速地啟用從製作到發佈執行個體的內容。 在「大量啟動」對應中，您可以包含原生PDF輸出預設集、AEM網站、PDF、HTML5、自訂和JSON輸出。
如需詳細資訊，請檢視 [大量啟用已發佈內容](../user-guide/conf-bulk-activation.md).

## 改進的大量移動工具

現在，作為管理員，您可以使用改良的「大量移動工具」，將包含許多檔案的資料夾從一個位置移動到另一個位置。
您可以使用瀏覽檔案對話方塊來選取您要移動的來源資料夾。 您也可以瀏覽以選取要移動來源資料夾的目的地位置。 選取 ![資訊圖示](assets/info-icon.svg) {width="25" align="left"} 靠近欄位可檢視其相關詳細資訊。

如需詳細資訊，請檢視 [大量移動檔案](../user-guide/authoring-file-management.md#move-files-bulk).


## 內容功能表的增強預覽體驗

使用快顯功能表快速預覽檔案（.dita、.xml、音訊、視訊或影像），而不需開啟它。 您現在可以調整預覽窗格的大小，如果內容包含任何參考連結，您可以選取它，以在新標籤中開啟它。

![預覽窗格 ](assets/quick-preview_cs.png){width="800" align="left"}

*在窗格中預覽檔案。*

如需內容功能表的詳細資訊，請參閱 **檔案的選項** 中的功能說明 [左側面板](../user-guide/web-editor-features.md#id2051EA0M0HS) 區段。


## 在「目的地路徑」、「網站名稱」或「檔案名稱」選項中，使用目前日期和時間的變數

在AEM網站或PDF中產生輸出時，您可以使用變數來設定 **目的地路徑**， **網站名稱**，或 **檔案名稱** 選項。 您現在也可以使用 `${system_date}`和 `${system_time}` 變數。 這些變數可協助您將目前日期和時間附加至這些選項。

瞭解如何 [使用變數來設定目的地路徑、網站名稱或檔案名稱選項](../user-guide/generate-output-use-variables.md).
