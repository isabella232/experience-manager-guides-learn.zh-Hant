---
title: 上載現有DITA內容
description: 瞭解如何上載現有DITA內容
source-git-commit: 5ac066bb8db32944abd046f64da11eeb1bdbe467
workflow-type: tm+mt
source-wordcount: '1200'
ht-degree: 0%

---


# 上載現有DITA內容 {#id176FF000JUI}

您很可能擁有一個儲存有要與指南一起使用的現有DITA內容的存AEM儲庫。 對於此類現有內容，您可以使用以下任何方法將內容批量上載到儲存AEM庫。

## 使用WebDAV工具

如果您正在任何其他DITA編輯器中創作主題和映射，則可以使用任何WebDAV工具上載檔案。 本節中提供的過程使用WinSCP作為WebDAV工具來上載內容。

執行以下步驟以使用WinSCP上載檔案：

1. 在您的電腦上下載並安裝WinSCP。

1. 啟動WinSCP應用。

   此時將顯示「登錄」對話框。

1. 在「登錄」對話框中，通過選擇WebDAV作為 **檔案協定** 及提供其他連接詳情，如：

   - 伺服器AEM的URL,

   - 埠號\（預設為4502\）,

   - 訪問伺服器的用戶名和密碼AEM。

1. 按一下「**登入**」。

   成功連接後，您將在WinSCP用戶介面中看到AEM Assets的內容。 使用WinSCP檔案瀏覽器，您可以輕鬆瀏覽、建立、更新或刪除內容。


## 使用FrameMaker

Adobe FrameMaker提供了AEM一個功能強大的連接器，使您能夠輕鬆地將現有的DITA和其他FrameMaker文檔\(.book和.fm\)上傳到AEM中。 可以使用各種檔案上載功能，如上載單個檔案、上載包含或不包含依賴項的完整資料夾\（如內容引用、交叉引用和圖形\）。

執行以下步驟以使用FrameMaker的AEM連接器上載內容：

1. 啟動FrameMaker。

1. 開啟 **連接管理器** 對話框。

   ![](assets/fm-aem-connector.png){width="550" align="left"}

1. 輸入以下詳細資訊以連接到存AEM儲庫：

   - **名稱**:輸入描述性名稱以標識到伺服器AEM的連接。
   - **伺服器**:輸入伺服器的URL和端AEM口號。

   - **用戶名**/**密碼**:輸入用戶名和密碼以訪問服AEM務器。

1. 按一下 **連接**。

   成功建立連接後，「儲存庫管理器」(Repository Manager)窗AEM口中將顯示儲存庫中的「資產」(Assets)。

   ![](assets/fm-repo-manager.png){width="550" align="left"}

   按一下右鍵任何檔案或資料夾可以執行相關操作。 例如，如果按一下右鍵某個資料夾，則可獲取以下選項：上載檔案、上載具有依賴關係的檔案、上載整個資料夾等。


## 配置UUID檔案名模式

導入內容時，檔案名不必基於UUID。 在使用基於UUID的檔案名的系統中，必須使用其UUID而不是原始檔案名引用所有檔案。 如果導入的檔案沒有基於UUID的檔案名，則可以配置系統以將UUID添加到其file屬性中。 然後，此UUID用於引用此類檔案，其中UUID不用於命名檔案。

執行以下步驟，根據UUID模式檢查檔案名，並將UUID分配給未分配UUID的檔案：

1. 開啟「Adobe Experience ManagerWeb控制台配置」頁。

   訪問配置頁的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索並按一下 *com.adobe.fmdita.config.ConfigManager* 捆綁。

1. 在 **UUID檔案名模式** 屬性，指定一個模式以檢查導入的檔案的名稱。

   如果檔案不遵循指定的模式，則會將UUID添加到檔案的屬性中，並使用分配給該檔案的UUID更新對檔案的所有引用。

1. 按一下「**儲存**」。


## 使用WebDav工具以UUID上載內容 {#id201MI0I04Y4}

可以使用以下任何方法以UUID上載內容：

- 從本地系統拖放內容。
- 使用 **建立** \> **檔案** 工作AEM流。
- 使用WinSCP等工具。

如果您使用WinSCP等工具，則可以通過設定 **將具有相同UUID的舊檔案移動到新資料夾** 選項。 此選項定義對儲存庫中其他位置可用的檔案執行的AEM操作。 此設定在 *com.adobe.fmdita.config.ConfigManager* configMgr中的包。

預設情況下， **將具有相同UUID的舊檔案移動到新資料夾** 選項。 這意味著當要上載的檔案存在於儲存庫中的其他資料夾中時，現有檔案將被移動到當前位置，並被正在上載的檔案覆蓋。 如果未選擇此選項，則檔案將覆蓋其現有位置。

**有關使用基於UUID的檔案的附加說明**:

在儲存庫中移動或複製內容時必須考慮以AEM下幾點：

- 當將一個或多個檔案從一個位置複製到另一個位置時，將為沒有任何UUID的檔案生成新的UUID。 此UUID將添加到檔案的元資料中。

- 如果檔案有衝突或有重複檔案，則會為正在複製或移動的新檔案生成唯一的檔案名。

- 兩個檔案不能具有相同的UUID。 所有新檔案都分配了唯一UUID。


將內容從本地系統移動或複製到儲存庫時，必須考慮以AEM下幾點：

- 如果兩個不同的用戶同時上載檔案，則稍後處理的檔案將覆蓋以前的檔案。 但是，這種做法很少，應該避免。

- 當您從儲存庫中籤AEM出內容並在本地系統上進行更改時，請確保上載檔案時沒有更改檔案名。


## 使用curl命令

您還可以使用curl命令在DAM中建立資料夾、上載檔案以及在上載的內容上添加元資料。

**建立資料夾**

運行以下命令在儲存庫中建立AEM資料夾：

```curl
curl --user <username>:<password> --data jcr:primaryType=sling:Folder "<server folder path>"
```

指定以下參數以建立資料夾：

- `<username>:<passowrd>`:指定訪問儲存庫的用戶名和密碼AEM。 此用戶必須具有資料夾建立權限。

- `jcr:primaryType=sling:Folder`:指定此參數 *為* 建立資料夾類型資源。

- `<server folder path>`:完整的資料夾路徑，包括要在儲存庫中建立的新資料夾AEM的名稱。 例如，如果將路徑指定為 `http://192.168.1.1:4502/content/dam/projects/AEM-Guides`，則 `AEM-Guides` 在 `projects` 資料夾。


**上載檔案**

運行以下命令以上載儲存庫中的AEM檔案：

```curl
curl --user <username>:<password> -T "<local file path>" "<server folder path>"
```

指定以下參數以上載檔案：

- `<username>:<passowrd>`:指定訪問儲存庫的用戶名和密碼AEM。 此用戶必須對 `server folder path`。

- ``local file path``:完成要上載的本地系統上的檔案路徑。

- `<server folder path>`:要上載檔案的AEM伺服器上的完整資料夾路徑。


**添加元資料**

運行以下命令以在檔案上添加元資料：

```curl
curl --user <username>:<password> -F<attribute name>=<value> <metadata node path>
```

指定以下參數以添加元資料資訊：

- `<username>:<passowrd>`:指定訪問儲存庫的用戶名和密碼AEM。 此用戶必須對 ``metadata node path``。

- ``-F<attribute name>=<value>``:的 `<attribute name>` 是元資料屬性的名稱，如 `audience` 和 `<value>` 可能 `internal`。 可以指定多個按空格分隔的屬性名稱 — 值對。

- `<metadata node path>`:完整的資料夾路徑，包括檔案名及其元資料節點。 例如，如果將路徑指定為 `http://192.168.1.1:4502/content/dam/projects/AEM-Guides/intro.xml/jcr:content/metadata`，然後設定指定的元資料資訊 `intro.xml` 的子菜單。


**父主題：**[&#x200B;遷移現有內容](migrate-content.md)

