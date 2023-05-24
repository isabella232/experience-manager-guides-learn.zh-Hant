---
title: Adobe Experience Manager Guides的氧氣外掛程式
description: 瞭解如何使用Adobe Experience Manager Guides適用的氧氣外掛程式來建立和管理您的內容。
hide: true
hidefromtoc: true
exl-id: 2db9a34e-2efa-47ad-ba6b-02afc5197669
source-git-commit: 8073716bccacbe8d6a158b44d5106b083e3a5dcd
workflow-type: tm+mt
source-wordcount: '5762'
ht-degree: 0%

---

# Adobe Experience Manager Guides的氧氣外掛程式 {#id1645H6010Q5}

Adobe Experience Manager Guides的氧氣外掛程式\(稍後在指南中稱為AEM Guides的氧氣外掛程式\)可讓您將Oxygon XML Author連線到Adobe Experience Manager \(AEM\)存放庫，以創作和管理內容。 您可以使用外掛程式來瀏覽、搜尋和開啟檔案；取出和入庫檔案；在AEM存放庫中上傳資料夾和檔案。 案頭應用程式中的「AEM Guides」面板可讓您將所需的資料夾\(從AEM存放庫\)標示到我的最愛資料夾清單以快速存取。 此外，您可以在AEM網頁介面中安裝套件，並直接從AEM網頁介面在Ourney XML Author中開啟DITA檔案。

## 下載並安裝 {#id1826M0L0PUI}

AEM Guides適用的氧氣外掛程式可透過您的Adobe軟體發佈入口網站取得。 在「Experience Manager」標籤中搜尋「氧氣」，然後從以下位置下載外掛程式安裝程式： [Adobe軟體發佈入口網站](https://experience.adobe.com/#/downloads/content/software-distribution/en/general.html).

>[!NOTE]
>
>檢視特定Adobe Experience Manager Guides發行說明中的氧氣聯結器版本相容性。

安裝程式安裝完畢後，請將其安裝在安裝Oxygon XML Author的本機電腦上。 開始安裝程式之前，您必須確定您的系統符合安裝AEM Guides適用的氧氣外掛程式的技術需求。

### 技術需求

- Oxygon XML Author 24.1版

- Adobe Experience Manager Guides 3.4版或更新版本

- Adobe Experience Manager 6.5版（含Service Pack 10、11、12和13）

- Ourney XML Author 24.1版支援的作業系統

- Java Development Kit
   - oracleSE 8 JRE 1.8

### 在Windows上安裝外掛程式

>[!IMPORTANT]
>
>如果您的系統上已安裝舊版外掛程式，請務必先解除安裝該外掛程式，然後再開始安裝程式。 請參閱 **解除安裝套件** 中的區段 [如何使用套件](https://helpx.adobe.com/tw/experience-manager/6-4/sites/administering/using/package-manager.html) 解除安裝指示的文章。

在安裝Oxygon XML Author的系統上執行下列步驟：

1. 啟動安裝程式的 `.exe` 檔案。

   安裝精靈的歡迎畫面會出現。

1. 按一下 **下一個** 並瀏覽至可用Oxygon XML Author的.exe檔案的位置。

1. 選取檔案，然後按一下 **開啟**.

   選取檔案的位置會新增至安裝精靈中。

1. 按一下&#x200B;**下一步**。

1. 按一下 **安裝**.

1. 按一下 **完成** 以關閉安裝精靈。
1. 啟動Oxygon XML Author。

   「AEM Guides」面板會顯示在「氧氣XML作者」中。

   ![](images/oxygen-aem-connector.png)

   >[!NOTE]
   >
   >如果您看不到AEM Guides面板，請參閱疑難排解一節中的因應措施 — [缺少AEM Guides面板](#id192BH200ZAX).


### 在Mac上安裝外掛程式

>[!IMPORTANT]
>
>如果您的系統上已安裝舊版外掛程式，請務必先解除安裝該外掛程式，然後再開始安裝程式。 請參閱 **解除安裝套件** 中的區段 [如何使用套件](https://helpx.adobe.com/tw/experience-manager/6-4/sites/administering/using/package-manager.html) 文章解除安裝指示。

在安裝Oxygon XML Author的系統上執行下列步驟：

1. 在您的系統上找到外掛程式的.dmg檔案。

1. 連按兩下.dmg檔案以開啟檔案內容。

   .dmg檔案包含aem-connector-x.x資料夾和aem-connector-x.x安裝檔案。

   >[!NOTE]
   >
   >檔案名稱中的x.x是外掛程式的版本號碼。

1. 複製Oxygon XML Author外掛程式資料夾中的aem-connector-x.x資料夾。
1. 連按兩下aem-connector-x.x-setup檔案以啟動安裝程式。

1. 啟動Oxygon XML Author。

   「AEM Guides」面板會顯示在「氧氣XML作者」中。

   ![](images/oxygen-aem-connector-mac.png)

   >[!NOTE]
   >
   >如果您看不到AEM Guides面板，請參閱疑難排解一節中的因應措施 — [缺少AEM Guides面板](#id192BH200ZAX).


### 安裝可從AEM網頁介面啟用檔案編輯功能的套件 {#id182CE0Q0TY4}

身為作者，您可以直接從AEM網頁介面在Oxygon XML Author中開啟和編輯DITA map或主題。 若要在AEM網頁介面中啟用此功能，您的AEM管理員必須在AEM編寫執行個體中安裝套件。

以AEM管理員的身分，執行下列步驟來安裝套裝軟體：

1. 從您的IT團隊取得套件的.zip檔案。
1. 登入您的AEM執行個體 *\（作為管理員\）* 並導覽至CRX封裝管理員。 存取封裝管理器的預設URL為

   `http://<server name>:<port>/crx/packmgr/index.jsp`

   封裝管理員會管理本機AEM安裝上的封裝。 如需有關使用「封裝管理員」的詳細資訊，請參閱 [如何使用套件](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developer-tools/package-manager.html?lang=en) 在AEM檔案中。

   ![](images/package-manager.png)

1. 若要上傳氧氣包，請按一下 **上傳套裝**.
1. 在上傳封裝對話方塊中，瀏覽至您在步驟1下載的Oxygon封裝檔案，然後按一下「確定」。

   套件會上傳至您的AEM執行個體。

1. 若要開始安裝程式，請按一下 **安裝**.

   ![](images/oxygen-package.png)

1. 在安裝套件對話方塊中，按一下 **安裝**.
1. 安裝完成後，按一下CRX封裝管理員左上角的「首頁」按鈕。
1. 在資產資料夾中選取DITA檔案。

   **在氧氣中編輯** 選項在工具列中可用。 如需使用此選項的詳細資訊，請參閱 [從AEM網頁介面在Ourney XML Author中開啟DITA主題](#id182CE0I905Z).

   >[!NOTE]
   >
   >此 **在氧氣中編輯** 選項在您選取一個DITA主題時可見。 如果您選取多個主題，則不會顯示選項。


## 設定AEM Guides的氧氣外掛程式 {#id1826KF00AHS}

下載並安裝外掛程式後，您需要設定下列專案才能使用外掛程式：

- **Web驗證設定**：AEM Guides外掛程式中SSO驗證的設定。
- **一般設定**：外掛程式的連線設定，例如AEM伺服器URL、登入詳細資料等。
- **設定屬性自訂的偏好設定**：此檔案集的設定屬性配置需要此設定。

### Web驗證設定

氧氣聯結器外掛程式會使用JxBrowser進行SSO驗證。 它是以Chromium為基礎的瀏覽器。 若是Java 9+，需要非公用API的存取權，且您必須明確授與JxBrowser的此存取權。 如需詳細資訊，請參閱 [JxBrowser疑難排解](https://jxbrowser-support.teamdev.com/docs/guides/troubleshooting/issues.html).

更新指定檔案以設定AEM Guides的氧氣外掛程式中的網頁驗證設定：

>[!NOTE]
>
>在更新檔案之前，請先備份檔案。

**適用於Mac和氧氣24.1**

在env.sh中新增下列行

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

在ourneyAuthor.sh中新增下列行

```java
-Djdk.module.illegalAccess=permit\-Djava.ipc.external=true\
```

**適用於Windows和Oxygon 24.1**

在env.bat中新增下列行

```java
--illegal-access=permit --add-opens=java.desktop/javax.swing.plaf.basic=ALL-UNNAMED --add-exports=javafx.controls/com.sun.javafx.scene.control=ALL-UNNAMED --add-exports=javafx.graphics/com.sun.javafx.stage=ALL-UNNAMED --add-exports=javafx.graphics/com.sun.javafx.scene=ALL-UNNAMED --add-exports=javafx.graphics/com.sun.javafx.scene.traversal=ALL-UNNAMED --add-exports=javafx.graphics/com.sun.javafx.tk=ALL-UNNAMED --add-exports=javafx.graphics/com.sun.glass.ui=ALL-UNNAMED --add-opens=javafx.graphics/com.sun.glass.ui=ALL-UNNAMED --add-opens=javafx.graphics/javafx.stage=ALL-UNNAMED --add-opens=javafx.graphics/com.sun.javafx.tk.quantum=ALL-UNNAMED --add-exports=java.desktop/sun.awt=ALL-UNNAMED --add-opens javafx.swing/javafx.embed.swing=ALL-UNNAMED
```

在ourneyAuthor.bat中新增以下行

```java
-Djdk.module.illegalAccess=permit -Djava.ipc.external=true
```

>[!NOTE]
>
>您必須以管理員身分，從Mac的oxygonAuthor.sh和Windows的oxygonAuthor.bat執行Oxygon。

### 一般設定

執行以下步驟，在Adobe Experience Manager Guides的氧氣外掛程式中設定連線設定：

1. 在AEM Guides面板中，按一下設定圖示，然後選取 **設定**.

   ![](images/settings.png)

1. 指定下列詳細資料：
   - **伺服器URL**：AEM伺服器的URL，例如：

      ```http
      http[s]://<host>:<port>
      ```

      在上述URL中，指定部署AEM伺服器之伺服器的主機名稱和連線埠。

      >[!IMPORTANT]
      >
      >如果您的AEM伺服器部署在連線埠80或443上，則不需要在URL中指定。

   - **驗證：** 選擇來源 **基本\（使用者名稱/密碼\）** 或 **Web驗證**. 如果您選取 **基本** 驗證您需要輸入 **使用者名稱** 和 **密碼** 在「偏好設定」對話方塊中。

      如果您選取「Web驗證」，則會顯示「AEM登入」畫面。 輸入您的登入認證，然後按一下 **登入** 按鈕。 成功登入後，「AEM登入」畫面會關閉，「AEM Guides」面板會顯示AEM伺服器的檔案清單。

   - **連線逾時**：指定使用者端等候來自AEM伺服器回應的時間（以秒為單位）。 如果在指定的時間內未收到來自伺服器的回應，則請求會終止。 預設值為20秒。

   - **本機資料夾**：簽出後AEM存放庫中的檔案儲存於本機電腦上的位置。 如果您指定的位置不存在於磁碟機上，外掛程式會建立該位置。
   - **簽出時開啟檔案**：如果選取，會在簽出時開啟檔案。
   - **入庫時關閉檔案**：如果選取，會在入庫時關閉檔案。 在關閉檔案之前，會顯示一個快顯視窗，您可以在其中指定版本註解。
   - **關閉檔案時顯示簽入對話方塊**：如果選取，關閉檔案時會顯示快顯視窗。 從彈出式視窗中，您可以選擇入庫檔案或關閉檔案而不入庫。
   - **開啟時自動簽出檔案**：如果選取，連按兩下檔案會自動將其出庫並開啟以進行編輯。 如果檔案已經簽出，則只需將其開啟以進行編輯。 如果未選取此選項，則開啟沒有鎖定的檔案時，會在唯讀模式下將其開啟。
1. 按一下&#x200B;**「確定」**。

### 設定屬性自訂的偏好設定 {#id1827K0D0OHT}

您需要在Oxygon XML Author中設定偏好設定，以使用與AEM存放庫中的DITA主題相關聯的設定屬性。

執行以下步驟來設定效能分析屬性：

1. 在Oxygon XML Author中，按一下 **選項** \> **偏好設定**.
1. 在 **檔案型別關聯** 索引標籤，選取 **DITA**，然後按一下 **延伸**.

   ![](images/document_type_association.png)

1. 在 **類別路徑** 索引標籤中，選取com.adobe.o2.connector **透過ID使用外掛程式中的父級類別載入器** 下拉式清單。

   ![](images/dita-extension.png)

1. 在 **擴充功能** 標籤中，進行下列變更：
1. 
   - 按一下 **選擇** 旁邊 **作者擴充功能狀態監聽器** 在 **個別擴充功能** 並選取CustomAuthorExtensionStateListener - com.adobe.o2.framework.extn於 **類別** 清單。 按一下&#x200B;**「確定」**。
- 按一下 **選擇** 旁邊 **作者自訂屬性值編輯器** 在 **個別擴充功能** 並選取「 」中的「CustomValueEditor - com.adobe.o2.framework.extn」 **類別** 清單。 按一下&#x200B;**「確定」**。下列熒幕擷圖顯示設定的 **副檔名** DITA主題的索引標籤：

   ![](images/dita-topic-extension-tab.png)

1. 按一下 **確定** 以儲存變更。

### 設定DITA map擴充功能

需要DITA map擴充功能設定，才能直接從AEM網頁介面開啟Ourney XML Author中的地圖檔案。 這些組態類似於前述程式中所完成的屬性剖析組態。

執行以下步驟來設定DITA map擴充功能：

1. 在Oxygon XML Author中，按一下&#x200B;**選項** \> **偏好設定**.
1. 在 **檔案型別關聯** 索引標籤，選取 **DITA Map**，然後按一下 **延伸**.
1. 在 **類別路徑** 索引標籤中，選取com.adobe.o2.connector **透過ID使用外掛程式中的父級類別載入器** 下拉式清單。
1. 在 **擴充功能** 標籤中，進行下列變更：
1. 
   - 按一下 **選擇** 旁邊 **作者擴充功能狀態監聽器** 在 **個別擴充功能** 並選取CustomDITAMapAuthorExtensionStateListener - com.adobe.o2.framework.extn於 **類別** 清單。 按一下&#x200B;**「確定」**。
- 按一下 **選擇** 旁邊 **作者自訂屬性值編輯器** 在 **個別擴充功能** 並選取「 」中的「CustomValueEditor - com.adobe.o2.framework.extn」 **類別** 清單。 按一下&#x200B;**「確定」**。
- *\（可選\）* 如果您不想在開啟對應檔案時解析參照，則需要執行下列額外設定：

   按一下 **選擇** 旁邊 **引用解析器**&#x200B;在 **個別擴充功能** 並選取CustomDITAMapReferenceResolver - com.adobe.o2.framework.extn於 **類別** 清單。 按一下&#x200B;**「確定」**。

   下列熒幕擷圖顯示設定的 **副檔名** 標籤：

   ![](images/dita-map-extension-tab.png)

1. 按一下 **確定** 以儲存變更。

## 使用AEM Guides的氧氣外掛程式 {#id1826JG00WY4}

### AEM Guides面板

下列畫面顯示「AEM參考線」面板。

![](images/connector-panel.png)

**A**\)顯示搜尋列。

**B**\)顯示我的最愛資料夾。 依預設，它是空的。 您可以從AEM存放庫新增資料夾作為我的最愛，我的最愛資料夾會顯示在這裡。

**C**\) DAM資料夾會顯示AEM存放庫。 您可以展開和收合資料夾檢視。

**D**\)設定\（齒輪\）圖示包含以下選項：

- **Connect**：選取此選項以連線至AEM伺服器。 當Oxygon XML Author連線至AEM伺服器時，會停用此選項。
- **重新整理**：選取此選項，即可從AEM存放庫取得檔案和資料夾的最新狀態。

   >[!NOTE]
   >
   >在重新整理檔案之前，請務必先儲存檔案。 當您選取 **重新整理** 選項，您會收到一則警告，要求您在重新整理檔案前先儲存檔案。 如果您尚未儲存檔案，可以按一下 **取消** 並儲存。

- **設定**：您可以使用此選項開啟外掛程式的一般偏好設定對話方塊。
- **登出**：選取此選項以關閉AEM伺服器連線。 只有使用Web驗證模式時，才能使用此選項。

### 內容功能表功能

以滑鼠右鍵按一下AEM存放庫中的資料夾或檔案，即可使用AEM Guides適用的氧氣外掛程式的功能。 資料夾可用的功能與檔案不同。 以下是AEM Guides內容功能表氧氣外掛程式的完整功能清單：

- **開啟**：開啟所選檔案或展開所選資料夾。
- **開啟方式**：您可以選擇在AEM Guides的網頁編輯器、地圖儀表板或地圖編輯器中開啟選取的檔案。 如需這些選項的詳細資訊，請參閱 [在AEM Guides的編輯器中開啟檔案](#id195GH0V30KX).
- **簽出**：從AEM存放庫簽出檔案。 如需詳細資訊，請參閱 [簽出檔案](#id195HC020TS4).
- **與相依物件一起出庫**：出庫檔案及其直接參照。 如需詳細資訊，請參閱 [簽出檔案](#id195HC020TS4).
- **以唯讀相依專案簽出**：出庫選取的檔案及其相依專案。 您無法在相依檔案中進行任何變更。 如需詳細資訊，請參閱 [簽出檔案](#id195HC020TS4).
- **取消簽出**：取消已出庫的檔案、從編輯器中關閉檔案，並將變更還原為儲存在伺服器上之檔案的最後一個版本。
- **重新整理**：如果是檔案，會從AEM存放庫擷取檔案的最新副本。 若是資料夾，它會擷取資料夾結構和檔案的狀態。 這表示只要新增檔案，就會顯示在AEM Guides檢視中。 此外，如果檔案在AEM伺服器上出庫，在Oxygon Author中執行「重新整理」會將檔案顯示為已出庫。 但是，這不會更新中的檔案清單 *AEM Guides中出庫的檔案* 檢視。
- **重新整理出庫檔案**：重新整理中出庫檔案的清單 *AEM Guides中出庫的檔案* 檢視。 如果檔案在AEM伺服器上出庫，則執行「重新整理」將會更新中出庫的檔案清單 *AEM Guides中出庫的檔案* 檢視。 不過，如果新增了新檔案或檔案狀態已變更，則不會在AEM Guides樹狀檢視中更新它。 若要更新AEM上檔案的狀態，您必須執行「重新整理」。
- **簽入**：入庫您已出庫的檔案。 如需詳細資訊，請參閱 [簽入檔案](#id182CF0J0FHS).
- **與相依專案簽入**：如果您已出庫包含相依專案的檔案，則此選項會入庫主檔案及其相依專案。 如需詳細資訊，請參閱 [簽入檔案](#id182CF0J0FHS).
- **建立資料夾**：在AEM存放庫中建立資料夾。 此選項僅在資料夾層級可用。
- **上傳檔案**：上傳單一或多個檔案。 如需詳細資訊，請參閱 [上傳檔案和資料夾](#id195HC03F03J).
- **與相依專案一起上傳**：上傳DITA檔案\（XML、DITA、Book map或DITA map\）及其相依專案。 如需詳細資訊，請參閱 [上傳檔案和資料夾](#id195HC03F03J).
- **上傳資料夾**：上傳AEM存放庫上的資料夾。 如需詳細資訊，請參閱 [上傳檔案和資料夾](#id195HC03F03J).
- **新增至我的最愛**：將資料夾新增至 *我的最愛* 「AEM參考線」面板中的資料夾。 建議在此處新增工作資料夾，這樣可以更輕鬆地從AEM同步檔案和檔案狀態。
- **從我的最愛移除**：從移除資料夾 *我的最愛*. 如需詳細資訊，請參閱 [新增或移除我的最愛](#id195HC04405P).
- **檢視中繼資料**：顯示中繼資料，例如DITA類別、檔案的標題、型別、UUID和與檔案相關聯的其他資訊。 如需詳細資訊，請參閱 [檢視檔案的中繼資料](#id195GHN0H05C).
- **檢視版本**：顯示檔案的版本記錄。 如需詳細資訊，請參閱 [檢視檔案的版本記錄](#id195GI000D5Q).

### 在Oxygon XML作者中開啟檔案 {#id195GHJ0A0UB}

連線到AEM存放庫後，您就可以在Oxygon XML Author中開啟檔案以進行編輯。 執行以下步驟來開啟檔案，以便在Oxygon XML Author中編輯：

1. 以滑鼠右鍵按一下您要開啟以進行編輯的「AEM參考線」面板中的檔案。

1. 選取 **開啟** 從快顯選單中。

   檔案會在Oxygon XML作者的編輯器中開啟。

   ![](images/guid-in-file-tab.png)

   當您將滑鼠指標停留在檔案的索引標籤上時，會顯示伺服器路徑及其UUID。 在上述熒幕擷圖中，檔案的UUID會反白顯示。


如果您已選取 **開啟時自動簽出檔案** 選項\（在「偏好設定」對話方塊中\），然後在開啟檔案時，檔案會自動出庫並可供編輯。 若要開啟檔案，您可以連按兩下檔案名稱或以滑鼠右鍵按一下檔案名稱，然後選擇 **開啟** 從快顯選單中。 如果未選取此選項，則會以唯讀模式開啟檔案。

>[!NOTE]
>
>您也可以連按兩下檔案以開啟。

### 在AEM Guides的編輯器中開啟檔案 {#id195GH0V30KX}

如果要使用AEM Guides中可用的編輯器，您可以從快顯選單中選取所需選項來執行此操作。 執行以下步驟，使用AEM Guides的編輯器來取代Oxygon XML作者的編輯器：

1. 以滑鼠右鍵按一下您要開啟以進行編輯的「AEM參考線」面板中的檔案。

1. 選取 **開啟方式** 從快顯選單中，並從下列選項中選擇：

   - **網頁主題編輯器**：如果您要開啟的檔案是.xml或.dita檔案，則您可以在Web編輯器中開啟該檔案以進行編輯。 選擇 **網頁主題編輯器** 選項來開啟選取的檔案，以便在「網頁編輯器」中編輯。

   - **地圖儀表板**：您可以選擇在地圖控制面板中編輯.ditamap檔案，在其中可以對地圖檔案執行各種操作。 這些作業取決於您所屬的角色/群組。

   - **Web DITA Map編輯器**：如果您想要開啟.ditamap檔案以在地圖編輯器中編輯，請選擇此選項。 使用DITA Map編輯器選項，您可以在地圖上新增或移除主題、新增關係表及執行其他作業。


### 簽出檔案 {#id195HC020TS4}

當您簽出檔案時，該檔案會儲存在您系統上的本機中，並鎖定在AEM存放庫中以供編輯。 執行以下步驟來出庫檔案：

1. 在「AEM參考線」面板中的檔案上按一下滑鼠右鍵。
1. 選取下列其中一個選項：
   - **結帳：** 從AEM存放庫出庫檔案，並使其可用於編輯。
   - **與相依物件一起出庫**：出庫檔案及其直接參照。 您可以使用此選項變更父頁面和子頁面。 AEM Guides的氧氣外掛程式支援出庫一個層級的相依專案。 例如，對映A參考主題A和主題A參考主題B。出庫對映A將會出庫主題A，無論其在目錄階層中的層級為何。 不過，它不會簽出主題B，因為它未直接從地圖A連結。
   - **以唯讀相依專案簽出**：取出檔案並將其相依檔案以唯讀副本下載至本機電腦。 您無法在相依檔案中進行任何變更。

如果您已選取 **簽出時開啟檔案** 選項\（在「偏好設定」對話方塊中\），然後在出庫檔案時，檔案會自動開啟以進行編輯。

如果您已選取 **開啟時自動簽出檔案** 選項\（在「偏好設定」對話方塊中\），然後在開啟檔案時，檔案會自動出庫並可供編輯。 若要開啟檔案，您可以連按兩下檔案名稱或以滑鼠右鍵按一下檔案名稱，然後選擇 **開啟** 從快顯選單中。

當檔案出庫時，檔案的圖示會變更為顯示其鎖定狀態。

![](images/check-out-file.png)

在上述熒幕擷圖中，由其他使用者簽出的檔案會顯示一個黑色鎖定圖示\(A\)。 目前使用者簽出的檔案會以綠色鎖定顯示\(B\)。

>[!NOTE]
>
>如果出庫的檔案被刪除或移至AEM中的任何其他資料夾，則入庫檔案時會出現一則錯誤訊息。 確保未使用AEM網頁介面移動或刪除已出庫的檔案。

### 簽入檔案 {#id182CF0J0FHS}

當您入庫檔案時，您系統的本機副本會儲存在AEM存放庫中，且檔案上的鎖定會移除。 執行以下步驟來入庫檔案：

1. 按一下以儲存檔案 **檔案** \> **儲存**.

1. 以滑鼠右鍵按一下出庫檔案，然後從下列兩個選項中選擇：

   - **簽入**：將選取的檔案從您的本機系統簽入AEM存放庫。
   - **「與相依專案簽入」：** 如果您已出庫檔案及其從屬檔案，則使用此選項可在一次操作中入庫所有從屬檔案。 選取此選項時，您會看到包含所有相依檔案的「入庫」對話方塊。 按一下「確定」以一次入庫所有檔案。

   如果您尚未出庫相依檔案，然後選擇此選項，則只有您已出庫的相依檔案才會入庫。 您將會看到無法簽入的檔案清單：

   ![](images/check-in-error.png)

   強烈建議不要移動已出庫的檔案。 但是，如果出庫的檔案被移動到其他位置，則必須取消對該檔案的出庫。 如果您想要更新該檔案，請再次簽出檔案、進行變更，然後將其簽回。 如果您嘗試入庫已從其原始位置移動的檔案，則會發生錯誤。

   如果相依檔案在AEM中出庫，則「以相依專案入庫」不會在「入庫」對話方塊中顯示相依檔案。 若要取得在AEM中出庫的相依檔案清單，您必須執行資料夾重新整理。

   同樣地，如果您已透過AEM入庫相依檔案，則在您執行資料夾「重新整理」和「重新整理出庫檔案」之前，檔案清單不會在Oxygon Author中重新整理。 如果您對某些透過AEM簽入的檔案進行「依存專案簽入」，則會出現列出無法簽入的檔案的錯誤。

1. \（可選\）在簽入對話方塊中，新增註解 **版本註解** 文字方塊。

   >[!NOTE]
   >
   >此註解會顯示在檔案的AEM版本記錄中。

1. 按一下&#x200B;**「確定」**。

>[!NOTE]
>
>如果出庫的檔案被刪除或移至AEM中的任何其他資料夾，則入庫檔案時會出現一則錯誤訊息。 確保未使用AEM網頁介面移動或刪除已出庫的檔案。

### 在AEM Guides檢視中出庫的檔案

當您在多個資料夾中時，要找出一個檢視中出庫了多少檔案並不容易。 AEM Guides在AEM Guides檢視中提供檔案出庫，可提供目前出庫檔案的完整快照。 使用此檢視，您可以輕鬆找出哪些檔案已由您使用AEM Guides在AEM存放庫中檢查。 執行以下步驟來存取及使用此檢視：

1. 按一下 **視窗** \> **顯示檢視** \> **AEM Guides中出庫的檔案**.

   隨即顯示「AEM Guides」檢視中的「出庫檔案」。

   ![](images/files-checkedout-view.png)

1. 以滑鼠右鍵按一下此檢視中的檔案以取得下列選項：

   - [開啟](#id195GH0V30KX)
   - [開啟方式](#id195GH0V30KX)
   - 取消簽出
   - [簽入](#id182CF0J0FHS)
   - [與相依物件一起簽入](#id182CF0J0FHS)
   - [檢視中繼資料](#id195GHN0H05C)
   - [檢視版本](#id195GI000D5Q)

**AEM Guides檢視中出庫檔案的附註：**

- 此 *AEM Guides中出庫的檔案* 檢視會維護使用者的工作階段。 這表示目前使用者出庫的檔案會跨相同使用者的工作階段\（或快取\）儲存並維護在檢視中。

- 如果使用者變更登入認證或AEM伺服器，則檢視中出庫檔案的資料\（或cache\）會重設。 使用者必須手動執行 *重新整理取出檔案* 檔案先前出庫所在之每個資料夾上的命令。 若要簡化操作，建議將工作資料夾新增至 *我的最愛* 您可以在這裡快速重新整理資料夾。

- 您可以根據檔案名稱、標題或路徑來排序檔案清單。 如果新檔案已出庫，則檔案會以排序順序顯示在檢視中。


### 上傳檔案和檔案夾 {#id195HC03F03J}

執行以下步驟來上傳檔案或資料夾：

1. 在「AEM參考線」面板中的資料夾上按一下滑鼠右鍵。
1. 選取下列其中一個選項：
   - **上傳檔案**：選取此選項可將單一或多個檔案上傳至AEM存放庫中所選的資料夾。 在「選取要上傳的檔案\(s\)」對話方塊中，選取檔案並按一下 **開啟**.
   - **與相依專案一起上傳**：選取此選項以上傳DITA檔案及其相依專案。 在「選取要上傳的檔案」對話方塊中，選取檔案並按一下 **開啟**.
   - **上傳資料夾**：選取此選項以上傳AEM存放庫中的資料夾。 在「選擇」對話方塊中，選取資料夾並按一下 **選擇**.

**有關使用UUID型檔案的其他附註**：

將內容從本機系統移動或複製到AEM存放庫時，必須考量以下幾點：

- 上傳一或多個檔案時，系統會為不含任何UUID的檔案產生新的UUID。 此UUID會新增至 `topic id` DITA檔案的。

- 複製資料夾時，參照該資料夾中檔案的所有DITA map中的檔案\（在資料夾內\）參照都會自動更新。

- 複製DITA map檔案時，不會變更map檔案中的UUID參照。

- 如果檔案或資料夾有衝突或重複，則會為要複製或移動的新檔案產生唯一的檔案名稱。

- 沒有兩個檔案可以有相同的UUID。 會將唯一的UUID指派給所有新檔案。

- 如果檔案由兩個不同的使用者同時上傳，則稍後處理的檔案會覆寫較早的檔案。 不過，應避免這種作法。

- 當您從AEM存放庫簽出內容並在本機系統上變更時，請確保在上傳檔案時檔案名稱未變更。


### 新增或移除我的最愛 {#id195HC04405P}

執行以下步驟，在「AEM Guides」面板的「我的最愛」資料夾中新增或移除資料夾：

- 以滑鼠右鍵按一下資料夾並選取 **新增至我的最愛**. 如果資料夾不在「我的最愛」中，您可以將其新增到我的最愛。
- 您可以透過下列方式，從我的最愛移除資料夾：
   - 以滑鼠右鍵按一下中的資料夾 **我的最愛** 資料夾並選取 **從我的最愛移除**.
   - 以滑鼠右鍵按一下下方的AEM存放庫中的資料夾 **DAM** 已新增為最愛並選取的資料夾 **從我的最愛移除**.

### 檢視檔案的版本記錄 {#id195GI000D5Q}

執行以下步驟來檢視檔案的版本記錄：

1. 在「AEM參考線」面板中的檔案上按一下滑鼠右鍵。

1. 選取 **檢視版本** 從快顯選單中。

   檔案的版本記錄會顯示在「版本」對話方塊中。

   ![](images/version-history.png)


### 檢視檔案的中繼資料 {#id195GHN0H05C}

執行以下步驟來檢視檔案的中繼資料：

1. 在「AEM參考線」面板中的檔案上按一下滑鼠右鍵。

1. 選取 **檢視中繼資料** 從快顯選單中。

   檔案的中繼資料（例如DITA類別、檔案狀態、修改日期、大小、標題和UUID）會顯示在「中繼資料」對話方塊中。

   ![](images/metadata.png)


## 搜尋AEM存放庫中的主題 {#id1826J20405Z}

您可以使用AEM Guides面板中的搜尋列，搜尋AEM存放庫中的主題。 您可以在整個DAM資料夾中搜尋或選取資料夾，然後在該資料夾中搜尋主題。 搜尋結果會顯示文字與搜尋查詢相符的主題。

執行以下步驟來搜尋主題：

1. 在AEM存放庫中選取您要搜尋主題的資料夾。
1. 輸入搜尋查詢\(例如， `introduction`\)在AEM Guides的氧氣外掛程式搜尋列中。
1. 按一下搜尋按鈕或按Enter。

   結果在「搜尋結果」標籤中會顯示為包含檔案路徑的清單。 如果您的搜尋查詢沒有相符的結果，則在中找不到任何結果 &lt;path of=&quot;&quot; the=&quot;&quot; selected=&quot;&quot; folder=&quot;&quot;> 訊息便會顯示。

   ![](images/search.png)

1. \（可選\）在搜尋結果中按兩下檔案，以在Oxygon XML Author中開啟該檔案。
1. 若要返回「AEM存放庫」檢視，請執行下列任一項作業：
   - 若要檢視「AEM儲存區域」檢視而不清除搜尋結果，請按一下 **瀏覽** 標籤。
   - 若要清除搜尋結果並檢視AEM存放庫，請按一下刪除搜尋圖示。

## 從AEM網頁介面在Ourney XML Author中開啟DITA主題 {#id182CE0I905Z}

您可以從AEM網頁介面在Ourney XML Author中開啟及編輯DITA主題。 您必須在AEM中安裝套件才能啟用此選項。 如需套件安裝的詳細資訊，請參閱 [安裝可從AEM網頁介面啟用檔案編輯功能的套件](#id182CE0Q0TY4).

>[!NOTE]
>
>此 **在氧氣中編輯** 選項可從AEM中的各個位置存取：選取主題時、預覽主題時，或從DITA map主控台的「主題與報表」索引標籤存取。 如果您選取多個主題，則工具列中不會顯示選項。

**開啟DITA主題**

執行以下步驟，在Oxygon XML Author中開啟DITA主題：

1. 在資產中選取主題，然後按一下 **在氧氣中編輯** 工具列中的選項。

   >[!NOTE]
   >
   >如果主題未出庫，則會先出庫主題，然後在編輯模式下在Oxygon中將其開啟。

1. 選取氧氣XML作者 *&lt;version>* 在 **啟動應用程式** 訊息方塊。 您可以選取 **記住我的AEM連結選擇** 儲存偏好設定的選項。

**編輯DITA主題**

執行以下步驟，在Ourney XML Author中編輯DITA主題：

1. 選取並簽出資產中的主題。
1. 按一下 **在氧氣中編輯** 工具列中的選項。

   >[!NOTE]
   >
   >如果主題未出庫，則會先出庫主題，然後在編輯模式下在Oxygon中將其開啟。

1. 選取氧氣XML作者 *&lt;version>* 在 **啟動應用程式** 訊息方塊。 您可以選取 **記住我的AEM連結選擇** 儲存偏好設定的選項。
1. 在Oxygon XML Author中編輯主題。
1. 檢視AEM Guides氧氣外掛程式的主題。

   如需使用AEM Guides的氧氣外掛程式簽入主題的詳細資訊，請參閱 [簽入檔案](#id182CF0J0FHS).

   >[!NOTE]
   >
   >請確定您使用AEM Guides的氧氣外掛程式來簽入主題，如果您從AEM網頁介面簽入，您在Ourney XML Author中所做的變更不會儲存在主題的簽入版本中。


## 使用屬性設定檔 {#id1827JA002YK}

AEM Guides可讓您使用相關的DITA屬性，輕鬆建立及關聯條件屬性。 您可以在全域層級或檔案夾層級定義條件屬性。 全域定義的條件會出現在所有專案中，而資料夾層級的條件只會出現在指定資料夾內建立的專案中。 內容作者可以使用這些條件屬性，在他們建立或使用的DITA主題或地圖中條件化內容。 若要進一步瞭解如何使用AEM Guides在AEM中建立條件屬性，請參閱 *設定全域或資料夾層級設定檔的條件屬性* 安裝與設定Adobe Experience Manager Guides一節。

>[!NOTE]
>
>請確定您已在AEM中新增條件屬性並設定 [設定屬性自訂的偏好設定](#id1827K0D0OHT) 將條件屬性新增至內容之前。

執行以下步驟，在Oxygon XML Author中新增條件屬性至您的內容：

1. 從取出並開啟主題 *AEM Guides的氧氣外掛程式*.
1. 選取要套用條件屬性的內容部分。
1. 連按兩下Oxygon XML Author的「屬性」面板中的條件屬性。

   ![](images/attribute-panel.png)

1. 在 **可用** 編輯屬性對話方塊的資料欄，選取屬性並按一下 **新增**.

   下列畫面顯示 `audience` 屬性。

   ![](images/edit-attributes.png)

1. 按一下&#x200B;**「確定」**。

   屬性會新增至內容。


## 疑難排解常見問題 {#id188ABC00RY4}

此主題涵蓋您使用外掛程式時最常遇到的一些問題，以及外掛程式的解決方案。

### 缺少AEM Guides面板 {#id192BH200ZAX}

**問題**  — 如果您在Oxygon XML Author中看不到AEM Guides面板，請嘗試下列解決方案：

解決方案1：

1. 在Oxygon XML Author中，啟用外掛程式。

   按一下 **選項** \> **偏好設定** \> **外掛程式** 並選取 **Adobe Experience Manager Guides的氧氣外掛程式。**

1. 重新啟動Oxygon XML Author。


解決方案2：

1. 如果您還是看不到「AEM Guides」面板，請啟用「AEM Guides」視窗。

   在Oxygon XML Author中，按一下 **視窗** \> **顯示檢視** \> **AEM指南**.

解決方案3：

1. 解除安裝並重新安裝Adobe Experience Manager Guides的氧氣外掛程式。

   - 在Windows上，從解除安裝外掛程式 **新增或移除程式** 清單。 然後，重新安裝外掛程式。

   - 在Mac上，存取Oxygon XML Author的plugins資料夾中的aem-connector-x.x資料夾，並將其移至 **垃圾桶**. 然後，清空 **垃圾桶** 資料夾。


### 設定DITA-OT轉換的連線埠

**問題**  — 當您對由外掛程式處理的檔案執行任何DITA-OT轉換時，轉換會失敗並出現以下錯誤：

![](images/proxy-server-path-error-new.png)

**解決方案**  — 此問題已透過在DITA-OT和外掛程式之間新增Proxy伺服器來修正。 此Proxy伺服器會處理並共用DITA-OT要求的所有檔案以進行轉換。 已設定此伺服器的預設連線埠為： `5972`. 如果您將此連線埠用於其他伺服器，則可以為Proxy伺服器指定不同的連線埠。

執行以下步驟來變更Proxy伺服器的預設連線埠：

1. 瀏覽至您的\(user&#39;s\)主目錄。
1. 建立名為aem\_connector\_proxy的檔案。
1. 在任何文字編輯器中開啟檔案，並在檔案的第一行新增可用的連線埠號碼。
1. 儲存並關閉檔案。
1. 重新啟動Ourney XML Author並執行DITA-OT轉換。


### AEM Guides面板未瀏覽至開啟的檔案位置

問題：當您選擇從AEM伺服器開啟檔案以在Oxyo XML Author中編輯時，檔案會開啟以在Oxyo XML Author中編輯。 不過，「AEM參考線」面板不會顯示檔案在導覽樹狀結構中的位置。

解決方案：在檔案路徑中包含/content/dam兩次的情況下，已發現此問題。 根據預設，AEM中的所有資產都儲存在/content/dam資料夾下。 如果您上傳或建立的資料夾結構也包含/content/dam，則會發現此問題。 您可以對這類檔案執行所有一般操作，但依照預設不會顯示它們在導覽樹狀結構中的位置。 若要在導覽樹狀結構中存取此類檔案，您必須手動瀏覽至檔案的位置。 請注意，在導覽樹狀結構中，重複的/content/dam路徑會取代為/content/assets。

### 設定記錄

問題：根據預設，AEM Guides適用的氧氣外掛程式不會產生任何記錄，這使得對任何錯誤案例進行偵錯都變得困難。

解決方案：執行以下步驟，在外掛程式中啟用記錄產生功能：

1. 瀏覽至Ourney XML Author的安裝位置。

1. 在文字編輯器中開啟oxygonAuthor19.1.vmoptions檔案。

   >[!NOTE]
   >
   >檔案的版本號碼可能會因系統上安裝的應用程式版本號碼而異。

1. 在檔案中附加下列行：

   ```java
   -Djava.util.logging.config.file=./log.properties
   ```

1. 儲存並關閉檔案。

1. 在相同位置，建立名為log.properties的檔案，其內容如下：

   ```java
   handlers=java.util.logging.FileHandler
   java.util.logging.FileHandler.level = DEBUG
   java.util.logging.FileHandler.limit = 1048576
   java.util.logging.FileHandler.count = 5
   java.util.logging.FileHandler.pattern = %h/aem-plugin%g.log
   java.util.logging.FileHandler.formatter = java.util.logging.SimpleFormatter
   java.util.logging.FileHandler.format=[%1$tF %1$tT] [%4$s] %5$s %n
   ```

1. 儲存並關閉檔案。
1. 啟動Oxygon XML Author。


外掛程式現在會在使用者的主目錄中以aem-pluginX.log \(*其中X代表旋轉數*\)。
