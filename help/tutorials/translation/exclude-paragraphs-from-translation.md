---
title: 從翻譯中排除主題內的段落
description: 如何從翻譯中排除主題中的段落
feature: Translation
role: User
exl-id: 21e41bb4-52f3-4352-92d9-4a60f636de99
source-git-commit: b5e64512956f0a7f33c2021bc431d69239f2a088
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 0%

---

# 如何從翻譯中排除主題中的段落

最簡單的方法是使用translation=no attribute。

+ 作者可以將附加屬性插入為 **翻譯=否** 他們不想翻譯的段落。 翻譯供應商需要得到通知，他們可以在其末尾進行配置以忽略具有此屬性的文本。
+ OOTB機器翻譯(帶試用的Microsoft翻譯連接器)表現出相同的行為。
+ 測試Microsoft翻譯：定義 **轉換=否** 屬性，則它不翻譯完整段落。 可以在任何元素上定義此屬性，並且不會翻譯該元素中的內容。


下面是幾個螢幕截圖，進一步解釋了這一點：

**源內容**

![源內容](assets/source-content.jpg)

**西班牙語翻譯內容**

![西班牙語翻譯內容](assets/trans-content.jpg)
