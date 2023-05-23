---
title: 整合基於案頭的XML編輯器
description: 瞭解如何整合基於案頭的XML編輯器
source-git-commit: 5ac066bb8db32944abd046f64da11eeb1bdbe467
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 0%

---


# 整合基於案頭的XML編輯器 {#id181GB01G0HS}

市場上有很多XML編輯器可用，而且您可能已經在使用了它。 Adobe FrameMaker是連接器附帶的最強大的XML編輯AEM器。 使用AEMFrameMaker中的連接器，可以輕鬆地與儲存庫AEM連接、簽出和簽入檔案，以及直接在FrameMaker中編輯檔案。 您還可以配置AEM參考線，以從Web編輯器啟動FrameMaker。 在FrameMaker中開啟檔案後，可以編輯檔案並將其簽回儲存AEM庫。

## 從Web編輯器在FrameMaker中啟用檔案編輯

可以使用FrameMaker或任何其他DITA編輯器建立和更新DITA內容。 但是，如果您的組織將FrameMaker用作DITA編輯器，則您可以為用戶提供一個選項，從中直接在FrameMaker中打AEM開DITA文檔。

預設情況下，您的用戶看不到 **在FrameMaker中開啟** 的子AEM菜單。 執行以下步驟以在工具欄上添加此AEM按鈕：

1. 開啟「Adobe Experience ManagerWeb控制台配置」頁。

   訪問配置頁的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索並按一下 **com.adobe.fmdita.xmleditor.config.XmlEditorConfig** 捆綁。

   ![](assets/open-in-fm-toolbar.png){width="550" align="left"}

1. 選擇 **在FrameMaker按鈕中顯示「開啟」** 的雙曲餘切值。

1. 按一下「**儲存**」。


啟用 **在FrameMaker按鈕中顯示「開啟」** ，則 **在FrameMaker中開啟** 頁籤頁面中的DITA檔案。 當此選項為 *未啟用*，也請參見Wiki頁。 **在FrameMaker中開啟** 僅當在儲存庫中選擇.fm或.book檔案時，才顯示按鈕。

