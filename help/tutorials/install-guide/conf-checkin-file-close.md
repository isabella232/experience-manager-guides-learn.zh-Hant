---
title: 配置在關閉時提示簽入檔案
description: 瞭解如何在關閉時配置提示以簽入檔案
source-git-commit: 801c306fa120e7889d4b9428fd5bee2849bf1956
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 1%

---


# 配置在關閉時提示簽入檔案 {#id222HC040PE8}

當用戶嘗試使用 **關閉** 的子菜單。 **關閉**&#x200B;選項，如果檔案有未保存的資料或未保存的版本，則會顯示對話框。 如果檔案已鎖定，則系統會提示用戶解鎖該檔案。

的 **解鎖檔案** 複選框預設未啟用，您需要從configMgr中啟用該複選框。 執行以下步驟以在Web編輯器中預設啟用該選項：

1. 開啟「Adobe Experience ManagerWeb控制台配置」頁。

   訪問配置頁的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索並按一下 **com.adobe.fmdita.xmleditor.config.XmlEditorConfig** 捆綁。

1. 選擇 **在關閉時請求籤入** 的雙曲餘切值。

1. 按一下「**儲存**」。


啟用此配置後， **解鎖檔案** 複選框。

有關詳細資訊，請參閱 *檔案關閉和保存方案* 的上界。

**父主題：**[&#x200B;自定義Web編輯器](conf-web-editor.md)

