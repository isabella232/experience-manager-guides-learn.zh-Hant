---
title: 設定輸出產生設定
description: 瞭解如何設定輸出產生設定
exl-id: b5cf4f6c-dc56-428e-a514-6c9f879ac03d
source-git-commit: 22d364d28859e6aa3ae147a72b736669f56788b3
workflow-type: tm+mt
source-wordcount: '5340'
ht-degree: 1%

---

# 設定輸出產生設定 {#id181AI0B0E30}

AEM Guides隨附許多設定選項，供您自訂輸出產生程式。 本主題涵蓋可協助您設定輸出產生程式的所有設定和自訂。

## 在DITA map圖示板上設定基準線標籤 {#id223MD0D0YRM}

若要隱藏DITA map圖示板上的「基準線」標籤，請執行下列步驟：

1. 使用中提供的指示 [設定覆寫](download-install-additional-config-override.md#) 以建立組態檔。
1. 在組態檔中，提供下列\(property\)詳細資訊，以設定地圖圖示板上的基準線標籤。

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.config.ConfigManager` | `hide.tabs.baseline` | 布林值\(`true/false`\).**預設值**: `true` |

>[!NOTE]
>
> 預設會啟用此設定，且地圖控制面板上無法使用「基準線」標籤。

## 在現有AEM網站中設定混合發佈 {#id1691I0V0MGR}

如果您的AEM網站包含DITA內容，您可以設定AEM網站輸出，將DITA內容發佈至網站內預先定義的位置。 例如，在以下AEM Site頁面的熒幕擷圖中， `ditacontent` 節點已保留以儲存DITA內容：

![](assets/publish-in-aem-site.png)

頁面中的其餘節點會直接從AEM網站編輯器撰寫。 將發佈設定設為將DITA內容發佈至預先定義的位置，可確保不會由AEM Guides發佈程式修改任何現有的非DITA內容。

您需要在現有網站上執行下列設定，以允許將DITA內容發佈到預先定義的節點：

- 設定網站的範本屬性

- 在您的網站中新增節點以發佈DITA內容


執行以下步驟來設定您現有網站的範本屬性：

1. 使用封裝管理員來下載/libs/fmdita/config/templates/default檔案。

   >[!NOTE]
   >
   > 請勿讓預設組態檔案中的任何自訂功能可用於 `libs` 節點。 您必須建立 `libs` 中的節點 `apps` 節點並更新中 `apps` 僅限節點。

1. 新增下列屬性：

   | 屬性名稱 | 類型 | 值 |
   |-------------|----|-----|
   | `topicContentNode` | 字串 | 指定要發佈DITA內容的節點名稱。 例如，AEM Guides發佈DITA內容的預設節點為： <br> `jcr:content/contentnode` |
   | `topicHeadNode` | 字串 | 指定要儲存DITA內容的中繼資料資訊的節點名稱。 例如，AEM Guides儲存中繼資料資訊的預設節點為： <br> `jcr:content/headnode` |


下次當您使用網站的範本設定發佈任何DITA內容時，該內容會發佈到 `topicContentNode` 和 `topicHeadNode` 屬性。

## 自訂AEM網站輸出 {#id166TG0B30WR}

AEM Guides支援以下列格式建立輸出：

- AEM網站
- PDF
- HTML5
- ePub
- 透過DITA-OT自訂輸出

對於AEM Site輸出，您可以為不同的輸出任務指派不同的設計範本。 這些設計範本可以不同的版面配置呈現DITA內容。 例如，您可以為內部和外部對象指定不同的設計範本。

您也可以使用自訂的DITA Open Toolkit \(DITA-OT\)外掛程式搭配AEM Guides。 您可以上傳這些自訂DITA-OT外掛程式，以特定方式產生PDF輸出。

>[!TIP]
>
> 請參閱 *AEM網站發佈* 區段，以取得建立AEM網站輸出相關的最佳實務。


### 自訂設計範本以產生輸出 {#customize_xml-add-on}

AEM Guides使用一組預先定義的設計範本來產生AEM Site輸出。 您可以自訂AEM Guides設計範本，以產生符合您公司品牌的輸出結果。 設計範本是各種樣式\(CSS\)、指令碼\（伺服器端和使用者端\）、資源\（影像、標誌和其他資產\）以及將所有這些資源繫結在一起的JCR節點的集合。 設計範本可以像單一伺服器端指令碼一樣簡單，只包含幾個JCR節點，或樣式、資源和JCR節點的複雜組合。 AEM Guides發佈子系統會在產生AEM Site輸出時使用設計範本，這些範本可控制所產生輸出的結構、外觀和風格。

設計範本資源在伺服器上的放置位置沒有限制，但通常會根據其功能進行邏輯組織。 例如，預設範本的所有JavaScript和CSS檔案都儲存在 `/etc/designs/fmdita/clientlibs/siteoutput/default` 資料夾。 無論這些檔案位於何處，都會由JCR節點集合連結在一起。 這些JCR節點和檔案共同構成了整個設計範本。

AEM Guides隨附的預設設計範本可讓您自訂登陸、主題和搜尋頁面元件。 您可以複製預設設計和對應的參照範本，並指定不同的元件以產生所需的輸出。

執行以下步驟，指定您自己的設計範本，以用於AEM Site輸出產生：

1. 使用「封裝管理員」從下列位置下載預設設計範本：

   /libs/fmdita/config/templates

1. 在Cloud Manager的Git存放庫中的以下位置建立已下載檔案的副本：

   /apps/fmdita/config/templates

1. 您也必須下載並複製從預設範本節點參照的範本。 參照的範本放置在：

   /libs/fmdita/templates/default/cqtemplates

   下表說明AEM Guides設計範本的屬性。

   | 屬性 | 說明 |
   |--------|-----------|
   | `landingPageTemplate`, `searchPageTemplate`, `topicPageTemplate`, `shadowPageTemplate` | 指定 `cq:Template` 這些對應頁面的節點\（登陸、搜尋和主題\）。 根據預設 `cq:Template` 這些頁面的節點可在以下位置找到： `/libs/fmdita/templates/default/cqtemplates` 節點。 此節點會定義登陸、搜尋和主題頁面的結構和屬性。<br> 此 `shadowPageTemplate` 用於最佳化區塊內容。 您必須將此屬性的值設為： `fmdita/templates/default/cqtemplates/shadowpage` <br> **注意：** 您必須指定 `topicPageTemplate`. 此 `landingPageTemplate` 和 `searchPageTemplate` 是選用屬性。 如果您不想產生搜尋和登入頁面，請勿指定這些屬性。 |
   | `title` | 設計範本的描述性名稱。 |
   | `topicContentNode` | 將在主題頁面中包含DITA內容的節點位置。 路徑是相對於主題頁面的路徑。 |
   | `topicHeadNode` | 節點的位置，此節點將包含衍生自DITA內容的head值\（或metadata\）。 路徑是相對於主題頁面的路徑。 |
   | `tocNode` | 包含目錄的節點位置。 路徑是相對於登陸頁面或目的地路徑的。 |
   | `basePathProp` | 用來儲存已發佈網站根目錄路徑的屬性名稱。 |
   | `indexPathProp` | 用於儲存已發佈網站之登陸/索引頁面路徑的屬性名稱。 |
   | `pdfPathProp` | 儲存主題PDF路徑的屬性名稱(如果已啟用主題PDF產生)。 |
   | `pdfTypeProp` | 用於儲存PDF產生型別的屬性名稱。 目前此屬性一律包含「主題」。 |
   | `searchPathProp` | 儲存搜尋頁面路徑的屬性名稱（如果範本包含搜尋頁面）。 |
   | `siteTitleProp` | 用來儲存發佈之網站標題的屬性名稱。 此標題通常與正在發佈的地圖的標題相同。 |
   | `sourcePathProp` | 用來儲存目前頁面之來源DITA主題之路徑的屬性名稱。 |
   | `tocPathProp` | 用於儲存已發佈站台TOC根目錄路徑的屬性名稱。 |


>[!NOTE]
>
> 建立自訂設計範本節點後，您必須更新AEM Site輸出預設集中的「設計」選項才能使用自訂設計範本節點。

如需詳細資訊，請參閱 [建立您的第一個Adobe Experience Manager網站](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=en) 和 [基本資訊](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/full-stack/develop-wknd-tutorial.html?lang=en) 在AEM上開發您自己的網站。

### 使用檔案標題來產生AEM網站輸出

產生AEM Site輸出時，產生URL的方式在內容的可發現性方面扮演重要角色。 如果您使用UUID型檔案名稱，根據檔案的UUID產生URL將不利於搜尋。 身為管理員或發佈者，您可以控制要如何產生AEM Site輸出的URL。 AEM Guides提供設定，您可選擇使用檔案標題而非UUID型檔案名稱來產生AEM Site輸出的URL。 對於以UUID為基礎的檔案系統，此選項預設為開啟。 這表示當您產生UUID型檔案系統的AEM Site輸出時，會使用檔案的標題來產生URL，而非檔案的UUID。

>[!NOTE]
>
> 您可以進一步設定規則，以僅允許AEM Site輸出的URL中的一組字元。 如需詳細資訊，請參閱 [設定檔案名稱清理規則，以建立主題和發佈AEM網站輸出](#id2164D0KD0XA).

使用中提供的指示 [設定覆寫](download-install-additional-config-override.md#) 以建立組態檔。 在設定檔案中，提供下列\(property\)詳細資訊，以設定AEM Site輸出中的URL產生：

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.config.ConfigManager` | `aemsite.pagetitle` | 布林值\(true/false\)。 如果您想使用頁面標題產生輸出，則將此屬性設定為true。 預設會設定為使用檔案名稱。<br> **預設值**： false |

### 設定檔案名稱清理規則，以建立主題和發佈AEM網站輸出 {#id2164D0KD0XA}

作為管理員，您可以定義檔案名稱中允許的有效特殊字元清單，這些字元最終會形成AEM Site輸出的URL。 在舊版中，使用者可定義包含特殊字元的檔案名稱，例如 `@`， `$`， `>`、等等。 這些特殊字元會在產生AEM網站頁面時產生編碼的URL。

自3.8發行版本開始，已新增設定以定義檔案名稱中允許的特殊字元清單。 依預設，有效的檔案名稱設定包含&quot;`a-z A-Z 0-9 - _`「。 這表示在建立檔案時，檔案標題中可以有任何特殊字元，但在內部會以連字型大小取代\(`-`\)的檔案名稱。 例如，您可以將檔案的標題設為Introduction 1或Introduction@1，針對這兩種情況產生的對應檔案名稱都是Introduction-1。

定義有效字元清單時，請記得這些字元»`*/:[\]|#%{}?&<>"/+`」和 `a space` 將一律以連字型大小取代\(`-`\)。

>[!NOTE]
>
> 如果您未設定有效的特殊字元清單，檔案建立程式可能會為您提供一些未預期的結果。

使用中提供的指示 [設定覆寫](download-install-additional-config-override.md#) 以建立組態檔。 在設定檔案中，提供下列\(property\)詳細資訊，以便在檔案名稱和AEM Site輸出中設定有效的特殊字元：

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.common.SanitizeNodeNameImpl` | `aemsite.DisallowedFileNameChars` | 確認屬性已設為 ``'<>`@$``. 您可以在此清單中新增更多特殊字元。 |

您也可以設定其他屬性，例如檔案名稱中的使用小寫、處理無效字元的分隔符號，以及檔案名稱中允許的最大字元數。 若要設定這些屬性，請在設定檔案中新增下列機碼值組：

| 屬性索引鍵 | 屬性值 |
|------------|--------------|
| `nodename.uselower` | 布林值\(true/false\)。<br> **預設值**： true |
| `nodename.separator` | 任何字元。 <br> **預設值**： \_ *\（底線\）* |
| `nodename.maxlength` | 整數值。<br> **預設值**：50 |

### 設定AEM網站節點結構的平面化

產生AEM Site輸出時，主題中每個元素的節點都會在內部建立。 對於包含數千個主題的DITA map，此節點結構可能會變得太深。 對於較大的網站，這種深度巢狀節點結構可能會出現效能問題。 下列快照會顯示AEM Site輸出的深度巢狀節點結構：

![](assets/deep-nested-aem-site-node-structure.png)

在上述快照中，請注意每個都會建立一個節點， `p` 元素及其後續子元素和類似結構會針對主題中使用的其他所有元素而建立。

AEM Guides可讓您設定AEM Site輸出的節點結構在內部建立的方式。 您可以在指定元素處平面化節點結構，這表示您可以定義元素，將其視為主要元素，其內的所有子元素將與主要元素合併。 例如，如果您決定將 `p` 元素，然後出現在 `p` 元素將會與主要 `p` 元素。 系統不會為中的任何子元素建立單獨的附註。 `p` 元素。 下列快照顯示展平於的節點結構 `p` 元素：

![](assets/flattened-aem-site-node-structure.png)

若要平面化AEM Site節點結構，請執行下列步驟：

1. 識別您要平面化節點結構的元素：

1. 覆蓋 `libs` 中的節點 `apps` 節點並開啟elementmapping.xml檔案。

1. 新增 `<flatten>true</flatten>` 屬性（在您要平面化節點結構的元素定義中）。 例如，如果您想將節點結構平面化於 `p` 元素，然後將flatten屬性新增至的定義中 `p` 元素如下所示：

   ```XML
   <ditaelement>
         <name>p</name>
         <class>- topic/p</class>
         <componentpath>fmdita/components/dita/wrapper</componentpath>
         <type>COMPOSITE</type>
         <target>para</target>
         <flatten>true</flatten>
         <wrapelement>div</wrapelement>
      </ditaelement>
   ```

   >[!NOTE]
   >
   > 根據預設，flatten node屬性設定在 `p` 元素。

1. 使用中提供的指示 [設定覆寫](download-install-additional-config-override.md#) 以建立組態檔。
1. 在設定檔中，提供下列\(property\)詳細資料：

   | PID | 屬性索引鍵 | 屬性值 |
   |---|------------|--------------|
   | `com.adobe.dxml.flattening.FlatteningConfigurationService` | `flattening.enabled` | 布林值\(true/false\)。<br> **預設值**: `false` |


現在，當您產生AEM Site輸出時， `p` 元素會平面化並儲存在 `p` 元素本身。 您可以找到新的平面化屬性 `p` CRXDE中的元素。

![](assets/flatten-aem-site-note-props-crxde.png)

**在AEM Site輸出的內容中搜尋字串**

依預設，您只能在AEM Site輸出中搜尋標題中的字串。 您可以設定系統以搜尋字串，同時搜尋標題以及AEM Site輸出的內容或內文。

>[!NOTE]
>
> 有時您的搜尋可能適用於內容中的某些元素，但您可以將其設定為適用於整個內容。

![](assets/flatten-aem-site-note-props-crxde-search.png)

若要啟用搜尋，您應該設定AEM Site節點結構的平面化。

注意:

您最多可以搜尋1MB的平面化內容。 例如，在上一個熒幕擷圖中，您可以搜尋下方的內容 &lt;p> 標籤小於= 1Mb。

>[!NOTE]
>
> 只有在符合以下條件時，搜尋才會對元素生效： `<flatten>`屬性設為true。 依預設，AEM Guides具有 `<flatten>` 對於常用的文字元素，例如屬性，設定為true &lt;p> &lt;ul> &lt;li>. 不過，如果您已建立一些自訂元素，則應設定 `<flatten>` attribute為true。

**防止AEM網站節點結構平面化**

與在AEM Site輸出中指定要平面化的節點類似，您也可以指定要從此設定中排除的元素。 例如，如果您想將節點平面化於 `body` 元素，但您不想要任何 `table` 元素在內 `body` 若要平面化，您可以在 `table` 元素的定義。

若要排除 `table` 將元素平面化，將下列屬性新增至 `table` 元素的定義：

`<preventancestorflattening>true|false</preventancestorflattening>`

### 在AEM網站輸出中設定已刪除頁面的版本設定

當您使用產生AEM Site輸出時 **刪除和**&#x200B;建立&#x200B;****為「現有輸出頁面」設定選取的選項，會為要刪除的頁面建立版本。 您可以設定系統在刪除前停止建立版本。

執行以下步驟，停止建立要刪除之頁面的版本：

1. 使用中提供的指示 [設定覆寫](download-install-additional-config-override.md#) 以建立組態檔。
1. 在設定檔案中，提供下列\(property\)詳細資料以設定 **不要建立已刪除頁面的版本** 選項：

   | PID | 屬性索引鍵 | 屬性值 |
   |---|------------|--------------|
   | `com.adobe.fmdita.confi g.ConfigManager` | `no.version.creation.on.deletion` | 布林值\(true/false\)。<br> **預設值**: `true` |

   >[!NOTE]
   >
   > 選取此選項後，使用者可直接刪除任何頁面，而不需為其建立任何版本。 如果未選取選項，則會在刪除頁面之前建立版本。

### 使用Experience Manager指南設定自訂重寫程式 {#custom-rewriter}

「Experience Manager指南」有自訂Sling [**重寫程式**](https://sling.apache.org/documentation/bundles/output-rewriting-pipelines-org-apache-sling-rewriter.html) 用於處理交叉地圖情況下產生的連結的模組（兩個不同地圖主題之間的連結）。 此重寫程式組態會安裝在下列路徑： <br> `/apps/fmdita/config/rewriter/fmdita-crossmap-link-patcher`。

如果您的程式碼基底中有另一個自訂Sling重寫程式，請使用 `'order'` 值大於50，因為Experience Manager指南sling重寫程式使用 `'order'` 50.  若要覆寫此值，您需要大於50的值。 如需詳細資訊，請檢視 [輸出重寫管道](https://sling.apache.org/documentation/bundles/output-rewriting-pipelines-org-apache-sling-rewriter.html).


## 透過DITA-OT在發佈輸出中使用中繼資料 {#id191LF0U0TY4}

AEM Guides提供在使用DITA-OT發佈輸出時傳遞自訂中繼資料的方法。 作為管理員和發佈者，您需要執行以下任務以在發佈輸出中設定和使用自訂中繼資料：

- 以管理員身分，在系統中新增必要的中繼資料，使其可在DITA map的「屬性」頁面上使用。

- 作為管理員，在中繼資料清單中新增自訂中繼資料，使其顯示在DITA map主控台中。

- 作為發行者，使用DITA map設定並新增自訂中繼資料，並產生所需的輸出。


若要在系統中新增必要的中繼資料，請執行下列步驟：

1. 以管理員身分登入Adobe Experience Manager。

1. 按一下頂端的Adobe Experience Manager連結，然後選擇 **工具**.

1. 選取 **資產** 工具清單中。

1. 按一下 **中繼資料結構** 圖磚。

   此時會顯示「中繼資料結構描述表單」頁面。

1. 選取 **預設** 從清單中移除。

   >[!NOTE]
   >
   > DITA map的「屬性」頁面上顯示的屬性取自此表單。

1. 按一下 **編輯**.

1. 新增您要在發佈的輸出中使用的自訂中繼資料。 例如，我們將使用下列步驟新增對象中繼資料：

   1. 從 **建置表單** 元件清單，拖放 **單行文字** 元件至表單。

   2. 選取新欄位以開啟 **設定** 欄位的。

   3. 在 **欄位標籤**，輸入中繼資料名稱 — Audience。

   4. 在 **對應至屬性** 設定，指定。/jcr：content/metadata/&lt;name of=&quot;&quot; the=&quot;&quot; metadata=&quot;&quot;>. 例如我們的範例，我們將其設為。/jcr：content/metadata/audience。

   使用這些步驟，新增所有必要的中繼資料引數。

1. 按一下「**儲存**」。


現在，所有DITA map的「屬性」頁面中都會顯示新引數。

![](assets/properties-page-custom-metadata.PNG)

接下來，您需要在DITA map主控台中提供自訂中繼資料。 執行下列步驟，讓自訂中繼資料可在DITA map虛線板上使用：

1. 使用套件管理器存取metadataList檔案，該檔案可在您的Cloud Manager Git存放庫中的以下位置找到：

   /libs/fmdita/config/metadataList

   >[!NOTE]
   >
   > metadataList檔案包含顯示在 **屬性** 地圖儀表板中DITA map的下拉式清單。 依預設，此檔案中列出四個屬性：docstate、dc：language、dc：description和dc：title。

1. 新增您在中繼資料結構Forms頁面中新增的自訂中繼資料。 例如，將對象引數新增至預設清單的結尾。


現在，自訂中繼資料會顯示在DITA map主控台的 **屬性** 下拉式清單。

最後，身為「發佈者」，您需要在發佈的輸出中包含自訂中繼資料。 若要在產生輸出時處理自訂中繼資料，請執行下列步驟：

1. 在Assets UI中，導覽至您要發佈的DITA map。

1. 選取DITA map檔案並開啟其屬性頁面。

1. 在「屬性」頁面上，指定自訂中繼資料的值。 例如，我們為對象引數指定了External值。

   ![](assets/properties-page-custom-metadata-value.png)

1. 按一下&#x200B;**「儲存並關閉」**。

1. 按一下DITA map檔案以開啟DITA map主控台。

1. 在 **輸出預設集** 索引標籤上，選取您要用來產生輸出的輸出預設集。

1. 按一下 **編輯**.

1. 從 **屬性** 從下拉式清單中，選取您要傳遞給發佈程式的屬性。

   ![](assets/props-in-publish-output.PNG)


選取的屬性/中繼資料會傳遞至發佈程式，並可在最終輸出中使用。

### 驗證傳遞至DITA-OT以進行處理的中繼資料

為了驗證傳遞至DITA-OT的中繼資料值，可以使用使用雲端就緒jar的本機環境。 由於我們無法在雲端上存取本機檔案系統，因此驗證中繼資料檔案的唯一方式是透過雲端就緒的jar。

- 檔案名稱： metadata.xml
- 檔案位置： crx-quickstart/profiles/ditamaps/&lt;ditamap-1234>

  若要存取metadata.xml：

   - 登入執行AEM執行個體的伺服器位置。
   - 移轉至crx-quickstart/profiles/ditamaps/&lt;newly-created-directory-name>/metadata.xml.
- 範例檔案格式：

  **metadata.xml**

  ```XML
  <?xml version="1.0" encoding="UTF-8" standalone="no"?>
  <root>
     <Path id="/absolutePath/sampleMap.ditamap">
        <metadata>
           <meta isArray="false" key="dc:description">This is a file</meta>
           <meta isArray="false" key="dc:title">Myfile</meta>
           <meta isArray="true" key="multivalueText">One;Two;Three</meta>
        </metadata>
     </Path>
     <Path id="/absolutePath/sampleTopic.dita">
        <metadata>
           <meta isArray="false" key="dc:description">description for the accountability</meta>
           <meta isArray="false" key="dc:title">accountability title</meta>
           <meta isArray="true" key="multivalueText">value1</meta>
        </metadata>
     </Path>
  </root>
  ```


- isArray：布林屬性，定義中繼資料是否為多值\(Array\)。 值以分號分隔。
- 路徑ID：暫時目錄下所儲存檔案的絕對路徑。

>[!NOTE]
>
> 如果檔案不存在特定的中繼資料， &lt;meta> 含有索引鍵的標籤不會在metadata.xml檔案中顯示為該檔案的屬性。

## 使用AEM元件自訂DITA元素對應 {#id1679J600HEL}

AEM Guides中的DITA元素會對應至其對應的AEM元件。 AEM Guides在工作流程（例如發佈和稽核）中使用此對應，將DITA元素轉換為對應的AEM元件。 該對應定義於 `elementmapping.xml` 檔案，可使用封裝管理員進行存取。

>[!NOTE]
>
> 請勿讓預設組態檔案中的任何自訂功能可用於 ``libs`` 節點。 您必須建立 ``libs`` 中的節點 ``apps`` 節點並更新中 ``apps`` 僅限節點。

您可以使用預先定義的DITA元素對映，也可以將DITA元素對映至自訂AEM元件。 若要使用自訂AEM元件，您必須瞭解 `elementmapping.xml` 檔案。

### elementmapping.xml結構

概略說明 `elementmapping.xml` 結構說明如下：

1. 系統會根據元素名稱，先搜尋每個DITA元素以尋找對應的元件對應。 例如：

   ```XML
   <ditaelement>     
      <name>**substeps**</name>  
      <class>- topic/ol task/substeps</class>  
      <componentpath>dita/components/ditaolist</componentpath>  
      <type>COMPOSITE</type>  
      <target>para</target>
   </ditaelement>
   ```

   在上述範例中，所有 `substeps` DITA元素會使用 `dita/components/ditaolist` 元件。

1. 如果DITA元素找不到以名稱為依據的相符專案，則會找到以名稱為依據的相符專案。 `class` 已完成。 例如：

   ```XML
   <ditaelement>  
      <name>topic</name>  
      <class>**- topic/topic**</class>  
      <componentpath>fmdita/components/dita/topic</componentpath>  
      <type>COMPOSITE</type>  
      <target>para</target>  
      <attributemap> 
         <attribute from="id" to="id" />  
      </attributemap>
   </ditaelement>
   ```

   在上述範例中，如果沒有為定義對應 `task` 元素，然後 `task` 元素對應至上述元件，因為 `task` 繼承自 `topic` 元件。

1. 當元素具有對應的元件對應時，其子元素的進一步處理由決定 `type`. 例如：

   ```XML
   <ditaelement>  
      <name>title</name>  
      <class>- topic/title</class>  
      <componentpath>foundation/components/title</componentpath>  
      <type>**STANDALONE**</type>  
      <target>para</target>  
      <textprop>jcr:title</textprop>
   </ditaelement>
   ```

   `type` 會採用下列值：

   - COMPOSITE：元素至元件 *子元素的對應仍會繼續進行* 以及。

   - STANDALONE：目前元素的子元素為 *未進一步對應*.

   在上述範例中，如果 `<title>` 元素具有任何子元素，不會對應至任何其他元件。 的元件 `<title>` 元素負責呈現內的所有子元素 `<title>` 元素。

1. 如果有多個元件對應至單一DITA元素，則會選取該元素的最佳相符專案。 若要選取最佳相符元件，會考慮DITA元素的領域和結構專門化。

   如果有具有領域專門化的DITA元素，且元件對應到領域專門化，則該元件會獲得高優先順序。

   同樣地，如果有具有結構專門化的DITA元素，且元件對應結構專門化，則該元件會獲得高優先順序。

1. 您可以使用 `<attributemap>` 元素對應，將屬性值對應至對應的節點屬性。
1. `textprop` 可用來將DITA元素的文字內容序列化為node屬性。 此外，它可以在元素標籤中多次使用，以將已發佈階層中多個位置的文字內容序列化。 您也可以自訂目標屬性的位置和名稱。 例如：

   ```XML
   <ditaelement>
      <name>title</name>
      <componentpath>foundation/components/title</componentpath>
      <type>STANDALONE</type>
      <target>para</target>
       <textprop>**jcr:title**</textprop>
   </ditaelement>
   ```

   上述元素對應會指定 `<title>` 元素將儲存為下列屬性的值： `jcr:title` 在輸出節點上。

1. `xmlprop` 可用來將指定元素的整個XML序列化為node屬性。 元件將可讀取此節點屬性並執行自訂轉譯。 例如：

   ```XML
   <ditaelement>
       <name>svg-container</name>
      <class>+ topic/foreign svg-d/svg-container</class>
       <componentpath>fmdita/components/dita/svg</componentpath>
       <type>STANDALONE</type>
       <target>para</target>
      <xmlprop>**data**</xmlprop>
   </ditaelement>
   ```

   上述元素對應會指定元素的整個XML標籤 `<svg-container>` 將儲存為下列屬性的值： `data` 在輸出節點上。

1. 有一個特殊的屬性對應，可在輸出產生程式中處理路徑解析。 例如：

   ```XML
   <attributemap>
      <attribute from="href" to="fileReference" ispath="true" rel="source" />
      <attribute from="height" to="height" />
       <attribute from="width" to="width" />
   </attributemap>
   ```

   對於上述專案 `attributemap`，則 `href` DITA元素中的屬性將對映至名為的節點屬性 `fileReference`. 現在開始於 `ispath` 設為 `true`，輸出產生程式會解析此路徑，然後將其設定在 `fileReference` 節點屬性。

   此解析度的發生方式是根據 `rel` 屬性對應中的屬性。

   - 如果 `rel=source`，然後值 `href` 相對於目前處理中的DITA來源檔案來解析。 的值 `href` 解析並放置在的值中 `fileReference` 屬性。

   - 如果 `rel=target`，然後值 `href` 已相對於根發佈位置來解析。 的值 `href` 解析並放置在的值中 `fileReference` 屬性。

   如果您不希望路徑屬性上發生任何預先處理或解析，則不需要指定 `ispath` 屬性。 值會依原樣複製，元件可執行所需的解析度。


### DITA元素結構描述

以下為中的DITA元素結構描述範例 `elementmapping.xml` 檔案：

```XML
<ditaelement>        
    <name>element_name</name>    
    <class>element_class</class>    
    <componentpath>fmdita/components/dita/component_name</componentpath>    
    <type>COMPOSITE|STANDALONE</type>     
    <attributeprop>propname_a</attributeprop>      
    <textprop>propname_t</textprop>    
    <xmlprop>propname_x</xmlprop>     
    <xpath>xpath expression string</xpath>     
    <target>head|para</target>     
    <wrapelement>div</wrapelement>     
    <wrapclass>class_name</wrapclass>     
    <attributemap>         
        <attribute from="attrname"         to="propname"         ispath="true|false"         rel="source|target" />    
    </attributemap>    
    <skip>true|false</skip> 
</ditaelement>
```

下表說明DITA元素結構描述中的元素：

| 元素 | 說明 |
|-------|-----------|
| `<ditaelement>` | 每個對應元素的頂層節點。 |
| `<class>` | 您正在寫入元件的目標DITA元素的類別屬性。<br> 例如，DITA主題的class屬性為： <br> `- topic/topic` |
| `<componentpath>` | 對應AEM元件的CRXDE路徑。 |
| `<type>` | 可能的值：<br> -   **複合**：也會處理子元素 <br> -   **獨立**：略過子元素的處理 |
| `<attributeprop>` | 用於將序列化DITA屬性和值作為屬性對應至AEM節點。 例如，如果您擁有 `<note type="Caution">` 元素且針對此元素對應的元件具有 `<attributeprop>attr_t</ attributeprop>`，則節點的屬性和值會序列化為 `attr_t` 對應AEM節點的屬性\( `attr_t->type="caution"`\)。 |
| `<textprop>propname_t</textprop>` | 儲存 `getTextContent()` 輸出至由定義的屬性 `propname_t.` <br> **注意：** 這是最佳化的屬性。 |
| `<xmlprop>propname_x </xmlprop>` | 將此節點的序列化XML儲存至所定義的屬性 `propname_x.<br> `**注意：** 這是最佳化的屬性。 |
| `<xpath>` | 如果在元素對應中提供了XPath元素，則應該連同元素名稱和類別一起滿足XPath條件，才能使用元件對應。 |
| `<target>` | 將DITA元素放置在crx存放庫中的指定位置。<br> 可能的值： <br> - **head**：在head節點下 <br> - **文字**：在段落節點下 |
| `<wrapelement>` | 包住內容的HTML元素。 |
| `<wrapclass>` | 屬性的元素值 `wrapclass.` |
| `<attributemap>` | 包含一或多個的容器節點 `<attribute>` 節點。 |
| `<attribute from="attrname" to="propname" ispath="true|false" rel="source|target" />` | 將DITA屬性對應至AEM屬性： <br> -   **`from`**： DITA屬性名稱 <br> -   **`to`**：AEM元件屬性名稱 <br> -   **`ispath`**：如果屬性是路徑值\(例如： *影像*\) <br> -   **`rel`**：如果路徑是來源或目標 <br> **注意：** 如果 `attrname` 開頭為 `%`，然後地圖 `attrname minus '%'` 至prop ` `propname`&#39;. |

**其他附註**

- 如果您計畫覆寫預設要素對應，建議您不要在預設值中進行變更 `elementmapping.xml` 檔案。 您應該建立新的對應XML檔案，並將檔案放置於其他位置，最好是放在您建立的自訂應用程式資料夾內。

- 在 `elementmapping.xml` 檔案中，有許多對應專案會參照fmdita/components/dita/wrapper元件。 包裝函式是一種泛型元件，會使用其網站節點上的屬性來產生相關HTML，以呈現相對簡單的DITA建構。 它會使用 `wrapelement` 屬性以產生封閉標籤，並將子轉譯委派給對應的元件。 當您只想要容器元件時，這個用法就相當實用。 不要建立可轉譯特定容器標籤的新元件，例如 `div` 或 `p`，您可以將包裝函式元件搭配 `wrapelement` 和 `wrapclass` 屬性以獲得相同的效果。

- 不建議在字串JCR屬性中儲存大量文字。 輸出產生中最佳化的屬性型別計算可確保大型文字內容不會儲存為字串型別。 反之，當需要儲存大於某個臨界值的內容時，屬性的型別會變更為二進位。 預設會將此臨界值設定為512位元組，但可在Configuration Manager \(*com.adobe.fmdita.config.ConfigManager*\)透過變更 **另存為二進位臨界值** 設定。

- 如果您計畫覆寫部分\（而非全部\）元素對應，則不需要復寫整個 `elementmapping.xml` 檔案。 您需要建立新的XML對應檔案，並只定義要覆寫的元素。

- 在自訂位置中建立XML檔案之後，請更新 `Override Element Mapping` 在中設定 `com.adobe.fmdita.config.ConfigManager` 套件組合。


## 自訂DITA map主控台 {#id188HC08M0CZ}

AEM Guides可讓您彈性擴充DITA map主控台的功能。 例如，如果您有一組與AEM Guides中可用的報表不同，您可以將這類報表新增至地圖主控台。 若要自訂對應主控台，您必須建立AEM使用者端程式庫\（或ClientLib\），其中包含執行所需功能的程式碼。

>[!NOTE]
>
> 不建議直接修改頁面元件，因為產品的新版本會加以覆寫。

AEM指南提供 `apps.fmdita.dashboard-extn` 用於自訂地圖主控台的類別。 每當載入地圖主控台時，在 `apps.fmdita.dashboard-extn` 類別會執行並載入。

>[!NOTE]
>
> 如需建立AEM使用者端資料庫的詳細資訊，請參閱 [使用使用者端資料庫](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/full-stack/clientlibs.html?lang=en).

## 在產生輸出期間處理影像轉譯 {#id177BF0G0VY4}

AEM隨附一組預設工作流程和媒體控制代碼以處理資產。 在AEM中，有預先定義的工作流程可處理最常見MIME型別的資產處理。 一般而言，AEM會針對您上傳的每個影像，以二進位格式建立相同的多個轉譯。 這些轉譯可能大小不同、解析度不同、加上浮水印或其他已變更的特性。 如需AEM如何處理資產的詳細資訊，請參閱 [使用媒體處理常式和工作流程處理資產](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/asset-microservices-overview.html?lang=en) 在AEM檔案中。

AEM Guides可讓您設定在為檔案產生輸出時要使用的影像轉譯。 例如，您可以選擇其中一個預設影像轉譯，或建立並使用相同的影像轉譯來發佈檔案。 用於發佈檔案的影像轉譯對應會儲存在 `/libs/fmdita/config/ **renditionmap.xml**` 檔案。 片段 `renditionmap.xml` 檔案如下：

>[!NOTE]
>
> 建議您建立 `renditionmap.xml` 中的檔案 `apps` 所有自訂的資料夾。

```XML
<renditionmap>
   <mapelement>
      <mimetype>image/png</mimetype>
      <rendition output="AEMSITE">cq5dam.web.1280.1280.jpeg</rendition>
      <rendition output="PDF">original</rendition>
      <rendition output="HTML5">cq5dam.web.1280.1280.jpeg</rendition>
      <rendition output="EPUB">cq5dam.web.1280.1280.jpeg</rendition>
      <rendition output="CUSTOM">cq5dam.web.1280.1280.jpeg</rendition>
   </mapelement>
...
</renditionmap>
```

此 `mimetype` 元素會指定檔案格式的MIME型別。 此 `rendition output` element指定輸出格式的型別和轉譯的名稱\(例如， `cq5dam.web.1280.1280.jpeg`\)來發佈指定的輸出。 您可以指定用於所有支援輸出格式的影像轉譯 — AEMSITE、PDF、HTML5、EPUB和CUSTOM。

如果指定的轉譯不存在，AEM Guides發佈程式會先尋找指定影像的網頁轉譯。 如果找不到網頁轉譯，則會使用影像的原始轉譯。

>[!NOTE]
>
> 這些影像轉譯只會控制輸出產生。 當您開啟檔案以進行預覽或檢閱時，會使用影像的Web轉譯。

## 設定輸出記錄的自動永久刪除期間 {#id19AAI070V8Q}

產生輸出時，會建立輸出與輸出記錄。 對於大型DITA map，這些記錄可能會佔用存放庫中的大量空間。 依預設，記錄檔會儲存在存放庫的下列位置：

`/var/dxml/metadata/outputHistory`

在一段時間內，所有記錄檔的集體大小可能會達到GB。 AEM Guides可讓您設定將這些記錄檔保留在存放庫中的時段。 在指定的時段後，記錄以及輸出產生歷史記錄會從存放庫中刪除。

>[!NOTE]
>
> 輸出產生歷史記錄是「輸出」標籤中「產生的輸出」清單中的記錄專案。

設定歷史記錄清除功能會影響儲存庫中所有DITA map的輸出產生。 在DITA map的「輸出」標籤中，在指定的天數之後，以及在設定中指定的時間清除歷史記錄。

>[!NOTE]
>
> 移除記錄檔和輸出產生歷程記錄對產生的輸出沒有任何影響。

使用中提供的指示 [設定覆寫](download-install-additional-config-override.md#) 以建立組態檔。 在設定檔中，提供下列\(property\)詳細資訊，以設定清除輸出歷史記錄和記錄檔的日期和時間：

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.config.ConfigManager` | `output.history.purgeperiod` | 指定清除輸出歷史記錄以及輸出日誌的天數。 若要停用此功能，請將此屬性設為0。每天在指定的時間，針對此屬性指定天數之前產生的輸出執行清除程式。 <br> **預設值**：5 |
| `output.history.purgetime` | 指定開始永久刪除處理的時間。 <br> **預設值**：0:00 \（或12:00午夜\） |

## 變更最近產生的輸出清單限制 {#id1679JH0H0O2}

您可以變更DITA map在「輸出」標籤中顯示的已產生輸出最大數目。

使用中提供的指示 [設定覆寫](download-install-additional-config-override.md#) 以建立組態檔。 在設定檔案中，提供下列\(property\)詳細資訊，以變更要在清單中顯示的輸出數量：

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.config.ConfigManager` | `output.historylimit` | 整數值。<br> **預設值**：25 |

>[!TIP]
>
> 請參閱 *輸出歷程記錄* 最佳作法指南中的區段，以瞭解有關使用輸出歷史記錄的最佳作法。
