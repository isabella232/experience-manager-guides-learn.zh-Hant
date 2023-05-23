---
title: 為站點輸出配置有AEM效檔案名
description: 瞭解如何配置站點輸出的有AEM效檔案名
source-git-commit: 801c306fa120e7889d4b9428fd5bee2849bf1956
workflow-type: tm+mt
source-wordcount: '140'
ht-degree: 0%

---


# 為站點輸出配置有AEM效檔案名 {#id214GK0X0KXA}

與DITA主題允許的有效檔案名字元清單類似，您也可以配置站點輸出的有效檔案名字元AEM清單。 URL中不允許的某些已知字元是： ```'<>`@$```。 這些字元在生成站點輸出檔案名時被配置為在找到時自動轉換為下划線AEM「_」。 允許在「站點」輸出中設定有效字AEM符的配置在中 `com.adobe.fmdita.common.SanitizeNodeNameImpl` 捆綁。 **將不允許的發佈字元集設定為AEM Sites** 設定為在「站點」輸出檔案名中包含要替換為下划線AEM的字元。

**父主題：**[&#x200B;配置檔案名](conf-file-names.md)

