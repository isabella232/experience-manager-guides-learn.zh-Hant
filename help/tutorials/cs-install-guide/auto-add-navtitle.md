---
title: 預設包含@navtitle屬性
description: 瞭解如何依預設包含@navtitle屬性
source-git-commit: 6051181e243cf71919901093c1b5590f21832545
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 1%

---


# 預設包含@navtitle屬性 {#id2115BC0J0XA}

您可以在地圖中新增不同型別的參考檔案，例如主題、參考、任務、\(sub\)地圖等。 這些檔案大多支援 `@navtitle` 屬性。 不過，一致使用它的作者並不多。 如果您想要強制使用 `@navtitle` 屬性，然後您可以透過簡單的設定執行此操作。

啟用後，您在地圖中新增的每個參考檔案都會自動取得 `@navtitle` 屬性已新增至其屬性。 此 `@navtitle` 也會取得 `title` 參考內容的元素。

加入 `@navtitle` 屬性預設為參照檔案的屬性，請執行下列步驟：

1. 若要下載UI設定檔，請以管理員身分登入Adobe Experience Manager。

1. 按一下頂端的Adobe Experience Manager連結，然後選擇 **工具**.
1. 選取 **指南** 從工具清單中按一下 **資料夾設定檔**.
1. 按一下 **全域設定檔** 圖磚。
1. 選取 **XML編輯器設定** 標籤並按一下 **編輯** 圖示在頂端
1. 按一下 **下載** 圖示可在本機系統上下載ui\_config.json檔案。
1. 您可以在全域層級或資料夾層級設定檔中進行此變更。 視您要在何處進行此變更而定，您需要下載個別的ui\_config.json檔案。 如需有關下載ui\_config.json檔案的詳細資訊，請參閱 [設定和自訂XML Web編輯器](conf-folder-level.md#id2065G300O5Z).

1. 搜尋 `ditaAttributes` 定義。

   的預設定義 `ditaAttributes` 為：

   ```
   "ditaAttributes": {
                           "attributes": [],
                           "constraint": false,
                           "required": {}
                           },
   ```

1. 變更 `required` 引數為：

   ```
   "required": {"navtitle": true}
   ```

1. 儲存檔案。

1. 上傳對應設定檔中的檔案\（全域或資料夾\）。


透過此設定，您新增至對應的每個參考檔案將包含 `@navtitle` 屬性。

**父級主題：**[&#x200B;自訂Web編輯器](conf-web-editor.md)

