---
title: 版本管理
description: 瞭解版本管理的工作原理
source-git-commit: 5ac066bb8db32944abd046f64da11eeb1bdbe467
workflow-type: tm+mt
source-wordcount: '1657'
ht-degree: 0%

---


# 版本管理 {#id181GB000XY4}

版本控制是任何內容管理系統的一個重要方面。 它允許您在特定時間點建立數字資產的快照。 如果已部署了數字資產的版本，則可以恢復該資產的所需版本並對其進行更新。 通常，為建立任何資產的版本，您需要簽出和簽入所需資產。

作為管理員，您可以強制實施規則，限制用戶編輯檔案而不簽出檔案。 同樣，您可以確保所有簽出的檔案都被簽回，以避免任何資料丟失。

在多用途環境中，確保用戶不會從系統中刪除檔案也很重要。 對於其他用戶簽出的檔案，此要求更為重要。您可以允許或阻止用戶覆蓋其他用戶簽出的檔案。 為防止用戶意外從系統中刪除簽出的檔案，AEM「參考線」提供了可使用的配置。 除簽出檔案外，還可以控制刪除包含引用或從其他檔案引用的檔案。 此外，您還可以為上載的檔案建立新版本。

## 為上載的檔案建立新版本

>[!NOTE]
>
> 此配置僅在上載檔案時適用。

要建立已上載檔案的新版本，請執行以下步驟：

1. 開啟「Adobe Experience ManagerWeb控制台配置」頁。

   訪問配置頁的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索並按一下 **com.adobe.fmdita.config.ConfigManager** 捆綁。

1. 選擇 **為上載的檔案建立新版本** 的雙曲餘切值。

   預設情況下，此選項為OFF。

   當選中該選項時，將執行新版本管理機制並覆蓋預設上載行為（用於任何後續上載），它將將上載檔案的內容另存為新版本。 如果取消選中該選項，AEM則參考線使AEM用預設版本管理機制。

1. 按一下「**儲存**」。


>[!NOTE]
>
> 如果啟用該屬性，則可以按70批或更少的批次上載檔案 **為上載的檔案建立新版本** \(create.ver.new.content\)並使用 **資產UI**&#x200B;批量上載資產。

## 配置設定以允許編輯簽出的檔案

使用AEM指南的Web編輯器可以建立和更新DITA主題。 您可以配置Web編輯器，以僅允許編輯從儲存庫中籤出的文檔。 這可確保沒有其他作者意外覆蓋另一個作者開啟的要編輯的主題。 開啟主題進行編輯後，作者可以在關閉檔案時簽入檔案。

另一個重要規則是確保已簽出的檔案已簽回系統。 這可以防止用戶在不重新簽入檔案的情況下意外關閉檔案。

執行以下步驟以啟用這些功能：

1. 開啟「Adobe Experience ManagerWeb控制台配置」頁。

   訪問配置頁的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索並按一下 **com.adobe.fmdita.xmleditor.config.XmlEditorConfig** 捆綁。

1. 選擇 **禁用「編輯而不簽出」** 的雙曲餘切值。

   ![](assets/xml-editor-config.png){width="650" align="left"}

   使用此選項，用戶在簽出檔案之前將看不到工具欄中的「編輯」選項。

1. 選擇 **在關閉時請求籤入** 選項，在關閉簽出檔案時顯示警告消息，但不保存或將其簽回儲存庫。

1. 按一下「**儲存**」。


>[!NOTE]
>
> 無論您是開啟還是關閉此功能，「檢出」(Check Out)和「檢入」(Check In)選項始終在主題預覽中可用。

## 上載時覆蓋簽出的檔案

>[!NOTE]
>
> 此配置僅在您從資產UI建立檔案時才適用，而在您使用WebDAV工具上載檔案時則不適用。

要允許用戶在上載時覆蓋已由其或其他用戶簽出的檔案，請執行以下步驟：

1. 開啟「Adobe Experience ManagerWeb控制台配置」頁。

   訪問配置頁的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索並按一下 **com.adobe.fmdita.config.ConfigManager** 捆綁。

1. 選擇 **上載時覆蓋簽出的檔案** 的雙曲餘切值。

   預設情況下，此選項為「開啟」。 選中此選項後，用戶將能夠覆蓋簽出的檔案。 如果未選中該選項，則如果檔案被其或某些其他用戶簽出，則會阻止覆蓋該檔案。

1. 按一下「**儲存**」。


## 防止刪除簽出的檔案

要防止用戶意外刪除已由其或其他用戶簽出的檔案，請執行以下步驟：

1. 開啟「Adobe Experience ManagerWeb控制台配置」頁。

   訪問配置頁的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索並按一下 **com.adobe.fmdita.xmleditor.config.XmlEditorConfig** 捆綁。

1. 選擇 **防止刪除已簽出內容** 的雙曲餘切值。

   預設情況下，此選項為「開啟」。 如果選擇此選項，用戶將無法刪除已簽出的檔案。

1. 按一下「**儲存**」。


要支援此功能，請使用新的索引屬性 `drivelock` 已添加到 `oak:index`:

`/oak:index/damAssetLucene/indexRules/dam:Asset/properties/drivelock`

![](assets/index-property-oak-index-drivelock.png){width="800" align="left"}

除了新索引屬性外，請確保以下屬性已設定為 `/oak:index/damAssetLucene`:

- `jcr:primaryType`=`"oak:QueryIndexDefinition"`
- `async`=`"async"`
- `compatVersion`=`"{Long}2"`
- `evaluatePathRestrictions`=`"{Boolean}true"`
- `reindex`=`"{Boolean}false"`
- `reindexCount`=`"{Long}3"` *\（這是重複索引完成多少次的計數，將替換為安裝軟體包\）*
- `type`=`"lucene"`

>[!NOTE]
>
> 您可以更改 `reindex` 至 `"{Boolean}true"`。 這將加快資料夾層次結構中籤出檔案的搜索結果的速度。

## 防止刪除引用的檔案

作為管理員，您可以控制哪些人可以從儲存庫中刪AEM除檔案。 具體來說，如果某個檔案包含引用或被某些其他檔案引用，則可以定義可以刪除此類檔案的人。

使用此配置，您可以允許或禁止所有用戶刪除檔案，或者只允許特定用戶組刪除檔案。 如果允許刪除檔案，則執行以下過程：

- 如果要刪除包含所有引用和引用檔案的資料夾，則會刪除所有檔案。 該過程將首先刪除不包含任何引用的所有檔案，然後刪除包含引用或被引用的檔案。

- 如果正在刪除資料夾，且資料夾內的任何檔案都被該資料夾外的檔案引用，則在刪除該檔案之前，系統將提示您刪除該引用。


要定義可以刪除包含引用或被其他檔案引用的檔案的人員，請執行以下步驟：

1. 開啟「Adobe Experience ManagerWeb控制台配置」頁。

   訪問配置頁的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索並按一下 **com.adobe.fmdita.config.ConfigManager** 捆綁。

1. 查找 **阻止刪除引用的資產** 的雙曲餘切值。

1. 根據您要授予刪除訪問權限的對象，指定以下常數之一：

   - allow\_unsafe\_delete\_for\_all:授予所有用戶刪除檔案的權限。 在這種情況下，如果檔案\(s\)包含引用或被其他檔案引用，則也可以強制刪除此類檔案\(s\)。 在刪除檔案之前，將顯示帶有引用的提示，您可以取消刪除操作、刪除引用，然後最後刪除檔案\(s\)。 或者，可以強制刪除檔案\(s\)而不刪除引用。

      ![](assets/allow_unsafe_delete-force-delete.PNG){width="550" align="left"}

   - allow\_unsafe\_delete\_for\_delete\_assets\_group:管理員或屬於 *刪除資產* 允許組刪除檔案。 如果任何其他用戶嘗試刪除帶有任何引用的檔案，則在刪除所有引用之前，不允許他們刪除這些檔案。 當沒有權限的用戶嘗試刪除檔案時，將顯示以下螢幕截圖。

      ![](assets/allow_unsafe_delete_for_delete_assets_group.PNG){width="550" align="left"}

   - block\_unsafe\_delete\_for\_all:在刪除對檔案\(s\)的引用之前，不允許所有用戶\（包括管理員\）刪除檔案。

1. 按一下「**儲存**」。


## 清除舊版本的DITA檔案

更新內容並建立新版本時，DITA檔案的早期版本將保留在儲存庫中。 許多版本可能會在一段時間內為您的DITA檔案建立，並且可能會共同佔用儲存庫中的大量空間。 使AEM用指南可以配置應從儲存庫中刪除的舊版本。

如果您具有管理權限，則可以使用給定的URL訪問此實用程式：

`<server folder path> /libs/fmdita/clientlibs/xmleditor_version_purge/page.html`

維護並未清除滿足任何給定條件的DITA檔案的版本：

- 是檔案的第一個版本
- 包含在基線中
- 包含在任何翻譯或審閱工作流中
- 已對其應用標籤
- 滿足已定義的年齡或版本標準數

執行以下步驟清除舊版本：

1. 輸入有關要清除的檔案的以下詳細資訊：

   ![](assets/preview-purge-report.png){width="350" align="left"}

1. 
   - **要從最新版本保留的版本數**:輸入應保留且未清除的版本數。 例如，如果輸入5，則保留最後5個版本，並且在滿足其它清除條件時，保留前5個版本。
- **保留在時間範圍內建立的版本\（以天為單位\）**:輸入版本的最大年限（天）。 在滿足其他清除條件時，超過給定天數的版本將被限定清除。 例如，如果輸入100，則在滿足其它清除條件時，所有在100天前建立的版本都被限定為清除。
- **路徑**:選擇要清除其檔案的檔案或資料夾的路徑。

   >[!NOTE]
   >
   > 您只能清除DITA檔案。

1. 按一下 **預覽清除報表**。

   >[!NOTE]
   >
   > 一次只能執行一個清除任務。 如果正在執行另一個版本清除操作，則無法啟動該操作。

   將生成版本清除報告。

1. 下載版本清除報告並檢查要清除的檔案和版本。
1. 您可以選擇 **取消清除** 或 **開始清除**。

   ![](assets/download-purge-report.png){width="350" align="left"}

   將顯示清除狀態。

   按一下 **下載版本清除報告** 的子菜單。 此報表提供所有版本的清除狀態以及特定版本保留的原因或清除原因。


>[!NOTE]
>
> 報告將在以下位置下載：/var/dxml/versionpurge

