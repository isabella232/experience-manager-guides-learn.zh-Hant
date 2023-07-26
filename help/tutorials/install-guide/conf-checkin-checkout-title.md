---
title: 設定簽入和簽出圖示的標題
description: 瞭解如何設定簽入和簽出圖示的標題
source-git-commit: bb4b875864b31197437a944ded5862bbf937bc29
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%

---

# 設定簽入和簽出圖示的標題

AEM Guides可讓您在網頁編輯器中設定簽入和簽出圖示的標題。 執行以下步驟來設定「入庫」和「出庫」圖示的標題：

1. 以管理員身分登入Adobe Experience Manager以下載UI設定檔。
1. 按一下頂端的Adobe Experience Manager連結，然後選擇 **工具**.
1. 選取 **指南** 從工具清單中，按一下 **資料夾設定檔**.
1. 按一下 **全域設定檔** 圖磚。
1. 選取 **XML編輯器設定** 標籤並按一下 **編輯** 圖示在頂端。
1. 在 **XML編輯器UI設定** 區段，按一下 **下載** 圖示以下載 `ui_config.json` 檔案。
1. 在 `ui_config.json` 檔案中，變更「頂端列」區段中的標題。 您可以變更下列值：

   ```json
   //Change title to "Check out" instead of "Lock"
           "title": "Check out"
   
   //Change title to "Check in" instead of "@checkOutBy
            "title": "Check in"
   ```

1. 儲存檔案並上傳。

