---
title: 附錄
description: 瞭解如何準備InDesign檔案以進行轉換
source-git-commit: 5ac066bb8db32944abd046f64da11eeb1bdbe467
workflow-type: tm+mt
source-wordcount: '2861'
ht-degree: 0%

---

# 附錄 {#id195AD0L60Y4}

## 準備InDesign檔案以進行轉換 {#id195DBF0045Z}

InDesign為作者提供了豐富的功能集，用於建立具有吸引力且複雜的文檔。 這通常意味著文檔的各個部分以視覺方式放置在頁面上，但不會嘗試在這些文本框架之間提供任何流。 當&#39;*閱讀順序*「未定義文本框架中，IDML檔案將包含可能不遵循任何有意義順序的文章。 最終結果將是一個或多個DITA主題，其中段落、表和圖形按隨機順序排列。

雖然可以在DITA編輯器中將DITA內容編輯為合理順序，但在建立IDML檔案之前更容易修復InDesign檔案。 這可以在不改變源文檔外觀的情況下完成。 通過正確定義閱讀順序，還可使源文檔可訪問。

***線程化文本框架***

InDesign使用術語 *「線程」* 用於將一個框架連結到另一個框架的過程。 有關線程化文本框架的詳細資訊，請參閱 *[線程文本](https://helpx.adobe.com/in/indesign/using/threading-text.html)* InDesign文檔中的主題。

***重疊幀***

某些InDesign文檔由於佈局原因使用無線重疊框架。 將此內容合併到主線程可能非常困難。 最佳選項可能是在DITA環境中編輯結果。

***InDesign故事***

InDesign文檔中的每個線程化內容流稱為「 」*故事*「 」。 為獲得最佳效果，建議將報導數量限制在一定範圍內。 但是，DITA輸出中可能不需要文檔的某些部分。 例如，頁腳很少需要，但如果不仔細處理，頁腳可能會出現在主題的中間。

排除文檔中不需要的文本的最簡單的方法是為其提供特殊 *段落標籤* 只用於不需要的內容。 例如，不再重用 *\[基本段落\]* 對於頁腳，建立專用 *頁腳* 標籤。 然後，在MapStyle檔案中，只需 *頁腳* 要刪除的段落如下：

```XML
<paraRule style="Footer" local="0" refactor="drop">
   <attributeRules createID="false"/>
</paraRule>
```

***映射到DITA文檔類型***

源文檔至少具有一個可標籤主題開始的段落樣式或元素，這一點非常重要。 文檔常用 *標題1* 作為文檔中頂級標題的名稱。 然後，可以建立從該樣式到特定DITA doctype的映射。 如果您的文檔組織良好， *標題1* 始終不變，就會有好的效果。

***多個DITA文檔類型***

如果 *標題1* 段落需要轉換為不同的DITA文檔類型，然後複製InDesign中的段落樣式。 使這些樣式易於識別名稱，如 *標題1\_genTask* 或 *標題1\_疑難解答* 視情況而定。 然後，按如下所示設定mapStyle檔案：

```XML
<doctypes>
   <doctypeParaRule style="Heading1" local="0" mapToDoctype="concept">
      <attributeRules createID="true"/>
   </doctypeParaRule>
   <doctypeParaRule style="Heading1_genTask" local="0" mapToDoctype=" generalTask">
      <attributeRules createID="true"/>
   </doctypeParaRule>
   <doctypeParaRule style="Heading1_troubleshooting" local="0"mapToDoctype=" troubleshooting">
      <attributeRules createID="true"/>
   </doctypeParaRule>
</doctypes>
```

***結構化InDesign文檔***

InDesign與XML有鬆散的關係。 雖然文檔可以包含XML DTD，並且主文章對於該DTD可能有效，但也可以建立混合文檔，其中某些內容是XML，但不包括DTD。 這些是成功轉換到DITA的不需要的情況。 如果文檔包含XML部件，請嘗試將輸出保存為XML，並查看結果是否可接受。 否則，DITA內容還將包含無效內容，或者可能完全失敗。

***表格格式***

從InDesign表格格式規則到DITA中等效表格格式的轉換是一個複雜的過程。 這是因為與DITA中使用的Oasis \(CALS\)表模型提供的基本選項相比，源檔案中提供了豐富的格式功能。 提供了垂直和水準文本對齊，並且會產生類似結果，儘管「對齊」文本始終根據文本方向對齊，而「InDesign」允許「左對齊」和「右對齊」。

InDesign對列和行分隔符的處理能力再次遠遠強於Oasis表模型的基本選項。 InDesign提供四個單元格邊框 — 邊框類型\（實體或圖案\）、邊框粗細、邊框顏色、邊框色調、邊框間隙顏色和邊框間隙色調。 所有這些內容都必須下移到每個單元格\(entry element\)右下方的邊框上，其中唯一的選項是0或1 — 隱藏邊框或顯示邊框。

InDesign中的邊界裁定可以應用於以下級別：

- 表格樣式
- 單元格樣式
- 每個單元格上的本地覆蓋

InDesign到DITA轉換過程應用如下邊框裁定：

- 表樣式映射到 `colspec/@colsep` 屬性。 水準規則映射到 `row/@rowsep` 屬性。 在這兩種情況下，如果未定義邊框，則不建立屬性。
- 單元格樣式映射到 `entry/@colsep` 和 `entry/@rowsep` 屬性。 這些值將覆蓋任何「表樣式」派生的邊框規則。
- 本地覆蓋將格式設定直接應用於單元格，並覆蓋表格樣式和單元格樣式。

***交替圖案***

InDesign表樣式允許列和單元格規則遵循交替模式。 雖然此功能支援轉換，但僅當一個模式組映射為顯示規則\(1\)而另一個模式組映射為隱藏規則\(0\)時，結果才會明顯。

## 準備映射檔案以InDesign到DITA遷移 {#id194AF0003HT}

正確的DITA轉換需要與源文檔內容匹配的映射檔案。 對於非結構化InDesign文檔，這意味著需要映射所有可用的段落樣式和字元樣式。 對於XML結構化InDesign文檔，必須映射其關聯DTD中的所有元素。

非結構化文檔和結構化InDesign文檔的映射檔案不同。 這是由於將非結構化源內容轉換為DITA的處理要求更複雜。

下面提供了映射檔案的示例：

```XML
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE styleMap SYSTEM "mapStyle.dtd">
<styleMap xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="mapStyle.xsd" >
   <doctypes>
      <mapDoctypeParaRule root="itpx:stories" mapToDoctype="map">
         <attributeRules createID="true">
            <addNew name="outputclass" value="map"/>
         </attributeRules>
      </mapDoctypeParaRule>
      <doctypeParaRule style="Heading 1" local="0" mapToDoctype="concept">
         <attributeRules createID="true"/>
      </doctypeParaRule>
      <doctypeParaRule style="Heading A" local="0" mapToDoctype="topic">
         <attributeRules createID="true"/>
      </doctypeParaRule>
   </doctypes>
   <wrappingRules>
      <wrap elements="li+" context="number" wrapper="ol">
         <attributeRules createID="true"/>
      </wrap>
      <wrap elements="li+" context="bullet" wrapper="ul">
         <attributeRules createID="true"/>
      </wrap>
   </wrappingRules>
   <paragraphStyleRules>
      <paraRule style="Heading 2" local="0"  mapTo="p">
         <attributeRules createID="true"/>
      </paraRule>
      <paraRule style="Heading 3" local="0"  mapTo="p">
         <attributeRules createID="true"/>
      </paraRule>
      <paraRule style="List Paragraph" local="p[-|-|-|-|-|b|-|-]" context="bullet" mapTo="li">
         <attributeRules createID="true"/>
      </paraRule>
      <paraRule style="List Paragraph" local="p[-|-|-|-|-|n|-|-]" context="number" mapTo="li">
         <attributeRules createID="true"/>
      </paraRule>
      <paraRule style="List Paragraph" local="0" context="bullet" mapTo="li">
         <attributeRules createID="true"/>
      </paraRule>
      <paraRule style="Normal" local="0"  mapTo="p">
         <attributeRules createID="true"/>
      </paraRule>
      <paraRule style="Normal" local="p[-|-|-|-|-|b|-|-]" context="bullet" mapTo="li">
         <attributeRules createID="true"/>
      </paraRule>
      <paraRule style="Title" local="0"  mapTo="p">
         <attributeRules createID="true"/>
      </paraRule>
   </paragraphStyleRules>
   <characterStyleRules>
      <charRule style="Bold" local="0" mapTo="b">
         <attributeRules createID="false"/>
      </charRule>
      <charRule style="Code" local="0" mapTo="codeph">
         <attributeRules createID="false"/>
      </charRule>
      <charRule style="[No character style]" local="c[Bold|-|-|-|-|-|-|-]" mapTo="b">
         <attributeRules createID="false"/>
      </charRule>
      <charRule style="[No character style]" local="c[Italic|-|-|-|-|-|-|-]" mapTo="i">
         <attributeRules createID="false"/>
      </charRule>
   </characterStyleRules>
</styleMap>
```

映射檔案是XML檔案，其簡單結構列出所有源段落樣式和字元樣式代碼。 檔案內容說明如下：

**樣式映射**

在 `styleMap` 元素，可以指定兩個可選屬性 —  `@map_date` 和 `@map_version` 用於記錄映射檔案的版本。

**文檔類型**

的 `doctypes` 元素列出了支援的DITA映射和主題映射。

**映射文檔類型段落規則**

的 `mapDoctypeParaRule` 元素是必需的。 不能編輯此元素的屬性，因為源XML的根元素始終映射到DITA映射的根 `map` 的子菜單。

**文檔類型段落規則**

的 `doctypeParaRule` 元素是必需的。 這為轉換過程提供了一種確定新主題開始的方法。 通常 `@style` 屬性單獨與 `@local` 屬性設定為0。 但是，如果所選樣式上始終存在本地格式覆蓋，則必須為每個樣式加上其本地覆蓋添加規則。 在生成的映射檔案中，很容易識別可以找到此類或類似內容：

```XML
<paraRule style="Heading 1" local="0" mapTo="p">
   <attributeRules createID="true"/>
</paraRule>
<paraRule style="Heading 1" local="p[Italic|-|-|-|-|-|-|-]" mapTo="p">
   <attributeRules createID="true"/>
</paraRule>
```

在上例中，有兩個 `paraRule` 元素 `@style` = &quot;標題1&quot;。 只需建立等效項 `doctypeParaRule` 元素 `@mapToDoctype` 屬性集。

中使用的屬性 `doctypeParaRule` 如下：

- `@style`:源InDesign文檔中樣式的名稱。
- `@local`:請參閱 [\#id194CG0V005Z](#id194CG0V005Z)。
- `@mapToDoctype`:所有有效枚舉清單中的DITA主題類型的名稱 `doctypes`。

**元素環繞規則**

元素環繞規則定義了根據一組屬性值將傳入文檔中的元素包絡或移動到預定義元素的方法。

***`wrap`元素***

這是可選元素。 的 `wrap` 元素列出要包裝或移動的元素。 在必須給一系列元素指定公共父元素的情況下，通常使用環繞。 例如，多 `li` 包裝在 `ol` 的子菜單。 此外， `wrap` 可用於移動元素，如圖形和表格的標題。

中使用的屬性 `wrap` 如下：

- `@element`:元素名稱后的加號顯示具有相同名稱的所有相鄰元素將包裝在 `@wrapper`屬性。
- `@wrapper`:包裝元素的名稱。
- `@context`:提供了進一步細化給定元素的包裝方式的方法。 以下示例顯示了映射一系列 `li` 排序清單中的任意一個元素 `ol` 或無序清單 `ul` 根據 `@context` 值\(上下文是在 `paraRule` 元素\):

   ```XML
   <wrap elements="li+" context="number" wrapper="ol">
      <attributeRules createID="true"/>
   </wrap>
   <wrap elements="li+" context="bullet" wrapper="ul">
      <attributeRules createID="true"/>
   </wrap>
   ```


以下示例說明如何建立 `fig` 元素 `title` 和 `image` 元素：

- `@elements`:以逗號列出和分隔的元素將包裝在 `@wrapper` 屬性。 由於通常將圖形標題包含在影像下方，標題將是 `title` 緊跟在元素後面 `image`。

   以下換行規則：

   ```XML
   <wrap elements="title, image" context="FigTitle" wrapper="fig">
      <attributeRules createID="true"/>
   </wrap>
   ```

   轉換以下中間XML:

   ```XML
   <image href="Links/myImage.png" scale="59">
      <title>IDML2DITA workflow</title>
   ```

   進入以下有效的DITA圖形結構：

   ```XML
   <fig id="id397504">
      <title>IDML2DITA workflow</title>
      <image href="Links/myImage.png" scale="59">
   </fig>
   ```

- `@wrapper`:包裝元素的名稱。
- `@context`:提供了進一步細化給定元素包裝方式的方法\(上下文在 `paraRule` 元素\)。

以下示例說明如何移動 `title` 進入 `table`:

- `@elements`:的 `title` 元素，該元素位於 `table` 將包裝在 `@wrapper` 屬性。 XPath樣式謂詞可以將標題元素的位置標識為 `[before]` 或 `[after]`。

   示例：以下換行規則：

   ```XML
   <wrap elements="title[before]" context="TableTitle" wrapper="table">
      <attributeRules createID="true"/>
   </wrap>
   ```

   轉換以下中間XML:

   ```XML
   <title>IDML2DITA workflow</title>
   <table id="id289742" outputclass="BasicTable">
      <tgroup cols="2">
         <colspec colname="0" colwidth="0.7*">
            <colspec colname="1" colwidth="0.3*">
   ```

   在此有效的DITA圖形結構中：

   ```XML
   <table id="id289742" outputclass="BasicTable">
      <title>IDML2DITA workflow</title>
      <tgroup cols="2">
         <colspec colname="0" colwidth="0.7*">
            <colspec colname="1" colwidth="0.3*">
   ```

- `@wrapper`:包裝元素的名稱。

- `@context`:提供了進一步細化給定元素包裝方式的方法\(上下文在 `paraRule` 元素\)。


**段落樣式規則**

的 `<paragraphStyleRule>` 元素如下所述：

***`paraRule`元素***

的 `paraRule` 元素是必需的。 這指定所有段落樣式的映射規則。 在InDesign文檔中，所有文本都包含在「段落樣式」的子結構中，即使沒有任何樣式的段落也會被命名 `[No paragraph style]`。 方括弧表示內置的InDesign樣式名稱。

>[!NOTE]
>
> 方括弧表示內置InDesign樣式名稱。

中使用的屬性 `paraRule` 如下：

- `@style`:源InDesign文檔中樣式的名稱。
- `@local`:請參閱 [\#id194CG0V005Z](#id194CG0V005Z)。
- `@mapTo`:DITA目標元素的名稱。

- `@context`:此屬性用於連結到特定 **包** 的子目錄。 示例：這樣 `li` 元素可以包裝在 `ol`或 `ul` 的子菜單。 要標識不同的清單類型，可以使用特定樣式名稱或 `@local` 屬性，它可顯示以下內容：
   - `local="p[-|-|-|-|-|b|-|-]"` 「 」的位置`b`&#39;在欄位6中表示項目符號清單項。 在本例集中 `@context` 到&#39;`bullet`「 」。
   - `local="p[-|-|-|-|-|n|-|-]"` 「 」的位置`n`欄位6中的「表示編號清單項。 在本例集中 `@context` 到&#39;`number`「 」。

- `@commentOut`:此屬性允許在XML注釋中包裝目標元素，這樣資訊不會丟失，但用戶可以手動處理。 如果源內容無法強制符合DITA結構規則，則此功能非常有用。

- `@refactor`:此可選屬性可以選擇兩個值：

- `unwrap`:在保留其內容的同時刪除匹配的元素。

- `drop`:匹配的元素及其所有內容都被刪除。


**字元樣式規則**

的 `charRule` 元素如下所述：

>[!NOTE]
>
> 內置字元樣式沒有映射 `[No character style]` 何時 `local="0"`，因為在預處理過程中會刪除它們。

***`charRule`元素***

這是可選元素。

這些是所有字元樣式的映射規則。 在InDesign文檔中，所有文本都包含在「字元樣式」的子元素中。

中使用的屬性 `charRule` 如下：

- `@style`:源InDesign文檔中樣式的名稱。
- `@local`:請參閱 [\#id194CG0V005Z](#id194CG0V005Z)。
- `@mapTo`:DITA目標元素的名稱。
- `@refactor`:此可選屬性可以選擇兩個值：
   - `unwrap`:在保留其內容的同時刪除匹配的元素。

   - `drop`:匹配的元素及其所有內容都被刪除。


**屬性規則**

此元素可以是以下元素上下文的子項：

- `mapDoctypeParaRule`
- `mapDoctypeElemRule`
- `doctypeParaRule`
- `doctypeElemRule`
- `paraRule`
- `charRule`
- `elementRule`

屬性規則的目的是管理匹配元素的屬性。

根據上下文，以下屬性可用於 `attributeRules` 元素：

- `@createID`:為匹配元素生成唯一ID。 允許的值 `true` 或 `false`。 可在所有上下文中使用。
- `@copyAll`:僅複製結構化源檔案的源XML內容中的所有屬性。 允許的值為 `true` 或 `false`。 可用於上下文 `mapDoctypeParaRule`。 `mapDoctypeElemRule`。 `doctypeElemRule` 和 `elementRule`。


中使用的屬性 `attributeRules` 如下：

>[!NOTE]
>
> 此元素可包含多個子元素。

- `addNew`:向匹配的元素添加新屬性。 可用於所有上下文。 它有兩個屬性：
   - `@name`:必須是合法的XML名稱，最好對DITA上下文有效。
   - `@value`:可以是文字文本或簡單的XPath表達式。
- `copyAtt`:將單個屬性複製到目標，同時可選地在進程中更名該屬性。 值未更改。 可用於上下文 `mapDoctypeParaRule`。 `mapDoctypeElemRule`。 `doctypeElemRule` 和 `elementRule`。 當此元素存在時 `@copyAllAtts` 假定值 `false`。 它有兩個屬性：
   - `@name`:必須是源XML元素上存在的屬性的名稱。
   - `@mapTo`:必須是合法的XML名稱，最好對DITA上下文有效。

**本地格式代碼**

在任何InDesign文檔中，段落樣式和字元樣式都可能包含數百種不同的格式覆蓋。 這些屬性中的大多數在轉換過程中沒有提供有用的角色。 但是，我們已經確定了一組核心的格式化特徵，這些特徵會影響文檔的語義，並且需要影響轉換過程。

的 `@local` 屬性以特殊的分隔格式顯示，其中提供八個欄位以及前置詞，以顯示格式覆蓋的類型。 下面列出了格式代碼欄位：

- 前置詞 **p** 對於段落樣式本地覆蓋或 **c** 用於字元樣式本地覆蓋。
- **字型樣式** 即族名和屬性，如「***粗斜體***「 」。
- **字型大小** 點。
- **字元位置** 上標或下標。
- **下** 的子菜單。
- **罷工** 為脫衣舞。
- **清單代碼** 將清單類型標識為項目符號或編號 — 不總是由InDesign使用。
- **項目符號代碼** 列出文檔中所有定義的項目符號類型。
- **編號代碼** 列出文檔中所有定義的編號樣式。

仔細使用此功能，否則會丟失本地格式有助於提高從樣式內容到DITA的傳輸質量。 此示例可解析為項目符號清單中16pt的「斜體」文本： `p[Italic|16|-|-|-|b|-|-]`。

**結構映射**

結構映射檔案類似於「樣式映射」檔案，其簡單結構列出了所有源元素和相關的屬性類型。 兩個屬性， `@map_date` 和 `@map_version` 提供用於記錄要使用的映射檔案的版本。

**文檔類型**

的 `doctypes` 元素列出了支援的DITA映射和主題映射。

**映射文檔類型元素規則**

的 `mapDoctypeElemRule` 元素是必需的。 不能編輯此元素的屬性，因為源XML的根元素始終映射到DITA映射的根 `map` 的子菜單。

**元素環繞規則**

**`elementRules`元素** 這列出了所有元素。

**`elementRule`元素** 的 `elementRule` 元素是必需的。 這些是所有源元素的映射規則。 雖然InDesign文檔確實包含非結構化樣式元素，但對於結構化內容，這些元素將被忽略，除非「 」***混合模式***&#39;處理已啟用。

中使用的屬性 `elementRule` 如下：

- `@elementName`:源InDesign文檔中元素的名稱。

- `@local`:請參閱 [\#id194CG0V005Z](#id194CG0V005Z)。 \（僅適用於混合文檔\）。

- `@mapTo`:DITA目標元素的名稱。

- `@refactor`:此可選屬性可以選擇兩個值：

   - `unwrap`:在保留其內容的同時刪除匹配的元素。

   - `drop`:匹配的元素及其所有內容都被刪除。

- `@context`:當有多個包裝選項可用時，此屬性用於連結到特定包裝規則。 示例：這樣 `li` 元素可以包裝在 `ol`或 `ul` 的子菜單。

- `@commentOut`:此屬性允許在XML注釋中包裝目標元素，這樣資訊不會丟失，但用戶可以手動處理。 如果源內容無法強制符合DITA結構規則，則此功能非常有用。


## 故障排除指AEM南

安裝及設定指南AEM後，您就可以排除故障。

## 驗證引用

您可以運行給定的指令碼來驗證引用。 這些指令碼可以幫助您識別損壞的引用，然後修補或修復它們。

- `/bin/fmdita/validatebtree?operation=validate`  — 報告任何損壞的內容引用，但不修復它們。
- `/bin/fmdita/validatebtree?operation=patch` — 列出損壞的內容引用和修補程式或修復它們。

**驗證指令碼**

使用產品包中可用的驗證指令碼，執行以下步驟檢查引用：

1. 運行驗證指令碼\[`/bin/fmdita/validatebtree?operation=validate`\]檢查是否有新的損壞引用。
1. 如果驗證指令碼報告任何錯誤，則可以使用修補程式指令碼對其進行修補。
1. 記錄以下給定的詳細資訊，並在必要時與客戶成功團隊共用這些資訊：
1. 
   - 通過驗證指令碼打印的日誌
- 「」的包`/content/fmdita/references`&quot;
- 根據報告的方案，任何其他所需詳細資訊

**修補程式指令碼**

使用產品包中提供的修補程式指令碼，執行以下步驟來修補任何損壞的引用：

1. 運行修補程式指令碼 `[/bin/fmdita/validatebtree?operation=patch]` 修復損壞的參照。 指令碼執行需要幾分鐘時間，並在執行過程中打印日誌。 執行完成後，將打印「`Done`最後。

   **注：* 建議您複製並保存日誌以供參考。

1. 成功執行修補程式指令碼後，可以執行以下檢查：
1. 
   - 檢查新節點「」`references_backup_<timestamp>"` 已建立 `/content/fmdita`
- 檢查參照是否已修復

**Logger**

您還可以根據下面提供的詳細資訊為此指令碼執行建立單獨的記錄器：

- 在類&#39;&#39;上添加記錄器`adobe.fmdita.common.BTreeReferenceValidator`&quot;
- 將其設定為 `DEBUG`

建立的日誌檔案將記錄與指令碼執行相關的所有資訊，在從瀏覽器觸發指令碼時，這些資訊在瀏覽器會話超時時非常有用。

