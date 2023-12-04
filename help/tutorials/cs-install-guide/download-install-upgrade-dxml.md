---
title: 升級AEM指南
description: 瞭解如何升級AEM Guides
source-git-commit: 880cd344ceb65ea339be699ebcad41c0d62e168a
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---

# 升級AEM指南 {#id213BD050YPH}

1. 存取您的Cloud Manager的Git存放庫。

1. 更新dox/dox.installer/pom.xml檔案。

1. 將dox.version變數的值更新為Adobe提供的版本詳細資料。

1. 提交變更並執行Cloud Manager管道以部署升級的套件。


>[!NOTE]
>
> 如需有關使用CI/CD管道的詳細資訊，請參閱 [在Adobe Cloud Manager中使用CI/CD管道](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/cloud-manager/use-the-cicd-pipeline-in-cloud-manager-for-aem.html).

## 清除瀏覽器快取

完成升級程式後，所有使用者必須先清除瀏覽器快取，才能使用AEM Guides的升級版本。

**父級主題：**[&#x200B;下載並安裝](download-install.md)
