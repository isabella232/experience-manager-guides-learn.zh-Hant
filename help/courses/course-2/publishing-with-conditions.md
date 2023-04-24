---
title: 使用條件發佈
description: 使用Adobe Experience Manager指南發佈條件
exl-id: ea94824a-884b-447f-9562-e6c629b8133b
source-git-commit: 67ba514616a0bf4449aeda035161d1caae0c3f50
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 1%

---

# 使用條件發佈

條件式發佈可讓您為一或多個對象、產品或平台編寫一個內容來源。 然後，即可動態發佈此資訊，且僅限輸出中包含特定必要內容。

>[!VIDEO](https://video.tv.adobe.com/v/339041?quality=12&learn=on)

## 為練習做準備

您可以在此處下載練習的範例檔案。

[練習 — 下載](assets/exercises/publishing-with-conditions.zip)

## 使用條件屬性來標籤內容

1. 開啟要修改的主題。

1. 輸入要成為條件的文本。 例如，一個或多個段落、整個表、圖或其他內容。

   ![演示資訊](images/presenting-info.png)

1. 選取要指派條件屬性的特定內容。 例如，源中的單個段落。

   ![範本選擇](images/template-choice.png)

1. 在右側邊欄中，確定顯示「屬性」。

1. 為對象、產品或平台新增屬性。

1. 為屬性指派值。 已套用顯示條件標籤的內容顯示更新。

   ![指定模板](images/specify-template.png)

## 預覽條件式內容

1. 按一下 **預覽**.

1. 在 **篩選器**，選取或取消選取要顯示或隱藏的條件。

1. 選擇或取消選擇 **反白標示條件文字**.

   ![預覽 — 條件 — 內容](images/preview-conditional-content.png)

## 建立條件預設集

條件預設集是屬性集合，定義在產生輸出期間要包括或排除或以其他方式標籤的內容。

1. 從「對應控制面板」中選取 **條件預設集** 標籤。

1. 按一下&#x200B;**建立**。

1. 選擇 **新增** (或 **全部新增**)。

1. 為條件命名。

1. 選取屬性、標籤和動作組合。

   ![Create-Condition-Preset](images/create-condition-preset.png)

1. 視需要重複。

1. 按一下「**儲存**」。

## 生成條件輸出

條件套用至內容後，即可產生為輸出。 這可以使用條件預設集或DITAval檔案。

## 使用條件預設集產生條件式輸出

1. 選取 **輸出預設集** 標籤。

1. 選取輸出預設集。

1. 按一下 **編輯**.

1. 在 **使用套用條件** 選取條件預設集。

   ![Generate-Conditional-Output](images/generate-conditional-output.png)

1. 按一下 **完成**.

1. 產生輸出預設集並檢閱內容。

## 使用DITAval檔案產生條件式輸出

DITAval檔案可用來發佈條件式內容。 這需要建立或上傳檔案，然後在發佈時參考。

1. 選取 **輸出預設集** 標籤。

1. 選取輸出預設集。

1. 按一下 **編輯**.

1. 在使用選擇DITAval檔案的應用條件下。

   ![Generate-Using-DITAval](images/generate-using-ditaval.png)

1. 按一下 **完成**.

1. 產生輸出預設集並檢閱內容。
