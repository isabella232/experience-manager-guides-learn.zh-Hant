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

InDesign為作者提供豐富的功能，用於建立吸引人且複雜的檔案。 這通常表示檔案的各個部分會以視覺化方式放置在頁面上，但不嘗試在這些文字框之間提供任何流量。 當&#39;*閱讀順序*&#x200B;未定義文字框的&#39;，IDML檔案會包含可能未依循任何有意義順序的內文。 最終結果將是一個或多個DITA主題，其中包含以隨機順序排列的段落、表格和圖形。

雖然可以在DITA編輯器中將DITA內容編輯成合理的順序，但在建立IDML檔案之前修正InDesign檔案會容易得多。 這可以在不改變來原始檔外觀的情況下完成。 透過正確定義閱讀順序，也可以存取來原始檔。

***串連文字框***

InDesign使用術語 *&#39;執行緒&#39;* 用於連結一個影格至另一個影格的程式。 如需串連文字框的詳細資訊，請參閱 *[執行緒文字](https://helpx.adobe.com/in/indesign/using/threading-text.html)* InDesign檔案中的主題。

***重疊影格***

有些InDesign檔案會基於版面配置原因而使用非執行緒的重疊框架。 可能很難將此內容合併到主對話串中。 最佳選項可能是在DITA環境中編輯結果。

***InDesign劇本***

InDesign檔案中的每個串連內容流都稱為&#39;*story*&#39;. 為達到最佳效果，建議限制劇本數量。 不過，DITA輸出中可能不需要檔案的某些部分。 例如，很少需要頁尾，但如果未小心處理，頁尾可能會出現在主題的中間。

排除檔案中不需要的文字最簡單的方法是賦予它特殊的 *段落標籤* 僅用於不需要的內容。 例如，不要重複使用 *\[基本段落\]* 對於頁尾，請建立專用的 *頁尾* 標籤之間。 然後在MapStyle檔案中，只要設定 *頁尾* 要捨棄的段落如下：

```XML
<paraRule style="Footer" local="0" refactor="drop">
   <attributeRules createID="false"/>
</paraRule>
```

***對應到DITA doctypes***

您的來原始檔至少必須有一個段落樣式或元素可以標籤主題的開頭。 檔案通常會使用 *標題1* 作為檔案中頂層標題的名稱。 然後，您可以建立從該樣式到特定DITA doctype的對應。 如果您的檔案井然有序，而且使用 *標題1* 是固定不變的，那麼您會獲得良好的結果。

***多個DITA檔案型別***

如果某些 *標題1* 段落需要轉換為不同的DITA檔案型別，然後複製InDesign的段落樣式。 為這些樣式提供易於辨識的名稱，例如 *Heading1\_genTask* 或 *標題1\_疑難排解* 視情況而定。 然後，設定mapStyle檔案，如下所示：

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

***結構化InDesign檔案***

InDesign與XML的關係不牢固。 雖然檔案可以包含XML DTD，且主要內文可能對該DTD有效，但也可以建立混合檔案，其中某些內容為XML，但不包含DTD。 這些是不希望成功轉換成DITA的情況。 如果檔案包含XML零件，請嘗試將輸出儲存為XML並檢視結果是否可接受。 如果沒有，則DITA內容也將包含無效的內容，或可能完全失敗。

***表格格式設定***

從DITA中的InDesign表格格式規則轉換為對等表格格式是一個複雜的過程。 這是因為與DITA中使用的Oasis \(CALS\)表格模型所提供的基本選項相比，來源檔案中提供了豐富的格式功能。 提供垂直和水平文字對齊方式，並且提供類似的結果，儘管「對齊」文字總是根據文字方向對齊，而「InDesign」允許「靠左對齊」和「靠右對齊」。

InDesign處理欄和列分隔符號的能力再次比Oasis表格模型的基本選項強大得多。 「InDesign」提供四個儲存格邊界 — 邊框型別\（實線或圖樣\）、邊框粗細、邊框顏色、邊框色調、邊框間隙顏色和邊框間隙色調。 所有這些都必須向下對應至每個儲存格右下方的框線\(entry element\)，其中唯一選項為0或1 — 隱藏框線或顯示框線。

InDesign的邊框規則可套用至下列層級：

- 表格樣式
- 儲存格樣式
- 每個儲存格上的本機覆寫

DITA轉換程式的InDesign會套用邊框規則，如下所示：

- 表格樣式會對應至 `colspec/@colsep` 垂直規則的屬性。 水準規則會對應至 `row/@rowsep` 屬性。 在這兩種情況下，如果未定義邊框，則不會建立屬性。
- 儲存格樣式會對應至 `entry/@colsep` 和 `entry/@rowsep` 屬性。 這些值將覆寫任何表格樣式衍生的邊框規則。
- 本機覆寫會將格式直接套用至儲存格，並覆寫表格樣式和儲存格樣式。

***交替圖樣***

「InDesign表格樣式」允許欄和儲存格的排版遵循交替模式。 雖然轉換支援此功能，但只有當一個圖樣群組對映至顯示直線\(1\)，而另一個圖樣群組對映至隱藏直線\(0\)時，結果才會明顯。

## 準備對應檔案以InDesign至DITA移轉 {#id194AF0003HT}

正確的DITA轉換需要符合來原始檔內容的對應檔案。 對於非結構化InDesign檔案，這表示所有可用的段落樣式和字元樣式都需要對應。 對於XML結構化InDesign檔案，其相關DTD中的所有元素都必須對應。

非結構化和結構化InDesign檔案的對應檔案不同。 這是因為將非結構化來源內容轉換為DITA的處理要求較為複雜。

以下提供對應檔案的範例：

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

對應檔案是結構簡單的XML檔案，列出所有原始段落樣式和字元樣式代碼。 檔案內容說明如下：

**樣式對應**

在 `styleMap` 元素，您可以指定兩個選擇性屬性 —  `@map_date` 和 `@map_version` 用於記錄對應檔案的版本。

**檔案型別**

此 `doctypes` 元素列出支援的DITA map和主題對應。

**對應檔案型別段落規則**

此 `mapDoctypeParaRule` 元素為必要專案。 不得編輯此元素的屬性，因為來源XML的根元素一律對應至DITA map的根 `map` 元素。

**檔案型別段落規則**

此 `doctypeParaRule` 元素為必要專案。 這可讓轉換程式識別新主題的開始。 通常 `@style` 屬性會單獨搭配使用， `@local` 屬性設為0。 但是，如果所選樣式上總是有區域性格式覆寫，則必須為每個樣式新增規則及其區域性覆寫。 在產生的對應檔案中，很容易辨識出可能找到以下或類似專案的位置：

```XML
<paraRule style="Heading 1" local="0" mapTo="p">
   <attributeRules createID="true"/>
</paraRule>
<paraRule style="Heading 1" local="p[Italic|-|-|-|-|-|-|-]" mapTo="p">
   <attributeRules createID="true"/>
</paraRule>
```

在上述範例中，有兩種 `paraRule` 下列專案元素： `@style` = &quot;Heading1&quot;。 只需建立對等專案 `doctypeParaRule` 元素和 `@mapToDoctype` 屬性集視需要。

中使用的屬性 `doctypeParaRule` 說明如下：

- `@style`：來源InDesign檔案中的樣式名稱。
- `@local`：請參閱 [\#id194CG0V005Z](#id194CG0V005Z).
- `@mapToDoctype`：所有有效列舉清單中的DITA主題型別名稱 `doctypes`.

**元素換行規則**

元素包裝規則會根據一組屬性值，定義將傳入檔案中的元素包裝或移動至預先定義元素的方法。

***`wrap`元素***

此為選用元素。 此 `wrap` element會列出要包裝或移動的元素。 換行通常用於必須為一系列元素指定通用父元素的情況。 例如，多個 `li` 包在中的元素 `ol` 元素。 此外， `wrap` 可用於移動元素，例如插圖和表格的標題。

中使用的屬性 `wrap` 說明如下：

- `@element`：元素名稱后的加號會顯示，名稱相同的所有相鄰元素都將包裝在 `@wrapper`屬性。
- `@wrapper`：包裝元素的名稱。
- `@context`：提供進一步調整指定元素包裝方式的方式。 以下範例說明對應一系列 `li` 已排序清單中的元素 `ol` 或無順序清單 `ul` 根據 `@context` 值\(內容定義於 `paraRule` element\)：

   ```XML
   <wrap elements="li+" context="number" wrapper="ol">
      <attributeRules createID="true"/>
   </wrap>
   <wrap elements="li+" context="bullet" wrapper="ul">
      <attributeRules createID="true"/>
   </wrap>
   ```


以下範例說明如何建立 `fig` 元素來自 `title` 和 `image` 元素：

- `@elements`：以逗號列出和分隔的元素將包裝在 `@wrapper` 屬性。 由於通常在影像下方包含圖形標題，標題會是 `title` 緊接在 `image`.

   以下換行規則：

   ```XML
   <wrap elements="title, image" context="FigTitle" wrapper="fig">
      <attributeRules createID="true"/>
   </wrap>
   ```

   轉換下列中繼XML：

   ```XML
   <image href="Links/myImage.png" scale="59">
      <title>IDML2DITA workflow</title>
   ```

   進入下列有效的DITA圖結構：

   ```XML
   <fig id="id397504">
      <title>IDML2DITA workflow</title>
      <image href="Links/myImage.png" scale="59">
   </fig>
   ```

- `@wrapper`：包裝元素的名稱。
- `@context`：提供進一步調整特定元素包裝方式的方法\(內容定義於 `paraRule` element\)。

下列範例說明如何移動 `title` 變成 `table`：

- `@elements`：此 `title` 元素之前或之後緊鄰的元素 `table` 將會包裝在名為的元素中， `@wrapper` 屬性。 XPath樣式述詞可將title元素的位置識別為 `[before]` 或 `[after]`.

   範例：以下換行規則：

   ```XML
   <wrap elements="title[before]" context="TableTitle" wrapper="table">
      <attributeRules createID="true"/>
   </wrap>
   ```

   轉換下列中繼XML：

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

- `@wrapper`：包裝元素的名稱。

- `@context`：提供進一步調整特定元素包裝方式的方法\(內容定義於 `paraRule` element\)。


**段落樣式規則**

此 `<paragraphStyleRule>` 元素說明如下：

***`paraRule`元素***

此 `paraRule` 元素為必要專案。 這會指定所有段落樣式的對應規則。 在InDesign檔案中，所有文字都包含在「段落樣式」的子結構中，即使沒有任何樣式的段落也被命名 `[No paragraph style]`. 方括弧，表示內建的InDesign樣式名稱。

>[!NOTE]
>
> 方括弧代表內建的InDesign樣式名稱。

中使用的屬性 `paraRule` 說明如下：

- `@style`：來源InDesign檔案中的樣式名稱。
- `@local`：請參閱 [\#id194CG0V005Z](#id194CG0V005Z).
- `@mapTo`：DITA目標元素的名稱。

- `@context`：此屬性用於連結至特定 **換行** 有多個包裝函式選擇可供使用時的規則。 範例： `li` 元素可以包在 `ol`，或 `ul` 元素。 若要識別不同的清單型別，您可以使用特定的樣式名稱或 `@local` 可顯示下列專案的屬性：
   - `local="p[-|-|-|-|-|b|-|-]"` 其中&#39;`b`&#39; （在欄位6中）表示專案符號清單專案。 在此案例中設定 `@context` 至&#39;`bullet`&#39;.
   - `local="p[-|-|-|-|-|n|-|-]"` 其中&#39;`n`&#39;在欄位6中表示編號清單專案。 在此案例中設定 `@context` 至&#39;`number`&#39;.

- `@commentOut`：此屬性可啟用目標元素在XML註解中的換行，因此資訊不會遺失，但使用者可手動處理。 如果來源內容無法強制符合DITA結構規則，這會很有用。

- `@refactor`：此選擇性屬性可選擇兩個值：

- `unwrap`：移除相符的元素，同時保留其內容。

- `drop`：相符的元素及其所有內容都會被移除。


**字元樣式規則**

此 `charRule` 元素說明如下：

>[!NOTE]
>
> 內建字元樣式沒有對應 `[No character style]` 時間 `local="0"`，因為這些物件會在預先處理期間移除。

***`charRule`元素***

此為選用元素。

這些是所有字元樣式的對應規則。 在InDesign檔案中，所有文字都包含在字元樣式的子元素中。

中使用的屬性 `charRule` 說明如下：

- `@style`：來源InDesign檔案中的樣式名稱。
- `@local`：請參閱 [\#id194CG0V005Z](#id194CG0V005Z).
- `@mapTo`：DITA目標元素的名稱。
- `@refactor`：此選擇性屬性可選擇兩個值：
   - `unwrap`：移除相符的元素，同時保留其內容。

   - `drop`：相符的元素及其所有內容都會被移除。


**屬性規則**

此元素可以是下列元素前後關聯的子項：

- `mapDoctypeParaRule`
- `mapDoctypeElemRule`
- `doctypeParaRule`
- `doctypeElemRule`
- `paraRule`
- `charRule`
- `elementRule`

屬性規則的用途是管理相符元素的屬性。

根據前後關聯，下列屬性可用於 `attributeRules` 元素：

- `@createID`：為相符的元素產生唯一識別碼。 允許的值 `true` 或 `false`. 可用於所有內容。
- `@copyAll`：僅從結構化來源檔案的來源XML內容複製所有屬性。 允許值為 `true` 或 `false`. 可用於前後關聯 `mapDoctypeParaRule`， `mapDoctypeElemRule`， `doctypeElemRule` 和 `elementRule`.


中使用的屬性 `attributeRules` 說明如下：

>[!NOTE]
>
> 此元素可包含多個子元素。

- `addNew`：將新屬性新增至相符的元素。 可用於所有前後關聯。 它有兩個屬性：
   - `@name`：必須是合法的XML名稱，最好對DITA內容有效。
   - `@value`：可以是常值文字或簡單的XPath運算式。
- `copyAtt`：將單一屬性複製到目標，但可選擇在此程式中重新命名。 值不會變更。 可用於前後關聯 `mapDoctypeParaRule`， `mapDoctypeElemRule`， `doctypeElemRule` 和 `elementRule`. 出現此元素時， `@copyAllAtts` 值假設為 `false`. 它有兩個屬性：
   - `@name`：必須是存在於來源XML元素上的屬性名稱。
   - `@mapTo`：必須是合法的XML名稱，最好對DITA內容有效。

**本機格式代碼**

在任何InDesign檔案中，段落樣式和字元樣式都可能包含數百種不同的格式覆寫。 這些屬性大多在轉換過程中不提供有用的角色。 不過，我們已找出一組會影響檔案語意且需要影響轉換程式的核心格式化功能。

此 `@local` 屬性會以特殊分隔格式顯示，其中有8個欄位連同前置詞一起提供，以顯示格式覆寫型別。 格式程式碼欄位列示如下：

- 前置詞 **p** 用於段落樣式本機覆寫或 **c** 用於字元樣式本機覆寫。
- **字型樣式** 這是家族名稱和屬性，例如&#39;***粗體緊縮斜體***&#39;.
- **字型大小** 以點為單位。
- **字元位置** （上標或下標）。
- **下** 底線。
- **刪除線** （刪除線）。
- **清單代碼** 將清單型別識別為專案符號或編號 — 並不一定由InDesign使用。
- **專案符號代碼** 列出檔案中所有已定義的專案符號型別。
- **編號代碼** 列出檔案中所有已定義的編號樣式。

謹慎使用此功能，否則會遺失本機格式設定，有助於改善將已設定樣式的內容轉移到DITA的品質。 此範例可解析為專案符號清單中表示斜體、16pt文字： `p[Italic|16|-|-|-|b|-|-]`.

**結構對應**

結構對應檔案類似於「樣式對應」檔案，其簡單結構會列出所有來源元素和相關屬性型別。 兩個屬性， `@map_date` 和 `@map_version` 提供來記錄要使用的對應檔案的版本。

**檔案型別**

此 `doctypes` 元素列出支援的DITA map和主題對應。

**對應檔案型別元素規則**

此 `mapDoctypeElemRule` 元素為必要專案。 不得編輯此元素的屬性，因為來源XML的根元素一律對應至DITA map的根 `map` 元素。

**元素換行規則**

**`elementRules`元素** 這會列出所有元素。

**`elementRule`元素** 此 `elementRule` 元素為必要專案。 這些是所有來源元素的對應規則。 雖然InDesign檔案確實包含非結構化樣式元素，但結構化內容會忽略這些元素，除非「***混合模式***&#39;處理已啟用。

中使用的屬性 `elementRule` 說明如下：

- `@elementName`：來源InDesign檔案中的元素名稱。

- `@local`：請參閱 [\#id194CG0V005Z](#id194CG0V005Z). \（僅適用於混合式檔案\）。

- `@mapTo`：DITA目標元素的名稱。

- `@refactor`：此選擇性屬性可選擇兩個值：

   - `unwrap`：移除相符的元素，同時保留其內容。

   - `drop`：相符的元素及其所有內容都會被移除。

- `@context`：有多個包裝函式選擇可供使用時，此屬性可用來連結至特定的包裝規則。 範例： `li` 元素可以包在 `ol`，或 `ul` 元素。

- `@commentOut`：此屬性可啟用目標元素在XML註解中的換行，因此資訊不會遺失，但使用者可手動處理。 如果來源內容無法強制符合DITA結構規則，這會很有用。


## 疑難排解AEM Guides

安裝並設定AEM Guides後，您就可以疑難排解問題。

## 驗證參考

您可以執行指定的指令碼來驗證參考。 這些指令碼可協助您識別中斷的參照，然後修補或修正它們。

- `/bin/fmdita/validatebtree?operation=validate`  — 會報告任何損壞的內容參照，但不會加以修正。
- `/bin/fmdita/validatebtree?operation=patch` — 列出中斷的內容參照和修補程式或修正程式。

**驗證指令碼**

使用產品套件中可用的驗證指令碼，執行以下步驟來檢查參考：

1. 執行驗證指令碼\[`/bin/fmdita/validatebtree?operation=validate`\]以檢查是否有任何新的中斷參照。
1. 如果驗證指令碼報告任何錯誤，您可以使用修補程式指令碼進行修補。
1. 紀錄以下提供的詳細資訊，並在必要時與客戶成功團隊分享：
1. 
   - 驗證指令碼列印的記錄
- 「 」的套件`/content/fmdita/references`&quot;
- 根據所報告案例的任何其他必要細節

**修補程式指令碼**

使用產品套件中提供的修補程式指令碼，執行下列步驟來修補任何中斷的參照：

1. 執行修補程式指令碼 `[/bin/fmdita/validatebtree?operation=patch]` 修復中斷的參照。 指令碼執行需要幾分鐘的時間，並會隨著進度列印記錄。 執行完成後，會列印&quot;`Done`」在結尾處。

   **注意：* 建議您複製並儲存記錄檔以供參考。

1. 順利執行修正程式指令碼後，您可以執行下列檢查：
1. 
   - 檢查新節點»`references_backup_<timestamp>"` 已建立於 `/content/fmdita`
- 檢查參考是否已修正

**Logger**

您也可以為此指令碼執行建立個別的記錄器，詳細資訊如下：

- 在類別&#39;&#39;上新增記錄器`adobe.fmdita.common.BTreeReferenceValidator`&quot;
- 設定為 `DEBUG`

建立的記錄檔將記錄與指令碼執行相關的所有資訊，並在瀏覽器工作階段逾時時從瀏覽器觸發指令碼時很有用。

