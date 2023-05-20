---
title: 在webeditor工具欄中添加新的自定義可操作按鈕
description: 瞭解如何在webeditor工具欄中添加新的自定義按鈕並調用javascript以自定義操作它。
exl-id: 118c4545-9eda-4e1e-a224-843767e49b5b
source-git-commit: ed3adf0cf8006c76461de34c6a2a4ba38d8b3406
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 0%

---

# 在webeditor工具欄中添加新的自定義可操作按鈕

在本文中，我們將瞭解如何在webeditor工具欄中添加新的自定義按鈕並調用javascript以執行所需的自定義操作。

將可操作的按鈕添加到Webeditor涉及以下步驟：
- 在 *ui_config_json* 在需要它的地方
- 在編輯器中註冊按鈕，讓用戶在按一下按鈕時執行操作


## 以實例實施

讓我們通過一個示例來瞭解這一點，作者希望將jira引用添加到主題prolog節。 帶有嵌入式jira reference-id的prolog節可能如下所示：

![帶JIRA ID引用的Prolog節](../../../assets/authoring/webeditor-add-customtoolbarbutton-prolog-sample.png)

應從API中檢索包含JIRA ID的「change-request-id」元素（例如，基於應用程式描述的特定JIRA查詢）。 當用戶正在創作prolog節時，用戶應能夠按一下按鈕並從Web編輯器工具欄插入jira引用ID，類似於：

![Prolog節 — 添加JIRA引用](../../../assets/authoring/webeditor-add-customtoolbarbutton-prolog-insertjirareference.png)

當用戶按一下該按鈕時，它應顯示一個對話框，該對話框應會拉出可能的選項並允許用戶選擇所需的JIRA ID，類似於：

![Prolog節添加JIRA ID對話框](../../../assets/authoring/webeditor-add-customtoolbarbutton-prolog-insertjirareference-dialog.png)

然後應將&quot;change-request-id&quot;添加到prolog:

![帶JIRA ID引用的Prolog節](../../../assets/authoring/webeditor-add-customtoolbarbutton-prolog-sample.png)



## 實施此


### 通過在中配置按鈕，在Webeditor中添加按鈕 *ui_config_json*

使用資料夾配置檔案檢查 *ui_config_json* 在「XML編輯器配置」頁籤下，將按鈕配置JSON添加到「工具欄」組的所需部分

```
{
    "on-click":"insertJIRARef",
    "icon":"linkCheck",
    "variant":"quiet",
    "type":"button",
    "title":"Insert JIRA Reference"
}
```

[使用此連結可瞭解有關資料夾配置檔案和配置ui_config.json的詳細資訊](https://experienceleague.adobe.com/docs/experience-manager-guides-learn/videos/advanced-user-guide/editor-configuration.html?lang=en)


### 處理新按鈕的點擊事件

    注：下面提到的步驟可作為本帖中附加的軟體包提供


- 保存資料夾配置檔案後，在項目目錄下建立一個「cq:ClientLibraryFolder」(可能位於 */app*)並添加屬性，如下面的螢幕快照所示：
   ![Webeditor的客戶端庫設定](../../../assets/authoring/webeditor-add-customtoolbarbutton-clientlibrarysettings.png)

```
This example uses "coralui3" library to show a dialog as it is used in the Javascript sample we presented.
You may use different library of your choice.
```

- 在此客戶端庫資料夾下，建立以下兩個檔案：
   - *覆蓋.js*:它將具有javascript代碼來處理「insertJIRARef」的按一下事件（使用附加的包獲取此javascript的內容）
   - *js.txt*:其中將包含&quot;overrides.js&quot;以啟用此javascript

- 保存更改，您應準備好test。


### 測試

- 開啟Web編輯器
- 從用戶首選項中選擇添加自定義的資料夾配置檔案 *ui_config_json*。 如果將其添加到全局配置檔案中，則您可能已在使用它。
- 開啟主題時，您會注意到工具欄有一個新按鈕「插入Jira引用」
- 然後，您可以將prolog節添加到主題中，並嘗試在prolog元素&quot;change-request-reference&quot;內按一下&quot;Insert Jira Reference&quot;按鈕

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

請參閱下面的螢幕截圖，瞭解其外觀：

![Test新按鈕](../../../assets/authoring/webeditor-add-customtoolbarbutton-testing.png)


### 附件

- 將安裝webeditor客戶端庫的示例客戶端軟體包，其中包含用於工具欄按鈕操作的javascript代碼： [使用此連結下載](../../../assets/authoring/webeditor-addbuttonontoolbar-insertjira-clientlib.zip)
- 示例 *ui_config_json* 可以上載到資料夾配置檔案： [下載示例ui_config_json](../../../assets/authoring/sample_ui_config_Guides4.2-InsertJiraReference.json)

```
Please note this is compatible to AEM 6.5 and AEM Guides version 4.2.
If you are using a different version please add the toolbar button to the ui_config.json manually.
```
