---
title: 本地PDF |PDF輸出生成
description: 在《Adobe Experience Manager指南》as a Cloud Service生成PDF輸出
exl-id: ec3d59b7-1dda-4fd1-848e-21d8a36ff5e4
source-git-commit: 1b46f5e496e6c974abeba019a9d3174d5bc5315c
workflow-type: tm+mt
source-wordcount: '2170'
ht-degree: 0%

---

# 發佈PDF輸出

使用「AEM參考線」解決方案，您可以生成單個主題的PDF或整個映射檔案。 您可以使用以下三種方法之一以PDF格式發佈內容：

* **DITA-OT**

使用此方法可從映射儀表板生成映射的PDF輸出。 通過為在映射儀表板中開啟的映射建立輸出預設，可以在生成PDF之前設定發佈屬性。 要建立或編輯輸出預設， *瞭解輸出預設* 的 [指南AEMas a Cloud Service使用手冊](https://helpx.adobe.com/content/dam/help/en/xml-documentation-solution/cs-apr-22/XML-Documentation-for-Adobe-Experience-Manager_CS_User-Guide_EN.pdf)。

有關使用DITA-OT方法生成PDF的詳細資訊，請參見 [使用DITA-OT生成PDF](https://help.adobe.com/en_US/xml-documentation-for-adobe-experience-manager/index.html#t=DXML-master-map%2Fgenerate-output-pdf.html)。

* **FrameMaker發佈伺服器(FMPS)**

使用此方法不僅可從DITA內容生成PDF輸出，還可從儲存庫中提供的FrameMaker文檔(.book和.fmAEM)生成。 可通過配置輸出預設並使用FrameMaker發佈伺服器(FMPS)來建立PDF。 您可以設計和配置輸出的外觀以用於PDF和其它格式，並將其儲存在設定檔案(.sts)中。 然後，FMPS將使用此設定檔案為DITA映射或.book檔案生成輸出。 要建立或編輯輸出預設，請參閱  *瞭解輸出預設* 的 [指南AEMas a Cloud Service使用手冊](https://helpx.adobe.com/content/dam/help/en/xml-documentation-solution/cs-apr-22/XML-Documentation-for-Adobe-Experience-Manager_CS_User-Guide_EN.pdf)。

有關配置FMPS的詳細資訊，請參見 [從FrameMaker文檔生成輸出](https://help.adobe.com/en_US/xml-documentation-for-adobe-experience-manager/index.html#t=DXML-master-map%2Ffm-output-generatation.html)。

* **本地PDF發佈**

使用此方法可基於W3C CSS3和CSS分頁媒體標準生成功能豐富的PDF輸出。 通過本機PDF發佈，您可以使用模板來設定內容的佈局和樣式，並應用各種設定來微調PDF。 此外，您還可以使用模板編輯器修改和建立自己的模板。

有關本機PDF發佈的詳細資訊，請參見 [使用本機PDF發佈](#native-pdf-publishing)。


## 使用本機PDF發佈 {#native-pdf-publishing}

在創作內容時，必須確保內容經過優化，以便查看、編輯和打印。 使用W3C CSS3等標準進行內容樣式設定，使用CSS頁面媒體標準進行頁面定義屬性（如大小、邊距、方向、分頁符、頁眉、頁腳和頁碼），您可以設定PDF文檔的視圖和佈局以確保一致性和可用性。 本地PDF發佈功能使用這些標準生成PDF。

通過本機PDF發佈，您可以使用預定義模板來確保內容佈局和結構的一致性、應用樣式表來改變輸出的外觀、優化PDF、設定打印機標籤、允許螢幕閱讀器支援、設定PDF一致性、嵌入字型等。

使用本地PDF發佈生成PDF有兩個方面：

* 使用模板將樣式應用於內容、設定頁面佈局和各種設定來微調PDF。 作者可以選擇使用/修改提供的示例模板，或建立自定義模板，並設定發佈者和開發人員使用的高級配置選項。

* 建立或配置PDF輸出預設以控制PDF設定。 建立PDF輸出預設後，可以生成PDF。

有關詳細資訊，請參見 [生成PDF輸出](#generate-pdf-output)。

## 建立PDF輸出預設 {#create-output-preset}

生成PDF輸出的第一步是建立PDF輸出預設，該預設是分配給映射的發佈屬性的集合。 您可以為「映射視圖」面板中開啟的任何映射建立輸出預設，或配置現有預設以快速生成同一映射的PDF。

從PDF輸出預設中，您可以選擇模板、應用條件、設定限制以控制用戶如何與PDF交互，配置高級設定，如壓縮、一致性等。

要建立或配置PDF輸出預設：

1. 在「輸出」(Output)頁籤中，按一下 **預設** 的下界。
「預設」面板開啟。
   ![預設面板](assets/preset-panel.png)
2. 在輸出中 **預設** 面板，執行下列操作之一：
   * 按兩下預定義的PDF輸出預設以查看它。
   * 按一下+表徵圖 **預設** 添加新輸出預設值 **類型：PDF**
3. 配置現有PDF預設的設定：
   * 按一下  **選項** ![選項](assets/options.svg) 表徵圖，位於所需輸出「預設」旁並選擇 **編輯**。
可以在 **常規**。 **佈局**。 **安全**, **高級** 頁籤以配置PDF輸出預設：

**一般**

用於指定基本輸出設定，如指定輸出路徑、PDF檔案名等。

| 設定 | 說明 |
| --- | --- |
| **輸出路徑** | 儲存PDF輸AEM出的儲存庫中的路徑。 確保輸出路徑不在項目資料夾內。 如果為空，則在預設DITA映射輸出位置生成輸出。 |
| **PDF 檔案** | 指定檔案名以保存PDF。 預設情況下，PDF檔案名會添加DITA映射名稱以及預設名稱。 例如，ditamap是「TestMap」，預設的名稱是「preset1」，則pdf的預設名稱將是「TestMap_preset1.pdf」。 |
| **使用** | 對於條件化內容，請從以下選項中選擇以根據這些條件生成PDF輸出： <br>* **未應用** 如果不想對映射和源內容應用任何條件，請選擇此選項。 <br> * **迪塔瓦爾檔案** 選擇DITAVAL檔案以生成條件化內容。 要選擇，請按一下「條件預設」並查找檔案。 <br> * **條件預設** 從下拉清單中選擇條件預設，以便在發佈輸出時應用條件。 如果已為DITA映射檔案添加了條件，則此選項可見。 條件設定在DITA映射控制台的「條件預設」頁籤中可用。 要瞭解有關條件預設的詳細資訊，請參閱 [使用條件預設](https://help.adobe.com/en_US/xml-documentation-for-adobe-experience-manager/index.html#t=DXML-master-map%2Fgenerate-output-use-condition-presets.html)。 <br> |
| **使用基線** | 如果已為所選DITA映射建立基線，請選擇此選項以指定要發佈的版本。 請參閱 [使用基線](https://help.adobe.com/en_US/xml-documentation-for-adobe-experience-manager/index.html#t=DXML-master-map%2Fgenerate-output-use-baseline-for-publishing.html) 的子菜單。 |

**配置**

用於設定頁面佈局並指定PDF輸出的頁面視圖選項，如「頁面顯示」和設定「縮放」級別。

| 設定 | 說明 |
| --- | --- |
| **PDF模板** | PDF模板為定義頁面佈局、內容樣式和將各種設定應用到PDF輸出提供了清晰的結構。 從PDF模板下拉選項中選擇，以選擇首選模板。 |
| **頁面顯示** | 使用「頁面顯示」(Page Display)查看頁面視圖，該視圖顯示PDF開啟時的顯示方式。 從「頁面顯示」下拉選項中選擇以選擇首選視圖。 <br>* **預設**  按用戶電腦上PDF查看器的預設設定顯示。  <br> * **單頁視圖** 一次顯示一頁。   <br> * **單頁滾動** 在連續垂直列中顯示單頁。  <br> * **雙頁視圖** 同時顯示兩頁跨頁。。<br> * **兩頁滾動** 以連續滾動方式並排顯示兩頁跨頁。 |
| **縮放** | 選擇以調整顯示開啟PDF時顯示方式的頁面視圖的大小。  <br>* **預設** 按用戶電腦上PDF查看器的預設設定顯示    <br> * **100%** 使頁面以實際大小顯示。     <br> * **調整頁** 使頁面寬度和高度適合文檔窗格。。<br> * **調整頁寬** 使頁面寬度填充文檔窗格的寬度。  <br> * **調整頁面高度** 使頁面的高度填充文檔窗格的高度。 |

**安全性**

Protect您的PDF，添加限制以開啟和讀取檔案。 使用以下選項來避免未經授權的訪問。

| 設定 | 說明 |
| --- | --- |
| **設定密碼以開啟文檔** | 選擇以添加安全密碼以查看您的PDF檔案。 在 **用戶密碼** 的子菜單。 用戶只能通過輸入此欄位中提供的密碼來開啟PDF。 |
| **設定文檔限制** | 選擇以限制用戶與PDF交互的方式。 在 **所有者密碼** 欄位，以便使用以下限制設定。  <br>* **打印** 選擇以允許用戶打印PDF。 <br> * **草稿質量打印** 選擇以允許用戶以較低解析度打印PDF。  <br> * **內容複製** 選擇以允許用戶從PDF複製內容。   <br> * **注釋** 選擇以允許用戶在PDF中添加註釋或注釋。  <br> * **內容修改** 選擇以允許用戶更改PDF中的內容。  <br> * **內容複製以用於輔助功能** 選擇以允許螢幕閱讀器閱讀和導航PDF中的內容。  <br> * **文檔程式集** 選擇以允許用戶在PDF中插入頁面。  <br> **注釋**:用戶需要輸入所有者密碼才能更改Adobe Acrobat的「檔案」>「屬性」中的任何限制。 |

**進階**

使用以下選項指定高級設定以合併PDF、使用壓縮、選擇符合性標準等。

| 設定 | 說明 |
| --- | --- |
| **建立可訪問（標籤）PDF** | 選擇此選項可生成帶標籤的PDF。 帶標籤的PDF使螢幕閱讀器更容易閱讀和導航內容、超連結、書籤等。 例如，如果表被標籤，螢幕閱讀器將知道它正在讀取表，而不只是線條和文本。 |
| **合併目錄中包含的PDF** | 選擇此選項可通過將現有PDF添加到目錄中，將其合併到輸出中。 PDF將插入目錄中所示的位置，頁面將相應遞增。 |
| **嵌入使用的字型** | 當使用可能未安裝在最終用戶電腦上的字型時，選擇此選項。 選擇此選項後，使用的字型將嵌入到PDF中，確保即使在其電腦上未安裝字型，用戶也能按預期看到PDF。 <br> **注釋**:只有當字型包含允許嵌入的字型供應商的設定時，才能嵌入字型。 在嵌入字型之前，請確保您具有所需的設定或許可證。 |
| **使用自動連字** | 啟用自動連字後，行末的單詞將以語法正確的位置用連字元斷開。 |
| **啟用JavaScript** | 如果在生成PDF之前要使用JavaScript代碼動態轉換內容，請啟用此選項。 |
| **嵌入多媒體檔案** | 選擇此選項可將任何音頻、視頻和任何交互內容包括到PDF。 |
| **使用完全PDF優化壓縮大小** | 如果要壓縮/減小大型PDF的大小，請選擇此選項。 請記住，壓縮PDF可能會降低檔案質量。 |
| **使用影像壓縮優化PDF大小** | 如果要壓縮/縮小PDF中使用的影像大小，請選擇此選項。 請記住，壓縮影像可能會降低影像質量。 |
| **使用自定義解析度（像素/英吋）** | 它是以像素/英吋為單位的頁面顯示解析度。 在選中此選項時顯示的欄位中輸入首選值。 預設值為96像素/英吋。 設定一個較高的值，以便在一英吋內容納更多內容，反之亦然，如果設定了較低的值。 |
| **顯示水印** | 選擇此選項可呈現內容中存在的MathML公式。 否則將忽略方程。 |
| **啟用MathML方程** | 選擇此選項可呈現內容中存在的MathML公式。 否則，預設情況下將忽略公式。 |
| **PDF一致性** | 這是您要保存PDF以確保符合標準的標準。 從下拉清單中選擇，從可用PDF標準清單中進行選擇。 有關支援標準的詳細資訊，請參見 [關於PDF標準](https://helpx.adobe.com/acrobat/using/pdf-conversion-settings.html#about_pdf_x_pdf_e_and_pdf_a_standards)。 |

## 生成PDF輸出 {#generate-pdf-output}

配置輸出預設後，可以使用 **生成預設** 的子菜單。

1. 在 **作者** 頁籤 **儲存庫** 。\
   這將開啟「儲存庫」面板。

2. 在「儲存庫」面板中，在 **映射視圖**。

3. 在 **輸出** 按鈕 **預設** 按鈕。
要建立或配置輸出預設，請參見 [建立PDF輸出預設](#create-output-preset)。
4. 要保存設定，請按一下 **全部保存** ![全部保存](assets/SaveFloppy_icon.svg) 表徵圖。
5. 按一下 **生成預設** ![生成預設](assets/generate-output.svg) 按鈕。
可以在「輸出預設」面板中查看選定輸出預設旁邊的進度條。
6. 輸出生成完成後，按一下  **查看輸出** ![查看輸出](assets/view-output.svg) 表徵圖。\
   A **成功** 對話框。
如果輸出不成功，則顯示以下錯誤消息。
   ![錯誤日誌](assets/error-log.png)

要查看錯誤日誌，請按一下 **消除**，懸停在選定的預設頁籤上，然後按一下 ![選項](assets/options.svg) **選項** > **查看日誌**。
