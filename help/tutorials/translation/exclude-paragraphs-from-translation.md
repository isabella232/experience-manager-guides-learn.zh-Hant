---
title: 從翻譯中排除主題中的段落
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

最簡單的方式是使用translation=no attribute。

+ 作者可以將其他屬性插入為 **translation=no** 在它們不想翻譯的段落上。 需要通知翻譯廠商，他們可以在終端進行設定，以忽略具有此屬性的文字。
+ OOTB機器翻譯(搭配試用Microsoft翻譯聯結器)具有相同的行為。
+ 使用Microsoft翻譯進行測試：如果您定義 **translate=no** 屬性位於段落層級，則不會翻譯完整的段落。 此屬性可在任何元素處定義，且不會翻譯該元素內的內容。


以下是幾個熒幕擷取畫面，進一步說明此問題：

**來源內容**

![來源內容](assets/source-content.jpg)

**西班牙文翻譯內容**

![西班牙文翻譯內容](assets/trans-content.jpg)
