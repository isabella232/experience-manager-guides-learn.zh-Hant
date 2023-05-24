---
title: 使用基準線建立與發佈
description: 使用基準線在中建立和發佈 [!DNL Adobe Experience Manager Guides]
exl-id: 3c229c30-f2e0-4fb0-b60c-7bae60ef1a5b
source-git-commit: 67ba514616a0bf4449aeda035161d1caae0c3f50
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 1%

---

# 使用基準線建立與發佈

使用基準線可讓您建立地圖主題和相關參考內容的版本。 這可以根據特定日期或時間或標籤。

>[!VIDEO](https://video.tv.adobe.com/v/338993?quality=12&learn=on)

## 存取地圖控制面板中的「基準線」標籤

您可以在「地圖控制面板」中存取您的基準線。

1. 存放庫檢視，選取地圖上的省略符號圖示以開啟「選項」功能表，然後 **開啟地圖控制面板。**

   ![省略符號 — map-dashboard.png](images/ellipsis-map-dashboard.png)
「對映圖示板」會在另一個標籤中開啟。

1. 選取 **基準線**.

   ![baseline-tab.png](images/baseline-tab.png)

「基準線」標籤隨即顯示。

## 根據標籤建立基準線

1. 在「基準線」標籤中，選取 **建立**.

   ![create-baseline.png](images/create-baseline.png)

   新基準線的資訊隨即顯示。 其預設名稱以其建立日期為基礎。

1. 視需要為基準線指定新名稱。

1. 在「設定版本依據」標題下，選取「標籤」的圓形。
   ![set-the-version.png](images/set-the-version.png)

   >[!NOTE]
   >
   >注意： *如果標籤不存在，則使用最新版本* 預設會選取核取方塊。 如果未選取此專案，且地圖中存在沒有所選標籤的主題或媒體檔案，基準線建立程式將會失敗。

1. 輸入您要使用的標籤。

1. 選取&#x200B;**儲存**。

您的基準線已建立。 所有主題及其相關資訊的表格隨即顯示。

### 使用瀏覽所有主題功能

「瀏覽所有主題」功能可讓您檢視主題資訊，包括版本和標籤，以及指定使用的版本。 您可以選取「 」 **瀏覽所有主題** 建立或編輯基準線時。

![browse-all-topics.png](images/browse-all-topics.png)

## 根據日期和時間建立基準線

您也可以建立即時快照的基準線。

1. 確定已開啟「基準線」標籤，然後選取「建立」。

   ![create-baseline.png](images/create-baseline.png)

1. 在「設定版本依據」標題下，選取「版本開啟」的圓形。

   ![version-on.png](images/version-on.png)

1. 選取行事曆圖示並指定您想要的日期和時間。

   ![calendar.png](images/calendar.png)

1. 視需要為基準線指定新名稱。

1. 選取&#x200B;**儲存**。

您的基準線已建立。 所有主題及其相關資訊的表格隨即顯示。

### 新增標籤至您的基準線

您可能想要大量指派新標籤給所有地圖內容。

1. 選取您要新增標籤的基準線。

1. 選取 **新增標籤**.

   ![add-labels.png](images/add-labels.png)

   「新增標籤」對話方塊隨即顯示。

1. 輸入您要指派的標籤，然後選取 **新增**.

標籤已新增至所有主題。

## 使用基準線產生AEM Site輸出

1. 導覽至「地圖」控制面板中的「輸出預設集」標籤。

1. 選取「AEM網站」核取方塊。

   ![aem-site-checkbox.png](images/aem-site-checkbox.png)

1. 選取&#x200B;**編輯**。

   ![edit-aem.png](images/edit-aem.png)

   新頁面隨即顯示。

1. 選取「使用基準線」核取方塊，然後從下拉式選單中選擇您要使用的基準線。

   ![baseline.png](images/baseline.png)

1. 選取 **完成**.

   ![done.png](images/done.png)

1. 選取 **產生**.

   ![generate.png](images/generate.png)

   您的輸出已使用基準線產生。

## 檢視產生的輸出

1. 導覽至「地圖」控制面板中的「輸出」標籤。

1. 選取「層代設定」欄中的文字以開啟輸出。
   ![aem-site-link.png](images/aem-site-link.png)

## 移除基準線

1. 在「基準線」標籤中，選取您要移除的基準線。

1. 選取 **移除**.

   ![remove-baseline.png](images/remove-baseline.png)

   「移除基準線」對話方塊隨即顯示。

1. 選取 **移除**.

會移除基準線。

## 複製基準線

1. 在「基準線」標籤中，選取您要複製的基準線。

1. 選取 **複製**.

   ![duplicate.png](images/duplicate.png)

1. 選取&#x200B;**儲存**。

   ![save.png](images/save.png)

會建立重複的基準線。

## 修改基準線

您可以直接指定基準線中使用的主題版本。

1. 在「基準線」頁簽中，選取要修改的基準線。
1. 選取&#x200B;**編輯**。

   ![edit-aem.png](images/edit-aem.png)

1. 選取 **瀏覽所有主題**.

   ![browse-all-topics.png](images/browse-all-topics.png)

   主題及其相關資訊的表格隨即顯示。

1. 對於您要修改的主題，請從「版本」欄下的下拉式清單中選取所需的版本。

   ![version-dropdown.png](images/version-dropdown.png)

1. 選取&#x200B;**儲存**。

已儲存您的變更。 您的基準線現在將使用您指定的主題版本。

## 建立自訂的AEM Site輸出預設集

在「輸出」標籤中很難區分相同型別的預設輸出。 使用具有唯一好記名稱的自訂輸出預設集，可讓您解決此問題。

在此情況下，我們會根據基線建立輸出預設集。

1. 導覽至「地圖」控制面板中的「輸出預設集」標籤。

1. 選擇 **建立**。

   ![create-output-preset.png](images/create-output-preset.png)

   隨即顯示新的輸出預設集頁面，稱為「新輸出」。
1. 在「設定名稱」欄位中，輸入好記的名稱。

1. 選取「使用基準線」核取方塊，然後從下拉式選單中選取所需的基準線。

   ![baseline.png](images/baseline.png)

1. 選取 **完成**.

已建立您的新輸出預設集，並顯示在輸出預設集頁面上。
