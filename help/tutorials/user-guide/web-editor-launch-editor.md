---
title: 啟動Web編輯器
description: 瞭解如何啟動Web編輯器
exl-id: f02f9612-7aaa-42ea-bad3-c44d23b5d034
source-git-commit: 8073716bccacbe8d6a158b44d5106b083e3a5dcd
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---

# 啟動Web編輯器 {#id2056B0140HS}

可以從以下位置啟動Web編輯器：

- [導AEM航頁](#id2056BG00RZJ)
- [AEM AssetsUI](#id2056BG0307U)
- [DITA映射控制台](#id2056BG090BF)

以下各節介紹如何從不同位置訪問和啟動Web編輯器的詳細資訊。

## 導AEM航頁 {#id2056BG00RZJ}

登錄時，AEM將顯示「導航」頁：

![](images/web-editor-from-navigation-page_cs.png){width="800" align="left"}

按一下 **XML編輯器** 連結將您直接轉到Web編輯器。

![](images/web-editor-launch-page.png){width="800" align="left"}

當您啟動Web編輯器而未選擇任何檔案時，將顯示空白的Web編輯器螢幕。 可以從儲存庫或收藏夾集AEM合中開啟要編輯的檔案。

## AEM AssetsUI {#id2056BG0307U}

可以從中啟動Web編輯器的另一個位置是AEM AssetsUI。 您可以選擇一個或多個主題，並直接在Web編輯器中開啟它們。 要在Web編輯器中開啟主題，請執行以下步驟：

1. 在資產UI中，導航到要編輯的主題。

   >[!NOTE]
   >
   > 您還可以看到主題的UUID。

   .

   ![](images/assets_ui_with_uuid_cs.png){width="800" align="left"}

   >[!IMPORTANT]
   >
   > 確保您對包含要編輯的主題的資料夾具有讀寫權限。

1. 要獲取主題的獨佔鎖定，請選擇該主題並按一下 **簽出**。

   >[!IMPORTANT]
   >
   > 如果管理員已配置 **禁用「編輯而不簽出」** 選項，則編輯前必須簽出檔案。 如果不簽出檔案，則將看不到編輯選項。

1. 關閉資產選擇模式，然後按一下要編輯的主題。

   將顯示主題的預覽。

   可以從「清單」視圖、「卡」視圖和「預覽」模式開啟Web編輯器。

   >[!IMPORTANT]
   >
   > 如果要開啟多個主題進行編輯，請從資產UI中選擇所需主題，然後按一下編輯。 確保您的瀏覽器未啟用彈出窗口阻止程式，否則只開啟選定清單中的第一個主題進行編輯。

   ![](images/edit-from-preview_cs.png){width="800" align="left"}

   如果不想預覽主題並想在Web編輯器中直接將其開啟，則按一下卡視圖中快速操作菜單中的「編輯」表徵圖：

   ![](images/edit-topic-from-quick-action_cs.png){width="800" align="left"}

1. 按一下 **編輯** 開啟Web編輯器中的主題。

   ![](images/edit-mode.png){width="800" align="left"}


## DITA映射控制台 {#id2056BG090BF}

要從DITA映射控制台開啟Web編輯器，請執行以下步驟：

1. 在資產UI中，導航到包含要編輯的主題的DITA映射檔案並按一下該檔案。

   將顯示DITA映射控制台。

1. 按一下 **主題**。

   將顯示映射檔案中的主題清單。 主題的UUID顯示在主題標題下。

1. 選擇要編輯的主題檔案。

1. 按一下 **編輯主題**。

   ![](images/edit-topics-map-console_cs.png){width="800" align="left"}

1. 主題在Web編輯器中開啟。

   >[!IMPORTANT]
   >
   > 如果管理員已配置 **禁用「編輯而不簽出」** 選項，則編輯前必須簽出檔案。 如果不簽出檔案，則文檔將以只讀模式在編輯器中開啟。


**父主題：**[&#x200B;使用Web編輯器](web-editor.md)
