---
title: 預設情況下包@navtitle屬性
description: 瞭解如何預設包@navtitle屬性
source-git-commit: 801c306fa120e7889d4b9428fd5bee2849bf1956
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 1%

---


# 預設情況下包@navtitle屬性 {#id2115BC0J0XA}

可以在映射中添加不同類型的引用檔案，如主題、引用、任務、\(sub\)映射等。 這些檔案大多支援 `@navtitle` 屬性。 然而，並沒有多少作者一貫使用它。 如果要強制使用 `@navtitle` 屬性，然後可以使用簡單的配置執行此操作。

啟用後，您在映射中添加的每個引用檔案將自動獲取 `@navtitle` 屬性。 的 `@navtitle` 也將獲得 `title` 引用內容的元素。

要包括 `@navtitle` 預設情況下，在引用檔案的屬性中執行以下步驟：

1. 下載ui\_config.json檔案。

   您可以在全局級別或資料夾級別配置檔案中進行此更改。 根據您要進行此更改的位置，您需要下載相應的ui\_config.json檔案。 有關下載ui\_config.json檔案的詳細資訊，請參見 [配置和自定義XML Web編輯器](conf-folder-level.md#id2065G300O5Z)。

1. 搜索 `ditaAttributes` 定義。

   預設定義 `ditaAttributes` 為：

   ```json
   "ditaAttributes": {
   "attributes": [],
   "constraint": false,
   "required": {}
   },
   ```

1. 更改 `required` 參數為：

   ```json
   "required": {"navtitle": true}
   ```

1. 儲存檔案。

1. 上載相應配置檔案\（全局或資料夾\）中的檔案。


使用此配置，添加到映射的每個引用檔案都將包含 `@navtitle` 屬性。

