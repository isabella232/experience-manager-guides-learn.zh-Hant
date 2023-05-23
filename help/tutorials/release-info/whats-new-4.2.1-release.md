---
title: 發行說明 | 《Adobe Experience Manager指南》4.2.1版新增內容
description: 瞭解《Adobe Experience Manager指南》4.2.1版中的新增和增強功能
source-git-commit: 66b83f940457c64dadc5b319e1274960ac0f6da8
workflow-type: tm+mt
source-wordcount: '694'
ht-degree: 0%

---

# 《Adobe Experience Manager指南》4.2.1版的新增功能（2023年5月）

本文介紹《Adobe Experience Manager指南》4.2.1版(後稱 *參考AEM線*)。

有關升級說明、相容性清單以及此版本中修復的問題的詳細資訊，請參見 [發行說明](release-notes-4.2.1.md) 文章。

## 從Web編輯器導航到主AEM頁

現在，您可以輕鬆從Web編輯器導航到「導AEM航」頁。

![](assets/web-editor-launch-page.png){width="800" align="left"}

* 按一下 **參考線** 表徵圖。![](assets/aem-guides-icon.png) )，返回「導航」AEM頁面。


## PDF發佈中的高級元資料支援

指AEM南現在為映射到PDF輸出中元資料的元資料提供高級支援。 元資料選項包括關於文檔及其內容的資訊，例如作者的名稱、文檔標題、關鍵字、版權資訊以及其他資料欄位。

<img src="assets/pdf-metadata.png" alt=" 本地pdf元資料">

可以導入文XMP件，「AEM參考線」可以從檔案中選取資訊。 您還可以選擇使用下拉菜單提供元資料名稱和值。 也可以通過在名稱欄位中直接鍵入來添加自定義元資料。

有關詳細資訊，請參閱 **元資料** 功能說明 [建立PDF輸出預設](../web-editor/native-pdf-web-editor.md)。

### 「增強的大綱視圖」面板

參考AEM線提供了一個改進的「大綱視圖」面板，在該面板中可以獲取文檔中使用的元素的分層視圖。

<img src="assets/select-element-content-outline-view_cs.png" alt=" 本地pdf元資料">

「大綱視圖」提供了以下增強：

* 「視圖選項」下拉清單顯示在「大綱視圖」面板的頂部。 如果元素具有ID、屬性和文本，則可以從下拉清單中選擇它們以與元素一起顯示它們。 可在「大綱視圖」面板中顯示的屬性由管理員在「大綱視圖」中配置的「顯示屬性」設定確定 **編輯器設定**。

* 使用搜索功能，可以按元素的名稱、id、文本或屬性值搜索元素。

有關詳細資訊，請參閱 [左面板](../user-guide/web-editor-features.md) 的子菜單。

## 從Web編輯器生成多媒體報告

指AEM南提供了生成技術文檔報告的功能。  您可以使用此功能查看主題清單並管理文檔的元資料。 現在，您還可以從 **報告** 的子菜單。

您可以生成多媒體報告，其中包含有關當前映射中參考中使用的多媒體的詳細資訊。 您可以靈活地過濾和排序報告中列出的多媒體檔案。
您還可以生成CSV以下載DITA映射中使用的多媒體的當前快照。

<img src="assets/web-editor-reports-multimedia.png" alt="多媒體報告" width="600">

有關詳細資訊，請參閱中的「生成多媒體報告」功能說明 [來自Web編輯器的DITA映射報告](../user-guide/reports-web-editor.md) 的子菜單。

## 本地PDF |更改欄以指示目錄中更改的主題

現AEM在，參考線允許您快速確定PDF輸出目錄中更改的主題。  它顯示目錄中更改主題左側的更改欄。 可以按一下目錄中的主題並查看詳細更改。

<img src="assets/change-marker-toc.png" alt="更改目錄中的標籤 " width="500">

有關詳細資訊，請參閱 [使用自定義更改條樣式](../native-pdf/change-bar-style.md)。



## 本地PDF |在腳注元件中設定頁面標籤樣式

現在，您可以在腳注中設定頁面標籤樣式。 例如，可添加括弧或更改其顏色。 這些樣式可幫助用戶輕鬆識別文檔中的頁面標籤。

有關詳細資訊，請參閱 [在腳注中使用自定義樣式](../native-pdf/footnote-number-style.md)。

## 在Web編輯器中開啟和播放視頻或音頻檔案

指AEM南現在提供了在Web編輯器中開啟和播放音頻或視頻檔案的功能。 可以更改音量或視頻的視圖。 在快捷菜單中，您還可以 **下載**&#x200B;更改 **回放速度**&#x200B;或 **圖片**。

<img src="assets/video-web-editor.png" alt="播放視頻" width="600">

有關詳細資訊，請參閱 [左面板](../user-guide/web-editor-features.md) 的子菜單。
