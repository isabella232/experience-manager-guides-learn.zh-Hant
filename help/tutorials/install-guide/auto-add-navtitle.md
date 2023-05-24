---
title: 預設包含@navtitle屬性
description: 瞭解如何依預設包含@navtitle屬性
source-git-commit: 801c306fa120e7889d4b9428fd5bee2849bf1956
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 1%

---


# 預設包含@navtitle屬性 {#id2115BC0J0XA}

您可以在地圖中新增不同型別的參考檔案，例如主題、參考、任務、\(sub\)地圖等。 這些檔案大多支援 `@navtitle` 屬性。 不過，一致使用它的作者並不多。 如果您想要強制使用 `@navtitle` 屬性，然後您可以透過簡單的設定執行此操作。

啟用後，您在地圖中新增的每個參考檔案都會自動取得 `@navtitle` 屬性已新增至其屬性。 此 `@navtitle` 也會取得 `title` 參考內容的元素。

加入 `@navtitle` 屬性預設為參照檔案的屬性，請執行下列步驟：

1. 下載ui\_config.json檔案。

   您可以在全域層級或資料夾層級設定檔中進行此變更。 視您要在何處進行此變更而定，您需要下載個別的ui\_config.json檔案。 如需有關下載ui\_config.json檔案的詳細資訊，請參閱 [設定和自訂XML Web編輯器](conf-folder-level.md#id2065G300O5Z).

1. 搜尋 `ditaAttributes` 定義。

   的預設定義 `ditaAttributes` 為：

   ```json
   "ditaAttributes": {
   "attributes": [],
   "constraint": false,
   "required": {}
   },
   ```

1. 變更 `required` 引數為：

   ```json
   "required": {"navtitle": true}
   ```

1. 儲存檔案。

1. 上傳對應設定檔中的檔案\（全域或資料夾\）。


透過此設定，您新增至對應的每個參考檔案將包含 `@navtitle` 屬性。

