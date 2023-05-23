---
title: 為「標籤」視圖配置預設值
description: 瞭解如何為「標籤」視圖配置預設值
source-git-commit: 5ac066bb8db32944abd046f64da11eeb1bdbe467
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---


# 為「標籤」視圖配置預設值 {#id223GN0M0NDC}

AEM參考線允許您在Web編輯器中配置「標籤視圖」的預設狀態，這有助於在新用戶會話中將「標籤視圖」預設保持開啟或關閉。請執行以下步驟來配置「標籤視圖」的預設值：

1. 以管理員身份登錄到Adobe Experience Manager，下載UI配置檔案。
1. 按一下頂部的Adobe Experience Manager連結，然後選擇 **工具**。
1. 選擇 **參考線** 按一下 **資料夾配置檔案**。
1. 按一下 **全局配置檔案** 平鋪。
1. 選擇 **XML編輯器配置** ，然後按一下 **編輯** 表徵圖。
1. 在 **XML編輯器UI配置** 的 **下載** 表徵圖 `ui_config.json` 檔案。
1. 在 `ui_config.json` 檔案，通過更改defaultValues部分更改預設標籤視圖狀態，如下所示：

   ```json
   "defaultValues":
                   {
                   "tagsView": true
                   }
   ```

1. 保存檔案並上傳。

>[!NOTE]
>
> 用戶在Web編輯器中啟用/禁用「標籤視圖」的首選項優先於此預設值。 因此，如果用戶從Web編輯器啟用「標籤視圖」，則即使在會話中也仍啟用該視圖。

**父主題：**[&#x200B;自定義Web編輯器](conf-web-editor.md)

