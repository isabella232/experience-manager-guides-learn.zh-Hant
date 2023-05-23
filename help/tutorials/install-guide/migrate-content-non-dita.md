---
title: 遷移非DITA內容
description: 瞭解如何遷移非DITA內容
source-git-commit: 5ac066bb8db32944abd046f64da11eeb1bdbe467
workflow-type: tm+mt
source-wordcount: '2792'
ht-degree: 0%

---


# 遷移非DITA內容 {#id181AH0R02HT}

本節將指導您完成遷移過程，將非DITA文檔遷移到DITA格式。 指AEM南提供從以下源遷移：

- [Microsoft Word](#id1949B040Z5Z)

- [InDesign文檔](#id195AD0B0K5Z)

- [XHTML](#id1949B04L0Y4)

- [非結構化FrameMaker文檔](#id1949B050VUI)

- [任何其他結構化文檔](#id1949B0590YK)


## 遷移MicrosoftWord文檔 {#id1949B040Z5Z}

指AEM南允許您遷移現有Word文檔\(`.docx`\)。 您需要指定輸入和輸出資料夾的位置以及其他參數，文檔將轉換為DITA文檔。 根據內容，您可以有.dita檔案和.ditamap檔案。

要成功轉換Word文檔，您的文檔應該結構良好。 例如，您的文檔應具有標題，後跟標題1、標題2等。 每個標題都應包含一些內容。 如果文檔結構不完善，則該過程可能不按預期工作。

預設情況下，AEM參考線使用 [Word-to-DITA \(Word2DITA\)轉換框架](http://www.dita4publishers.org/docs/repo/org.dita4publishers.word2dita/word2dita/word2dita-intro.html)。 此轉換取決於 [樣式到標籤映射](http://www.dita4publishers.org/docs/repo/org.dita4publishers.word2dita/word2dita/style-to-tag-map-overview.html) 配置檔案。 要成功使用Word2DITA轉換，必須考慮以下準備Word文檔以進行轉換的准則：

>[!NOTE]
>
> 如果在預設樣式到標籤映射配置檔案中進行了任何更改，則必須更新並使用准則確認更新的樣式映射。

- 確保文檔以標題開頭；此標題映射到DITA映射標題。 此外，標題後必須有一些常規內容。

- 標題後應有標題1、標題2等。 每個標題都必須包含一些內容。 標題將轉換為新的概念類型主題。 生成的主題的層次結構與文檔中的標題級別相同，例如，標題1將位於標題2之前，標題2將位於標題3內容之前。

- 文檔必須至少包含一個標題類型內容。

- 確保沒有任何分組映像。 如果文檔中已對影像進行分組，請取消對所有此類影像的分組。

- 刪除所有頁眉和頁腳。

- 內聯樣式（如粗體、斜體和下划線）將轉換為 `b`。 `i`, `u` 元素。

- 所有已排序清單和未排序清單都轉換為 `ol` 和 `ul` 元素。 這也適用於嵌套清單、表、注釋或腳注中的清單。

- 所有超連結都轉換為 `xref`。

- 轉換後檔案的檔案名基於標題文本，後跟檔案號。 檔案編號是基於標題文本在文檔中的位置而生成的連續編號。 例如，如果標題文本是「示例標題」，並且是文檔中的第10個標題，則此主題的結果檔案名將與Sample\_Heading\_10.dita類似。


執行以下步驟將現有Word文檔轉換為DITA主題類型文檔：

1. 登錄並AEM開啟CRXDE Lite模式。

1. 導航到以下位置可用的預設配置檔案：

   `/libs/fmdita/config/w2d_io.xml`

1. 建立的覆蓋節點 `config` 資料夾 `apps` 的下界。

1. 導航到中可用的配置檔案 `apps` 節點：

   `/apps/fmdita/config/w2d_io.xml`

   的 `w2d_io.xml` 檔案包含以下可配置參數：

   - 在 `inputDir` 元素，指定源Word文檔可用的輸入資料夾的位置。 例如，如果Word文檔儲存在名為 `wordtodita` 在 `projects` 資料夾，然後將位置指定為： `/content/dam/projects/wordtodita/`

   - 在`outputDir` 元素，指定輸出資料夾的位置或保留預設輸出位置以保存轉換的DITA文檔。 如果DAM上不存在指定的輸出資料夾，則轉換工作流將建立輸出資料夾。

   - 對於 `createRev` 元素，指定是否建立轉換的DITA主題的新版本\(`true`\或不\(`false`\)。

   - 在 `s2tMap` 元素，指定映射檔案的位置，該映射檔案包含Word文檔樣式到DITA元素的映射。 預設映射儲存在位於以下位置的檔案中：

      ```XML
      /libs/fmdita/word2dita/word-builtin-styles-style2tagmap.xml
      ```

      >[!NOTE]
      >
      > 有關的結構的詳細資訊 `word-builtin-styles-style2tagmap.xml` 檔案以及如何自定義它，請參閱 [樣式到標籤映射](http://www.dita4publishers.org/docs/repo/org.dita4publishers.word2dita/word2dita/style-to-tag-map-overview.html) 在 *《 DITA For Publishers使用手冊》*。

   - 在props2Propagate元素中，指定應傳遞給DITA映射的屬性。 將預設元資料（如dc:title,dc:subject,dam:keywords,dam:category）從文檔元資料傳遞到轉換的DITA資產時，需要此屬性。

1. 保存 `w2d_io.xml` 的子菜單。

1. 在中配置所需參數後 `w2d_io.xml` 檔案，登AEM錄並開啟Assets UI。

1. 導航到輸入資料夾位置\(`wordtodita`\)。

1. 將源Word文檔上載到此資料夾。 有關在DAM上載內容的資訊，請參見 [上載現有DITA內容](migrate-content-upload-existing-dita-content.md#)。


使用 `config` `/config` 塊，可以定義一個或多個配置塊以進行轉換。 將執行轉換工作流，並將DITA主題形式的最終輸出保存在在 `outputDir` 的子菜單。

## 遷移Adobe InDesign文檔 {#id195AD0B0K5Z}

參AEM考線允許您轉換InDesign文檔。 與FrameMaker類似，InDesign還允許您建立非結構化和結構化文檔。 非結構化文檔使用段落和字元樣式來格式化內容。 結構化文檔使用元素及其相應屬性。

轉換過程需要將段落和字元樣式格式映射到相關的DITA元素。 同樣，對於結構化文檔，映射檔案將包含InDesign元素和屬性與DITA元素和屬性的一對一映射。

轉換過程涉及後端中的以下操作：

- 的 *InDesign標籤語言* \(IDML\)檔案已解壓縮到工作目錄。
- 讀取designmap.xml檔案以查找各個InDesign文章。
- 所有文章合併到單個XML實例中，「空」文章被丟棄。
- 所有嵌入式圖形都會導出。
- 將標準結構（如表和圖形）預轉換為DITA格式。
- 基於映射檔案到最終輸出的樣式或結構映射。
- 建立和驗證單個DITA主題和DITA映射檔案。
- 刪除臨時檔案。

通常，轉換過程要求您 [準備InDesign檔案以進行轉換](appendix.md#id195DBF0045Z) 和 [準備映射檔案以InDesign到DITA遷移](appendix.md#id194AF0003HT) 然後，您需要遵循運行轉換進程的給定過程。

執行以下步驟將現有InDesign文檔轉換為DITA主題類型文檔：

1. 登錄並AEM開啟CRXDE Lite模式。

1. 導航到以下位置可用的預設配置檔案：

   `/libs/fmdita/config/idml2dita_io.xml`

1. 建立的覆蓋節點 `config` 資料夾 `apps` 的下界。

1. 導航到中可用的配置檔案 `apps` 節點：

   `/apps/fmdita/config/idml2dita_io.xml`

   在 `idml2dita_io.xml` 檔案：

   - 在 `inputDir` 元素，指定輸入資料夾的位置，其中源InDesign文檔可用。 例如，如果InDesign文檔儲存在名為 `indesigntodita` 在 `projects` 資料夾，然後將位置指定為： `/content/dam/idmlfiles/indesigntodita/`

   - 在`outputDir` 元素，指定輸出資料夾的位置或保留預設輸出位置以保存轉換的DITA文檔。 如果DAM上不存在指定的輸出資料夾，則轉換工作流將建立輸出資料夾。

   - 在 `mapStyle` 元素，指定映射檔案的位置，該映射檔案包含將文檔樣式InDesign到DITA元素的映射。 預設映射儲存在位於以下位置的檔案中：

      ```XML
      /stmap.adobeidml.xml
      ```

      >[!NOTE]
      >
      > 有關的結構的詳細資訊 `stmap.adobeidml.xml` 以及如何自定義檔案，請參閱 [準備映射檔案以InDesign到DITA遷移](appendix.md#id194AF0003HT) 部分 *附錄*。

1. 保存 `idml2dita_io.xml` 的子菜單。

1. 在中配置所需參數後 `idml2dita_io.xml` 檔案，登AEM錄並開啟Assets UI。

1. 導航到輸入資料夾位置\(`indesigntodita`\)。

1. 將源InDesign文檔上載到此資料夾。 有關在DAM上載內容的資訊，請參見 [上載現有DITA內容](migrate-content-upload-existing-dita-content.md#)。


## 遷移XHTML文檔 {#id1949B04L0Y4}

AEM參考線允許您將現有XHTML文檔轉換為DITA主題類型文檔。 您需要指定輸入和輸出資料夾的位置以及其他參數，文檔將轉換為DITA格式。 有兩種方法可用於轉換結構化HTML文檔：

- 將所有文檔上載到輸入資料夾，或
- 建立所有文檔的ZIP以及媒體檔案，並將其上載到輸入資料夾中。 此方法通常用於一組彼此連結的HTML檔案，其中有目錄\(index.html\)。 index.html檔案包含指向集中所有HTML檔案的連結。

無論您是單獨上載所有檔案，還是在ZIP中綁定所有檔案，轉換過程都會在HTML檔案和生成的DITA檔案之間建立一對一的映射。 這實際上意味著在輸入資料夾中為每個.html檔案建立了一個.dita檔案。

在將文檔上載到ZIP檔案時，必須考慮以下幾點：

- 所有引用的主題都應放在ZIP檔案中。

- 所有引用的媒體檔案都應使用相對連結在主題檔案中引用。

- 建立index.html檔案，並將連結添加到要添加到目錄中的主題。 此index.html檔案用於建立DITA映射檔案。 在index.html檔案中，還可以建立嵌套主題清單，如以下代碼示例所示：

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

   請注意 `ul` 標籤必須具有 `class` 屬性集 `book`。 同樣， `li` 標籤 `class` 必須設定為 `topicref`。

- 如果使用內聯樣式，則將內聯樣式轉換為XHTML檔案中基於CSS的樣式類。 然後使用樣式 — 屬性映射將這些基於類的樣式轉換為DITA `outputclass` 屬性。

   從這些DITA文AEM件生成HTML或站點輸出時， `outputclass` 屬性可用於在生成的HTML或站點上應AEM用style-class以匹配源HTML內容。


除了建立ZIP檔案的考慮事項外，XHTML文檔還必須結構良好。 例如，您的文檔應 *標題*，後跟 *標題1*。 *標題2*&#x200B;等等。 每個標題都應包含一些內容。 如果文檔結構不良，遷移過程可能不會按預期工作。

要將現有XHTML文檔轉換為DITA主題，請執行以下步驟：

1. 登錄並AEM開啟CRXDE Lite模式。

1. 導航到以下位置可用的預設配置檔案：

   `/libs/fmdita/config/h2d_io.xml`

1. 建立的覆蓋節點 `config` 資料夾 `apps` 的下界。

1. 導航到中可用的配置檔案 `apps` 節點：

   `/apps/fmdita/config/h2d_io.xml`

   的 `h2d_io.xml` 檔案包含以下可配置參數：

   - 在 `inputDir` 元素，指定輸入資料夾的位置，其中源XHTML文檔可用。 例如，如果XHTML文檔儲存在名為 `xhtmltodita` 在 `projects` 資料夾，然後將位置指定為： `/content/dam/projects/xhtmltodita/`

   - 在`outputDir` 元素，指定輸出資料夾的位置或保留預設輸出位置。 如果DAM上不存在指定的輸出資料夾，則轉換工作流將建立輸出資料夾。

   - 對於 `createRev` 元素，指定是否建立轉換的DITA主題的新版本\(`true`\或不\(`false`\)。

1. 保存 `h2d_io.xml` 的子菜單。

1. 在中配置所需參數後 `h2d_io.xml` 檔案，登AEM錄並開啟Assets UI。

1. *\（可選\）* 您還可以將相關連結部分添加到已轉換的文檔。 執行以下步驟以啟用此功能：

   >[!NOTE]
   >
   > 預設情況下，不會在轉換的文檔中建立相關連結部分。

   1. 導航到以下位置中的h2d.xsl檔案：

      /libs/fmdita/html2dita/

   2. 搜索以下參數：

      `<xsl:param name="generate-related-links" select="false()"/>`

   3. 將上述參數的值設定為 `true()`。
   4. 保存並關閉檔案。
1. 導航到輸入資料夾位置\(`xhtmltodita`\)。

1. 將源XHTML文檔上載到此資料夾。 有關在DAM上載內容的資訊，請參見 [上載現有DITA內容](migrate-content-upload-existing-dita-content.md#)。


使用 `<config> </config>` 塊，可以定義一個或多個配置塊以進行轉換。 將執行轉換工作流，並將DITA主題形式的最終輸出保存在在 `outputDir` 的子菜單。

## 遷移非結構化FrameMaker文檔 {#id1949B050VUI}

參考AEM線允許您轉換現有的非結構化FrameMaker \(`.fm` 和 `.book`\)文檔到DITA文檔。 第一步是使用FrameMaker建立樣式映射，並將這些設定保存在.sts檔案中。 接下來，如果您使用自定義DITA，則可以使用源FrameMaker格式在 `ditaElems.xml` 的子菜單。 例如，如果已建立名為 `impnote` 要處理所有重要注釋，則可在 `ditaElems.xml` 的子菜單。 定義此自定義元素後，AEM參考線在轉換包含FrameMaker文檔時不會引發錯誤 `impnote` 的子菜單。

此外，如果要使用自定義或有效的DITA元素指定一些附加屬性，則可以在style2attrMap.xml檔案中定義這些屬性。 例如，可以指定 `type` 值為 `important` 與 `impnote` 的子菜單。 可以在style2attrMap.xml檔案中指定此附加資訊。

除了指定

要將現有的非結構化FrameMaker文檔轉換為DITA格式，請執行以下步驟：

1. 在FrameMaker中建立樣式映射，並將這些設定保存在.sts檔案中。

1. 登錄並AEM開啟CRXDE Lite模式。

1. 如果您有自定義DITA元素，請在 `ditaElems.xml` 檔案在以下位置可用：

   `/libs/fmdita/config/ditaElems.xml`

1. 建立的覆蓋節點 `config` 資料夾 `apps` 的下界。

1. 導航到中可用的配置檔案 `apps` 節點：

   `/apps/fmdita/config/ditaElems.xml`

   的 `ditaElems.xml` 檔案包含單個可配置參數：

   - 在 `elem` 參數，指定要在轉換的DITA文檔中使用的自定義元素的名稱。 此元素將像生成的DITA文檔中一樣傳遞。

1. 如果要指定附加屬性，請在 `style2attrMap.xml` 檔案在以下位置可用：

   `/libs/fmdita/config/style2attrMap.xml`

1. 建立的覆蓋節點 `config` 資料夾 `apps` 的下界。

1. 導航到中可用的配置檔案 `apps` 節點：

   `/apps/fmdita/config/style2attrMap.xml`

   的 `style2attrMap.xml` 檔案包含以下可配置參數：

   - 在 `fmStyle` 參數，指定要映射的FrameMaker文檔中使用的源格式。

   - 在`ditaAttr` 元素，指定要用源格式映射的DITA屬性。

   - 在 `ditaVal` 元素，指定映射屬性的值。 如果您沒有任何值，則可以將此條目留空。

1. 保存 `style2attrMap.xml` 的子菜單。

1. 在中配置所需參數後 `style2attrMap.xml` 檔案，登AEM錄並開啟Assets UI。

1. 導航到要轉換的FrameMaker文檔並按一下。

   DITA映射控制台將顯示可用於生成輸出的輸出預設的清單。

1. 選擇DITA輸出格式並配置所需參數。

   >[!NOTE]
   >
   > 必須使用在FrameMaker中建立的相同設定檔案\(.sts\)。 另外，指定「設定名稱」和「目標路徑」。

1. 按一下 **生成** 表徵圖以啟動輸出生成進程。


使用 `<attrMap> </attrMap>` 塊，可以定義一個或多個配置塊以進行轉換。 根據內容，可以將.dita檔案和.ditamap檔案作為轉換的檔案。

## 遷移任何其他結構化文檔 {#id1949B0590YK}

指AEM南允許您將現有結構化文檔轉換為有效的DITA文檔。 您需要指定輸入和輸出資料夾位置、轉換檔案的位置、保存最終輸出的副檔名，以及是否需要新版本的文檔。

要將現有結構化文檔轉換為DITA格式，請執行以下步驟：

1. 登錄並AEM開啟CRXDE Lite模式。

1. 導航到以下位置可用的預設配置檔案：

   `/libs/fmdita/config/XSLConfig.xml`

1. 建立的覆蓋節點 `config` 資料夾 `apps` 的下界。

1. 導航到中可用的配置檔案 `apps` 節點：

   `/apps/fmdita/config/XSLConfig.xml`

   的 `XSLConfig.xml` 檔案包含以下可配置參數：

   - 在 `inputDir` 元素，指定輸入資料夾的位置，其中源結構化文檔可用。 例如，如果結構化文檔儲存在名為 `xsltodita` 在 `projects` 資料夾，然後將位置指定為： `/content/dam/projects/xsltodita/`

   - 在`outputDir` 元素，指定輸出資料夾的位置或保留預設輸出位置。 如果DAM上不存在指定的輸出資料夾，則轉換工作流將建立輸出資料夾。

   - 在 `xslFolder` 元素，指定儲存XSL轉換檔案的資料夾的位置。

   - 在 ``xslPath`` 元素，指定用於啟動轉換進程的主.XSL檔案的位置。

   - 在 ``outputExt`` 元素，指定從轉換流建立的最終輸出檔案的檔案副檔名。

   - 對於 `createRev` 元素，指定是否建立轉換的DITA主題的新版本\(`true`\或不\(`false`\)。

1. 保存 `XSLConfig.xml` 的子菜單。

1. 在中配置所需參數後 `XSLConfig.xml` 檔案，登AEM錄並開啟Assets UI。

1. 導航到輸入資料夾位置\(`xsltodita`\)。

1. 將源結構化文檔上載到此資料夾。 有關在DAM上載內容的資訊，請參見 [上載現有DITA內容](migrate-content-upload-existing-dita-content.md#)。


使用 `<config> </config>` 塊，可以定義一個或多個配置塊以進行轉換。 將執行轉換工作流，並將DITA主題形式的最終輸出保存在在 `outputDir` 的子菜單。

**父主題：**[&#x200B;遷移現有內容](migrate-content.md)

