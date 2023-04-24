---
title: 使用基線建立和發佈
description: 在中建立和發佈含基線 [!DNL Adobe Experience Manager Guides]
exl-id: 3c229c30-f2e0-4fb0-b60c-7bae60ef1a5b
source-git-commit: 67ba514616a0bf4449aeda035161d1caae0c3f50
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 1%

---

# 使用基線建立和發佈

使用基線可讓您建立地圖主題和相關參考內容的版本。 這可以根據特定日期、時間或標籤。

>[!VIDEO](https://video.tv.adobe.com/v/338993?quality=12&learn=on)

## 存取「對應」控制面板中的「基線」索引標籤

您可以在「對應控制面板」中存取基線。

1. 儲存庫檢視，選取地圖上的刪節號圖示，開啟選項選單，然後 **開啟「地圖控制面板」。**

   ![ellipsis-map-dashboard.png](images/ellipsis-map-dashboard.png)
「對應控制面板」會在另一個索引標籤中開啟。

1. 選擇 **基線**.

   ![baseline-tab.png](images/baseline-tab.png)

「基線」(Baselines)頁簽隨即顯示。

## 根據標籤建立基線

1. 在「基線」(Baselines)頁簽中，選擇 **建立**.

   ![create-baseline.png](images/create-baseline.png)

   新基線的資訊隨即顯示。 其預設名稱是根據其建立日期。

1. 視需要為基線指定新名稱。

1. 在「根據設定版本」標題下，為「標籤」選取社交圈。
   ![set-the-version.png](images/set-the-version.png)

   >[!NOTE]
   >
   >注意：此 *如果標籤不存在，請使用最新版本* 預設會選取核取方塊。 如果未選擇此選項，且映射中存在未選擇標籤的主題或媒體檔案，則基線建立過程將失敗。

1. 輸入您要使用的標籤。

1. 選取&#x200B;**儲存**。

已建立基線。 隨即顯示所有主題及其相關資訊的表格。

### 使用「瀏覽所有主題」功能

「瀏覽所有主題」功能允許您查看主題的資訊，包括版本和標籤，以及指定使用的版本。 您可以選取 **瀏覽所有主題** 建立或編輯基線時。

![browse-all-topics.png](images/browse-all-topics.png)

## 根據日期和時間建立基線

您也可以建立及時作為快照的基線。

1. 確保「基線」頁簽已開啟，然後選擇「建立」。

   ![create-baseline.png](images/create-baseline.png)

1. 在「根據設定版本」標題下，選取「版本於」的社交圈。

   ![version-on.png](images/version-on.png)

1. 選取日曆圖示並指定您想要的日期和時間。

   ![calendar.png](images/calendar.png)

1. 視需要為基線指定新名稱。

1. 選取&#x200B;**儲存**。

已建立基線。 隨即顯示所有主題及其相關資訊的表格。

### 將標籤新增至基線

您可能想要將新標籤大量指派給所有對應內容。

1. 選擇要添加標籤的基線。

1. 選擇 **新增標籤**.

   ![add-labels.png](images/add-labels.png)

   將顯示「添加標籤」對話框。

1. 輸入要分配的標籤，然後選擇 **新增**.

標籤已新增至所有主題。

## 使用基線產生AEM網站輸出

1. 導覽至「對應控制面板」中的「輸出預設集」標籤。

1. 選取「AEM Site」核取方塊。

   ![aem-site-checkbox.png](images/aem-site-checkbox.png)

1. 選取&#x200B;**編輯**。

   ![edit-aem.png](images/edit-aem.png)

   隨即顯示新頁面。

1. 選取「使用基線」核取方塊，然後從下拉式清單中選取您要使用的基線。

   ![baseline.png](images/baseline.png)

1. 選擇 **完成**.

   ![done.png](images/done.png)

1. 選擇 **產生**.

   ![generate.png](images/generate.png)

   已使用基線生成輸出。

## 查看生成的輸出

1. 導覽至「對應控制面板」中的「輸出」標籤。

1. 在層代設定列中選擇文本以開啟輸出。
   ![aem-site-link.png](images/aem-site-link.png)

## 移除基線

1. 在「基線」(Balesines)頁簽中，選擇要刪除的基線。

1. 選擇 **移除**.

   ![remove-baseline.png](images/remove-baseline.png)

   將顯示「刪除基線」(Remove Baseline)對話框。

1. 選擇 **移除**.

基線已移除。

## 複製基線

1. 在「基線」(Balesines)頁簽中，選擇要複製的基線。

1. 選擇 **複製**.

   ![duplicate.png](images/duplicate.png)

1. 選取&#x200B;**儲存**。

   ![save.png](images/save.png)

已建立重複的基線。

## 修改基線

您可以直接指定基線中使用的主題版本。

1. 在「基線」(Balesines)頁簽中，選擇要修改的基線。
1. 選取&#x200B;**編輯**。

   ![edit-aem.png](images/edit-aem.png)

1. 選擇 **瀏覽所有主題**.

   ![browse-all-topics.png](images/browse-all-topics.png)

   隨即顯示主題表及其相關資訊。

1. 對於您要修改的主題，從「版本」欄下的下拉式清單中選取所需的版本。

   ![version-dropdown.png](images/version-dropdown.png)

1. 選取&#x200B;**儲存**。

您的更改已保存。 您的基線現在將使用您指定的主題版本。

## 建立自訂的AEM Site輸出預設集

在「輸出」(Outputs)頁簽中很難區分相同類型的預設輸出。 使用具有唯一且好記名稱的自訂輸出預設集，即可解決此問題。

在此情況下，我們會根據基線建立輸出預設集。

1. 導覽至「對應控制面板」中的「輸出預設集」標籤。

1. 選擇 **建立**。

   ![create-output-preset.png](images/create-output-preset.png)

   隨即顯示名為New Output的新輸出預設頁。
1. 在「設定名稱」欄位中，輸入好記的名稱。

1. 選取「使用基線」核取方塊，然後從下拉式功能表中選取所需的基線。

   ![baseline.png](images/baseline.png)

1. 選擇 **完成**.

已建立新的輸出預設集，並顯示在輸出預設集頁面上。
