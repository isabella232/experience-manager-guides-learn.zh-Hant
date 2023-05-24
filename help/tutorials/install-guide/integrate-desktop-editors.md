---
title: 整合案頭式XML編輯器
description: 瞭解如何整合桌上型XML編輯器
source-git-commit: 5ac066bb8db32944abd046f64da11eeb1bdbe467
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 0%

---


# 整合案頭式XML編輯器 {#id181GB01G0HS}

市面上有許多XML編輯器，而且您可能已經使用了一個。 Adobe FrameMaker是最強大的XML編輯器之一，它附帶AEM聯結器。 使用FrameMaker中的AEM聯結器，您可以輕鬆連線到AEM存放庫、取出和入庫檔案，以及直接在FrameMaker中編輯檔案。 您也可以設定AEM Guides以從網頁編輯器啟動FrameMaker。 在FrameMaker中開啟檔案後，您可以編輯該檔案，並將其簽回AEM存放庫。

## 從Web編輯器在FrameMaker中啟用檔案編輯

您可以使用FrameMaker或任何其他DITA編輯器來建立和更新DITA內容。 不過，如果您的組織使用FrameMaker作為DITA編輯器，則您可以讓使用者選擇直接在AEM的FrameMaker中開啟DITA檔案。

依預設，您的使用者看不到 **在FrameMaker中開啟** AEM按鈕。 執行以下步驟，在AEM工具列上新增此按鈕：

1. 開啟Adobe Experience Manager Web主控台設定頁面。

   存取設定頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜尋並按一下 **com.adobe.fmdita.xmleditor.config.XmlEditorConfig** 套件組合。

   ![](assets/open-in-fm-toolbar.png){width="550" align="left"}

1. 選取 **在FrameMaker中顯示開啟按鈕** 選項。

1. 按一下「**儲存**」。


當您啟用 **在FrameMaker中顯示開啟按鈕** 選項，然後 **在FrameMaker中開啟** 在AEM存放庫中選取任何DITA檔案時，按鈕就會顯示。 當此選項為 *未啟用*，則 **在FrameMaker中開啟** 按鈕只有在您選取存放庫中的.fm或.book檔案時才會顯示。

