---
title: 移轉非DITA內容
description: 瞭解如何移轉非DITA內容
source-git-commit: 5ac066bb8db32944abd046f64da11eeb1bdbe467
workflow-type: tm+mt
source-wordcount: '2792'
ht-degree: 0%

---


# 移轉非DITA內容 {#id181AH0R02HT}

本節將引導您完成移轉程式，將非DITA檔案移轉至DITA格式。 AEM Guides提供以下來源的移轉：

- [Microsoft Word](#id1949B040Z5Z)

- [InDesign檔案](#id195AD0B0K5Z)

- [XHTML](#id1949B04L0Y4)

- [非結構化FrameMaker檔案](#id1949B050VUI)

- [任何其他結構化檔案](#id1949B0590YK)


## 移轉Microsoft Word檔案 {#id1949B040Z5Z}

AEM Guides可讓您移轉現有的Word檔案\(`.docx`\)加入DITA主題型別檔案。 您需要指定輸入和輸出資料夾位置以及其他引數，檔案會轉換為DITA檔案。 視內容而定，您可以有.dita檔案和.ditamap檔案。

為了能夠成功轉換Word檔案，您的檔案應該結構良好。 例如，您的檔案應該有標題，然後是標題1、標題2，依此類推。 每個標題都應該有一些內容。 如果您的檔案結構不正確，該流程可能無法如預期運作。

根據預設，AEM Guides會使用 [Word對DITA \(Word2DITA\)轉換架構](http://www.dita4publishers.org/docs/repo/org.dita4publishers.word2dita/word2dita/word2dita-intro.html). 此轉換取決於 [樣式與標籤對應](http://www.dita4publishers.org/docs/repo/org.dita4publishers.word2dita/word2dita/style-to-tag-map-overview.html) 設定檔。 為了能夠成功使用Word2DITA轉換，您必須考慮以下準備Word檔案以進行轉換的准則：

>[!NOTE]
>
> 如果您在預設的樣式對標籤對應組態檔案中進行任何變更，則必須更新並使用確認已更新樣式對應的准則。

- 確定您的檔案以標題開頭；此標題已對應到DITA map標題。 此外，「標題」後面必須跟一些一般內容。

- 在標題之後，應該會有標題1、標題2等。 每個標題中都必須有一些內容。 標題會轉換為新的概念型別主題。 所產生主題的階層會根據檔案中的標題層級，例如，標題1會放在標題2之前，而標題2會放在標題3內容之前。

- 檔案必須至少有一個標題型別內容。

- 確定您沒有任何分組的影像。 如果您在檔案中已將影像分組，請取消所有此類影像的分組。

- 移除所有頁首和頁尾。

- 粗體、斜體和底線等內嵌樣式會轉換為 `b`， `i`、和 `u` 元素。

- 所有已排序和未排序清單都會轉換為 `ol` 和 `ul` 元素。 這也適用於巢狀清單、表格、附註或註腳內的清單。

- 所有超連結都會轉換為 `xref`.

- 轉換後檔案的檔案名稱是根據標題文字，後跟檔案編號。 檔案編號是根據檔案中標題文字位置的連續數字。 例如，如果標題文字是「範例標題」，而且是檔案中的第10個標題，則此主題的結果檔案名稱將類似於Sample\_Heading\_10.dita。


執行下列步驟，將現有的Word檔案轉換為DITA主題型別檔案：

1. 登入AEM並開啟CRXDE Lite模式。

1. 導覽至下列位置可用的預設組態檔：

   `/libs/fmdita/config/w2d_io.xml`

1. 建立「 」的覆蓋節點 `config` 內的資料夾 `apps` 節點。

1. 導覽至「 」中可用的設定檔 `apps` 節點：

   `/apps/fmdita/config/w2d_io.xml`

   此 `w2d_io.xml` 檔案包含下列可設定的引數：

   - 在 `inputDir` 元素，指定您的來源Word檔案可用的輸入資料夾位置。 例如，如果您的Word檔案儲存在名為的資料夾中 `wordtodita` 在 `projects` 資料夾，然後指定位置為： `/content/dam/projects/wordtodita/`

   - 在`outputDir` 元素，指定輸出資料夾的位置，或保留預設輸出位置以儲存轉換的DITA檔案。 如果DAM上不存在指定的輸出資料夾，則轉換工作流程會建立輸出資料夾。

   - 對於 `createRev` 元素，指定是否要建立新版本的轉換DITA主題\(`true`\)或不是\(`false`\)。

   - 在 `s2tMap` 元素，指定包含Word檔案樣式與DITA元素對應之對應檔案的位置。 預設對應會儲存在檔案中，檔案位於：

      ```XML
      /libs/fmdita/word2dita/word-builtin-styles-style2tagmap.xml
      ```

      >[!NOTE]
      >
      > 如需有關結構的詳細資訊， `word-builtin-styles-style2tagmap.xml` 檔案以及如何自訂，請參閱 [樣式至標籤對應](http://www.dita4publishers.org/docs/repo/org.dita4publishers.word2dita/word2dita/style-to-tag-map-overview.html) 在 *發佈者適用的DITA使用手冊*.

   - 在props2Propagate元素中，指定應傳遞至DITA map的屬性。 若要將預設中繼資料（例如dc：title、dc：subject、dam：keywords、dam：category）從檔案中繼資料傳遞至轉換的DITA資產，則需要此屬性。

1. 儲存 `w2d_io.xml` 檔案。

1. 在中設定必要的引數後 `w2d_io.xml` 檔案登入AEM並開啟Assets UI。

1. 導覽至輸入資料夾位置\(`wordtodita`\)。

1. 將來源Word檔案上傳至此資料夾。 如需在DAM上傳內容的詳細資訊，請參閱 [上傳現有DITA內容](migrate-content-upload-existing-dita-content.md#).


使用 `config` `/config` 區塊，您可以定義要轉換的一或多個設定區塊。 會執行轉換工作流程，並將最終輸出以DITA主題的形式儲存在中指定的位置 `outputDir` 元素。

## 移轉Adobe InDesign檔案 {#id195AD0B0K5Z}

AEM Guides可讓您轉換InDesign檔案。 與FrameMaker類似，InDesign也可讓您建立非結構化檔案。 非結構化檔案使用段落和字元樣式來格式化內容。 結構化檔案使用元素及其對應的屬性。

轉換程式需要將段落和字元樣式格式對應到相關的DITA元素。 同樣地，如果是結構化檔案，對應檔案將包含具有DITA元素和屬性的InDesign元素和屬性的一對一對應。

轉換程式涉及後端中的下列動作：

- 此 *InDesign標籤語言* \(IDML\)檔案會解壓縮至工作目錄。
- 會讀取designmap.xml檔案，以找出個別InDesign劇本。
- 所有劇本都會合併到單一XML例項中，「空白」劇本會被捨棄。
- 所有內嵌圖形都會匯出。
- 將標準結構（例如表格和圖形）預先轉換成DITA格式。
- 根據對應檔案將樣式或結構對應到最終輸出。
- 建立及驗證個別DITA主題與DITA map檔案。
- 刪除暫存檔。

一般而言，轉換程式要求您 [準備InDesign檔案以進行轉換](appendix.md#id195DBF0045Z) 和 [準備對應檔案以InDesign至DITA移轉](appendix.md#id194AF0003HT) 之後，您需要依照指定的程式執行轉換程式。

執行下列步驟，將現有InDesign檔案轉換為DITA主題型別檔案：

1. 登入AEM並開啟CRXDE Lite模式。

1. 導覽至下列位置可用的預設組態檔：

   `/libs/fmdita/config/idml2dita_io.xml`

1. 建立「 」的覆蓋節點 `config` 內的資料夾 `apps` 節點。

1. 導覽至「 」中可用的設定檔 `apps` 節點：

   `/apps/fmdita/config/idml2dita_io.xml`

   在「 」中設定以下引數 `idml2dita_io.xml` 檔案：

   - 在 `inputDir` 元素，指定您的來源InDesign檔案可用的輸入資料夾位置。 例如，如果您的InDesign檔案儲存在名為的資料夾中 `indesigntodita` 在 `projects` 資料夾，然後指定位置為： `/content/dam/idmlfiles/indesigntodita/`

   - 在`outputDir` 元素，指定輸出資料夾的位置，或保留預設輸出位置以儲存轉換的DITA檔案。 如果DAM上不存在指定的輸出資料夾，則轉換工作流程會建立輸出資料夾。

   - 在 `mapStyle` 元素，指定對應檔案的位置，該對應檔案包含InDesign檔案樣式至DITA元素的對應。 預設對應會儲存在檔案中，檔案位於：

      ```XML
      /stmap.adobeidml.xml
      ```

      >[!NOTE]
      >
      > 如需有關結構的詳細資訊， `stmap.adobeidml.xml` 檔案以及如何自訂，請參閱 [準備對應檔案以InDesign至DITA移轉](appendix.md#id194AF0003HT) 中的區段 *附錄*.

1. 儲存 `idml2dita_io.xml` 檔案。

1. 在中設定必要的引數後 `idml2dita_io.xml` 檔案登入AEM並開啟Assets UI。

1. 導覽至輸入資料夾位置\(`indesigntodita`\)。

1. 將來源InDesign檔案上傳至此資料夾。 如需在DAM上傳內容的詳細資訊，請參閱 [上傳現有DITA內容](migrate-content-upload-existing-dita-content.md#).


## 移轉XHTML檔案 {#id1949B04L0Y4}

AEM Guides可讓您將現有的XHTML檔案轉換為DITA主題型別檔案。 您需要指定輸入和輸出資料夾位置以及其他引數，檔案會轉換為DITA格式。 有兩種方法可用來轉換結構化HTML檔案：

- 將所有檔案上傳至輸入資料夾，或
- 建立包含所有檔案及媒體檔案的ZIP，並將其上傳至輸入資料夾。 這種方法通常用於一組相互連結的HTML檔案，並且有一個目錄\(index.html\)。 index.html檔案包含集合中所有HTML檔案的連結。

無論您是個別上傳所有檔案，還是以ZIP格式組合上傳所有檔案，轉換程式都會在HTML檔案與產生的DITA檔案之間建立一對一的對應。 這基本上表示在輸入資料夾中會為每個.html檔案建立一個.dita檔案。

在ZIP檔案中上傳檔案時，必須考量下列幾點：

- 所有參考的主題都應放在ZIP檔案中。

- 所有參照的媒體檔案都應在主題檔案中使用相對連結參照。

- 建立index.html檔案，並將連結新增至您要在目錄中新增的主題。 此index.html檔案用於建立DITA map檔案。 在index.html檔案中，您也可以建立巢狀主題清單，如下列程式碼範例所示：

   ```XML
   <?xml version="1.0" encoding="UTF-8"?>
   <html
   xmlns="http://www.w3.org/1999/xhtml">
       <head>
           <title>Sample Index File</title>
       </head>
       <body>
           <h1>Sample Index</h1>
           <div class="content">
               <ul class="book">
                   <li class="topicref">
                       <a href="Topic1.html">Topic 1</a>
                       <ul class="book">
                           <li class="topicref">
                               <a href="Topic1-1.html">Topic 1.1</a>
                           </li>
                           <li class="topicref">
                               <a href="Topic1-2.html">Topic 1.2</a>
                           </li>
                       </ul>
                   </li>
                   <li class="topicref">
                       <a href="Topic2.html">Topic 2</a>
                   </li>
               </ul>
           </div>
       </body>
   </html>
   ```

   請注意，每隔 `ul` 標籤必須具有 `class` 屬性設定為 `book`. 同樣地，每 `li` 標籤的 `class` 必須設定為 `topicref`.

- 如果您使用內嵌樣式，請在XHTML檔案中將內嵌樣式轉換為CSS型樣式類別。 然後使用樣式屬性對映將這些基於類別的樣式轉換為DITA `outputclass` 屬性轉換後的DITA檔案。

   從這些DITA檔案產生HTML或AEM網站輸出時， `outputclass` 屬性可用於在產生的HTML或AEM網站上套用樣式類別，以符合您的來源HTML內容。


除了建立ZIP檔案的考量外，您的XHTML檔案也必須結構良好。 例如，您的檔案應具有 *標題*，後接 *標題1*， *標題2*、等等。 每個標題都應該有一些內容。 如果您的檔案結構不正確，移轉程式可能無法如預期運作。

若要將現有的XHTML檔案轉換為DITA主題，請執行下列步驟：

1. 登入AEM並開啟CRXDE Lite模式。

1. 導覽至下列位置可用的預設組態檔：

   `/libs/fmdita/config/h2d_io.xml`

1. 建立「 」的覆蓋節點 `config` 內的資料夾 `apps` 節點。

1. 導覽至「 」中可用的設定檔 `apps` 節點：

   `/apps/fmdita/config/h2d_io.xml`

   此 `h2d_io.xml` 檔案包含下列可設定的引數：

   - 在 `inputDir` 元素，指定可使用來源XHTML檔案的輸入資料夾位置。 例如，如果您的XHTML檔案儲存在名為的資料夾中 `xhtmltodita` 在 `projects` 資料夾，然後指定位置為： `/content/dam/projects/xhtmltodita/`

   - 在`outputDir` 元素，指定輸出資料夾的位置或保留預設輸出位置。 如果DAM上不存在指定的輸出資料夾，則轉換工作流程會建立輸出資料夾。

   - 對於 `createRev` 元素，指定是否要建立新版本的轉換DITA主題\(`true`\)或不是\(`false`\)。

1. 儲存 `h2d_io.xml` 檔案。

1. 在中設定必要的引數後 `h2d_io.xml` 檔案登入AEM並開啟Assets UI。

1. *\（可選\）* 您也可以將相關連結區段新增至轉換後的檔案。 執行以下步驟來啟用此功能：

   >[!NOTE]
   >
   > 依預設，轉換後的檔案中不會建立相關連結區段。

   1. 導覽至下列位置的h2d.xsl檔案：

      /libs/fmdita/html2dita/

   2. 搜尋下列引數：

      `<xsl:param name="generate-related-links" select="false()"/>`

   3. 將上述引數的值設定為 `true()`.
   4. 儲存並關閉檔案。
1. 導覽至輸入資料夾位置\(`xhtmltodita`\)。

1. 將來源XHTML檔案上傳至此資料夾。 如需在DAM上傳內容的詳細資訊，請參閱 [上傳現有DITA內容](migrate-content-upload-existing-dita-content.md#).


使用 `<config> </config>` 區塊，您可以定義要轉換的一或多個設定區塊。 會執行轉換工作流程，並將最終輸出以DITA主題的形式儲存在中指定的位置 `outputDir` 元素。

## 移轉非結構化FrameMaker檔案 {#id1949B050VUI}

AEM Guides可讓您轉換現有的非結構化FrameMaker \(`.fm` 和 `.book`\)將檔案匯入DITA檔案。 第一步是使用FrameMaker建立樣式對應，並將這些設定儲存至.sts檔案中。 接下來，如果您使用自訂DITA，則可以在下列位置將自訂元素與來源FrameMaker格式對應： `ditaElems.xml` 檔案。 例如，如果您建立了自訂元素，命名為 `impnote` 若要處理所有重要附註，您可在以下位置定義此自訂元素： `ditaElems.xml` 檔案。 定義此自訂元素後，轉換AEM Guides所包含的FrameMaker檔案時，不會發生錯誤 `impnote` 元素。

此外，如果您想要使用自訂或有效的DITA元素指定一些其他屬性，可以在style2attrMap.xml檔案中定義這些屬性。 例如，您可以指定 `type` 屬性值為的屬性 `important` 要傳遞的 `impnote` 元素。 您可以在style2attrMap.xml檔案中指定此額外資訊。

除了指定

若要將現有的非結構化FrameMaker檔案轉換為DITA格式，請執行下列步驟：

1. 在FrameMaker中建立樣式對應，並將這些設定儲存在.sts檔案中。

1. 登入AEM並開啟CRXDE Lite模式。

1. 如果您有自訂DITA元素，請在 `ditaElems.xml` 檔案可從下列位置取得：

   `/libs/fmdita/config/ditaElems.xml`

1. 建立「 」的覆蓋節點 `config` 內的資料夾 `apps` 節點。

1. 導覽至「 」中可用的設定檔 `apps` 節點：

   `/apps/fmdita/config/ditaElems.xml`

   此 `ditaElems.xml` 檔案包含單一可設定引數：

   - 在 `elem` 引數，指定您要在轉換的DITA檔案中使用的自訂元素名稱。 此元素會像在產生的DITA檔案中一樣傳遞。

1. 如果要指定其他屬性，請在 `style2attrMap.xml` 檔案可從下列位置取得：

   `/libs/fmdita/config/style2attrMap.xml`

1. 建立「 」的覆蓋節點 `config` 內的資料夾 `apps` 節點。

1. 導覽至「 」中可用的設定檔 `apps` 節點：

   `/apps/fmdita/config/style2attrMap.xml`

   此 `style2attrMap.xml` 檔案包含下列可設定的引數：

   - 在 `fmStyle` 引數，指定您要對映的FrameMaker檔案中使用的來源格式。

   - 在`ditaAttr` 元素，指定您要與來源格式對應的DITA屬性。

   - 在 `ditaVal` 元素，指定對應屬性的值。 如果您沒有任何值，可將此專案留白。

1. 儲存 `style2attrMap.xml` 檔案。

1. 在中設定必要的引數後 `style2attrMap.xml` 檔案登入AEM並開啟Assets UI。

1. 導覽至您要轉換的FrameMaker檔案，並按一下該檔案。

   DITA map主控台隨即出現，顯示可用於產生輸出的輸出預設集清單。

1. 選取DITA輸出格式並設定必要的引數。

   >[!NOTE]
   >
   > 您必須使用您在FrameMaker中建立的相同設定檔案\(.sts\)。 此外，請指定「設定名稱」和「目的地路徑」。

1. 按一下 **產生** 圖示以啟動輸出產生程式。


使用 `<attrMap> </attrMap>` 區塊，您可以定義要轉換的一或多個設定區塊。 視內容而定，您可能會有.dita檔案和.ditamap檔案作為轉換的檔案。

## 移轉任何其他結構化檔案 {#id1949B0590YK}

AEM Guides可讓您將現有的結構化檔案轉換為有效的DITA檔案。 您需要指定輸入和輸出資料夾位置、轉換檔案的位置、儲存最終輸出的副檔名，以及是否需要檔案的新版本。

若要將現有的結構化檔案轉換為DITA格式，請執行下列步驟：

1. 登入AEM並開啟CRXDE Lite模式。

1. 導覽至下列位置可用的預設組態檔：

   `/libs/fmdita/config/XSLConfig.xml`

1. 建立「 」的覆蓋節點 `config` 內的資料夾 `apps` 節點。

1. 導覽至「 」中可用的設定檔 `apps` 節點：

   `/apps/fmdita/config/XSLConfig.xml`

   此 `XSLConfig.xml` 檔案包含下列可設定的引數：

   - 在 `inputDir` 元素，指定您的來源結構化檔案可用的輸入資料夾位置。 例如，如果您的結構化檔案儲存在名為的資料夾中 `xsltodita` 在 `projects` 資料夾，然後指定位置為： `/content/dam/projects/xsltodita/`

   - 在`outputDir` 元素，指定輸出資料夾的位置或保留預設輸出位置。 如果DAM上不存在指定的輸出資料夾，則轉換工作流程會建立輸出資料夾。

   - 在 `xslFolder` 元素，指定儲存XSL轉換檔案的資料夾位置。

   - 在 ``xslPath`` 元素，指定用來起始轉換程式的主要.XSL檔案的位置。

   - 在 ``outputExt`` 元素，指定從轉換資料流建立之最終輸出檔案的副檔名。

   - 對於 `createRev` 元素，指定是否要建立新版本的轉換DITA主題\(`true`\)或不是\(`false`\)。

1. 儲存 `XSLConfig.xml` 檔案。

1. 在中設定必要的引數後 `XSLConfig.xml` 檔案登入AEM並開啟Assets UI。

1. 導覽至輸入資料夾位置\(`xsltodita`\)。

1. 將來源結構化檔案上傳至此資料夾。 如需在DAM上傳內容的詳細資訊，請參閱 [上傳現有DITA內容](migrate-content-upload-existing-dita-content.md#).


使用 `<config> </config>` 區塊，您可以定義要轉換的一或多個設定區塊。 會執行轉換工作流程，並將最終輸出以DITA主題的形式儲存在中指定的位置 `outputDir` 元素。

**父級主題：**[&#x200B;移轉現有內容](migrate-content.md)

