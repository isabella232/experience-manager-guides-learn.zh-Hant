---
title: 在Webeditor工具列中新增自訂可操作按鈕
description: 瞭解如何在瀏覽器工具列中新增自訂按鈕，並呼叫javascript以自訂操作。
exl-id: 118c4545-9eda-4e1e-a224-843767e49b5b
source-git-commit: ed3adf0cf8006c76461de34c6a2a4ba38d8b3406
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 0%

---

# 在Webeditor工具列中新增自訂可操作按鈕

在本文中，我們將瞭解如何在瀏覽器工具列中新增自訂按鈕，並呼叫javascript以執行所需的自訂操作。

將可操作的按鈕新增至Webeditor涉及以下步驟：
- 將按鈕新增至 *ui_config.json* 在需要的位置
- 在瀏覽器中註冊按一下按鈕的事件，讓使用者在按一下按鈕時執行動作


## 以範例來實作

讓我們透過作者想要在主題序言區段新增jira參考的範例來瞭解這一點。 內嵌jira reference-id的prolog區段可能如下所示：

![含JIRA ID參考的Prolog區段](../../../assets/authoring/webeditor-add-customtoolbarbutton-prolog-sample.png)

包含JIRA ID的「change-request-id」元素應從API中擷取（比方說，根據應用程式描述的特定JIRA查詢）。 當使用者編寫prolog區段時，使用者應該能夠按一下按鈕並從網頁編輯器工具列插入jira參考id，例如：

![Prolog區段 — 新增JIRA參考](../../../assets/authoring/webeditor-add-customtoolbarbutton-prolog-insertjirareference.png)

而且當使用者按一下按鈕時，應該會顯示對話方塊，其中應提取可能的選項，並允許使用者選取所需的JIRA ID，例如：

![Prolog區段新增JIRA ID對話方塊](../../../assets/authoring/webeditor-add-customtoolbarbutton-prolog-insertjirareference-dialog.png)

然後應將「change-request-id」新增至prolog：

![含JIRA ID參考的Prolog區段](../../../assets/authoring/webeditor-add-customtoolbarbutton-prolog-sample.png)



## 實作此專案


### 藉由在中設定按鈕，將其新增至Webeditor *ui_config.json*

使用資料夾設定檔來檢查 *ui_config.json* 在「XML編輯器設定」索引標籤下方，將按鈕設定JSON新增到「工具列」群組的所需區段中

```
{
    "on-click":"insertJIRARef",
    "icon":"linkCheck",
    "variant":"quiet",
    "type":"button",
    "title":"Insert JIRA Reference"
}
```

[使用此連結來進一步瞭解資料夾設定檔和設定ui_config.json](https://experienceleague.adobe.com/docs/experience-manager-guides-learn/videos/advanced-user-guide/editor-configuration.html?lang=en)


### 處理新按鈕的點按事件

    注意：以下提及的步驟可作為此貼文附加的套件提供


- 儲存資料夾設定檔後，在專案目錄(可能位於 */apps*)並新增屬性，如下列熒幕擷圖所示：
   ![Webeditor的使用者端資料庫設定](../../../assets/authoring/webeditor-add-customtoolbarbutton-clientlibrarysettings.png)

```
This example uses "coralui3" library to show a dialog as it is used in the Javascript sample we presented.
You may use different library of your choice.
```

- 在此使用者端程式庫資料夾底下建立兩個檔案，如下所述：
   - *覆寫.js*：會有javascript程式碼來處理「insertJIRARef」的點選事件（使用附加的套件取得此javascript的內容）
   - *js.txt*：其中包含「overrides.js」以啟用此javascript

- 儲存變更，您就可以開始測試了。


### 測試

- 開啟Web編輯器
- 從使用者偏好設定中選擇您新增自訂的資料夾設定檔 *ui_config.json*. 如果您將其新增至全域設定檔，表示您可能已經在使用它。
- 開啟一個主題，您會注意到工具列有一個新按鈕「插入Jira參考」
- 然後，您可以將prolog區段（如下所示）新增至主題，並嘗試在prolog元素「change-request-reference」內按一下「插入Jira參考」按鈕

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

請參考下方的熒幕擷圖以瞭解其外觀：

![測試新按鈕](../../../assets/authoring/webeditor-add-customtoolbarbutton-testing.png)


### 附件

- 範例clientlibs套件將會安裝具有工具列按鈕動作javascript程式碼的webeditor使用者端程式庫： [使用此連結下載](../../../assets/authoring/webeditor-addbuttonontoolbar-insertjira-clientlib.zip)
- 範例 *ui_config.json* 上傳至資料夾設定檔的許可權： [下載範例ui_config.json](../../../assets/authoring/sample_ui_config_Guides4.2-InsertJiraReference.json)

```
Please note this is compatible to AEM 6.5 and AEM Guides version 4.2.
If you are using a different version please add the toolbar button to the ui_config.json manually.
```
