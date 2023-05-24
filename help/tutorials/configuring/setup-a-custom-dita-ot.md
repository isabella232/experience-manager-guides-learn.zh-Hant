---
title: 在中設定自訂DITA-OT [!DNL AEM Guides]
description: 瞭解如何在中設定自訂DITA-OT [!DNL Adobe Experience Manager Guides]
role: Admin
exl-id: f479c2cf-5b8b-4517-be97-81303468007a
source-git-commit: b5e64512956f0a7f33c2021bc431d69239f2a088
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

---

# 在中設定自訂DITA-OT [!DNL AEM Guides] 適用於AEM

新增自訂DITA-OT的步驟記錄於區段中 _使用自訂DITA-OT外掛程式_ 的 _安裝及設定指南_.

整體而言，步驟如下：

+ 取得基本DITA-OT
   + 如果要從取得現成DITA-OT的副本 [!DNL AEM Guides]，從路徑下載 `/etc/fmdita/dita_resources/DITA-OT.zip`
   + 如果您想要取得不同的版本，可以從下載 [dita-ot repo](https://www.dita-ot.org/download)
+ 變更為DITA-OT相似 [新增外掛程式](https://www.dita-ot.org/dev/topics/plugins-installing.html)，或自訂現有外掛程式（請參閱下文相關連結一節中的範例）
+ 上傳 `DITA-OT.zip` 接收至 `/apps/<project-folder>/dita_resources` （建議使用建立自訂專案資料夾的方法）
+ 透過新增DITA設定檔 **[!UICONTROL 工具]** > **[!UICONTROL 指南]** > **[!UICONTROL DITA設定檔]** （使用上傳自訂DITA-OT的DITA-OT路徑，請參閱下面的熒幕擷圖）
   ![DITA設定檔](assets/dita-profile.png)

>[!MORELIKETHIS]
>
>+ [自訂DITA-OT外掛程式範例](https://www.dita-ot.org/dev/topics/pdf-customization.html)

