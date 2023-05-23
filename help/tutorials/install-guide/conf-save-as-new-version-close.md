---
title: 配置關閉時提示另存為新版本
description: 瞭解如何在關閉時配置提示以另存為新版本
source-git-commit: 801c306fa120e7889d4b9428fd5bee2849bf1956
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---


# 配置關閉時提示另存為新版本 {#id222HBI00XXA}

當用戶嘗試使用 **關閉** 的子菜單。 **關閉** 選項，如果檔案有未保存的資料或未保存的版本，則會顯示對話框。 如果未保存版本，則系統將提示用戶將檔案另存為新版本。

的 **另存為新版本** 複選框預設未啟用，您需要從configMgr中啟用該複選框。 執行以下步驟以在Web編輯器中預設啟用該選項：

1. 開啟「Adobe Experience ManagerWeb控制台配置」頁。

   訪問配置頁的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索並按一下 **com.adobe.fmdita.xmleditor.config.XmlEditorConfig** 捆綁。

1. 選擇 **在關閉時請求新版本** 的雙曲餘切值。

1. 按一下「**儲存**」。


選中此選項時， **另存為新版本** 複選框。

有關詳細資訊，請參閱 *檔案關閉和保存方案* 的上界。

**父主題：**[&#x200B;自定義Web編輯器](conf-web-editor.md)

