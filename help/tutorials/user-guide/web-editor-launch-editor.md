---
title: 啟動Web編輯器
description: 了解如何啟動網頁編輯器
source-git-commit: cc0fbca257d82cc82db5b5da8d263309fd71de55
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---


# 啟動Web編輯器 {#id2056B0140HS}

您可以從下列位置啟動Web編輯器：

- [AEM導覽頁面](#id2056BG00RZJ)
- [AEM Assets UI](#id2056BG0307U)
- [DITA映射控制台](#id2056BG090BF)

以下小節將介紹如何從各種位置訪問和啟動Web編輯器的詳細資訊。

## AEM導覽頁面 {#id2056BG00RZJ}

登入AEM時，會顯示「導覽」頁面：

![](images/web-editor-from-navigation-page_cs.png){width="800" align="left"}

按一下 **XML編輯器** 連結會直接將您導向網頁編輯器。

![](images/web-editor-launch-page.png){width="800" align="left"}

當您啟動Web編輯器而未選擇任何檔案時，將顯示一個空白Web編輯器螢幕。 您可以從AEM存放庫或您的我的最愛集合開啟檔案進行編輯。

## AEM Assets UI {#id2056BG0307U}

您可從其中啟動Web編輯器的另一個位置是AEM Assets UI。 您可以選取一或多個主題，並直接在網頁編輯器中開啟這些主題。 若要在網頁編輯器中開啟主題，請依照下列步驟操作：

1. 在「資產」UI中，導覽至您要編輯的主題。

   >[!NOTE]
   >
   > 您也可以看到主題的UUID。

   .

   ![](images/assets_ui_with_uuid_cs.png){width="800" align="left"}

   >[!IMPORTANT]
   >
   > 請確定您對包含您要編輯之主題的資料夾具有讀取和寫入權限。

1. 要獲取主題的獨佔鎖，請選擇主題，然後按一下 **結帳**.

   >[!IMPORTANT]
   >
   > 如果管理員已設定 **禁用編輯而不簽出** 選項，則必須先簽出檔案才能編輯。 如果您未結帳檔案，將看不到編輯選項。

1. 關閉資產選取模式，然後按一下您要編輯的主題。

   此時會顯示主題的預覽。

   您可以從「清單」視圖、「卡片」視圖和「預覽」模式開啟Web編輯器。

   >[!IMPORTANT]
   >
   > 如果您想要開啟多個主題以進行編輯，請從資產UI中選取所需的主題，然後按一下編輯。 請確定您的瀏覽器未啟用快顯封鎖程式，否則只會開啟所選清單中的第一個主題進行編輯。

   ![](images/edit-from-preview_cs.png){width="800" align="left"}

   如果您不想預覽主題，並想要直接在Web編輯器中開啟它，請從卡片檢視按一下快速動作功能表中的「編輯」圖示：

   ![](images/edit-topic-from-quick-action_cs.png){width="800" align="left"}

1. 按一下 **編輯** 以在網頁編輯器中開啟主題。

   ![](images/edit-mode.png){width="800" align="left"}


## DITA映射控制台 {#id2056BG090BF}

要從DITA映射控制台開啟Web編輯器，請執行以下步驟：

1. 在資產UI中，導覽至，然後按一下包含您要編輯之主題的DITA對應檔案。

   將顯示DITA映射控制台。

1. 按一下 **主題**.

   將顯示映射檔案中的主題清單。 主題的UUID顯示在主題標題下方。

1. 選擇要編輯的主題檔案。

1. 按一下 **編輯主題**.

   ![](images/edit-topics-map-console_cs.png){width="800" align="left"}

1. 主題在網頁編輯器中開啟。

   >[!IMPORTANT]
   >
   > 如果管理員已設定 **禁用編輯而不簽出** 選項，則必須先簽出檔案才能編輯。 如果未簽出檔案，則文檔將在編輯器中以只讀模式開啟。


**上層主題：**[&#x200B;使用Web編輯器](web-editor.md)

