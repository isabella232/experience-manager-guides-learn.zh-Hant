---
title: 交叉引用和連結
description: 在AEM Guides中建立互動參照和連結
exl-id: bee7d50f-cbdd-4ac8-b15b-101febc4ae80
source-git-commit: 67ba514616a0bf4449aeda035161d1caae0c3f50
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---

# 交叉引用和連結

XML編輯器和DITA提供在主題之間連結的強大方式。 請務必有效管理您的內容參照，包括使用唯一ID值。

檔案中提供您可選擇用於本課程的範例檔案
[crossreferencesandlinks.zip](assets/crossreferencesandlinks.zip)

>[!VIDEO](https://video.tv.adobe.com/v/342764?quality=12&learn=on)

## 建立外部主題的互動參照

將主題從存放庫拖放至開啟的檔案中，可以建立外部互動參照。 不過，為了避免破壞的互動參照，必須先將ID定義為與父元素相關的值。 這是建立互動參照的一種簡單方法，同時確保ID已正確指派。

1. 開啟要插入外部互動參照的檔案。

1. 為要參考的元素指派ID。

   a.按一下元素內部。

   b.在「內容屬性」面板上，選擇 **ID** 從「屬性」下拉式清單。

   c.在「值」欄位中輸入邏輯名稱。

   d.在中檢視元素及其值 **大綱檢視** 視需要而定。

1. **儲存** 確儲存放庫有更新ID的主題。

1. 按一下 [!UICONTROL **參考資料**] 圖示加以檢視。

   ![工具列](images/lesson-7/references-icon.png)

1. 從 **內容參考** 標籤中，選取要插入作為互動參照的ID和元素配對。

1. 按一下 [!UICONTROL **選取**].

交叉參照已新增至主題。

## 連結至網站

您可以在任何主題中插入網站的連結。 如需詳細資訊，請參閱連結至網站的AEM Guides課程1影片。


## 檢視中斷的連結

某些修改可能會導致交叉參照失效。 其中包括刪除主題、重新組織包含互動參照的截面，或在插入互動參照後變更ID。 請注意，範例主題 _crossreferencesandlinks.zip_ 本課程隨附，將導致內部內容的多個專案符號互動參照中斷。

1. 導覽至 **大綱檢視** 在左側面板。

1. 按一下 [!UICONTROL **篩選**] 圖示。

1. 選取 **中斷的連結**.

   ![篩選下拉式清單](images/lesson-7/broken-links.png)

中斷的連結會顯示為可點按的物件。 您可以在主題中以紅色文字來識別它們。
