---
title: 使用發佈儀表板管理發布任務
description: 瞭解如何使用發佈儀表板管理發布任務
exl-id: 5ede608d-f905-44b7-9147-ab678ad68ee7
source-git-commit: c74badebbcb4733fb9caa79c646b1d1e5c8bfe8e
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 0%

---

# 使用發佈儀表板管理發布任務 {#id205CC08305Z}

當您的系統上執行大量發佈任務時，實際上不可能單獨檢查每個DITA map以監視其發佈任務。 AEM Guides可讓管理員和發佈者統一檢視系統中執行的所有發佈任務。 「發佈控制面板」中提供所有作用中發佈任務的清單。

「發佈儀表板」提供目前系統中執行的所有發佈任務的完整概觀。

![](images/publish-dashboard.png){width="800" align="left"}

發佈儀表板包含下列詳細資訊：

- **地圖示題**  — 目前正在發佈或位於發佈佇列中的對應檔標題。

- **檔案名稱** - DITA map的檔案名稱。

- **輸出預設集**  — 用來產生輸出的輸出預設集名稱。

- **啟動者**  — 起始發佈工作之使用者的使用者名稱。

- **開始日期**  — 開始發佈工作的日期和時間。

- **經過的時間**  — 從發佈任務在系統中執行以來的時間。

- **「刪除」圖示**  — 取消或終止發佈任務。

發佈控制面板中的左側面板提供下列篩選選項：

- **輸出預設集**  — 選取一或多個您想要檢視目前作用中發佈任務的輸出預設集。 在下列熒幕擷圖中，會對發佈工作進行篩選，以僅顯示使用AEM Site輸出預設集的工作：

   ![](images/publish-dashboard-preset-filter.png){width="800" align="left"}

- **啟動者**  — 從清單中選取使用者名稱，以顯示所選使用者起始的發佈任務。

- **地圖**  — 從清單中選取對應檔案，以顯示針對所選對應執行的發佈工作。

## 存取發佈控制面板 {#id205CC100DY4}

執行以下步驟以存取「發佈控制面板」：

>[!NOTE]
>
> 只有管理員或發佈者可以存取發佈儀表板。

1. 按一下頂端的Adobe Experience Manager連結，然後選擇 **工具**.

1. 選取&#x200B;**指南** 工具清單中的。

1. 按一下 **發佈控制面板** 圖磚。

   「發佈儀表板」隨即開啟，其中包含系統中所有作用中發佈任務的清單。

   如果按一下「檔案名稱」連結，則會顯示所選地圖的DITA map主控台。

   ![](images/publish-dashboard-click-filename-link.png){width="800" align="left"}


>[!NOTE]
>
> 您也可以在從地圖儀表板產生輸出時，從「輸出」標籤存取「發佈儀表板」。 如需詳細資訊，請參閱 [檢視輸出產生任務的狀態](generate-output-for-a-dita-map.md#viewing_output_history).

## 取消發佈任務

執行以下步驟，從「發佈控制面板」取消輸出產生工作：

1. [存取發佈控制面板](#id205CC100DY4).

1. 從作用中發佈任務清單中，按一下您要取消之任務的刪除圖示。

   ![](images/publish-dashboard-cancel-task.png){width="800" align="left"}

1. 按一下 **是** 在Confirm Cancellation訊息提示上。

   只要工作保持作用中，就會接受取消指令，並嘗試取消。 工作一旦成功終止，就會從目前作用中的工作清單中移除。 任務狀態也會在DITA map主控台中更新為「已取消」。 在下列熒幕擷圖中， *HTML5* 從「發佈儀表板」取消任務，其狀態也會在DITA map主控台中變更。

   ![](images/cancelled-output-task.png){width="800" align="left"}


**父級主題：**[&#x200B;輸出產生](generate-output.md)
