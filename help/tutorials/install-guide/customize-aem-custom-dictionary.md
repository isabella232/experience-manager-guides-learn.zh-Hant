---
title: 自定義AEM預設詞典
description: 瞭解如何自定義默AEM認詞典
source-git-commit: 5ac066bb8db32944abd046f64da11eeb1bdbe467
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---


# 自定義AEM預設詞典 {#id209SD8000WU}

可以將Web編輯器配置為使AEM用拼寫檢查器或瀏覽器的拼寫檢查器。 如果您選擇使用拼寫檢AEM查器，則您可以靈活地定義自定義詞清單。 然後，這些自定義詞會添加AEM到字典中，並且這些詞在Web編輯器中不會標籤為\（不正確\）。

執行以下步驟以建立在詞典中添加的自定義詞AEM清單：

1. 登錄並AEM開啟CRXDE Lite模式。

1. 導航到以下節點：

   /apps/fmdita/config

1. 建立名為user\_dictionary.txt的新檔案。

1. 開啟檔案並添加要在自定義詞典中定義的詞清單。

   以下螢幕快照顯示添加到user\_dictionary.txt檔案中的自定義詞清單：

   ![](assets/custom-words-list-dictionary.png){width="650" align="left"}

1. 保存並關閉檔案。


作者需要重新啟動其Web編輯器會話，以便在字典中更新自定義詞AEM表。

**父主題：**[&#x200B;自定義Web編輯器](conf-web-editor.md)

