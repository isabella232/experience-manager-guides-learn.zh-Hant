---
title: 用於Adobe Experience Manager指南的氧插件
description: 瞭解如何使用《Adobe Experience Manager指南》的氧插件建立和管理您的內容。
hide: true
hidefromtoc: true
exl-id: 2db9a34e-2efa-47ad-ba6b-02afc5197669
source-git-commit: 8073716bccacbe8d6a158b44d5106b083e3a5dcd
workflow-type: tm+mt
source-wordcount: '5762'
ht-degree: 0%

---

# 用於Adobe Experience Manager指南的氧插件 {#id1645H6010Q5}

「Adobe Experience Manager指南的氧氣插件」\(後稱「指南」中的「指南的氧氣插件」\AEM)使您能夠將Ox XML作者與Adobe Experience Manager的\(AEM\)儲存庫連接，以便創作和管理內容。 您可以使用插件瀏覽、搜索和開啟檔案；簽入檔案；上載儲存庫上的資料夾AEM和檔案。 案頭應AEM用程式中的「參考線」面板允許您將所需的資料夾\（從儲存庫\）標籤到最AEM喜愛的資料夾清單，以便快速訪問。 此外，您可以在Web介面AEM中安裝軟體包，並直接從Web介面開啟Oxon XML Author中的AEMDITA檔案。

## 下載並安裝 {#id1826M0L0PUI}

指南的氧氣插AEM件可通過Adobe軟體分發門戶提供。 在「Experience Manager」頁籤中搜索「ox」，然後從您的 [Adobe軟體分發門戶](https://experience.adobe.com/#/downloads/content/software-distribution/en/general.html)。

>[!NOTE]
>
>從發行說明中查看特定Adobe Experience Manager指南的氧連接器版本相容性。

安裝完安裝程式後，請將其安裝到安裝Oxion XML Author的本地電腦上。 在開始安裝過程之前，必須確保您的系統滿足安裝指南氧插件的技AEM術要求。

### 技術要求

- Oxy XML作者版本24.1

- Adobe Experience Manager指南3.4版或更高版本

- Adobe Experience Manager6.5版，帶Service Pack 10、11、12和13

- Oxon XML Author版本24.1支援的作業系統

- Java開發工具包
   - OracleSE 8 JRE 1.8

### 在Windows上安裝插件

>[!IMPORTANT]
>
>如果系統上安裝了較舊版本的插件，請確保在啟動安裝過程之前卸載該插件。 查看 **正在卸載包** 的 [如何使用包](https://helpx.adobe.com/tw/experience-manager/6-4/sites/administering/using/package-manager.html) 卸載說明的文章。

在安裝了Oxon XML Author的系統上執行以下步驟：

1. 啟動安裝程式 `.exe` 的子菜單。

   出現安裝嚮導的歡迎螢幕。

1. 按一下 **下一個** 並瀏覽到Oxon XML Author的.exe檔案可用的位置。

1. 選擇檔案，然後按一下 **開啟**。

   選定檔案的位置將添加到安裝嚮導中。

1. 按一下&#x200B;**下一步**。

1. 按一下 **安裝**。

1. 按一下 **完成** 關閉安裝嚮導。
1. 啟動Oxion XML作者。

   「Oxing XML AuthorAEM（氧XML作者）」中顯示「Guides（參考線）」面板。

   ![](images/oxygen-aem-connector.png)

   >[!NOTE]
   >
   >如果未看到「參考線」面AEM板，請參閱故障排除部分 — [「缺少AEM參考線」面板](#id192BH200ZAX)。


### 在Mac上安裝插件

>[!IMPORTANT]
>
>如果系統上安裝了較舊版本的插件，請確保在啟動安裝過程之前卸載該插件。 查看 **正在卸載包** 的 [如何使用包](https://helpx.adobe.com/tw/experience-manager/6-4/sites/administering/using/package-manager.html) 文章卸載說明。

在安裝了Oxon XML Author的系統上執行以下步驟：

1. 在系統上找到插件的.dmg檔案。

1. 按兩下.dmg檔案以開啟檔案內容。

   .dmg檔案包含aem-connector-x.x資料夾和aem-connector-x.x-setup檔案。

   >[!NOTE]
   >
   >檔案名中的x.x是插件的版本號。

1. 將aem-connector-x.x資料夾複製到Oxon XML Author的插件資料夾中。
1. 按兩下aem-connector-x.x-setup檔案以啟動安裝程式。

1. 啟動Oxion XML作者。

   「Oxing XML AuthorAEM（氧XML作者）」中顯示「Guides（參考線）」面板。

   ![](images/oxygen-aem-connector-mac.png)

   >[!NOTE]
   >
   >如果未看到「參考線」面AEM板，請參閱故障排除部分 — [「缺少AEM參考線」面板](#id192BH200ZAX)。


### 安裝包以從Web介面啟用文檔編AEM輯功能 {#id182CE0Q0TY4}

作為作者，您可以直接從Web介面開啟和編輯Oxing XML Author中的DITA映射AEM或主題。 要在Web介面中啟AEM用此功能，AEM管理員需要在創作實例中安AEM裝包。

作為AEM管理員，請執行以下步驟來安裝軟體包：

1. 從您的IT團隊獲取包的.zip檔案。
1. 登錄實AEM例 *\（作為管理員\）* 並導航到CRX包管理器。 訪問包管理器的預設URL為

   `http://<server name>:<port>/crx/packmgr/index.jsp`

   包管理器管理本地安裝上的AEM包。 有關使用包管理器的詳細資訊，請參見 [如何使用包](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developer-tools/package-manager.html?lang=en) 的上AEM界。

   ![](images/package-manager.png)

1. 要上載氧包，請按一下 **上載包**。
1. 在上載包對話框中，導航到您在步驟1中下載的氧包檔案，然後按一下確定。

   包已上載到實例AEM中。

1. 要啟動安裝過程，請按一下 **安裝**。

   ![](images/oxygen-package.png)

1. 在「安裝包」對話框中，按一下 **安裝**。
1. 安裝完成後，按一下CRX包管理器左上角的「首頁」按鈕。
1. 在資產資料夾中選擇DITA檔案。

   **在氧氣中編輯** 的上界。 有關使用此選項的詳細資訊，請參見 [從Web介面開啟Oxon XML作者中AEM的DITA主題](#id182CE0I905Z)。

   >[!NOTE]
   >
   >的 **在氧氣中編輯** 選項在選擇一個DITA主題時可見。 如果選擇多個主題，則選項將不可見。


## 配置指南的氧插AEM件 {#id1826KF00AHS}

下載並安裝該插件後，您需要配置以下元件以使用該插件：

- **Web身份驗證設定**:指南插件中SSO驗證的AEM設定。
- **常規設定**:插件的連接設定，如AEM伺服器URL、登錄詳細資訊等。
- **效能分析屬性自定義的首選項**:文檔集的效能分析屬性方案需要此配置。

### Web身份驗證設定

JxBrowser用於由Oxon連接器插件進行SSO驗證。 它是基於鉻的瀏覽器。 對於Java 9+對非公共API的訪問是必需的，並且您必須明確授予對JxBrowser的此訪問權限。 有關詳細資訊，請參閱 [JxBrowser故障排除](https://jxbrowser-support.teamdev.com/docs/guides/troubleshooting/issues.html)。

更新給定檔案以配置指南的氧插件中的Web驗證AEM設定：

>[!NOTE]
>
>在更新檔案之前，請備份該檔案。

**Mac和氧氣24.1**

在env.sh中添加以下行

```java
--illegal-access=permit\
--add-opens=java.desktop/javax.swing.plaf.basic=ALL-UNNAMED\
--add-exports=javafx.controls/com.sun.javafx.scene.control=ALL-UNNAMED\
--add-exports=javafx.graphics/com.sun.javafx.stage=ALL-UNNAMED\
--add-exports=javafx.graphics/com.sun.javafx.scene=ALL-UNNAMED\
--add-exports=javafx.graphics/com.sun.javafx.scene.traversal=ALL-UNNAMED\
--add-exports=javafx.graphics/com.sun.javafx.tk=ALL-UNNAMED\
--add-exports=javafx.graphics/com.sun.glass.ui=ALL-UNNAMED\
--add-opens=javafx.graphics/com.sun.glass.ui=ALL-UNNAMED\
--add-opens=javafx.graphics/javafx.stage=ALL-UNNAMED\
--add-opens=javafx.graphics/com.sun.javafx.tk.quantum=ALL-UNNAMED\
--add-exports=java.desktop/sun.awt=ALL-UNNAMED\
--add-opens javafx.swing/javafx.embed.swing=ALL-UNNAMED
```

在oxonAuthor.sh中添加以下行

```java
-Djdk.module.illegalAccess=permit\-Djava.ipc.external=true\
```

**對於Windows和Oxon 24.1**

在env.bat中添加以下行

```java
--illegal-access=permit --add-opens=java.desktop/javax.swing.plaf.basic=ALL-UNNAMED --add-exports=javafx.controls/com.sun.javafx.scene.control=ALL-UNNAMED --add-exports=javafx.graphics/com.sun.javafx.stage=ALL-UNNAMED --add-exports=javafx.graphics/com.sun.javafx.scene=ALL-UNNAMED --add-exports=javafx.graphics/com.sun.javafx.scene.traversal=ALL-UNNAMED --add-exports=javafx.graphics/com.sun.javafx.tk=ALL-UNNAMED --add-exports=javafx.graphics/com.sun.glass.ui=ALL-UNNAMED --add-opens=javafx.graphics/com.sun.glass.ui=ALL-UNNAMED --add-opens=javafx.graphics/javafx.stage=ALL-UNNAMED --add-opens=javafx.graphics/com.sun.javafx.tk.quantum=ALL-UNNAMED --add-exports=java.desktop/sun.awt=ALL-UNNAMED --add-opens javafx.swing/javafx.embed.swing=ALL-UNNAMED
```

在oxonAuthor.bat中添加以下行

```java
-Djdk.module.illegalAccess=permit -Djava.ipc.external=true
```

>[!NOTE]
>
>您需要以管理員身份為Mac運行oxAuthor.sh和oxAuthor.bat，用於Windows。

### 一般設定

執行以下步驟，在「Oxon Plugin for Guides(Adobe Experience Manager指南的氧氣插件)」中配置連接設定：

1. 在「參考AEM線」面板中，按一下設定表徵圖，然後選擇 **設定**。

   ![](images/settings.png)

1. 指定以下詳細資訊：
   - **伺服器URL**:伺服器AEM的URL，例如：

      ```http
      http[s]://<host>:<port>
      ```

      在上述URL中，指定部署伺服器的伺服器的主機名AEM和埠。

      >[!IMPORTANT]
      >
      >如果AEM伺服器部署在埠80或443上，則無需在URL中指定它。

   - **身份驗證：** 從 **基本\（用戶名/密碼\）** 或 **Web身份驗證**。 如果您選擇 **基本** 需要輸入的驗證 **用戶名** 和 **密碼** 的子菜單。

      如果選擇Web身份驗證，則將顯示「登錄」AEM螢幕。 輸入登錄憑據，然後按一下 **登錄** 按鈕 成功登錄後，「登AEM錄」螢幕將關閉，AEM「參考線」面板將顯示伺服器的文AEM件清單。

   - **連接超時**:指定客戶端等待伺服器響應的時間(秒AEM)。 如果在指定時間內未收到來自伺服器的響應，則終止請求。 預設值為20秒。

   - **本地資料夾**:在簽出後儲存儲存庫中AEM檔案的本地電腦上的位置。 如果指定驅動器上不存在的位置，則插件將建立該位置。
   - **簽出時開啟檔案**:如果選中，則在簽出時開啟檔案。
   - **簽入時關閉檔案**:如果選中，則在簽入時關閉檔案。 在關閉檔案之前，將顯示一個彈出窗口，您可以在其中指定版本注釋。
   - **關閉檔案時顯示簽入對話框**:如果選中，則在關閉檔案時會顯示一個彈出窗口。 在彈出窗口中，您可以選擇簽入檔案或關閉檔案而不簽入。
   - **開啟時自動簽出檔案**:如果選中，按兩下某個檔案將自動將其檢出並開啟以供編輯。 如果檔案已簽出，則只需開啟以進行編輯。 如果未選擇此選項，則開啟沒有鎖定的檔案會以只讀模式開啟該檔案。
1. 按一下&#x200B;**「確定」**。

### 效能分析屬性自定義的首選項 {#id1827K0D0OHT}

您需要配置Oxon XML Author中的首選項，以使用與儲存庫中的DITA主題關聯的效能分析AEM屬性。

執行以下步驟以配置效能分析屬性：

1. 在Oxon XML作者中，按一下 **選項** \> **首選項**。
1. 在 **文檔類型關聯** 頁籤 **DITA**，然後按一下 **擴展**。

   ![](images/document_type_association.png)

1. 在 **類路徑** 頁籤中，選擇com.adobe.o2.connector **使用具有ID的插件的父類載入器** 下拉。

   ![](images/dita-extension.png)

1. 在 **擴展** 頁籤，進行以下更改：
1. 
   - 按一下 **選擇** 的 **作者擴展狀態偵聽器** 在 **單個擴展** 並在中選擇CustomAuthorExtensionStateListener - com.adobe.o2.framework.extn **類** 清單框。 按一下&#x200B;**「確定」**。
- 按一下 **選擇** 的 **作者自定義屬性值編輯器** 在 **單個擴展** 並選擇CustomValueEditor - com.adobe.o2.framework.extn **類** 清單框。 按一下&#x200B;**「確定」**。以下螢幕快照顯示已配置 **擴展** 頁籤，用於DITA主題：

   ![](images/dita-topic-extension-tab.png)

1. 按一下 **確定** 的子菜單。

### 配置DITA映射擴展

DITA映射擴展配置是從Web介面直接開啟Oxion XML Author中的映AEM射檔案所必需的。 這些配置與前面步驟中完成的效能分析屬性的配置類似。

執行以下步驟來配置DITA映射擴展：

1. 在Oxon XML作者中，按一下&#x200B;**選項** \> **首選項**。
1. 在 **文檔類型關聯** 頁籤 **DITA映射**，然後按一下 **擴展**。
1. 在 **類路徑** 頁籤中，選擇com.adobe.o2.connector **使用具有ID的插件的父類載入器** 下拉。
1. 在 **擴展** 頁籤，進行以下更改：
1. 
   - 按一下 **選擇** 的 **作者擴展狀態偵聽器** 在 **單個擴展** 並選擇CustomDITAMapAuthorExtensionStateListener - com.adobe.o2.framework.extn **類** 清單框。 按一下&#x200B;**「確定」**。
- 按一下 **選擇** 的 **作者自定義屬性值編輯器** 在 **單個擴展** 並選擇CustomValueEditor - com.adobe.o2.framework.extn **類** 清單框。 按一下&#x200B;**「確定」**。
- *\（可選\）* 如果在開啟映射檔案時不想解析參照，則需要執行以下附加配置：

   按一下 **選擇** 的 **引用解析程式**&#x200B;在 **單個擴展** 並選擇CustomDITAMapReferenceResolver - com.adobe.o2.framework.extn **類** 清單框。 按一下&#x200B;**「確定」**。

   以下螢幕快照顯示已配置 **擴展** 頁籤：

   ![](images/dita-map-extension-tab.png)

1. 按一下 **確定** 的子菜單。

## 使用輔助線的氧氣插AEM件 {#id1826JG00WY4}

### AEM輔助線面板

下面的螢幕顯示「AEM參考線」面板。

![](images/connector-panel.png)

**A**\)顯示搜索欄。

**B**\)顯示「收藏夾」資料夾。 預設情況下為空。 您可以將儲存庫中的AEM資料夾添加為收藏夾，然後在此處顯示收藏夾。

**C**\)DAM資料夾顯示儲存AEM庫。 可以展開和折疊資料夾視圖。

**D**\)「設定」(Settings)「\(gear\)」表徵圖，其中包含以下選項：

- **連接**:選擇此選項以連接到服AEM務器。 當Oxon XML Author連接到伺服器時，該選項將被AEM禁用。
- **刷新**:選擇此選項可從儲存庫中獲取檔案和資料夾的最AEM新狀態。

   >[!NOTE]
   >
   >確保在刷新檔案之前保存檔案。 選擇時 **刷新** 選項，在刷新檔案之前，您會收到保存檔案的警告。 如果尚未保存檔案，可按一下 **取消** 並拯救他們。

- **設定**:可以使用此選項開啟插件的常規首選項對話框。
- **註銷**:選擇此選項可關閉服AEM務器連接。 此選項僅在您使用Web身份驗證模式時才可用。

### 上下文菜單函式

按一下右鍵儲存庫中的AEM資料夾或檔案後，可以使用「指南的氧插件」AEM功能。 資料夾可用的功能與檔案不同。 下面是「指南的氧氣插件」上下文菜單中AEM的完整功能清單：

- **開啟**:開啟選定檔案或展開選定資料夾。
- **開啟**:可以選擇在「參考線」的「Web編輯器」AEM、「映射儀表板」或「映射編輯器」中開啟選定檔案。 有關這些選項的詳細資訊，請參見 [在參考線編AEM輯器中開啟檔案](#id195GH0V30KX)。
- **簽出**:從儲存庫中籤出AEM檔案。 有關詳細資訊，請參閱 [簽出檔案](#id195HC020TS4)。
- **與家屬簽出**:檢出具有其直接引用的檔案。 有關詳細資訊，請參閱 [簽出檔案](#id195HC020TS4)。
- **使用只讀依存對象簽出**:檢出所選檔案及其依存對象。 不能對從屬檔案進行任何更改。 有關詳細資訊，請參閱 [簽出檔案](#id195HC020TS4)。
- **取消簽出**:取消簽出檔案，從編輯器關閉檔案，並將更改還原為伺服器上保存的檔案的最新版本。
- **刷新**:如果是檔案，則從儲存庫中讀取檔案的最新AEM副本。 對於資料夾，它將讀取資料夾結構和檔案的狀態。 這表示添加了檔案，然後將在「參考線視圖」AEM中顯示。 此外，如果在伺服器上簽出AEM檔案，則執行「在氧氣中刷新」將顯示檔案為簽出檔案。 但是，這不會更新 *在參考線中籤出的文AEM件* 。
- **刷新簽出的檔案**:刷新中已簽出檔案的清單 *在參考線中籤出的文AEM件* 。 如果在伺服器上簽出AEM檔案，則執行「刷新」將更新中已簽出檔案的清單 *在參考線中籤出的文AEM件* 。 但是，如果已添加新檔案或檔案的狀態已更改，則它不會在「參考線」樹視圖中更AEM新它。 要更新上的檔案狀態，AEM必須執行「刷新」。
- **簽入**:簽入已簽出的檔案。 有關詳細資訊，請參閱 [簽入檔案](#id182CF0J0FHS)。
- **與家屬簽入**:如果已簽出帶有依存對象的檔案，則此選項將簽入主檔案及其依存對象。 有關詳細資訊，請參閱 [簽入檔案](#id182CF0J0FHS)。
- **建立資料夾**:在儲存庫中創AEM建資料夾。 此選項僅在資料夾級別可用。
- **上載檔案\(s\)**:上載單個或多個檔案。 有關詳細資訊，請參閱 [上載檔案和資料夾](#id195HC03F03J)。
- **上載依存對象**:上載DITA檔案\（XML、DITA、帳簿映射或DITA映射\）及其從屬對象。 有關詳細資訊，請參閱 [上載檔案和資料夾](#id195HC03F03J)。
- **上載資料夾**:上載儲存庫上AEM的資料夾。 有關詳細資訊，請參閱 [上載檔案和資料夾](#id195HC03F03J)。
- **添加到收藏夾**:將資料夾添加到 *收藏夾* 資料夾AEM。 建議在此處添加您的工作資料夾，這樣便可更輕鬆地從中同步檔案和檔案的狀AEM態。
- **從收藏夾中刪除**:從中刪除資料夾 *收藏夾*。 有關詳細資訊，請參閱 [添加或刪除收藏夾](#id195HC04405P)。
- **查看元資料**:顯示元資料，如DITA類、文檔的標題、類型、UUID以及與檔案關聯的其他資訊。 有關詳細資訊，請參閱 [查看檔案的元資料](#id195GHN0H05C)。
- **查看版本**:顯示檔案的版本歷史記錄。 有關詳細資訊，請參閱 [查看檔案的版本歷史記錄](#id195GI000D5Q)。

### 在Oxon XML Author中開啟檔案 {#id195GHJ0A0UB}

連接到儲存庫後，AEM您可以在「Oxon XML作者」中開啟檔案進行編輯。 執行以下步驟以在「Oxon XML作者」中開啟要編輯的檔案：

1. 在「參考線」面板中右AEM鍵按一下要開啟進行編輯的檔案。

1. 選擇 **開啟** 的子菜單。

   檔案在Oxon XML Author的編輯器中開啟。

   ![](images/guid-in-file-tab.png)

   將滑鼠指針懸停在檔案的頁籤上時，將顯示伺服器路徑及其UUID。 在上面的螢幕快照中，將突出顯示文檔的UUID。


如果已選擇 **開啟時自動簽出檔案** 選項\（在「首選項」對話框\中），然後開啟檔案時，檔案將自動簽出並可供編輯。 要開啟檔案，可以按兩下檔案名或按一下右鍵檔案名並選擇 **開啟** 的子菜單。 如果未選擇此選項，則以只讀模式開啟檔案。

>[!NOTE]
>
>也可以按兩下檔案以將其開啟。

### 在參考線編AEM輯器中開啟檔案 {#id195GH0V30KX}

如果要使用「參考線」中提供的編輯AEM器，可以通過從上下文菜單中選擇所需選項來執行此操作。 執行以下步驟以AEM取代「Oxy XML Author」編輯器使用「Guides」編輯器：

1. 在「參考線」面板中右AEM鍵按一下要開啟進行編輯的檔案。

1. 選擇 **開啟** 從上下文菜單中選擇以下選項：

   - **Web主題編輯器**:如果要開啟的檔案是.xml或.dita檔案，則可以在Web編輯器中開啟該檔案進行編輯。 選擇 **Web主題編輯器** 選項，開啟在Web編輯器中編輯的選定檔案。

   - **映射儀表板**:您可以選擇在映射操控板中編輯.ditamap檔案，在其中可以對映射檔案執行各種操作。 這些操作取決於您所屬的角色/組。

   - **Web DITA映射編輯器**:如果要開啟.ditamap檔案以在「映射編輯器」中進行編輯，請選擇此選項。 使用DITA映射編輯器選項，可以添加或刪除主題、添加關係表以及在映射上執行其他操作。


### 簽出檔案 {#id195HC020TS4}

簽出檔案時，該檔案將本地儲存在系統上並鎖定在儲存庫中進行AEM編輯。 執行以下步驟以簽出檔案：

1. 在「參考線」面板中按一下右鍵AEM檔案。
1. 選擇以下選項之一：
   - **簽出：** 從儲存庫中籤AEM出檔案並使其可供編輯。
   - **與家屬簽出**:檢出具有其直接引用的檔案。 可以使用此選項在父頁和子頁中進行更改。 指南的氧AEM插件支援簽出一個級別的依存對象。 例如，映射引用主題A和主題A引用主題B。簽出映射A將簽出主題A，而不管其在TOC層次結構中的級別如何。 但是，它不會簽出主題B，因為它未直接從映射A連結。
   - **使用只讀依存對象簽出**:簽出檔案並將其依存對象作為只讀副本下載到本地電腦。 不能對從屬檔案進行任何更改。

如果已選擇 **簽出時開啟檔案** 選項\（在「首選項」對話框\中），然後簽出檔案時，檔案將自動開啟以進行編輯。

如果已選擇 **開啟時自動簽出檔案** 選項\（在「首選項」對話框\中），然後開啟檔案時，檔案將自動簽出並可供編輯。 要開啟檔案，可以按兩下檔案名或按一下右鍵檔案名並選擇 **開啟** 的子菜單。

簽出檔案時，檔案的表徵圖將更改以顯示其鎖定狀態。

![](images/check-out-file.png)

在上面的螢幕截圖中，其他用戶簽出的檔案顯示為黑色鎖表徵圖\(A\)。 當前用戶簽出的檔案顯示為綠色鎖定\(B\)。

>[!NOTE]
>
>如果已簽出檔案被刪除或移動到中的任何其AEM他資料夾，則在簽入檔案時會收到錯誤消息。 確保未使用Web介面移動或刪除已檢出AEM的檔案。

### 簽入檔案 {#id182CF0J0FHS}

簽入檔案時，系統的本地副本將儲存在儲存AEM庫中，並且檔案上的鎖將被移除。 執行以下步驟簽入檔案：

1. 通過按一下 **檔案** \> **保存**。

1. 按一下右鍵檢出檔案，然後從以下兩個選項中選擇：

   - **簽入**:將所選檔案從本地系統簽入到存AEM儲庫。
   - **使用依存對象簽入：** 如果已檢出檔案及其依存對象，則使用此選項在一個操作中檢入所有從屬檔案。 選擇此選項時，將顯示包含所有從屬檔案的「檢入」(Check in)對話框。 按一下「確定」(OK)以同時簽入所有檔案。

   如果尚未簽出相關檔案，然後選擇此選項，則只簽入已簽出\（單獨\）的相關檔案。 將顯示無法簽入的檔案清單：

   ![](images/check-in-error.png)

   強烈建議不要移動已簽出的檔案。 但是，如果檢出的檔案被移動到其他位置，則必須取消對該檔案的檢出。 如果要對該檔案進行更新，請再次簽出該檔案，進行更改，然後重新簽回。 如果嘗試簽入已從其原始位置移動的檔案，則會出錯。

   如果從屬檔案簽入，AEM則「與依存對象一起簽入」(Check in with Dependents)將不會在「簽入」(Check in)對話框中顯示從屬檔案。 要獲取已簽出的從屬檔案清單，AEM必須執行資料夾「刷新」。

   同樣，如果已通過簽入相關檔案，則在AEMOxon Author中，在執行「刷新和刷新簽出檔案」資料夾之前，不會刷新檔案清單。 如果對通過簽入的某些檔案執行「與依存對象一起簽入」AEM，則會出現錯誤，列出無法簽入的檔案。

1. \（可選\）在「簽入」對話框中，在 **版本注釋** 的子菜單。

   >[!NOTE]
   >
   >此注釋顯示在文AEM件的版本歷史記錄中。

1. 按一下&#x200B;**「確定」**。

>[!NOTE]
>
>如果已簽出檔案被刪除或移動到中的任何其AEM他資料夾，則在簽入檔案時會收到錯誤消息。 確保未使用Web介面移動或刪除已檢出AEM的檔案。

### 在「參考線」視圖中籤AEM出的檔案

當您在多個資料夾中存在時，很難在一個視圖中找出有多少個檔案已簽出。 參AEM考線提供「參考線視AEM圖中的已簽出檔案」，該視圖提供當前已簽出檔案的完整快照。 使用此視圖，您可以使用「參考線」輕鬆地查找儲存庫中已檢AEM查的AEM檔案。 執行以下步驟以訪問和使用此視圖：

1. 按一下 **窗口** \> **顯示視圖** \> **在參考線中籤出的文AEM件**。

   將顯示「參考線中檢出AEM的檔案」視圖。

   ![](images/files-checkedout-view.png)

1. 按一下右鍵此視圖中的檔案以獲取以下選項：

   - [開啟](#id195GH0V30KX)
   - [開啟](#id195GH0V30KX)
   - 取消簽出
   - [簽入](#id182CF0J0FHS)
   - [使用依存對象簽入](#id182CF0J0FHS)
   - [查看元資料](#id195GHN0H05C)
   - [查看版本](#id195GI000D5Q)

**「參考線」視圖中「檔案簽AEM出說明」：**

- 的 *在參考線中籤出的文AEM件* 視圖維護用戶的會話。 這意味著當前用戶簽出的檔案將通過同一用戶的會話\（或快取\）在視圖中儲存和維護。

- 如果用戶更改登錄憑據或服AEM務器，則重置視圖中籤出檔案的資料\（或快取\）。 用戶必須手動運行 *刷新已簽出檔案* 命令。 為簡化此過程，建議將工作資料夾添加到 *收藏夾* 從中可以快速刷新資料夾。

- 可以根據檔案清單的「檔案名」、「標題」或「路徑」對其進行排序。 如果簽出了新檔案，則檔案將按排序順序顯示在視圖中。


### 上傳檔案和檔案夾 {#id195HC03F03J}

執行以下步驟以上載檔案或資料夾：

1. 在「參考線」面板中按一下右鍵AEM資料夾。
1. 選擇以下選項之一：
   - **上載檔案\(s\)**:選擇此選項可將單個或多個檔案上載到儲存庫中的選定AEM資料夾。 在選擇要上載的檔案\(s\)對話框中，選擇檔案，然後按一下 **開啟**。
   - **上載依存對象**:選擇此選項可上載包含其從屬項的DITA檔案。 在「選擇要上載的檔案」對話框中，選擇檔案，然後按一下 **開啟**。
   - **上載資料夾**:選擇此選項可上載儲存庫中的AEM資料夾。 在「選擇」對話框中，選擇資料夾，然後按一下 **選擇**。

**有關使用基於UUID的檔案的附加說明**:

將內容從本地系統移動或複製到儲存庫時，必須考慮以AEM下幾點：

- 上載一個或多個檔案時，將為沒有任何UUID的檔案生成新的UUID。 此UUID將添加到 `topic id` 的子目錄。

- 複製資料夾時，對檔案\（在資料夾\中）的引用將在引用該資料夾中檔案的所有DITA映射中自動更新。

- 複製DITA映射檔案時，不會更改映射檔案中的UUID引用。

- 如果檔案或資料夾有衝突或有重複檔案，則會為要複製或移動的新檔案生成唯一檔案名。

- 兩個檔案不能具有相同的UUID。 所有新檔案都分配了唯一UUID。

- 如果兩個不同的用戶同時上載檔案，則稍後處理的檔案將覆蓋以前的檔案。 但是，應避免這種做法。

- 當您從儲存庫中籤AEM出內容並在本地系統上進行更改時，請確保在上載檔案時沒有更改檔案名。


### 添加或刪除收藏夾 {#id195HC04405P}

執行以下步驟，在「參考線」面板的「收藏夾」資料夾中添加或AEM刪除資料夾：

- 按一下右鍵資料夾並選擇 **添加到收藏夾**。 如果資料夾不在「收藏夾」中，則可將其添加到收藏夾。
- 可以通過以下方式從收藏夾中刪除資料夾：
   - 按一下右鍵 **收藏夾** 資料夾和 **從收藏夾中刪除**。
   - 按一下右鍵儲存庫中的AEM資料夾 **水壩** 已添加為收藏夾的資料夾，並選擇 **從收藏夾中刪除**。

### 查看檔案的版本歷史記錄 {#id195GI000D5Q}

執行以下步驟查看檔案的版本歷史記錄：

1. 在「參考線」面板中按一下右鍵AEM檔案。

1. 選擇 **查看版本** 的子菜單。

   檔案的版本歷史記錄顯示在「版本」對話框中。

   ![](images/version-history.png)


### 查看檔案的元資料 {#id195GHN0H05C}

執行以下步驟查看檔案的元資料：

1. 在「參考線」面板中按一下右鍵AEM檔案。

1. 選擇 **查看元資料** 的子菜單。

   檔案的元資料（如DITA類、文檔狀態、修改日期、大小、標題和UUID）顯示在元資料對話框中。

   ![](images/metadata.png)


## 在儲存庫中搜索主AEM題 {#id1826J20405Z}

可以使用「參考線」面AEM板中的「搜索」欄在儲存庫中AEM搜索主題。 您可以在整個DAM資料夾中搜索，或選擇一個資料夾，然後在該資料夾中搜索主題。 搜索結果顯示文本與搜索查詢匹配的主題。

執行以下步驟以搜索主題：

1. 在要搜索主AEM題的儲存庫中選擇資料夾。
1. 輸入搜索查詢\(例如， `introduction`\)指南的氧氣插件的搜索AEM欄。
1. 按一下搜索按鈕或按Enter。

   結果將以帶有檔案路徑的清單的形式顯示在「搜索結果」頁籤中。 如果搜索查詢沒有匹配結果，則在中找不到任何結果 &lt;path of=&quot;&quot; the=&quot;&quot; selected=&quot;&quot; folder=&quot;&quot;> 的子菜單。

   ![](images/search.png)

1. \（可選\）按兩下搜索結果中的檔案，以在Ox XML Author中開啟它。
1. 要返回「儲存庫」AEM視圖，請執行以下操作之一：
   - 要查看「儲存庫AEM」視圖而不清除搜索結果，請按一下 **瀏覽** 頁籤。
   - 要清除搜索結果並查看儲存庫，AEM請按一下「刪除」搜索表徵圖。

## 從Web介面開啟Oxon XML作者中AEM的DITA主題 {#id182CE0I905Z}

您可以從Web介面在Oxon XML Author中開啟和編輯DITAAEM主題。 您需要在中安裝包AEM以啟用此選項。 有關軟體包安裝的詳細資訊，請參見 [安裝包以從Web介面啟用文檔編AEM輯功能](#id182CE0Q0TY4)。

>[!NOTE]
>
>的 **在氧氣中編輯** 選項可從以下位置訪問AEM:選擇主題時，預覽主題時，或從DITA映射控制台的「主題和報告」頁籤中選擇主題。 如果選擇多個主題，則該選項在工具欄中不可見。

**開啟DITA主題**

執行以下步驟以在Oxion XML作者中開啟DITA主題：

1. 在資產中選擇主題，然後按一下 **在氧氣中編輯** 的子菜單。

   >[!NOTE]
   >
   >如果未簽出主題，則首先簽出該主題，然後在編輯模式下以「Oxon（氧）」開啟。

1. 選擇Oxon XML作者 *&lt;version>* 的 **啟動應用程式** 的子菜單。 可以選擇 **記住我選擇的鏈AEM接** 的子菜單。

**編輯DITA主題**

執行以下步驟以在Oxion XML作者中編輯DITA主題：

1. 在資產中選擇並簽出主題。
1. 按一下 **在氧氣中編輯** 的子菜單。

   >[!NOTE]
   >
   >如果未簽出主題，則首先簽出該主題，然後在編輯模式下以「Oxon（氧）」開啟。

1. 選擇Oxon XML作者 *&lt;version>* 的 **啟動應用程式** 的子菜單。 可以選擇 **記住我選擇的鏈AEM接** 的子菜單。
1. 在Oxon XML作者中編輯主題。
1. 從指南的氧氣插件中籤AEM入主題。

   有關使用指南的氧插件簽入主題的詳細信AEM息，請參見 [簽入檔案](#id182CF0J0FHS)。

   >[!NOTE]
   >
   >確保使用Oxion Plugin for AEM Guides簽入主題，如果從Web介面簽入，則在Oxion XML Author中所做的更改不會保存在主題的簽入版本中。


## 使用屬性配置檔案 {#id1827JA002YK}

指AEM南允許您使用相關DITA屬性輕鬆建立和關聯條件屬性。 您可以在全局級別或資料夾級別定義條件屬性。 全局定義的條件在所有項目中都可見，而資料夾級別的條件僅在指定資料夾中建立的項目中可見。 內容作者可以使用這些條件屬性對他們建立或使用的DITA主題或映射中的內容進行條件化。 要瞭解有關如何使用參考線建立條AEM件屬性的AEM詳細資訊，請參閱 *配置全局或資料夾級配置檔案的條件屬性* 的子菜單。

>[!NOTE]
>
>確保已在中添加條件屬性並AEM已設定 [效能分析屬性自定義的首選項](#id1827K0D0OHT) 添加條件屬性。

執行以下步驟，將條件屬性添加到Oxon XML Author中的內容：

1. 簽出並從 *指南的氧氣插AEM件*。
1. 選擇要應用條件屬性的內容部分。
1. 按兩下Ox XML作者的「屬性」面板中的條件屬性。

   ![](images/attribute-panel.png)

1. 在 **可用** 在「編輯屬性」對話框的列中，選擇屬性\(s\)並按一下 **添加**。

   以下螢幕顯示 `audience` 屬性。

   ![](images/edit-attributes.png)

1. 按一下&#x200B;**「確定」**。

   屬性將添加到內容。


## 排除常見問題 {#id188ABC00RY4}

本主題介紹在使用插件時可能遇到的一些最常見問題及其解決方案。

### 「缺少AEM參考線」面板 {#id192BH200ZAX}

**問題**  — 如果在「Ox XML Author（氧XML作者）」中AEM未看到「Guides（參考線）」面板，請嘗試以下解決方案：

解決方案1:

1. 在Oxon XML作者中，啟用插件。

   按一下 **選項** \> **首選項** \> **插件** 選擇 **用於Adobe Experience Manager指南的氧氣插件。**

1. Oxion XML重啟作者。


解決方案2:

1. 如果仍未看到「參考線」面AEM板，請啟AEM用「參考線」窗口。

   在Oxion XML作者中，按一下 **窗口** \> **顯示視圖** \> **參考AEM線**。

解決方案3:

1. 卸載並重新安裝《Adobe Experience Manager指南》的氧氣插件。

   - 在Windows上，從中卸載插件 **添加或刪除程式** 清單框。 然後，重新安裝插件。

   - 在Mac，訪問Ox XML Author插件資料夾中的aem-connector-x.x資料夾，並將其移到 **垃圾**。 然後，清空 **垃圾** 的子菜單。


### 配置DITA-OT轉換的埠

**問題**  — 在插件處理的檔案上運行任何DITA-OT轉換時，轉換失敗，出現以下錯誤：

![](images/proxy-server-path-error-new.png)

**解決方案**  — 通過在DITA-OT和插件之間添加代理伺服器解決了此問題。 此代理伺服器處理並共用DITA-OT請求的所有轉換檔案。 配置此伺服器的預設埠是： `5972`。 如果將此埠用於其他伺服器，則可以為代理伺服器指定其他埠。

執行以下步驟以更改代理伺服器的預設埠：

1. 瀏覽到\（用戶\）主目錄。
1. 建立名為aem\_connector\_proxy的檔案。
1. 在任何文本編輯器中開啟檔案，並在檔案的第一行中添加可用埠號。
1. 保存並關閉檔案。
1. 重新啟動Oxon XML作者並運行DITA-OT轉換。


### 輔助AEM線面板不瀏覽到開啟的檔案位置

問題：當您選擇從伺服器開啟要在Oxion XML Author中編輯的檔案AEM時，將在Oxion XML Author中開啟該檔案進行編輯。 但是，「AEM參考線」面板不顯示導航樹中檔案的位置。

解決方案：在檔案路徑中包含/content/dam兩次的情形中，已發現此問題。 預設情況下，中的所AEM有資產都儲存在/content/dam資料夾下。 如果上載或建立的資料夾結構中也包含/content/dam，則會發現此問題。 您可以對這些檔案執行所有正常操作，但預設情況下不會顯示它們在導航樹中的位置。 要在導航樹中訪問此類檔案，必須手動瀏覽到檔案的位置。 請注意，在導航樹中，複製的/content/dam路徑將替換為/content/assets。

### 配置日誌記錄

問題：預設情況下，指南的AEM氧插件不生成任何日誌，這使得調試任何錯誤方案變得困難。

解決方案：執行以下步驟以在插件中啟用日誌生成功能：

1. 瀏覽到Oxon XML Author的安裝位置。

1. 在文本編輯器中開啟oxAuthor19.1.vmoptions檔案。

   >[!NOTE]
   >
   >檔案的版本號可能因系統上安裝的應用程式的版本號而異。

1. 在檔案中追加以下行：

   ```java
   -Djava.util.logging.config.file=./log.properties
   ```

1. 保存並關閉檔案。

1. 在同一位置，建立名為log.properties的檔案，其中包含以下內容：

   ```java
   handlers=java.util.logging.FileHandler
   java.util.logging.FileHandler.level = DEBUG
   java.util.logging.FileHandler.limit = 1048576
   java.util.logging.FileHandler.count = 5
   java.util.logging.FileHandler.pattern = %h/aem-plugin%g.log
   java.util.logging.FileHandler.formatter = java.util.logging.SimpleFormatter
   java.util.logging.FileHandler.format=[%1$tF %1$tT] [%4$s] %5$s %n
   ```

1. 保存並關閉檔案。
1. 啟動Oxon XML作者。


插件現在使用檔案名aem-pluginX.log \(*其中X表示旋轉數*\)。
