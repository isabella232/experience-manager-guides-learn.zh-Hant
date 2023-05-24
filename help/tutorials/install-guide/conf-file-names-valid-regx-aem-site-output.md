---
title: 設定AEM網站輸出的有效檔案名稱
description: 瞭解如何為AEM網站輸出設定有效的檔案名稱
source-git-commit: 801c306fa120e7889d4b9428fd5bee2849bf1956
workflow-type: tm+mt
source-wordcount: '140'
ht-degree: 0%

---


# 設定AEM網站輸出的有效檔案名稱 {#id214GK0X0KXA}

與DITA主題允許的有效檔案名稱字元清單類似，您也可以為AEM Site輸出設定有效的檔案名稱字元清單。 URL中不允許使用的部分已知字元包括： ```'<>`@$```. 這些字元已設定為在產生AEM Site輸出檔案名稱時找到時自動轉換為底線「_」。 可讓您在AEM Site輸出中設定有效字元的設定會顯示在 `com.adobe.fmdita.common.SanitizeNodeNameImpl` 套件組合。 **設定發佈至AEM Sites時不允許使用的字元集** 設定在AEM Site輸出檔案名稱中包含您想要以底線取代的字元。

**父級主題：**[&#x200B;設定檔案名稱](conf-file-names.md)

