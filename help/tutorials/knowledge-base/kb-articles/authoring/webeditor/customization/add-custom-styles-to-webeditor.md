---
title: 新增自訂樣式至「參考線」編輯器
description: 瞭解如何新增自訂樣式以變更Guides編輯器的外觀。
exl-id: 3a9dd701-9d9d-4d7f-bc0c-855904404fd1
source-git-commit: ed3adf0cf8006c76461de34c6a2a4ba38d8b3406
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# 新增自訂樣式至「參考線」編輯器

在本文中，我們將瞭解如何新增自訂樣式以變更webeditor預設外觀。

這將涉及以下步驟：
- 透過資料夾設定檔XML編輯器設定新增自訂樣式
- 在Webeditor中選擇個別資料夾設定檔並測試變更


## 以範例來實作

以一個範例來瞭解此內容，我們想要將簡短說明和標題顯示為單獨的區塊，並在編輯器中加入一些樣式方面。

![使用自訂樣式預覽Webeditor](../../../assets/authoring/webeditor-customstyles-preview.png)


## 實作此專案


### 將自訂CSS新增至資料夾設定檔

使用資料夾設定檔來檢查 *css_layout.css* 在「XML編輯器設定」標籤下方，並新增具有自訂樣式的CSS

[使用此連結來進一步瞭解資料夾設定檔和設定CSS範本版面](https://experienceleague.adobe.com/docs/experience-manager-guides-learn/videos/advanced-user-guide/editor-configuration.html?lang=en#customize-the-css-template-layout)

使用下列專案在網路編輯器中設定上述樣式：
- 使用 [css_layout.css](../../../assets/authoring/webeditor-customstyles-css_layout.css) 並將其上傳至您選擇的資料夾設定檔
- 安裝附加的套件 [webeditor-styles-resources.zip](../../../assets/authoring/webeditor-styles-resources.zip) 使用AEM套件管理器安裝上述CSS檔案中使用的資源

```
This will install the resources at path "/content/dam/resources" which will include sub-folders "fonts" and "images"
```


### 測試

- 開啟Web編輯器
- 從使用者偏好設定中選擇您新增自訂樣式的資料夾設定檔。 如果您將其新增至全域設定檔，表示您可能已經在使用它。
- 開啟主題時，您會注意到編輯區域應具有自訂UI

```
Please note this is compatible to AEM Guides version 4.2 and AEM Guides cloud version 2303 (March)
```


## 引用

您可能也會對Webeditor設定和自訂中的專家座談會感興趣 [Webeditor專家講座](https://experienceleague.adobe.com/docs/experience-manager-guides-learn/tutorials/knowledge-base/expert-session/webbased-authoring-jan2023.html?lang=en)
