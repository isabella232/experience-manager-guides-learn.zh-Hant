---
title: 根據UUID設定自動檔案名稱
description: 瞭解如何根據UUID設定自動檔案名稱
source-git-commit: 4f15166b1b250578f07e223b0260aacf402224be
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 1%

---


# 根據UUID設定自動檔案名稱 {#id205QG070D5Z}

根據預設，建立主題或地圖檔案時，作者也可以選擇指定檔案名稱。 作者可自由依需求指派檔案名稱。 但是，這可能會導致不一致，並且在大型檔案系統中可以看到各種檔案名稱。 身為管理員，您可以限製作者為他們在系統中建立的檔案指派檔案名稱。 對於每個新主題或對應檔案，您可以選擇自動指派以UUID為基礎的檔案名稱。

使用中提供的指示 [設定覆寫](download-install-additional-config-override.md#) 以建立組態檔。 在設定檔案中，提供下列\(property\)詳細資訊，以根據UUID設定自動檔案名稱：

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.xmleditor.config.XmlEditorConfig` | `xmleditor.uniquefilenames` | 布林值\(true/false\)。<br> **預設值**： false |

>[!NOTE]
>
> 開啟此選項後，作者在建立新主題或對應檔案時，看不到指定檔案名稱的選項。 您可以從Assets UI和Web編輯器建立新的主題或地圖檔案。

**父級主題：**[&#x200B;設定檔案名稱](conf-file-names.md)

