---
title: 設定自訂DITA主題範本
description: 瞭解如何設定自訂DITA主題範本
source-git-commit: 801c306fa120e7889d4b9428fd5bee2849bf1956
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 2%

---


# 設定自訂DITA主題範本 {#id16A7G0O02TD}

AEM Guides隨附下列DITA主題範本：

- 主題

- 任務

- 概念

- 參考

- 字彙表

- 疑難排解

- 空白


您可以根據編寫需求，使用任何這些範本來建立主題範本。 空白DITA範本不包含其他範本的任何結構或元素。 如果您的範本是高度自訂的，且不是以任何一般DITA主題範本為基礎，則可以使用「空白」範本作為基礎。

若要自訂DITA主題範本並將其用於編寫，您需要執行下列三個主要工作：

1. *\（可選\）* [設定自訂DITA範本資料夾路徑](#id191LCF0095Z)

1. [建立自訂編寫範本](conf-folder-level.md#id1917D0EG0HJ)

1. 將自訂範本新增至全域或資料夾層級設定檔，如 [設定製作範本](conf-folder-level.md#id1889D0IL0Y4) 區段


## 設定自訂DITA範本資料夾路徑 {#id191LCF0095Z}

AEM Guides可讓您設定資料夾以儲存自訂的DITA map和範本。 根據預設，範本檔案儲存在DAM的以下資料夾中：

`/content/dam/dita-templates/`

為了管理主題和對應範本檔案，有專用的資料夾來儲存主題和對應範本。 依預設，所有主題範本都儲存在 `/content/dam/dita-templates/topics`

資料夾。 所有地圖範本都儲存在 `/content/dam/dita-templates/maps` 資料夾。

作為管理員，您可以選擇在預設資料夾中建立自訂地圖或主題範本，或建立您自己的資料夾來儲存自訂範本。 如果您計畫使用預設資料夾，則可以跳過此程式。

若要為自訂DITA主題範本設定資料夾，請執行下列步驟：

>[!IMPORTANT]
>
> 如果您想要使用預設資料夾來儲存自訂範本，可以跳過此程式。

1. 開啟Adobe Experience Manager Web主控台設定頁面。

   存取設定頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜尋並按一下 *com.adobe.fmdita.config.ConfigManager* 套件組合。

1. 在 **範本位置** 屬性，指定儲存自訂範本的位置。

1. 按一下「**儲存**」。


如果DAM中存在指定的位置，則所有預設地圖和主題範本都會複製到該資料夾中。 如果該位置不存在，則會使用所有預設地圖和主題範本建立該資料夾。

**父級主題：**[&#x200B;設定主題和對應範本](conf-template-tags.md)

