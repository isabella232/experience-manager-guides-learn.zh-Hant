---
title: 金鑰
description: 在AEM Guides中使用DITA時，索引鍵可讓您加入變數資訊
exl-id: cb64e094-fe6d-4a5e-8f0e-25ae58aaa2c6
source-git-commit: 67ba514616a0bf4449aeda035161d1caae0c3f50
workflow-type: tm+mt
source-wordcount: '585'
ht-degree: 0%

---

# 金鑰

不同的材料集可能包含類似的資訊，需要在選取的位置自訂。 鍵可讓您在使用DITA時包含變數資訊。

檔案中提供您可選擇用於本課程的範例檔案 [keys.zip](assets/keys.zip).

>[!VIDEO](https://video.tv.adobe.com/v/342756?quality=12&learn=on)

## 啟用金鑰

1. 上傳提供的範例檔案集。

   a.載入zip檔案。

   b.重新整理AEM環境。

   c.選取要擷取的檔案。

   ![選取Zip](images/lesson-9/select-zip.png)

   d.按一下 [!UICONTROL **擷取封存**] 在頂端工具列上。

   ![工具列](images/lesson-9/extract-archive.png)

   e.在對話方塊中，選擇要擷取檔案的特定位置，例如名為「金鑰」的資料夾。

   f.按一下 [!UICONTROL **下一個**].

   g.略過任何衝突，因為它們對於以前從未上傳過的內容不存在。

   h.選取 [!UICONTROL **Extract**] 在熒幕右上方。

1. 擷取完成後，按一下 [!UICONTROL **前往目標資料夾**].

   ![確認](images/lesson-9/go-to-target.png)

## 將索引鍵解析為參照的值

若要正確使用索引鍵，「使用者偏好設定」必須參照特定對應作為「根對應」。 此地圖內部是索引鍵集合，分組在主題群組內。 開啟地圖和主題會將鍵解析為此地圖參照的值。

1. 指定根對應。

   a.在「按鍵」畫面中，開啟地圖。

   b.設定使用者偏好設定。

   c.按一下 [!UICONTROL **使用者偏好設定**] 圖示加以檢視。

   ![頂端工具列](images/lesson-9/author-view.png)

   d.按一下鍵圖示以指定 **根對應** 將用於解析金鑰。

   e.選取任何所需資產的核取方塊。

   ![資產下拉式清單](images/lesson-9/select-assets.png)

   f.按一下 [!UICONTROL **選取**].

   g. **儲存** 使用者偏好設定。

1. 導覽至 **地圖檢視**.

1. 開啟指定的對應。

鍵值已解析。

## 手動新增索引鍵

1. 開啟具有指定根對映的對映。

1. 選取金鑰。

   ![索引鍵下拉式清單](images/lesson-9/hybrid-key.png)

1. 插入新的索引鍵。

   a.在地圖中的有效位置按一下。

   b.選取 **Keydef** 圖示加以檢視。

   ![按鍵工具列](images/lesson-9/key-icon.png)

   c.在「插入Keydef」對話方塊中，輸入唯一的「金鑰」值，該值符合您正在建立的定義。

   d.按一下 [!UICONTROL **插入**].

1. 在keydef中新增topicmeta。

   a.按一下 [!UICONTROL **插入元素**] 圖示加以檢視。

   ![按鍵工具列](images/lesson-9/add-icon.png)

   b.在「插入元素」對話方塊中，搜尋並選取「topicmeta」。

1. 在topicmeta中新增關鍵字。

   a.按一下 [!UICONTROL **插入元素**] 圖示加以檢視。

   ![按鍵工具列](images/lesson-9/add-icon.png)

   b.在「插入元素」對話方塊中，搜尋並選取「關鍵字」。

1. 在topicmeta中新增關鍵字。

   a.按一下 [!UICONTROL **插入元素**] 圖示加以檢視。

   ![按鍵工具列](images/lesson-9/add-icon.png)

   b.在 **插入元素** 對話方塊，搜尋並選取「關鍵字」

1. 在關鍵字中輸入keydef的值。

在地圖中，您的keydef現在看起來應該像這樣：

![Keydef已完成](images/lesson-9/keydef.png)

## 將keydef設定為程式碼片段

片段是小型內容片段，可在說明檔案專案的各種主題中重複使用。 您可以將單一金鑰定義設定為程式碼片段，而不需手動產生每個金鑰定義。

1. 在地圖中選取keydef元素。

1. 在內容功能表中，按一下 [!UICONTROL **建立代碼片段**].

1. 在新程式碼片段對話方塊中，新增標題和說明。
您也可以從內容中移除現有的索引鍵或關鍵字定義。

1. 按一下&#x200B;[!UICONTROL **建立**]。

1. 在左側面板上，選取 **代碼片段**.

1. 從「代碼片段」面板將您剛建立的代碼片段拖放至對映。

1. 視需要使用「內容屬性」更新Keydef。
儲存並重新整理後，此組金鑰將可供已定義包含相同根對映之對映的任何使用者使用。
