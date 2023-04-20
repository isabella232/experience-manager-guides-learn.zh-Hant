---
title: 在Webeditor工具列中新增自訂可操作按鈕
description: 了解如何在WebDitor工具列中新增自訂按鈕，並呼叫Javascript以自訂操作它。
source-git-commit: 26a6acde54953eab1d751f165d0f7769c7e790fe
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 0%

---

# 在Webeditor工具列中新增自訂可操作按鈕

在本文中，我們將了解如何在WebDitor工具列中新增自訂按鈕，並呼叫Javascript以執行所需的自訂操作。

將可操作的按鈕新增至Webeditor時，需執行下列步驟：
- 在 *ui_config.json* 在需要的位置
- 在瀏覽器中註冊按鈕點擊事件，讓使用者在點擊動作時執行動作


## 以實例進行實作

讓我們透過作者想要將jira參考新增至主題專案區段的範例來了解。 內嵌jira reference-id的prolog區段可能如下所示：

![帶有JIRA ID參考的Prolog部分](../../../assets/authoring/webeditor-add-customtoolbarbutton-prolog-sample.png)

應從API中擷取包含JIRA ID的「change-request-id」元素（例如，以應用程式所描述的特定JIRA查詢為基礎）。 當使用者編寫專案區段時，使用者應該可以按一下按鈕，並從網頁編輯器工具列插入jira參考id，類似以下項目：

![Prolog部分 — 添加JIRA引用](../../../assets/authoring/webeditor-add-customtoolbarbutton-prolog-insertjirareference.png)

當使用者按一下按鈕時，應該會顯示對話方塊，提取可能的選項，並允許使用者選取所需的JIRA ID，像是：

![Prolog節添加JIRA ID對話框](../../../assets/authoring/webeditor-add-customtoolbarbutton-prolog-insertjirareference-dialog.png)

接著，應將「change-request-id」新增至prolog:

![帶有JIRA ID參考的Prolog部分](../../../assets/authoring/webeditor-add-customtoolbarbutton-prolog-sample.png)



## 實作此


### 在Webeditor中新增按鈕，方法是在中進行設定 *ui_config.json*

使用資料夾設定檔來檢查 *ui_config.json* 在「XML編輯器設定」標籤下，將按鈕設定JSON新增至「工具列」群組的所需區段

```
{
    "on-click":"insertJIRARef",
    "icon":"linkCheck",
    "variant":"quiet",
    "type":"button",
    "title":"Insert JIRA Reference"
}
```

[使用此連結來進一步了解資料夾設定檔和設定ui_config.json](https://experienceleague.adobe.com/docs/experience-manager-guides-learn/videos/advanced-user-guide/editor-configuration.html?lang=en)


### 處理新按鈕的點按事件

    注意：以下提及的步驟可作為貼文中附加的套件使用


- 儲存資料夾設定檔後，在專案目錄下建立「cq:ClientLibraryFolder」(可能位於 */apps*)並新增屬性，如下方螢幕擷取所示：
   ![Webeditor的客戶端庫設定](../../../assets/authoring/webeditor-add-customtoolbarbutton-clientlibrarysettings.png)

```
This example uses "coralui3" library to show a dialog as it is used in the Javascript sample we presented.
You may use different library of your choice.
```

- 在此客戶端庫資料夾下，按如下所述建立兩個檔案：
   - *overrides.js*:其中會有javascript程式碼來處理「insertJIRARef」的點按事件（使用附加的套件來取得此javascript的內容）
   - *js.txt*:其中將包含「overrides.js」以啟用此javascript

- 儲存變更，您即可進行測試。


### 測試

- 開啟Web編輯器
- 從使用者偏好設定中，選擇您新增自訂的資料夾設定檔 *ui_config.json*. 如果您將其新增至全域設定檔，則您可能已使用過。
- 開啟主題時，您會注意到工具列有新按鈕「插入日誌參考」
- 然後，您可以如下文所述將prolog區段新增到主題，然後嘗試按一下prolog元素&quot;change-request-reference&quot;內的「插入Jira參考」按鈕

```
<prolog>
    <change-historylist>
        <change-item>
            <change-request-reference>
            </change-request-reference>
            <change-completed></change-completed>
            <change-summary></change-summary>
        </change-item>
    </change-historylist>
</prolog>
```

請參閱下方的螢幕截圖，了解其外觀：

![測試新按鈕](../../../assets/authoring/webeditor-add-customtoolbarbutton-testing.png)


### 附件

- 將安裝具有工具列按鈕動作之javascript程式碼的webeditor用戶端程式庫的clientlibs套件範例： [使用此連結下載](../../../assets/authoring/webeditor-addbuttonontoolbar-insertjira-clientlib.zip)
- 範例 *ui_config.json* 上傳至資料夾設定檔： [下載範例ui_config_json](../../../assets/authoring/sample_ui_config_Guides4.2-InsertJiraReference.json)

```
Please note this is compatible to AEM 6.5 and AEM Guides version 4.2.
If you are using a different version please add the toolbar button to the ui_config.json manually.
```
