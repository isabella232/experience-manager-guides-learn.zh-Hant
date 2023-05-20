---
title: 將自定義樣式添加到參考線編輯器
description: 瞭解如何添加自定義樣式以更改「參考線」編輯器的外觀。
exl-id: 3a9dd701-9d9d-4d7f-bc0c-855904404fd1
source-git-commit: ed3adf0cf8006c76461de34c6a2a4ba38d8b3406
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# 將自定義樣式添加到參考線編輯器

在本文中，我們將瞭解如何添加自定義樣式以更改瀏覽器預設外觀。

這將涉及以下步驟：
- 通過資料夾配置檔案XML編輯器配置添加自定義樣式
- 在Webeditor中選擇相應的資料夾配置檔案並測試更改


## 以實例實施

讓我們通過一個示例來瞭解這一點，在該示例中，我們希望將簡短說明和標題作為單獨的塊在編輯器中顯示一些樣式方面。

![使用自定義樣式預覽Webeditor](../../../assets/authoring/webeditor-customstyles-preview.png)


## 實施此


### 將自定義CSS添加到資料夾配置檔案

使用資料夾配置檔案檢查 *css_layout.css* 在「XML編輯器配置」頁籤下，添加具有自定義樣式的CSS

[使用此連結可瞭解有關資料夾配置檔案和配置CSS模板佈局的詳細資訊](https://experienceleague.adobe.com/docs/experience-manager-guides-learn/videos/advanced-user-guide/editor-configuration.html?lang=en#customize-the-css-template-layout)

使用以下方法在編輯器中設定上述樣式：
- 使用 [css_layout.css](../../../assets/authoring/webeditor-customstyles-css_layout.css) 將其上載到您選擇的資料夾配置檔案
- 安裝連接的包 [webeditor-styles-resources.zip](../../../assets/authoring/webeditor-styles-resources.zip) 使AEM用包管理器安裝上述CSS檔案中使用的資源

```
This will install the resources at path "/content/dam/resources" which will include sub-folders "fonts" and "images"
```


### 測試

- 開啟Web編輯器
- 從用戶首選項中選擇添加自定義樣式的資料夾配置檔案。 如果將其添加到全局配置檔案，則您可能已在使用它。
- 開啟主題時，您會注意到編輯區域應具有自定義UI

```
Please note this is compatible to AEM Guides version 4.2 and AEM Guides cloud version 2303 (March)
```


## 引用

您還可能對以下內容中涉及的圍繞WebDitor配置和自定義的專家會議感興趣： [關於Webeditor的專家會議](https://experienceleague.adobe.com/docs/experience-manager-guides-learn/tutorials/knowledge-base/expert-session/webbased-authoring-jan2023.html?lang=en)
