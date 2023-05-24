---
title: 地圖和書籤
description: 在AEM Guides中建立和編輯地圖和書籤
exl-id: 9c717e4b-017b-4f2b-b93e-f2c0e7525c55
source-git-commit: 67ba514616a0bf4449aeda035161d1caae0c3f50
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 1%

---

# 地圖和書籤

Adobe Experience Manager Guides的地圖編輯器可讓您建立和編輯地圖檔案。 使用「對映編輯器」，您可以編輯兩種型別的檔案 — DITA map和bookmap。 基於我們的目的，請將這些視為基本上可互換的概念。
地圖編輯器提供兩種模式 — 「基本地圖編輯器」和「進階地圖編輯器」。

>[!VIDEO](https://video.tv.adobe.com/v/342766?quality=12&learn=on)

## 建立地圖

AEM Guides提供兩種現成可用的地圖範本 — DITA map和bookmap。 您也可以建立自己的地圖範本，並與作者共用這些範本，以建立地圖檔案。

執行以下步驟來建立對應檔案。

1. 在Assets UI中，導覽至您要建立對應檔案的位置。

1. 按一下 [!UICONTROL **建立> DITA Map**].

1. 在Blueprint頁面上，選取您要使用的對應範本型別，然後按一下 [!UICONTROL **下一個**].

1. 在「屬性」頁面中，輸入 **標題** 和 **名稱** 以取得地圖。

1. 按一下&#x200B;[!UICONTROL **建立**]。

## 使用進階地圖編輯器開啟地圖

1. 在 **Assets UI**，選取要編輯的地圖。

1. 按一下 [!UICONTROL **編輯主題**].

   ![編輯主題UI](images/lesson-14/edit-topics.png)

或

1. 將滑鼠停留在地圖圖示上。

1. 選取 **編輯主題** 從 **動作** 功能表。


## 將內容新增至地圖或書籤

1. 導覽至 **存放庫檢視**.

1. 從「存放庫檢視」將內容拖放至地圖或書籤地圖中的有效位置。

或

1. 在地圖或書籤地圖內的有效位置按一下。

1. 按一下適當的 [!UICONTROL **工具列圖示**] 以新增章節、主題或主題參照。

   ![工具列圖示](images/lesson-14/toolbar-icons.png)

1. 選擇一或多個要新增的資產。

1. 按一下 [!UICONTROL **選取**].

### 升級或降級地圖中的元素

使用 **工具列箭頭** 提升或降階地圖或書籤地圖中的章節和主題參照。

1. 在地圖中選取元素。

1. 按一下 [!UICONTROL **向左鍵**] 將topicref提升至章節，或 [!UICONTROL **向右鍵**] 將章節降級為topicref。

   ![箭頭圖示](images/lesson-14/toolbar-arrows.png)

1. 視需要儲存地圖並進行版本設定。

或

1. 拖放元素以重新組織它們。

## 將中繼資料新增至地圖

1. 從 **地圖工具列**，插入主題群組。

   ![新增屬性](images/lesson-14/add-topicgroup.png)

1. 按一下 [!UICONTROL **加號圖示**] 以插入元素。

1. 選擇要插入的元素。

   ![插入中繼資料](images/lesson-14/insert-metadata.png)

1. 按一下&#x200B;[!UICONTROL **關閉**]。

## 將表格新增至地圖

可以在結構對應之後新增表格。

1. 在地圖中按一下要插入表格的位置。

1. 使用 **工具列圖示** 將表格新增至對映。

   ![關聯圖示](images/lesson-14/reltable-icon.png)

1. 設定對話方塊。

1. 按一下 [!UICONTROL **插入**].

1. 將必要的主題從 **存放庫** 放入關聯式中。

1. 使用標準鍵盤快速鍵，將地圖中的必要元素複製並貼到可發行元素中。

## 將屬性指派給地圖中的topicref

1. 在地圖中反白顯示topicref或巢狀topicref集合。

1. 在「內容屬性」面板的「其他屬性」下，選擇 **屬性** 及其 **值。**

   ![新增屬性](images/lesson-14/add-attribute.png)
