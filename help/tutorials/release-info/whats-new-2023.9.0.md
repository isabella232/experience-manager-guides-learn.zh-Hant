---
title: 發行說明 | Adobe Experience Manager Guides的新增功能（2023年9月發行）
description: 在2023年9月發行的Adobe Experience Manager Guidesas a Cloud Service中瞭解新功能和增強功能
source-git-commit: c01c3500b55f3579633ad1a954f9010783365add
workflow-type: tm+mt
source-wordcount: '1361'
ht-degree: 0%

---

# 2023年9月版Adobe Experience Manager Guides的as a Cloud Service新增功能

本文介紹2023年9月版Adobe Experience Manager Guides中的新功能和增強功能(以下稱為 *AEM Guidesas a Cloud Service*)。

如需有關升級指示、相容性矩陣，以及此版本中修正問題的詳細資訊，請參閱 [發行說明](release-notes-2023.7.0.md).

## 連線至資料來源並將資料插入您的主題

現在您可以使用AEM Guides中的現成聯結器快速連線到您的資料來源。 連線至資料來源可讓您的資訊與來源保持同步，且資料的任何更新都會自動反映在網站上，讓AEM Guides成為真正的內容中心。 此功能可協助您節省手動新增或複製資料的時間和精力。

AEM Guides可讓您的管理員為JIRA和SQL (MySQL、PostgreSQL、SQL Server、SQLite)資料庫設定現成的聯結器。 它們也可以藉由擴充預設介面來新增其他聯結器。
新增後，您可以在網頁編輯器的「資料來源」面板下檢視已設定的聯結器。

<img src="assets/data-sources.png" alt="面板中的資料來源清單" width="300">

*檢視連線的資料來源。*

建立內容片段，從連線的資料來源擷取資料。 然後，您可以將資料插入主題並進行編輯。 建立內容片段產生器後，您可以重複使用它來將資料插入任何主題。

現在您也可以從連線的資料來源建立主題。 主題可以包含各種格式的資料，例如表格、清單和段落。 它也可讓您為所有主題建立DITA map。 從資料來源提取時，您可以將中繼資料與主題建立關聯。

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

4.3.0版已完成下列原生PDF增強功能，讓AEM Guides成為更強大的產品：



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

如需更多詳細資訊，請檢視下列檔案中的合併頁面功能說明： [頁面順序](../native-pdf/components-pdf-template.md#page-order) 區段。

### 靜態頁面

您也可以建立自訂頁面配置，並在PDF輸出中發佈為靜態頁面。 這可協助您新增任何靜態內容，例如備註或空白頁面。

如需詳細資訊，請檢視靜態頁面功能說明，位置在： [頁面順序](../native-pdf/components-pdf-template.md#page-order) 區段。


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

#### 自訂樣式的屬性

現在，AEM Guides將向您介紹樣式預覽區段下的全新屬性面板。 您可以從「屬性」面板更有效率且快速地編輯樣式的屬性。



## 選取地圖集合中的所有預設集

您不僅可以選取個別預設集，也可以一次啟用DITA map的所有預設集。
![編輯地圖集合](assets/edit-map-collection.png){width="800" align="left"}\
*選取地圖集合中的所有預設集。*

如需詳細資訊，請檢視 [使用地圖集合產生輸出](../user-guide/generate-output-use-map-collection-output-generation.md).


## 大量發佈儀表板中的原生PDF支援


透過AEM Guides的大量啟用功能，您可以輕鬆快速地啟用從製作到發佈執行個體的內容。 在「大量啟動」對應中，您可以包含原生PDF輸出預設集、AEM網站、PDF、HTML5、自訂和JSON輸出。
如需詳細資訊，請檢視 [大量啟用已發佈內容](../user-guide/conf-bulk-activation.md).

## 改進的大量移動工具

現在，作為管理員，您可以使用改良的「大量移動工具」，將包含許多檔案的資料夾從一個位置移動到另一個位置。
您可以使用瀏覽檔案對話方塊來選取您要移動的來源資料夾。 您也可以瀏覽以選取要移動來源資料夾的目的地位置。 選取 ![資訊圖示](assets/info-icon.svg) {width="25" align="left"} 靠近欄位可檢視其相關詳細資訊。

如需詳細資訊，請檢視 [大量移動檔案](../user-guide/authoring-file-management.md#move-files-bulk).


