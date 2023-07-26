---
title: 發行說明 | Adobe Experience Manager Guides 4.3.0版的新增功能
description: 瞭解Adobe Experience Manager Guides 4.3.0版中的新功能和增強功能
source-git-commit: 7581085859785c5b8b597ecfeb7dbe58c7c9e2bc
workflow-type: tm+mt
source-wordcount: '2639'
ht-degree: 0%

---

# Adobe Experience Manager Guides 4.3.0版的新增功能（2023年7月）

本文介紹Adobe Experience Manager Guides 4.3.0版的新增和增強功能(以下稱為 *AEM指南*)。

如需有關升級指示、相容性矩陣，以及此版本中修正問題的詳細資訊，請參閱 [發行說明](./release-notes-4.3.md).


## 連線至資料來源並將資料插入您的主題

現在您可以使用AEM Guides中的現成聯結器快速連線到您的資料來源。 連線至資料來源可讓您的資訊與來源保持同步，且資料的任何更新都會自動反映在網站上，讓AEM Guides成為真正的內容中心。 此功能可協助您節省手動新增或複製資料的時間和精力。

AEM Guides可讓您的管理員為JIRA和SQL (MySQL、PostgreSQL、SQL Server、SQLite)資料庫設定現成的聯結器。 它們也可以藉由擴充預設介面來新增其他聯結器。
新增後，您可以在網頁編輯器的「資料來源」面板下檢視已設定的聯結器。

<img src="assets/data-sources.png" alt="面板中的資料來源清單" width="300">

建立內容片段，從連線的資料來源擷取資料。 然後，您可以將資料插入主題並進行編輯。 建立內容片段產生器後，您可以重複使用它來將資料插入任何主題。

現在您也可以從連線的資料來源建立主題。 主題可以包含各種格式的資料，例如表格、清單和段落。 它也可讓您為所有主題建立DITA map。 從資料來源提取時，您可以將中繼資料與主題建立關聯。

如需詳細資訊，請檢視 [使用來自您的資料來源的資料](../user-guide/web-editor-content-snippet.md).

## 將引文新增至您的內容

引文是新增至內容之資訊來源的參考。 引文可協助您建立信譽並防止剽竊。 引文可協助讀者找到來源並驗證文字中顯示的資訊。

在AEM Guides中，您可以新增引文或匯入引文，並將其套用至您的內容。 您可以從任何書籍、網站和分錄來源新增這些引文。

將您的引文插入主題後，您可以在網頁編輯器中預覽它們。 您也可以使用原生PDF來發佈引文內容。

![面板中列出的引文](assets/citation-panel.png){width="300" align="left"}


如需詳細資訊，請檢視 [新增和管理內容中的引文](../user-guide/web-editor-apply-citations.md).

## 發佈至內容片段

內容片段是AEM中的分散式內容片段。 它們是以內容模型為基礎的結構化內容。 內容片段是純內容，沒有設計或版面配置資訊。 它們可以獨立於AEM支援的管道之外進行編寫和管理。 內容片段的模組化和可重複使用性可帶來更大的彈性、一致性、效率，以及更簡單的管理。

現在，AEM Guides提供了將主題或主題內的元素發佈到內容片段的方法。 您可以在主題和內容片段模型之間建立JSON型對應。 使用此對應將主題內部分或全部元素中存在的內容發佈到內容片段。

充分運用AEM Guides和內容片段的強大功能，並在任何AEM網站中使用內容片段。 您也可以透過內容片段支援的API擷取詳細資料。

![發佈內容片段的選項](assets/content-fragment-publish.png){width="550" align="left"}


## 檢閱增強功能

AEM Guides現已提供改良的檢閱功能，其功能如下：

### 檢閱面板可顯示檢閱專案和作用中的檢閱任務

現在AEM Guides可讓您的評論更加順暢。 它提供網頁編輯器中的評論面板。 檢閱面板會顯示您所屬的檢閱專案中的所有檢閱專案和作用中檢閱任務。

身為作者，此功能可協助您輕鬆開啟稽核工作、檢視評論，並在集中式檢視中快速處理評論。
![](assets/active-review-task-comments.png){width="800" align="left"}
如需詳細資訊，請檢視 **檢閱** 內的功能說明 [左側面板](../user-guide/web-editor-features.md#id2051EA0M0HS) 區段。

### 搜尋稽核主題

進行檢閱是AEM Guides的重要功能。 它有助於稽核者稽核指派給他們的檔案。
現在，您可以在檢閱面板的主題檢視的搜尋列中，輸入標題或檔案路徑的部分文字，以搜尋主題。 您也可以選擇檢視所有主題或檢視含有註解的主題。 依預設，您可以檢視稽核任務中存在的所有主題。


![在評論主題面板中搜尋](assets/review-search-topic.png){width="800" align="left"}

如需詳細資訊，請檢視 [檢閱主題](../user-guide/review-topics.md).

## Guides擴充功能框架

在AEM Guides上建立自訂套件，以使用AEM Guides Extension Framework提供擴充功能。 這些套件對開發人員和顧問很有用，且可延伸至編輯器中的元件。 他們可以鎖定按鈕、對話方塊和下拉選單，並新增自訂JavaScript，以便與AEM Guides UI輕鬆互操作。



## 原生PDF增強功能

4.3.0版已完成下列原生PDF增強功能，讓AEM Guides成為更強大的產品：

### 支援語言變數

AEM Guides支援語言變數。 您可以使用語言變數來定義PDF輸出中現成可用標籤（例如「注意」、「警告」和「警告」或靜態文字）的本地化版本。
您可以將語言變數或當地語系化的標籤版本新增至PDF輸出和輸出範本中的適當區段。

#### PDF輸出中的語言變數

您可以使用語言變數來定義「注意」、「警告」等元素的本地化標籤。 您可以更新一或多種語言中這些變數的值，然後本地化值會自動在PDF輸出中選取。
例如，您可以在PDF輸出中以下列方式呈現標籤「註記」：

* 英文：備註
* 法文：雷馬克
* 德文：欣威文

#### 輸出範本中的語言變數

如果您想要以各種語言建立PDF輸出，則必須建立包含每種語言本地化文字的不同PDF範本。 現在有了語言變數功能，您只需要建立範本一次。 然後針對您需要當地語系化的任何靜態文字，您可以建立對應的語言變數，並在範本中使用這些變數。
您可以為較長的文字建立語言變數，例如整個句子或甚至段落。 您也可以套用樣式，並使用HTML標示來格式化這些語言變數。

如需詳細資訊，請檢視 [支援語言變數](../native-pdf/native-pdf-language-variables.md).

### 新增浮水印至草稿檔案的PDF輸出

現在，您可以在尚未核准的檔案的PDF輸出中新增浮水印。 如果您在「已核准」檔案狀態中產生檔案的PDF，此浮水印就不會出現。 例如，您可以為PDF輸出新增浮水印「草稿」 。

如需詳細資訊，請檢視 [在草稿檔案的PDF輸出中新增浮水印](../native-pdf/use-javascript-content-style.md#watermark-draft-document).

### 能夠在PDF配置中使用AEM中繼資料

中繼資料是內容的說明或定義。 此中繼資料會儲存在您的來源DITA map內容中。

現在在AEM Guides中，您也可以選取資產的中繼資料屬性，並將其新增至頁面版面。 然後AEM Guides會挑選資產的這些中繼資料屬性，並發佈在PDF輸出中。


![新增原生pdf的中繼資料](assets/native-pdf-metadata-asset.png){width="300" align="left"}

>[!NOTE]
>
> AEM Guides也支援DITA map的中繼資料屬性。

如需詳細資訊，請檢視 [新增欄位和中繼資料](../native-pdf/design-page-layout.md#add-fields-metadata).


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

### 從目前頁面開始任何章節

您可以設定從奇數或偶數頁開始章節的基本組態設定、目錄結構，以及定義目錄專案的導線格式。

現在您也可以從目前頁面開始章節。 如果您選擇這麼做，所有章節都會連續發佈，而不會出現任何分頁符號。 例如，如果章節結束於第15頁的中間，則下一個章節也會從第15頁本身開始。


### 可在產生原生HTML輸出時存取暫存PDF檔案

現在，AEM Guides可讓您下載在產生原生HTML輸出時建立的暫時PDF檔案。 在輸出預設集設定中，選取下載暫存檔的選項。  AEM Guides可讓您下載使用該預設集產生輸出時建立的暫存檔。

此功能可讓您透過存取臨時樣式和版面來更深入分析產生流程，並協助您根據需求修正或變更CSS樣式。

![原生pdf的進階設定對話方塊](assets/native-pdf-advanced-settings.png){width="800" align="left"}

如需詳細資訊，請檢視 [建立PDF輸出預設集](../web-editor/native-pdf-web-editor.md#create-output-preset).


### 重新設計CSS編輯器

現在，CSS編輯器經過重新設計，以更好的使用者體驗選取器和樣式屬性。

#### 增強新增樣式對話方塊

您現在可以使用自訂選取器來新增複雜樣式。 新的「選取器」欄位可協助您新增類別、標籤和虛擬類別組合以外的自訂選取器。 例如，您可以建立 `table a.link` 表格內所有超連結的樣式。

![在原生pdf範本中新增樣式](assets/add-styles-native-pdf.png){width="300" align="left"}

#### 自訂樣式的屬性

現在，AEM Guides將向您介紹樣式預覽區段下的全新屬性面板。 您可以從「屬性」面板更有效率且快速地編輯樣式的屬性。


## 在存放庫檢視中重新命名和移動檔案

現在您也可以從存放庫面板重新命名或移動檔案。 此功能很實用，並可協助您從「存放庫」面板輕鬆管理檔案。 您可以選取檔案，然後使用 **選項** 選單。 當您移動或重新命名檔案時，AEM Guides會顯示成功訊息。

![檔案的選項功能表](assets/rename-move-assets.png){width="550" align="left"}

如需檔案之「選項」功能表的詳細資訊，請檢視 **存放庫檢視** 中的功能說明 [左側面板](../user-guide/web-editor-features.md#id2051EA0M0HS) 區段。

## 網頁編輯器中的中斷連結報表

AEM Guides可讓您檢查技術檔案的整體完整性，以及從網頁編輯器產生報告。 現在在2023年6月版本，AEM Guides提供您檢視和修正中斷連結的功能。 此報表可協助您管理中斷的連結。 您可以輕鬆地檢視DITA map中存在的中斷連結並加以修正。
![中斷連結報告](assets/broken-link-report.png){width="800" align="left"}

修正連結後，該連結不會顯示在失效連結清單下。

如需詳細資訊，請參閱 [檢視並修正中斷的連結](../user-guide/reports-web-editor.md#report-broken-links).

## Schematron增強功能

### 使用報表陳述式來檢查Schematron中的規則

AEM Guides現在也支援包含Schematron的報告陳述式。 當測試陳述式評估為true時，報表陳述式會產生訊息。 例如，如果您希望簡短說明少於或等於150個字元，可以定義報表陳述式，以檢查簡短說明超過150個字元的主題。

如需詳細資訊，請檢視 [使用判斷提示和報表陳述式來檢查規則](../user-guide/support-schematron-file.md#schematron-assert-report).

### 使用規則運算式

您也可以使用Regex運算式定義具有matches()函式的規則，然後使用Schematron檔案執行驗證。

如需詳細資訊，請檢視 [使用規則運算式](../user-guide/support-schematron-file.md#schematron-assert-report).


### 定義抽象模式

AEM Guides也支援Schematron中的抽象模式。 您可以定義一般抽象模式並重複使用這些抽象模式。 抽象模式可以簡化您的Schematron結構，也有助於您管理和更新驗證邏輯。


如需詳細資訊，請檢視 [定義抽象模式](../user-guide/support-schematron-file.md#schematron-abstract-patterns).

## 支援翻譯中的XLIFF格式

AEM Guides也支援翻譯中的XML Localization Interchange File Format (XLIFF)格式。 現在您也可以選擇 **建立新的XLIFF翻譯專案** 將XML內容轉換為XLIFF格式。 AEM Guides支援XLIFF 1.2版。

使用此格式，您可以將內容匯出為業界標準XLIFF格式，然後將相同的格式提供給翻譯廠商。 如需詳細資訊，請檢視 [建立翻譯專案](../user-guide/translate-documents-web-editor.md#create-translation-project).

![翻譯專案型別](assets/translation-project-types.png){width="350" align="left"}


## 地圖集合增強功能

地圖集合可協助您組織多個地圖並批次發佈。 已對地圖集合進行許多新增強功能：

* 現在，您可以將原生PDF輸出預設集新增到地圖集合中，並使用它們來產生PDF輸出。
* 您可以檢視管理員建立的全域和資料夾設定檔預設集，並使用它們來產生PDF輸出。
* 現在，您不僅可以選取個別預設集，還可以一次為DITA map啟用所有資料夾設定檔預設集。
  ![編輯地圖集合](assets/edit-map-collection.png){width="800" align="left"}

如需詳細資訊，請檢視 [使用地圖集合產生輸出](../user-guide/generate-output-use-map-collection-output-generation.md).

## 大量發佈儀表板中的原生PDF支援


透過AEM Guides的大量啟用功能，您可以輕鬆快速地啟用從製作到發佈執行個體的內容。 在「大量啟動」對應中，您可以包含原生PDF輸出預設集、AEM網站、PDF、HTML5、自訂和JSON輸出。
如需詳細資訊，請檢視 [大量啟用已發佈內容](../user-guide/conf-bulk-activation.md).

## 改進的大量移動工具

現在，作為管理員，您可以使用改良的「大量移動工具」，將包含許多檔案的資料夾從一個位置移動到另一個位置。
您可以使用瀏覽檔案對話方塊來選取您要移動的來源資料夾。 您也可以瀏覽以選取要移動來源資料夾的目的地位置。 選取 ![資訊圖示](assets/info-icon.svg) {width="25" align="left"} 靠近欄位可檢視其相關詳細資訊。

如需詳細資訊，請檢視 [大量移動檔案](../user-guide/authoring-file-management.md#move-files-bulk).

## 已改進我的最愛面板

AEM Guides可協助您建立檔案和資料夾的收藏集或我的最愛清單，並輕鬆加以使用。 現在 **選項** 功能表也可在 **我的最愛** 面板。 您可以重新命名選取的集合，或將其從 **選項** 功能表。 您可以選取 **重新整理** 從存放庫取得新的檔案或資料夾清單的選項。 您也可以在Assets UI中檢視資料夾內容。

![我的最愛面板](assets/favorites-options.png){width="650" align="left"}

>[!NOTE]
>
> 您也可以使用重新整理清單 **重新整理** 圖示在頂端。

如需更多詳細資訊，請參閱 **選項** 我的最愛集合功能表，檢視 **我的最愛** 中的功能說明 [左側面板](../user-guide/web-editor-features.md#id2051EA0M0HS) 區段。

## 切換至系統主題

您現在也可以使用裝置主題。 使用 **使用者偏好設定**，您可以設定AEM Guides以根據裝置的主題自動在淺色和深色主題之間切換。

![使用者偏好設定](assets/device-theme-user-preferences.png){width="550" align="left"}

如需詳細資訊，請檢視 **使用者偏好設定** 中的功能說明 [主工具列](../user-guide/web-editor-features.md#id2051EA0G05Z) 區段。
