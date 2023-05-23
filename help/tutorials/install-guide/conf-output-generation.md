---
title: 配置輸出生成設定
description: 瞭解如何配置輸出生成設定
source-git-commit: 5ac066bb8db32944abd046f64da11eeb1bdbe467
workflow-type: tm+mt
source-wordcount: '5761'
ht-degree: 1%

---

# 配置輸出生成設定 {#id181AI0B0E30}

指AEM南附帶了許多配置選項，供您自定義輸出生成過程。 本主題涵蓋有助於設定輸出生成過程的所有配置和自定義。

## 在DITA映射儀表板上配置基線頁籤 {#id223MD0D0YRM}

可以配置和隱藏「基線」(Baseline)頁籤，該頁籤可用於映射儀表板。

的 **隱藏基線頁籤** 選項在預設情況下未啟用，您需要從configMgr中啟用此選項。 執行以下步驟以在Web編輯器中預設啟用該選項：

1. 開啟「Adobe Experience ManagerWeb控制台配置」頁。

   訪問配置頁的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索並按一下 **com.adobe.fmdita.config.ConfigManager** 捆綁。

1. 選擇 **隱藏基線頁籤** 的雙曲餘切值。

1. 按一下「**儲存**」。

   >[!NOTE]
   >
   > 預設情況下，此配置處於禁用狀態，「基線」(Baseline)頁籤在映射儀表板上可用。


## 配置FrameMaker發佈伺服器 {#id1678G0Z0TN6}

可以使用FrameMaker發佈伺服器\(FMPS\)為DITA內容生成輸出。 配置FMPS將允許您以FMPS支援的多種格式生成輸出。

>[!NOTE]
>
> 要使用FMPS生成輸出，需要設定FMPS伺服器。 有關安裝和配置的詳細資訊，請參閱《FrameMaker Publishing Server使用手冊》。

要配置AEM參考線以使用FMPS，請更新 `com.adobe.fmdita.config.ConfigManager` 在Web控制台中捆綁。

>[!NOTE]
>
> 訪問http://&lt;server name=&quot;&quot;>:&lt;port>/system/console/configMgr URL，用於開啟Web控制台。

| 屬性 | 說明 |
|--------|-----------|
| FrameMaker發佈伺服器登錄域 | 指定承載FrameMaker發佈伺服器的域名或工作組名稱。 根據FMPS版本，將域名提供為：-   **FMPS 2020**:IP地址為192.168.1.101 <br>- **2019年及更早**:IP地址或域名 |
| FrameMaker發佈伺服器URL | 指定FrameMaker發佈伺服器的URL。 根據FMPS版本，將FMPS URL提供為：<br>- **FMPS 2020**: `http://<fmps_ip>:<port>` \(http://192.168.1.101:7000\) <br> - **2019年及更早**: `http://<fmps_ip>:<port>/fmserver/v1/` |
| FMPS版本 | 指定FrameMaker發佈伺服器的版本號。 根據FMPS版本，提供版本資訊如下： <br>- **FMPS 2020**:2020 <br> - **2019年及更早**:2019或2017 |
| FrameMaker發佈伺服器用戶名和密碼 | 指定訪問FrameMaker發佈伺服器的用戶名和密碼。 |
| FMPS超時 | \(*可選*\)指定輔助線等待FrameMaker發佈伺服器AEM響應的時間\（秒\）。 如果在指定時間內收到任何響應，AEM則指南將終止發佈任務，並將任務標籤為失敗。 <br> 預設值：300秒\（5分鐘\） |
| 外部AEMURL | *\（可選\）* FrameMaker發AEM布伺服器將放置生成的輸出檔案的URL。 比如說， `http://<server-name>:<port>/`。 |
| 管AEM理員用戶名和密碼 | *\（可選\）* 安裝程式管理員的用戶名和密碼AEM。 FrameMaker發佈伺服器將使用此功能與通信AEM。 |
| FMPS任務執行等待超時 | 此設定僅適用於FMPS 2020。 指定FMPS在其後停止等待此進程執行的時間\（秒\）。 |

## 在現有站點內配置混合發AEM布 {#id1691I0V0MGR}

如果您的站AEM點包含DITA內容，則可以配置站AEM點輸出，將DITA內容發佈到站點內的預定義位置。 例如，在「站點」頁面的下AEM面螢幕快照中， `ditacontent` 節點被保留以儲存DITA內容：

![](assets/publish-in-aem-site.png){width="300" align="left"}

頁面中的其餘節點直接由站點編輯AEM器創作。 將發佈設定配置為將DITA內容發佈到預定義位置，可確保「指南」發佈過程不會修改任何現有AEM的非DITA內容。

您需要在現有站點上執行以下配置以允許將DITA內容發佈到預定義節點：

- 配置站點的模板屬性

- 添加站點中的節點以發佈DITA內容


執行以下步驟以配置現有站點的模板屬性：

1. 登錄並AEM開啟CRXDE Lite模式。

1. 導航到站點的模板配置節點。 例如，「參考AEM線」將預設模板配置儲存在以下節點中：

   `/libs/fmdita/config/templates/default`

   >[!NOTE]
   >
   > 請勿在中的預設配置檔案中進行任何自定義 `libs` 的下界。 必須建立 `libs` 中的 `apps` 節點，並更新 `apps` 僅節點。

1. 添加以下屬性：

   | 屬性名稱 | 類型 | 值 |
   |-------------|----|-----|
   | `topicContentNode` | 字串 | 指定要發佈DITA內容的節點名稱。 例如，參考線發佈DITAAEM內容的預設節點是： <br>`jcr:content/contentnode` |
   | `topicHeadNode` | 字串 | 指定要儲存DITA內容的元資料資訊的節點名稱。 例如，參考線儲存元資料信AEM息的預設節點是： <br>`jcr:content/headnode` |


以下螢幕快照顯示了在「參考線」的預設模板節點中添加的AEM屬性：

![](assets/add-content-node.png){width="800" align="left"}

下次使用站點的模板配置發佈任何DITA內容時，內容將發佈到在 `topicContentNode` 和 `topicHeadNode` 屬性。

但是，對於現有站點，必須手動添加 `topicContentNode` 和 `topicHeadNode` 節點。

執行以下步驟將所需節點添加到現有站點：

1. 登錄並AEM開啟CRXDE Lite模式。

1. 定位 `jcr:content` 在站點節點中。

1. 添加 `topicContentNode` 和 `topicHeadNode` 與在站點模板配置中指定的名稱相同的節點。


## 自定義AEM站點輸出 {#id166TG0B30WR}

指AEM南支援以下格式建立輸出：

- 站AEM點

- PDF

- HTML5
- ePub
- 通過DITA-OT自定義輸出

對於「站AEM點」輸出，您可以分配具有不同輸出任務的不同設計模板。 這些設計模板可以在不同佈局中呈現DITA內容。 例如，可以為內部和外部受眾指定不同的設計模板。

您還可以將自定義的DITA Open Toolkit \(DITA-OT\)插件與參考AEM線一起使用。 您可以上載這些自定義DITA-OT插件以以特定方式生成PDF輸出。

>[!TIP]
>
> 查看 *網AEM站發佈* 最佳實踐指南中的[附錄.md\#](appendix.md#) 用於建立站點輸出AEM的最佳實踐。

### 定制設計模板以生成輸出 {#customize_xml-add-on}

參考AEM線使用一組預定義的設計模板來生成AEM「站點」輸出。 您可以自定AEM義「參考線」的設計模板，以生成符合公司品牌的輸出。 設計模板是各種樣式的集合\(CSS\)、指令碼\（伺服器端和客戶端\）、資源\（影像、徽標和其他資產\）以及將所有這些資源連接在一起的JCR節點。 設計模板可以像只帶幾個JCR節點的單伺服器端指令碼一樣簡單，也可以像樣式、資源和JCR節點的複雜組合一樣簡單。 設計模板由Guides發AEM布子系統在生成站點AEM輸出時使用，它們控制生成的輸出的結構、外觀和感覺。

設計模板資源在伺服器上的位置沒有任何限制，但通常根據其功能對它們進行邏輯組織。 例如，預設模板將其所有JavaScript和CSS檔案儲存在 `/etc/designs/fmdita/clientlibs/siteoutput/default` 的子菜單。 無論這些檔案位於何處，它們都通過JCR節點集合連結在一起。 這些JCR節點和檔案共同構成了整個設計模板。

「參考線」附帶的預設設AEM計模板允許您自定義登錄、主題和搜索頁面元件。 可建立預設設計和相應參照模板的副本，並指定不同的元件以生成所需的輸出。

執行以下步驟以指定您自己的設計模板，以用於生AEM成站點輸出：

1. 登錄並AEM開啟CRXDE Lite模式。

1. 導航到預設設計模板節點。 預設設計模板節點的位置是：

   `/libs/fmdita/config/templates/`

   ![](assets/templates-node.png){width="300" align="left"}

   >[!NOTE]
   >
   > 從 `libs` 資料夾 `apps` 資料夾和在 `apps` 的子菜單。 還必須在從預設模板節點引用的模板中進行更改。 引用的模板放在 `/libs/fmdita/templates/default/cqtemplates` 的下界。 複製中引用的模板 `apps` 資料夾。

1. 按一下 *預設* 元件 *模板* 節點以訪問其屬性。

   下AEM表介紹了參考線的設計模板屬性。

   | 屬性 | 說明 |
   |--------|-----------|
   | `landingPageTemplate`, `searchPageTemplate`, `topicPageTemplate`, `shadowPageTemplate` | 指定 `cq:Template` 頁\（登錄、搜索和主題\）的節點。 預設情況下， `cq:Template` 可以在 `/libs/fmdita/templates/default/cqtemplates` 的下界。 此節點定義登錄、搜索和主題頁的結構和屬性。 <br>的 `shadowPageTemplate` 用於優化分塊內容。 您需要將此屬性的值設定為： <br> `fmdita/templates/default/cqtemplates/shadowpage` <br> **注釋** 必須為 `topicPageTemplate`。 的 `landingPageTemplate` 和 `searchPageTemplate` 是可選屬性。 如果不希望生成搜索和登錄頁，請不要指定這些屬性。 |
   | `title` | 設計模板的描述性名稱。 |
   | `topicContentNode` | 將在主題頁中包含DITA內容的節點的位置。 路徑相對於主題頁。 |
   | `topicHeadNode` | 包含從DITA內容派生的頭值\（或元資料\）的節點的位置。 路徑相對於主題頁。 |
   | `tocNode` | 包含TOC的節點的位置。 路徑相對於登錄頁或目標路徑。 |
   | `basePathProp` | 用於儲存已發佈站點根路徑的屬性名稱。 |
   | `indexPathProp` | 用於儲存已發佈站點的登錄/索引頁路徑的屬性名稱。 |
   | `pdfPathProp` | 如果啟用了主題PDF生成，則儲存主題PDF路徑的屬性名稱。 |
   | `pdfTypeProp` | 用於儲存PDF生成類型的屬性名稱。 當前，此屬性始終包含「Topic」。 |
   | `searchPathProp` | 用於儲存搜索頁路徑的屬性名稱（如果模板包括搜索頁）。 |
   | `siteTitleProp` | 用於儲存要發佈的站點標題的屬性名稱。 此標題通常與要發佈的地圖的標題相同。 |
   | `sourcePathProp` | 用於儲存當前頁的源DITA主題路徑的屬性名稱。 |
   | `tocPathProp` | 用於儲存已發佈站點的目錄根路徑的屬性名稱。 |


>[!NOTE]
>
> 建立自定義設計模板節點後，必須更新「站點」輸出預設中的「設AEM計」選項，才能使用自定義設計模板節點。

有關詳細資訊，請參見 [建立您的第一個Adobe Experience Manager6.3網站](https://helpx.adobe.com/experience-manager/using/first_aem63_website.html) 和 [基礎](https://helpx.adobe.com/experience-manager/6-3/sites/developing/using/the-basics.html) 開發自己的網AEM站。

### 使用文檔標題生成站AEM點輸出

在生AEM成站點輸出時，URL的生成方式在內容的可發現性方面起著重要作用。 如果使用基於UUID的檔案名，則基於檔案的UUID生成URL將不適合搜索。 作為管理員或發佈者，您可以控制如何為站點輸出生AEM成URL。 參AEM考線提供了一種配置，通過該配置，您可以選擇使用檔案標題(而AEM不是基於UUID的檔案名)生成站點輸出的URL。 預設情況下，對於基於UUID的檔案系統，此選項為ON。 這意味著，在為基於AEMUUID的檔案系統生成站點輸出時，檔案的標題用於生成檔案的URL，而不是UUID。

在生AEM成站點輸出時，URL的生成方式在內容的可發現性方面起著重要作用。 在非基於UUID的檔案系統中，使AEM用檔案名而不是檔案標題生成「站點」輸出。 作為管理員或發佈者，您可以控制如何為站點輸出生AEM成URL。 參AEM考線提供了一種配置，通過該配置，您可以選擇使用文AEM件標題而不是檔案名生成站點輸出的URL。 預設情況下，此選項為OFF。 這意味著在生AEM成「站點」輸出時，檔案名用於生成URL，而不是檔案的標題。 通過啟用此選項，可以選擇根據檔案標題生成URL。

>[!NOTE]
>
> 您可以進一步配置規則，以僅允許站點輸出的URL中AEM的一組字元。 有關詳細資訊，請參閱 [配置檔案名清除規則以建立主題和發佈站AEM點輸出](#id2164D0KD0XA)。

要在站點輸出中配AEM置URL生成，請執行以下步驟：

1. 開啟「Adobe Experience ManagerWeb控制台配置」頁。

   訪問配置頁的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索並按一下 **com.adobe.fmdita.config.ConfigManager** 捆綁。

1. 選擇 **使用網站頁AEM名的標題** 的雙曲餘切值。

   >[!NOTE]
   >
   > 如果要使用檔案名生成輸出，請取消選擇此選項。

1. 按一下「**儲存**」。


### 配置檔案名清除規則以建立主題和發佈站AEM點輸出 {#id2164D0KD0XA}

作為管理員，可以定義檔案名中允許的有效特殊字元清單，這些字元最終構成站點輸出AEM的URL。 在早期版本中，允許用戶定義包含特殊字元的檔案名，如 `@`。 `$`。 `>`。 這些特殊字元導致生成網站頁面的編AEM碼URL。

從3.8版開始，已添加配置以定義檔案名中允許的特殊字元清單。 預設情況下，有效檔案名配置包含「」`a-z A-Z 0-9 - _`。 這意味著在建立檔案時，檔案標題中可以包含任何特殊字元，但在內部，該檔案將替換為連字元\(`-`\)。 例如，您可以將檔案的標題設定為Introduction 1或Introduction@1 ，為這兩種情況生成的相應檔案名都為Introduction-1。

定義有效字元清單時，請記住這些字元&quot;`*/:[\]|#%{}?&<>"/+`」和 `a space` 將始終替換為連字元\(`-`\)。

>[!NOTE]
>
> 如果未配置有效的特殊字元清單，則檔案建立過程可能會給您帶來一些意外結果。

要在檔案名和站點輸出中配置有AEM效的特殊字元，請執行以下步驟：

1. 開啟「Adobe Experience ManagerWeb控制台配置」頁。

   訪問配置頁的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索並按一下 *com.adobe.fmdita.common.SaniticeNodeNameImpl* 捆綁。

1. 在 **不允許將字元集發佈到AEM Sites** 屬性，確保屬性設定為 ```'<>`@$```。 您可以向此清單添加更多特殊字元，但它必須具有這些所需的特殊字元。

   >[!NOTE]
   >
   > 還可以配置其他屬性，如 **使用小寫** 在檔案名中， **分隔符** 處理無效字元，和 **最大字元數** 檔案名中允許的。

1. 按一下「**儲存**」。

1. 搜索並按一下 **com.adobe.fmdita.config.ConfigManager** 捆綁。

1. 在 **有效字元的規則運算式** 屬性，確保屬性設定為 `[-a-zA-Z0-9_]`。 您可以向此清單添加更多字元，但它必須具有這些基本字元，並且清單必須以連字元\(`-`\)。

   >[!NOTE]
   >
   > 此屬性定義用於建立新檔案的有效字元的清單。

1. 按一下「**儲存**」。


### 配置站點節AEM點結構的拼合

生成「站AEM點」輸出時，會在內部為主題中的每個元素建立一個節點。 對於具有數千個主題的DITA映射，此節點結構可能變得太深。 此類深度嵌套的節點結構可能會對較大的站點產生效能問題。 以下快照顯示「站點」輸出的深度嵌套AEM的節點結構：

![](assets/deep-nested-aem-site-node-structure.png){width="300" align="left"}

在上面的快照中，請注意，每個快照都建立了一個節點 `p` 元素及其後續子元素，並為主題中使用的每個其它元素建立相似的結構。

指AEM南允許您配置站點AEM輸出的節點結構的內部建立方式。 可以在指定的元素上拼合節點結構，這意味著可以定義一個將被視為主元素的元素，並且其中的所有子元素將與主元素合併。 例如，如果您決定展平 `p` 元素，然後顯示在 `p` 元素將與主元素合併 `p` 的子菜單。 不會為中的任何子元素建立單獨的注釋 `p` 的子菜單。 以下快照顯示在 `p` 元素：

![](assets/flattened-aem-site-node-structure.png){width="300" align="left"}

要平AEM整「站點」節點結構，請執行以下步驟：

1. 指定要平整節點結構的元素。

   1. 覆蓋 `libs` 中的 `apps` 並開啟elementmapping.xml檔案。

   1. 添加 `<flatten>true</flatten>` 定義要展平節點結構的元素中的屬性。 例如，如果要在 `p` 元素，然後在定義中添加拼合屬性 `p` 元素，如下所示：

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
      > 預設情況下，在 `p` 的子菜單。

1. 在configMgr中啟用站點節點拼合配置。

   1. 開啟「Adobe Experience ManagerWeb控制台配置」頁。

      訪問配置頁的預設URL為：

      ```http
      http://<server name>:<port>/system/console/configMgr
      ```

   1. 搜索並按一下 *com.adobe.dxml.flaption.FlattingConfigurationService* 捆綁。

   1. 選擇 **屬性flopation.enabled** 的雙曲餘切值。

   1. 按一下「**儲存**」。


>[!IMPORTANT]
>
> 如果在elementmapping.xml檔案中做了任何更改，請確保開啟configMgr並保存任何捆綁包以使更改生效。

現在，當您生成站AEM點輸出時， `p` 元素被平整並儲存在 `p` 元素本身。 可以找到 `p` CRXDE中的元素。

![](assets/flatten-aem-site-note-props-crxde.png){width="650" align="left"}

**防止平AEM整站點注釋結構**

與在「站點」輸出中指AEM定要拼合的節點類似，您還可以指定要從此配置中排除的元素。 例如，如果要在 `body` 元素，但你不想 `table` 元素 `body` 要展平，則可以在 `table` 元素的定義。

排除 `table` 從拼合中的元素，將以下屬性添加到 `table` 元素的定義：

`<preventancestorflattening>true|false</preventancestorflattening>`

### 在站點輸出中配置已刪除頁AEM的版本控制

生成站AEM點輸出時 **刪除和**&#x200B;建立&#x200B;****選項「現有輸出頁」設定，將為要刪除的頁建立版本。 您可以配置系統以在刪除之前停止建立版本。

執行以下步驟以停止為要刪除的頁面建立版本：

1. 開啟「Adobe Experience ManagerWeb控制台配置」頁。

   訪問配置頁的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索並按一下 *com.adobe.fmdita.config.ConfigManager* 捆綁。

1. 選擇&#x200B;**不為已刪除的頁面建立版本** 的雙曲餘切值。

   >[!NOTE]
   >
   > 如果選擇此選項，用戶將可以直接刪除任何頁面，而不為其建立任何版本。 如果未選擇該選項，則在刪除頁面\(s\)之前建立版本。

1. 按一下「**儲存**」。

## 在通過DITA-OT發佈輸出時使用元資料 {#id191LF0U0TY4}

指AEM南提供了在使用DITA-OT發佈輸出時傳遞自定義元資料的方法。 作為管理員和發佈者，您需要執行以下任務來配置和使用發佈輸出中的自定義元資料：

- 作為管理員，在系統中添加所需的元資料，以便在DITA映射的「屬性」頁上可用。

- 作為管理員，在元資料清單中添加自定義元資料，以便它顯示在DITA映射控制台中。

- 作為發佈者，使用DITA映射配置和添加自定義元資料並生成所需的輸出。


要在系統中添加所需的元資料，請執行以下步驟：

1. 以管理員身份登錄Adobe Experience Manager。

1. 按一下頂部的Adobe Experience Manager連結，然後選擇 **工具**。

1. 選擇 **資產** 的雙曲餘切值。

1. 按一下 **元資料架構** 平鋪。

   此時會顯示「中繼資料結構描述表單」頁面。

1. 選擇 **預設** 的子菜單。

   >[!NOTE]
   >
   > DITA映射的「屬性」頁上顯示的屬性是從此表單獲取的。

1. 按一下 **編輯**。

1. 添加要在發佈輸出中使用的自定義元資料。 例如，我們將使用以下步驟添加受眾元資料：

   1. 從 **生成窗體** 元件清單，拖放 **單行文本** 元件。

   1. 選擇新欄位以開啟 **設定** 的上限。

   1. 在 **欄位標籤**，輸入元資料名稱 — 「受眾」。

   1. 在 **映射到屬性** 設定，指定。/jcr：內容/元資料/&lt;name of=&quot;&quot; the=&quot;&quot; metadata=&quot;&quot;>。 以我們的例子，我們把它設為。/jcr:content/metadata/audience。

   使用這些步驟，添加所有必需的元資料參數。

1. 按一下「**儲存**」。


新參數現在顯示在所有DITA映射的「屬性」頁上。

![](assets/properties-page-custom-metadata.PNG){width="650" align="left"}

接下來，您需要使自定義元資料在DITA映射控制台中可用。 執行以下步驟，使DITA映射破折號板上的自定義元資料可用：

1. 登錄並AEM開啟CRXDE Lite模式。

1. 訪問位於以下位置的metadataList檔案：

   /libs/fmdita/config/metadataList

   >[!NOTE]
   >
   > 元資料清單檔案包含在 **屬性** 映射儀表板中DITA映射的下拉清單。 預設情況下，此檔案中列出了四個屬性 — docstate 、 dc:language 、 dc:description和dc:title。

1. 添加在「元資料架構Forms」頁中添加的自定義元資料。 對於示例，將受眾參數添加到預設清單的末尾。

1. 按一下 **全部保存**。


現在，自定義元資料將顯示在DITA映射控制台的 **屬性** 的子菜單。

最後，作為發佈者，您需要在發佈的輸出中包含自定義元資料。 要在生成輸出時處理自定義元資料，請執行以下步驟：

1. 在資產UI中，導航到要發佈的DITA映射。

1. 選擇DITA映射檔案並開啟其屬性頁。

1. 在「屬性」頁上，指定自定義元資料的值。 對於我們的示例，我們為受眾參數指定了External值。

   ![](assets/properties-page-custom-metadata-value.png){width="650" align="left"}

1. 按一下&#x200B;**「儲存並關閉」**。

1. 按一下DITA映射檔案以開啟DITA映射控制台。

1. 在 **輸出預設** 頁籤，選擇要用於生成輸出的輸出預設。

1. 按一下 **編輯**。

1. 從 **屬性** 下拉清單中，選擇要傳遞給發佈過程的屬性。

   ![](assets/props-in-publish-output.PNG){width="650" align="left"}


所選屬性/元資料被傳遞到發佈進程，並在最終輸出中可用。

## 使用元件自定義DITA元AEM素映射 {#id1679J600HEL}

參考線中AEM的DITA元素將映射到其相應AEM的元件。 指AEM南在發佈和審閱等工作流中使用此映射將DITA元素轉換為相應AEM元件。 映射在 `elementmapping.xml` 檔案，可從CRXDE Lite模式訪問。 在CRXDE Lite模式下訪問以下URL:

`/libs/fmdita/config/elementmapping.xml`

>[!NOTE]
>
> 請勿在中的預設配置檔案中進行任何自定義 ``libs`` 的下界。 必須建立 ``libs`` 中的 ``apps`` 節點，並更新 ``apps`` 僅節點。

您可以使用預定義的DITA元素映射，也可以將DITA元素映射到自定義AEM元件。 要使用自定AEM義元件，需要瞭解 `elementmapping.xml` 的子菜單。

### elemapping.xml結構

高級概述 `elementmapping.xml` 架構說明如下：

1. 首先基於元素名稱搜索每個DITA元素以查找相應的元件映射。 例如：

   ```XML
   <ditaelement>     
      <name>**substeps**</name>  
      <class>- topic/ol task/substeps</class>  
      <componentpath>dita/components/ditaolist</componentpath>  
      <type>COMPOSITE</type>  
      <target>para</target>
   </ditaelement>
   ```

   在上例中，所有 `substeps` 使用 `dita/components/ditaolist` 元件。

1. 如果DITA元素未根據名稱找到匹配項，則根據 `class` 完成。 例如：

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

   在上例中，如果沒有為 `task` 元素，然後 `task` 元素映射到上述元件，因為 `task` 繼承自 `topic` 元件。

1. 當元件具有相應的元件映射時，其子元件的進一步處理由 `type`。 例如：

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

   `type` 採用以下值：

   - 複合：元素到元件 *子元素映射繼續* 也是。

   - 獨立：當前元素的子元素是 *未進一步映射*。

   在上例中，如果 `<title>` 元素具有任何子元素，它們不會映射到任何其他元件。 用於 `<title>` 元素負責呈現內部的所有子元素 `<title>` 的子菜單。

1. 如果有多個元件映射到單個DITA元素，則選擇該元素的最佳匹配項。 要選擇最佳匹配元件，將考慮DITA元素的域和結構專業化。

   如果存在具有域專用化的DITA元素，並且映射了用於域專用化的元件，則該元件將獲得高優先順序。

   同樣，如果存在具有結構專用化的DITA元素，並且映射了用於結構專用化的元件，則該元件將獲得高優先順序。

1. 您可以使用 `<attributemap>` 在元素映射中將屬性值映射到相應的節點屬性中。

1. `textprop` 可用於將DITA元素的文本內容序列化到節點屬性。 此外，可以在元素標籤中多次使用它來序列化發佈層次結構中多個位置的文本內容。 您還可以自定義目標屬性的位置和名稱。 例如：

   ```XML
   <ditaelement> 
       <name>title</name> 
       <class>- topic/title</class> 
       <componentpath>foundation/components/title</componentpath> 
       <type>STANDALONE</type> 
       <target>para</target> 
       <textprop>**jcr:title**</textprop>
   </ditaelement>
   ```

   以上元素映射指定 `<title>` 元素將另存為名為 `jcr:title` 在輸出節點上。

1. `xmlprop` 可用於將給定元素的整個XML序列化為節點屬性。 然後，元件可以讀取此節點屬性並執行自定義呈現。 例如：

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

   以上元素映射指定元素的整個XML標籤 `<svg-container>` 將另存為名為 `data` 在輸出節點上。

1. 在輸出生成過程中，有一個特殊的屬性映射來處理路徑解析。 例如：

   ```XML
   <attributemap> 
       <attribute from="href" to="fileReference" ispath="true" rel="source" /> 
       <attribute from="height" to="height" /> 
       <attribute from="width" to="width" />
   </attributemap>
   ```

   對於以上 `attributemap`，也請參見Wiki頁。 `href` DITA元素中的屬性將映射到名為的節點屬性 `fileReference`。 現在 `ispath` 設定為 `true`，輸出生成過程將解析此路徑，然後將其設定為 `fileReference` 節點屬性。

   此解決方案的發生方式根據 `rel` 屬性映射中的屬性。

   - 如果 `rel=source`，然後是值 `href` 已針對當前正在處理的DITA源檔案進行解析。 值 `href` 被解析並置於 `fileReference` 屬性。

   - 如果 `rel=target`，然後是值 `href` 將針對根發佈位置進行解析。 值 `href` 被解析並置於 `fileReference` 屬性。

   如果不希望在路徑屬性上執行任何預處理或解析，則無需指定 `ispath` 屬性。 值按原樣複製，元件可以執行所需的解析度。


### DITA元素架構

以下是中的DITA元素架構的示例 `elementmapping.xml` 檔案：

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
    <attribute from="attrname" to="propname" ispath="true|false" rel="source|target" />     
    </attributemap>     
    <skip>true|false</skip> 
</ditaelement>
```

下表介紹了DITA元素架構中的元素：

| 元素 | 說明 |
|-------|-----------|
| `<ditaelement>` | 每個映射元素的頂級節點。 |
| `<class>` | 要為其編寫元件的目標DITA元素的類屬性。 <br>例如，DITA主題的類屬性是： <br>`topic/topic` |
| `<componentpath>` | 映射元件的CRXDE路AEM徑。 |
| `<type>` | 可能的值： <br>- **複合**:處理子元素 <br>- **獨立**:跳過子元素的處理 |
| `<attributeprop>` | 用於將序列化DITA屬性和值作為屬AEM性映射到節點。 例如，如果 `<note type="Caution">` 元素和為此元素映射的元件具有 `<attributeprop>attr_t</ attributeprop>`，然後將節點的屬性和值序列化為 `attr_t` 相應節點的AEM屬性\( `attr_t->type="caution"`\)。 |
| `<textprop>propname_t</textprop>` | 保存 `getTextContent()` 輸出到定義的屬性 `propname_t.` **注：**  這是一個優化屬性。 |
| `<xmlprop>propname_x </xmlprop>` | 將此節點的序列化XML保存到由定義的屬性 `propname_x.` **注：** 這是一個優化屬性。 |
| `<xpath>` | 如果元素映射中提供了XPath元素，則還應滿足XPath條件，以便使用元件映射。 |
| `<target>` | 將DITA元素放在crx儲存庫中指定的位置。 <br>可能的值：<br>- **頭**:在頭節點下 <br>- **文本**:在段落節點下 |
| `<wrapelement>` | HTML元素，用於在中包裝內容。 |
| `<wrapclass>` | 屬性的元素值 `wrapclass.` |
| `<attributemap>` | 包含一個或多個容器節點 `<attribute>` 節點。 |
| `<attribute from="attrname" to="propname" ispath="true|false" rel="source|target" />` | 將DITA屬性映射到AEM屬性：<br>- **`from`**:DITA屬性名稱<br>- **`to`**:AEM元件屬性名稱 <br>- **`ispath`**:如果屬性是路徑值\(例如： *影像*\)<br>- **`rel`**:如果路徑是源或目標 <br>**注：** 如果 `attrname` 開頭 `%`，則 `attrname minus '%'` 到「」 `propname`「 」。 |

**附加說明**

- 如果計畫覆蓋預設元素映射，建議您不要在預設元素中進行更改 `elementmapping.xml` 的子菜單。 您應建立新的映射XML檔案，並將該檔案放在另一個位置，最好放在您建立的自定義應用資料夾內。

- 在 `elementmapping.xml` 檔案中，有許多引用fmdita/components/dita/wrapper元件的映射項。 Wrapper是一個泛型元件，它使用站點節點上的屬性來呈現相對簡單的DITA構造以生成相關HTML。 它使用 `wrapelement` 屬性，以生成封閉標籤並將子呈現委派給相應的元件。 這在您只需要容器元件時非常有用。 而不是建立呈現特定容器標籤(如 `div` 或 `p`，可將Wrapper元件與 `wrapelement` 和 `wrapclass` 效能達到相同效果。

- 建議不要在字串JCR屬性中保存大量文本。 輸出生成中的優化屬性類型計算可確保不將大文本內容另存為字串類型。 相反，當需要保存大於某個閾值的內容時，屬性的類型將更改為二進位。 預設情況下，此閾值配置為512位元組，但可以在Configuration Manager \(*com.adobe.fmdita.config.ConfigManager*\)通過更改 **另存為二進位閾值** 的子菜單。

- 如果計畫覆蓋某些元素映射的\（而非全部\），則不必複製整個 `elementmapping.xml` 的子菜單。 您需要建立新的XML映射檔案，並僅定義要覆蓋的元素。

- 在自定義位置建立XML檔案後，更新 `Override Element Mapping` 的 `com.adobe.fmdita.config.ConfigManager` 捆綁。


## 自定義DITA映射控制台 {#id188HC08M0CZ}

指AEM南讓您能夠靈活擴展DITA映射控制台的功能。 例如，如果您有一組報告與指南中提供的報告不同AEM，則可以將這些報告添加到映射控制台。 要自定義映射控制台，需要建立一個AEM客戶端庫\（或ClientLib\），該庫將包含執行所需功能的代碼。

>[!NOTE]
>
> 建議不要直接修改頁面元件，因為它將被產品的新版本覆蓋。

AEM參考線 `apps.fmdita.dashboard-extn` 自定義映射控制台的類別。 只要載入了映射控制台， `apps.fmdita.dashboard-extn` 將執行和載入類別。

>[!NOTE]
>
> 有關建立客戶端庫的AEM詳細資訊，請參見 [使用客戶端庫](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/clientlibs.html)。

## 在輸出生成期間處理影像再現 {#id177BF0G0VY4}

附AEM帶一組預設工作流和介質句柄來處理資產。 在AEM中，有預定義的工作流來處理最常見的MIME類型的資產處理。 通常，對於您上載的每個影像，AEM都會以二進位格式建立相同的多個格式副本。 這些格式副本可能具有不同大小、不同解析度、添加水印或某些其他更改的特徵。 有關如何處理資AEM產的詳細資訊，請參見 [使用媒體處理程式和工作流處理資產](https://helpx.adobe.com/experience-manager/6-5/assets/using/media-handlers.html) 的上AEM界。

AEM參考線允許您配置在生成文檔輸出時要使用的影像格式副本。 例如，您可以從預設影像格式副本中選擇一個，或建立一個格式副本並使用它發佈文檔。 用於發佈文檔的影像格式副本映射儲存在 `/libs/fmdita/config/ **renditionmap.xml**` 的子菜單。 代碼段 `renditionmap.xml` 檔案如下所示：

>[!NOTE]
>
> 建議您建立 `renditionmap.xml` 檔案 `apps` 資料夾。

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

的 `mimetype` element指定檔案格式的MIME類型。 的 `rendition output` 元素指定輸出格式的類型和格式副本的名稱\(例如， `cq5dam.web.1280.1280.jpeg`\)用於發佈指定輸出的。 您可以指定要用於所有支援的輸出格式的影像格式副本 — AEMSITE、PDF、HTML5、EPUB和CUSTOM。

如果指定的格式副本不存在，AEM則「參考線」發佈過程首先查找給定影像的Web格式副本。 即使找不到Web格式副本，也會使用影像的原始格式副本。

>[!NOTE]
>
> 這些影像格式副本僅控制輸出生成。 開啟文檔進行預覽或審閱時，將使用影像的Web格式副本。

## 為輸出歷史記錄配置自動清除期間 {#id19AAI070V8Q}

生成輸出時，輸出將隨輸出日誌一起建立。 對於大型DITA映射，這些日誌可能佔用儲存庫中的大量空間。 預設情況下，日誌儲存在儲存庫中的以下位置：

/var/dxml/metadata/outputHistory/

在一段時間內，所有日誌檔案的總大小可能會運行為GB。 指AEM南允許您配置將這些日誌檔案保留在儲存庫中的時間段。 在指定的時間段後，將從儲存庫中刪除日誌以及輸出生成歷史記錄。

>[!NOTE]
>
> 輸出生成歷史記錄是「輸出」(Outputs)頁籤的「已生成輸出」(Generated Outputs)清單中的日誌條目。

配置歷史記錄清除功能會影響儲存庫中所有DITA映射的輸出生成。 在DITA映射的輸出頁籤中，歷史記錄在指定的天數後和在設定中指定的時間清除。

>[!NOTE]
>
> 刪除日誌檔案和輸出生成歷史記錄對生成的輸出沒有任何影響。

執行以下步驟以設定清除輸出歷史記錄和日誌的日期和時間：

1. 開啟「Adobe Experience ManagerWeb控制台配置」頁。

   訪問配置頁的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索並按一下 **com.adobe.fmdita.config.ConfigManager** 捆綁。

1. 在 **輸出歷史記錄清除期間** 屬性，指定清除輸出歷史記錄和輸出日誌的天數。 預設情況下，它設定為5天。 如果要禁用此功能，請將此屬性設定為0。

1. 在 **輸出歷史記錄清除時間** 屬性，指定啟動清除過程的時間。 預設情況下，它設定為0:00 \（或12:00 mindight\）。 此時，清除流程每天都對在指定天數之前生成的輸出執行。 **輸出歷史記錄清除期間** 屬性。

   >[!NOTE]
   >
   > 預設情況下，清除功能將在5天以前的輸出上每午夜執行一次。

1. 按一下「**儲存**」。


## 更改最近生成的輸出清單限制 {#id1679JH0H0O2}

您可以更改DITA映射的輸出頁籤中顯示的最大生成輸出數。 預設情況下，將顯示最後25個生成輸出的清單。 要更改要在清單中顯示的輸出數，請更新 **輸出清單限制** 的 `com.adobe.fmdita.config.ConfigManager` 捆綁。

>[!TIP]
>
> 查看 *輸出歷史記錄* 最佳實踐指南中的[附錄.md\#](appendix.md#) 用於處理輸出歷史記錄的最佳實踐。

## 輸出生成效能優化 {#id176LB050VUI}

指AEM南允許您配置輸出生成進程池大小，該池大小控制併發運行的輸出生成進程數。 預設情況下，進程池大小設定為系統中可用的處理內核數加上一個。 如果希望按順序發佈，您可能希望將此值更改為1。 在這種情況下，將執行第一個發佈任務，然後將下一個發佈任務儲存在發佈隊列中。

要更改輸出生成處理池大小，請更新 **層代池大小** 的 `com.adobe.fmdita.publish.manager.PublishThreadManagerImpl` 捆綁。

