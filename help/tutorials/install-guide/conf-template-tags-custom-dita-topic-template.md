---
title: 配置自定義DITA主題模板
description: 瞭解如何配置自定義DITA主題模板
source-git-commit: 801c306fa120e7889d4b9428fd5bee2849bf1956
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 2%

---


# 配置自定義DITA主題模板 {#id16A7G0O02TD}

指AEM南附帶以下DITA主題模板：

- 主題

- 任務

- 概念

- 參考

- 字彙表

- 疑難排解

- 空白


您可以根據創作要求使用這些模板建立主題模板。 空白DITA模板不包含任何結構或元素，如其他模板。 如果您的模板是高度自定義的並且不基於任何常規DITA主題模板，則可以使用空白模板作為基本模板。

要自定義DITA主題模板並將其用於創作，您需要執行以下三項主要任務：

1. *\（可選\）* [配置自定義DITA模板資料夾路徑](#id191LCF0095Z)

1. [建立自定義創作模板](conf-folder-level.md#id1917D0EG0HJ)

1. 將自定義模板添加到全局或資料夾級配置檔案中，如 [配置創作模板](conf-folder-level.md#id1889D0IL0Y4) 節


## 配置自定義DITA模板資料夾路徑 {#id191LCF0095Z}

指AEM南允許您配置資料夾以儲存自定義的DITA映射和模板。 預設情況下，模板檔案儲存在DAM的以下資料夾中：

`/content/dam/dita-templates/`

要管理主題和映射模板檔案，有專用資料夾用於儲存主題和映射模板。 預設情況下，所有主題模板都儲存在 `/content/dam/dita-templates/topics`

的子菜單。 所有映射模板都儲存在 `/content/dam/dita-templates/maps` 的子菜單。

作為管理員，您可以選擇在預設資料夾中建立自定義映射或主題模板，或建立自己的資料夾以儲存自定義模板。 如果您計畫使用預設資料夾，則可以跳過此過程。

要為自定義DITA主題模板配置資料夾，請執行以下步驟：

>[!IMPORTANT]
>
> 如果要使用預設資料夾來儲存自定義模板，可以跳過此過程。

1. 開啟「Adobe Experience ManagerWeb控制台配置」頁。

   訪問配置頁的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索並按一下 *com.adobe.fmdita.config.ConfigManager* 捆綁。

1. 在 **模板位置** 屬性，指定儲存自定義模板的位置。

1. 按一下「**儲存**」。


如果DAM中存在指定的位置，則所有預設映射和主題模板都會複製到該資料夾中。 如果位置不存在，則使用所有預設映射和主題模板建立資料夾。

**父主題：**[&#x200B;配置主題和映射模板](conf-template-tags.md)

