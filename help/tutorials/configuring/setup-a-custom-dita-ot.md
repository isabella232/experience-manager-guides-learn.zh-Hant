---
title: 在中設定自定義DITA-OT [!DNL AEM Guides]
description: 瞭解如何在中設定自定義DITA-OT [!DNL Adobe Experience Manager Guides]
role: Admin
exl-id: f479c2cf-5b8b-4517-be97-81303468007a
source-git-commit: b5e64512956f0a7f33c2021bc431d69239f2a088
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

---

# 在中設定自定義DITA-OT [!DNL AEM Guides] AEM

添加自定義DITA-OT的步驟在一節中介紹 _使用自定義DITA-OT插件_ 的 _安裝及設定指南_。

從高度上講，步驟是：

+ 獲取基本DITA-OT
   + 如果要從中獲取現成DITA-OT的副本 [!DNL AEM Guides]，從路徑下載 `/etc/fmdita/dita_resources/DITA-OT.zip`
   + 如果要獲取其他版本，則可以從 [dita ot回購](https://www.dita-ot.org/download)
+ 對DITA-OT進行更改 [添加新插件](https://www.dita-ot.org/dev/topics/plugins-installing.html)，或自定義現有插件（請參閱下面相關連結部分中的示例）
+ 上載 `DITA-OT.zip` 接收 `/apps/<project-folder>/dita_resources` （建議使用建立自定義項目資料夾的方法）
+ 通過添加DITA配置檔案 **[!UICONTROL 工具]** > **[!UICONTROL 參考線]** > **[!UICONTROL DITA配置檔案]** （使用上載自定義DITA-OT的DITA-OT路徑，請參閱下面的螢幕截圖）
   ![DITA配置檔案](assets/dita-profile.png)

>[!MORELIKETHIS]
>
>+ [自定義DITA-OT插件示例](https://www.dita-ot.org/dev/topics/pdf-customization.html)

