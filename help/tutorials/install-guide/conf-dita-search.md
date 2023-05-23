---
title: 配置搜索AEM AssetsUI
description: 瞭解如何配置搜索AEM AssetsUI
source-git-commit: 5ac066bb8db32944abd046f64da11eeb1bdbe467
workflow-type: tm+mt
source-wordcount: '1697'
ht-degree: 1%

---


# 配置搜索AEM AssetsUI {#id192SC800MY4}

預設情AEM況下，不識別DITA內容，因此，它不提供任何機制來搜索其儲存庫中的DITA內容。 指AEM南允許您在儲存庫中添加DITA內容搜AEM索功能。

預設情AEM況下，不識別DITA內容，因此，它不提供任何機制來搜索其儲存庫中的DITA內容。 此外，沒有OOTB功能可根據內容的UUID來搜索內容。 指AEM南允許您在儲存庫中添加DITA內容搜索和基於UUID的搜AEM索功能。

配置DITA內容搜索涉及以下任務：

1. [在資產UI中添加DITA元素搜索元件](#id192SF0F50HS)
1. [在資產UI中添加基於UUID的搜索元件](#id2034F04K05Z)
1. [向用戶提供權限](#id192SF0G0RUI)
1. [在搜索中添加自定義元素或屬性](#id192SF0G10YK)
1. [從現有內容中提取元資料](#id192SF0GA0HT)

除了添加搜索功能外，還可以配置不應包含在搜索中的資料夾。 有關詳細資訊，請參閱 [從搜索結果中排除臨時檔案](#id197AHI0035Z)。

## 在資產UI中添加DITA元素搜索元件 {#id192SF0F50HS}

在AEM AssetsUI中添加DITA內容搜索元件，請執行以下操作：

1. 以管理員身份登錄Adobe Experience Manager。

1. 按一下 **Adobe Experience Manager** 在頂部連結，然後選擇 **工具**。

1. 選擇 **常規** 從工具清單中按一下 **搜索Forms** 平鋪。

1. 在 **搜索Forms** ，選擇 **資產管理搜索欄**。

1. 按一下 **編輯**。
1. 在 **選擇謂詞** 頁籤，滾動到清單的末尾。

1. 拖放 **DITA元素謂詞** 的位置。

   ![](assets/drag-search-predicate.png){width="650" align="left"}

1. 按一下 **完成** 的子菜單。

   訪問資產UI中的篩選器選項時，將獲取DITA元素搜索篩選選項。

   ![](assets/search-filter-asset-console.png){width="350" align="left"}


## 在資產UI中添加基於UUID的搜索元件 {#id2034F04K05Z}

在AEM AssetsUI中添加基於UUID的搜索元件，請執行以下操作：

1. 以管理員身份登錄Adobe Experience Manager。

1. 按一下 **Adobe Experience Manager** 在頂部連結，然後選擇 **工具**。

1. 選擇 **常規** 從工具清單中按一下 **搜索Forms** 平鋪。

1. 在 **搜索Forms** ，選擇 **資產管理搜索欄**。

1. 按一下 **編輯**。
1. 在 **選擇謂詞** 頁籤 **屬性謂詞** 並在搜索表單中所需的位置拖放。

1. 在 **設定** 頁籤，提供新添加的 **屬性謂詞** 元件：

   - **欄位標籤**:UUID
   - **屬性名稱**:jcr:content/fmUuid
1. 按一下 **完成** 的子菜單。

   訪問「資產」UI中的「篩選器」選項時，將獲取基於UUIS的搜索篩選選項。


## 向用戶提供權限 {#id192SF0G0RUI}

需要向作者和發佈者授予明確權限，以便能夠從資產UI訪問搜索功能。 如果您不授予這些權限，則用戶將無法根據其元素/屬性值或UUID搜索DITA內容。

執行以下步驟以提供對DITA搜索功能的訪問：

1. 訪問用戶和組權限頁。 訪問該頁的預設URL為：

   `http://<server name>:<port>/useradmin.html`

1. 搜索要向其授予訪問權限的用戶組或單個用戶。 例如，要授予對作者組中的所有用戶的訪問權限，請在 **篩選查詢** 欄位和按 **輸入**。

   ![](assets/authors-group-permission.png){width="350" align="left"}

1. 選擇 **作者** 組。

1. 在右窗格中，選擇 **權限** 頁籤。

1. 導航到以下資料夾位置：

   /conf/global/settings/dam/search

1. 提供 **閱讀** 權限。

   ![](assets/read-permission-authors.png){width="650" align="left"}

1. 按一下「**儲存**」。


所選用戶或用戶組現在將有權訪問資產UI中的搜索DITA內容功能。

## 在搜索中添加自定義元素或屬性 {#id192SF0G10YK}

要使DITA搜索工作，需要對DITA內容進行一些預處理。 此預處理步驟從單個DITA映射和主題中提取選擇性內容，以便可以對其進行索引，以便更快地搜索。 在內部，此過程稱為 *序列化*。 DITA檔案的序列化在內容上載期間進行，也可以按需執行。 它使用配置檔案來確定每個DITA檔案中應索引多少內容。 序列化檔案的預設位置是：

/libs/fmdita/config/serializationconfig.xml

預設搜索配置允許您搜索DITA中的所有元素和屬性 `prolog` 的子菜單。 如果要根據其他元素或屬性進行搜索，則需要配置搜索序列化檔案。

>[!NOTE]
>
> 如果要在 `prolog` 元素，然後可以跳過此進程。

此檔案包含兩個主要部分 — 屬性集和規則集。 下面提供了規則集節的代碼段：

```XML
<ruleset filetypes="xml dita"><!-- Element rules --><rule xpath="//[contains(@class, 'topic/topic')]/[contains(@class, 'topic/prolog')]//*[not(*)]" text="yes" attributeset="all-attrs" /><!-- Attribute rules --><rule xpath="//[contains(@class, 'topic/topic')]/[contains(@class, 'topic/prolog')]///@[local-name() != 'class']" /></ruleset>
```

在規則集部分中，可以指定：

- 提取元素的規則

- 提取屬性的規則


規則由以下部分組成：

xpath :這是從DITA檔案檢索元素或屬性的XPath查詢。 元素規則的預設配置將檢索所有 `prolog` 元素。 而且，屬性規則的預設配置將檢索 `prolog` 元素。 可以指定XPath查詢以序列化要搜索的元素或屬性。

    XPath查詢包含文檔類型的類名。 主題/主題類用於主題類型DITA文檔。 如果要為其他DITA文檔建立規則，則必須使用以下類名：
    
    |文檔類型|類名|
    |—|
    |主題| — 主題/主題|
    |任務| — 主題/主題任務/任務|
    |概念| — 主題/主題概念/概念|
    |引用| — 主題/主題引用/引用|
    |映射| — 映射/映射|

文本：如果要搜索指定元素中的文本，請指定yes值。 如果指定「否」為值，則只序列化元素中的屬性。 需要在屬性集節中指定要搜索的屬性。

屬性集：指定要與此規則關聯的屬性集的ID。 值all-attrs是一個特殊情況，用於指示必須序列化此規則的所有屬性。

屬性集包含要在DITA內容中搜索的屬性清單。 屬性集包含以下內容：

id :屬性集的唯一標識符。 此ID在規則集的屬性集參數中指定。

屬性：要搜索的屬性清單。 對於每個屬性，您需要在 `attribute` 的子菜單。

執行以下步驟以在搜索序列化檔案中添加自定義DITA元素或屬性：

1. 登錄並AEM開啟CRXDE Lite模式。

1. 導航到以下位置可用的序列化配置檔案：

   /libs/fmdita/config/serializationconfig.xml

1. 建立的覆蓋節點 `config` 資料夾 `apps` 的下界。

1. 導航到中可用的配置檔案 `apps` 節點：

   `/apps/fmdita/config/serializationconfig.xml`

1. 添加所需元素或屬性規則集。

1. 儲存檔案。

1. 開啟「Adobe Experience ManagerWeb控制台配置」頁。 訪問配置頁的預設URL為：

   http://&lt;server name=&quot;&quot;>:&lt;port>/system/console/configMgr

1. 搜索並按一下 *com.adobe.fmdita.config.ConfigManager* 捆綁。

1. 按一下「**儲存**」。


儲存並激活新的序列化資訊以進行搜索。 但是，必須從現有DITA內容中提取元資料，才能使其可用於搜索。

## 從現有內容中提取元資料 {#id192SF0GA0HT}

在預設搜索序列化檔案中進行任何更改後，必須在 *com.adobe.fmdita.config.ConfigManager* 綁定，然後運行工作流以提取元資料。 此操作將從現有DITA檔案中提取所需的元資料，然後將其用於搜索。

如果在更新序列化檔案後建立新檔案或編輯任何檔案，則會自動從這些檔案中提取元資料。 只有儲存庫中已存在的檔案才需要提取元資料的AEM過程。

從現有DITA檔案中提取元資料涉及兩個任務：

1. 在configMgr中啟用元資料提取選項
1. 運行元資料提取工作流

執行以下步驟以在configMgr中啟用元資料提取選項：

1. 開啟「Adobe Experience ManagerWeb控制台配置」頁。 訪問配置頁的預設URL為：

   http://&lt;server name=&quot;&quot;>:&lt;port>/system/console/configMgr

1. 搜索並按一下 *com.adobe.fmdita.config.ConfigManager* 捆綁。

1. 選擇 **啟用DITA元資料提取** 的雙曲餘切值。

1. 按一下「**儲存**」。


執行以下步驟以運行元資料提取工作流：

1. 以管理員身份登錄Adobe Experience Manager。

1. 按一下 **Adobe Experience Manager** 在頂部連結，然後選擇 **工具**。

1. 選擇 **參考線** 按一下 **DITA元資料提取** 平鋪。

1. 如果要從單個檔案及其依賴關係中提取元資料，請按一下 **選擇檔案** 連結並瀏覽檔案。

1. 如果要從資料夾內的多個檔案中提取元資料，請按一下 **選擇資料夾\(s\)** 連結，瀏覽並選擇所需的資料夾。 按一下 **添加** 按鈕，將資料夾添加到序列化任務清單。

   >[!NOTE]
   >
   > 您可以選擇多個資料夾並將其添加到序列化任務。

1. 按一下 **開始**。

1. 在「確認元資料提取」對話框中，按一下 **確定**。


## 從搜索結果中排除臨時檔案 {#id197AHI0035Z}

預設情況下，搜索將在的整個儲存庫上執AEM行。 可能有一些位置您希望從搜索中排除。 例如，在啟動內容翻譯工作流時，未批准的檔案將保留在臨時資料夾位置。 執行搜索時，此臨時位置的檔案也會在搜索結果中返回。

要防止AEM參考線搜索臨時翻譯資料夾位置，您需要在排除清單中添加臨時資料夾位置。

執行以下步驟以從搜索中排除臨時翻譯資料夾：

>[!NOTE]
>
> 您可以使用此過程將任何其他資料夾位置添加到排除清單中。

1. 登錄並AEM開啟CRXDE Lite模式。

1. 導航到位於以下位置的damAssetLucene節點：

   /oak:index/damAssetLucene

1. 在damAssetLucene節點中添加以下屬性：

   | 屬性名稱 | 類型 | 值 |
   |-------------|----|-----|
   | 排除的路徑 | 字串\[\] | 將以下值添加到此屬性： <br>/content/dam/projects/translation\output |

1. 導航到以下位置可用的lucene節點：

   /oak：索引/lucene

1. 在lucene節點中添加以下屬性：

   | 屬性名稱 | 類型 | 值 |
   |-------------|----|-----|
   | 排除的路徑 | 字串\[\] | 將以下值添加到此屬性： <br><ul><li>/var/dxml</li><li>/content/dam/projects/translation\output</li></ul> |


