---
title: 安裝文章式發佈的套件
description: 瞭解如何安裝文章式發佈的套件
source-git-commit: 6051181e243cf71919901093c1b5590f21832545
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---


# 安裝文章式發佈的套件 {#id21BNL02052Z}

AEM Guides提供與網頁編輯器整合的強大文章式發佈功能。 使用此功能，您可以同時發佈一個或多個主題。 在地圖編輯器中開啟地圖後，您可以導覽至「輸出」標籤以建立預設集，然後選擇一個或多個主題以產生輸出。 您可以使用以文章為基礎的發佈功能，以遞增方式產生一或多個主題的輸出，或以逐篇文章的方式將您的內容發佈到知識庫平台。 如需詳細資訊，請參閱 *從網頁編輯器區段以文章為基礎的發佈* 使用手冊中的。

若要建立AEM網站以發佈文章型輸出，請執行下列步驟：

1. 下載 **適用於Cloud Service的XML Documentation元件內容套件** 從您的 [Adobe軟體發佈入口網站](https://experience.adobe.com/#/downloads/content/software-distribution/en/general.html).
1. 開啟AEM Package Manager。 存取封裝管理器的預設URL為： `https://<hostname>/crx/packmgr/index.jsp`
1. 上傳XML Documentation元件內容套件以供Cloud Service，然後進行安裝。
1. 下載 `Knowledge-base-template-for-article-based-publishing-for-cloud-service.zip` 來自您的的檔案 [Adobe軟體發佈入口網站](https://experience.adobe.com/#/downloads/content/software-distribution/en/general.html).
1. 在全域導覽中選取 **網站**.
1. 在網站UI中，按一下 **建立** 按鈕。
1. 選取 **從範本建立網站** 從 **建立** 下拉式清單。
1. 按一下 **匯入** 按鈕，然後選取 `Knowledge-base-template-for-article-based-publishing-for-cloud-service.zip` 已在您的系統上下載。 網站範本匯入後，會列在底部。

   >[!NOTE]
   >
   > 您只需要第一次匯入ZIP檔案。 匯入後，網站範本即可在清單中使用。

   選取 **文章式發佈的知識庫範本** 建立AEM網站並按一下 **下一個** 右上角。

1. 輸入 **網站標題** 和 **網站名稱** 並按一下 **建立** 右上角。 AEM網站是使用Tragopan網站範本建立的。 \(Tragopan網站是範例知識庫AEM網站，其中包含類別、區段和文章頁面的範本。\)

   >[!NOTE]
   >
   > 您可以使用相同的範本建立多個AEM網站。


您可以使用AEM網站，透過網頁編輯器的輸出預設集發佈文章。

**父級主題：**[&#x200B;自訂Web編輯器](conf-web-editor.md)

