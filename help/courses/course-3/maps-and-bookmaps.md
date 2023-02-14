---
title: 地圖和書籤地圖
description: 在AEM指南中建立和編輯地圖和書籤地圖
exl-id: 9c717e4b-017b-4f2b-b93e-f2c0e7525c55
source-git-commit: 1c4d278a05f2612bc55ce277efb5da2e6a0fa9a9
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 1%

---

# 地圖和書籤地圖

Adobe Experience Manager參考線的地圖編輯器可讓您建立和編輯地圖檔案。 使用映射編輯器，可以編輯兩種類型的檔案 — DITA映射和書籤映射。 就我們的目的而言，將這些概念視為基本上可互換的概念。
地圖編輯器提供兩種模式：基本地圖編輯器和進階地圖編輯器。

>[!VIDEO](https://video.tv.adobe.com/v/342766?quality=12&learn=on)

## 建立地圖

AEM參考線提供兩個現成可用的對應範本 — DITA對應和書籤對應。 您也可以建立自己的地圖範本，並與作者共用這些範本以建立地圖檔案。

執行下列步驟以建立映射檔案。

1. 在「資產」UI中，導覽至您要建立對應檔案的位置。

2. 按一下 [!UICONTROL **建立> DITA映射**].

3. 在「Blueprint」(Blueprint)頁面上，選擇要使用的映射模板類型，然後按一下 [!UICONTROL **下一個**].

4. 在「屬性」頁面上，輸入 **標題** 和 **名稱** 地圖。

5. 按一下&#x200B;[!UICONTROL **建立**]。

## 使用進階地圖編輯器開啟地圖

1. 在 **Assets UI**，請選取要編輯的對應。

2. 按一下 [!UICONTROL **編輯主題**].

   ![編輯主題UI](images/lesson-14/edit-topics.png)

或

1. 將滑鼠移到地圖圖示上。

2. 選擇 **編輯主題** 從 **動作** 功能表。


## 將內容新增至地圖或書籤地圖

1. 導覽至 **儲存庫視圖**.

2. 從「存放庫檢視」將內容拖放至對映或書籤中的有效位置。

或

1. 按一下地圖或書籤地圖內的有效位置。

2. 按一下適當的 [!UICONTROL **工具欄表徵圖**] 添加章節、主題或topicref。

   ![工具欄表徵圖](images/lesson-14/toolbar-icons.png)

3. 選擇一或多個要新增的資產。

4. 按一下 [!UICONTROL **選擇**].

### 升級或降級地圖中的元素

使用 **工具列箭頭** 在地圖或書籤地圖中提升或降級章節和topicref。

1. 在地圖中選取元素。

2. 按一下 [!UICONTROL **左箭頭**] 將topicref提升至章節，或 [!UICONTROL **向右鍵**] 將章節降級為主題。

   ![箭頭表徵圖](images/lesson-14/toolbar-arrows.png)

3. 視需要儲存並版本對應。

或

1. 拖放元素以重新組織元素。

## 將中繼資料新增至地圖

1. 從 **映射工具欄**，插入topicgroup。

   ![新增屬性](images/lesson-14/add-topicgroup.png)

2. 按一下 [!UICONTROL **加號表徵圖**] 來插入元素。

3. 選擇要插入的元素。

   ![插入中繼資料](images/lesson-14/insert-metadata.png)

4. 按一下&#x200B;[!UICONTROL **關閉**]。

## 向地圖添加可變表

在結構化地圖後，可以新增可變表。

1. 按一下要插入可變表的對應。

2. 使用 **工具欄表徵圖** 將表添加到映射。

   ![可重複圖示](images/lesson-14/reltable-icon.png)

3. 設定對話方塊。

4. 按一下 [!UICONTROL **插入**].

5. 從 **存放庫** 放入變數中。

6. 使用標準鍵盤快速鍵，將需要的元素從地圖複製並貼到可重複使用中。

## 將屬性指派給地圖中的topicref

1. 在地圖中反白顯示topicref或巢狀topicref集合。

2. 在「內容屬性」面板的「其他屬性」下，選擇 **屬性** 和 **值。**

   ![新增屬性](images/lesson-14/add-attribute.png)
