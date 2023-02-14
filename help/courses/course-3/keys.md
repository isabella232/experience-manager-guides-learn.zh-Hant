---
title: 金鑰
description: 在AEM參考線中使用DITA時，索引鍵可讓您將變數資訊加入
exl-id: cb64e094-fe6d-4a5e-8f0e-25ae58aaa2c6
source-git-commit: 1c4d278a05f2612bc55ce277efb5da2e6a0fa9a9
workflow-type: tm+mt
source-wordcount: '585'
ht-degree: 0%

---

# 金鑰

不同的材料集可能包含需要在選定位置中定製的類似資訊。 使用索引鍵時，您可將變數資訊加入至。

檔案中提供您可選擇用於本課程的範例檔案 [keys.zip](assets/keys.zip).

>[!VIDEO](https://video.tv.adobe.com/v/342756?quality=12&learn=on)

## 啟用金鑰

1. 上傳提供的範例檔案集。

   a.載入zip檔案。

   b.重新整理AEM環境。

   c.選擇要提取的檔案。

   ![選擇郵遞區號](images/lesson-9/select-zip.png)

   d.按一下 [!UICONTROL **解壓縮封存**] 的下一頁。

   ![工具列](images/lesson-9/extract-archive.png)

   e.在對話方塊中，選擇要提取的檔案的特定位置，如名為「鍵」的資料夾。

   f.按一下 [!UICONTROL **下一個**].

   g.跳過任何衝突，因為以前從未上傳過的內容不存在這些衝突。

   h.選擇 [!UICONTROL **Extract**] 在畫面右上角。

2. 提取完成時，按一下 [!UICONTROL **前往目標資料夾**].

   ![確認](images/lesson-9/go-to-target.png)

## 將索引鍵解析為參考值

若要正確使用索引鍵，使用者偏好設定必須參考特定地圖作為根地圖。 此地圖內是索引鍵的集合，在topicgroup內分組。 開啟地圖和主題會解析此地圖所參考值的索引鍵。

1. 指定根映射。

   a.從「鍵」螢幕開啟地圖。

   b.配置用戶首選項。

   c.按一下 [!UICONTROL **使用者偏好設定**] 圖示。

   ![頂端工具列](images/lesson-9/author-view.png)

   d.按一下金鑰圖示以指定 **根圖** 將用於解析密鑰。

   e.選取任何所需資產的核取方塊。

   ![資產下拉式清單](images/lesson-9/select-assets.png)

   f.按一下 [!UICONTROL **選擇**].

   g. **儲存** 用戶首選項。

2. 導覽至 **地圖檢視**.

3. 開啟指定的映射。

密鑰已解析。

## 手動添加新的鍵定義

1. 開啟具有指定根映射的映射。

2. 選取金鑰。

   ![索引鍵下拉式清單](images/lesson-9/hybrid-key.png)

3. 插入新鍵定義。

   a.按一下對應中有效位置的。

   b.選取 **Keydef** 圖示。

   ![Keydef工具欄](images/lesson-9/key-icon.png)

   c.在「插入鍵定義」對話框中，為鍵輸入唯一值，該值對於您正在建立的定義有意義。

   d.按一下 [!UICONTROL **插入**].

4. 在keydef中新增topicmeta。

   a.按一下 [!UICONTROL **插入元素**] 圖示。

   ![Keydef工具欄](images/lesson-9/add-icon.png)

   b.在「插入元素」對話方塊中，搜尋並選取「topicmeta」。

5. 在topicmeta中新增關鍵字。

   a.按一下 [!UICONTROL **插入元素**] 圖示。

   ![Keydef工具欄](images/lesson-9/add-icon.png)

   b.在「插入元素」對話方塊中，搜尋並選取「關鍵字」。

6. 在topicmeta中新增關鍵字。

   a.按一下 [!UICONTROL **插入元素**] 圖示。

   ![Keydef工具欄](images/lesson-9/add-icon.png)

   b.在 **插入元素** 對話框，搜索並選擇「關鍵字」

7. 在關鍵字中鍵入keydef的值。

在地圖中，您的keydef現在看起來應該像這樣：

![Keydef已完成](images/lesson-9/keydef.png)

## 將keydef配置為代碼段

程式碼片段是小型內容片段，可在檔案專案的各種主題中重複使用。 您可以將單一鍵定義設定為程式碼片段，而不需手動產生每個鍵定義。

1. 在映射中選擇鍵定義元素。

2. 在內容功能表中，按一下 [!UICONTROL **建立程式碼片段**].

3. 在「新增程式碼片段」對話方塊中，新增標題和說明。
您也可以從「內容」中移除現有的索引鍵或關鍵字定義。

4. 按一下&#x200B;[!UICONTROL **建立**]。

5. 在左側面板上，選取 **程式碼片段**.

6. 將您剛從「片段」面板建立的程式碼片段拖放至對應。

7. 視需要使用「內容屬性」更新keydef。
儲存並重新整理後，任何已定義包含相同根地圖之地圖的使用者，都能使用這組索引鍵。
