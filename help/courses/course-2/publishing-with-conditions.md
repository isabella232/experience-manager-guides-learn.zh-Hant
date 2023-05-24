---
title: 使用條件發佈
description: 使用Adobe Experience Manager Guides發佈附帶條件
exl-id: ea94824a-884b-447f-9562-e6c629b8133b
source-git-commit: 67ba514616a0bf4449aeda035161d1caae0c3f50
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 1%

---

# 使用條件發佈

條件式發佈可讓您為一個或多個對象、產品或平台撰寫一個內容來源。 然後，這些資訊可以動態發佈，並且只會在輸出中包含特別需要的內容。

>[!VIDEO](https://video.tv.adobe.com/v/339041?quality=12&learn=on)

## 準備練習

您可以在此處下載練習的範例檔案。

[練習 — 下載](assets/exercises/publishing-with-conditions.zip)

## 使用條件屬性標示內容

1. 開啟要修改的主題。

1. 輸入要成為條件式內容的文字。 例如，一個或多個段落、整個表格、插圖或其他內容。

   ![簡報資訊](images/presenting-info.png)

1. 選取要指派條件屬性的特定內容。 例如，來源中的單一段落。

   ![Template-Choice](images/template-choice.png)

1. 在右側邊欄中，確定屬性已顯示。

1. 新增對象、產品或平台的屬性。

1. 為屬性指派值。 內容顯示更新以顯示已套用條件標籤。

   ![Specify-Template](images/specify-template.png)

## 預覽條件式內容

1. 按一下 **預覽**.

1. 下 **篩選器**，選取或取消選取要顯示或隱藏的條件。

1. 選取或取消選取 **反白顯示條件文字**.

   ![預覽 — Conditional-Content](images/preview-conditional-content.png)

## 建立條件預設集

條件預設集是屬性的集合，這些屬性定義在產生輸出期間要包含或排除的內容，或以其他方式標示的內容。

1. 從「地圖儀表板」中選取 **條件預設集** 標籤。

1. 按一下&#x200B;**建立**。

1. 選取 **新增** (或 **全部新增**)。

1. 為條件命名。

1. 選取屬性、標籤和動作組合。

   ![Create-Condition-Preset](images/create-condition-preset.png)

1. 視需要重複。

1. 按一下「**儲存**」。

## 正在產生條件式輸出

將條件套用至內容後，便可以將其產生為輸出。 這可以使用條件預設集或DITAval檔案。

## 使用條件預設集產生條件輸出

1. 選取 **輸出預設集** 標籤。

1. 選取輸出預設集。

1. 按一下 **編輯**.

1. 下 **套用條件，使用** 選取條件預設集。

   ![Generate-Conditional-Output](images/generate-conditional-output.png)

1. 按一下 **完成**.

1. 產生輸出預設集並檢閱內容。

## 使用DITAval檔案產生條件輸出

DITAval檔案可用於發佈條件式內容。 這需要建立或上傳檔案，然後在發佈時參考。

1. 選取 **輸出預設集** 標籤。

1. 選取輸出預設集。

1. 按一下 **編輯**.

1. 在套用條件使用下選取DITAval檔案。

   ![Generate-Using-DITAval](images/generate-using-ditaval.png)

1. 按一下 **完成**.

1. 產生輸出預設集並檢閱內容。
