---
title: 新增自訂樣式至參考線編輯器
description: 了解如何新增自訂樣式以變更指南編輯器的外觀和風格。
source-git-commit: 9e7d5bb4c8f6c6ebe21bfcebdd7d2e13971b8df2
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# 新增自訂樣式至參考線編輯器

在本文中，我們將了解如何新增自訂樣式以變更瀏覽器預設外觀和風格。

這將包括下列步驟：
- 通過資料夾配置檔案XML編輯器配置添加自定義樣式
- 在Webiditor中選擇相應的資料夾配置檔案並測試更改


## 以實例進行實作

讓我們透過一個範例來了解，其中我們要將簡短說明和標題顯示為個別區塊，並在編輯器中提供一些樣式方面。

![使用自訂樣式預覽編輯器](../../../assets/authoring/webeditor-customstyles-preview.png)


## 實作此


### 將自訂CSS新增至資料夾設定檔

使用資料夾設定檔來檢查 *css_layout.css* 在「XML編輯器配置」頁簽下，添加具有自定義樣式的CSS

[使用此連結可進一步了解資料夾設定檔和設定CSS範本配置](https://experienceleague.adobe.com/docs/experience-manager-guides-learn/videos/advanced-user-guide/editor-configuration.html?lang=en#customize-the-css-template-layout)

使用以下內容，在您的網站中設定上述樣式：
- 使用 [css_layout.css](../../../assets/authoring/webeditor-customstyles-css_layout.css) 並上傳至您選擇的資料夾設定檔
- 安裝附加的包 [webeditor-styles-resources.zip](../../../assets/authoring/webeditor-styles-resources.zip) 使用AEM套件管理器來安裝上述CSS檔案中使用的資源

```
This will install the resources at path "/content/dam/resources" which will include sub-folders "fonts" and "images"
```


### 測試

- 開啟Web編輯器
- 從使用者偏好設定中，選擇您新增自訂樣式的資料夾設定檔。 如果您將其新增至全域設定檔，則您可能已使用過。
- 開啟主題時，您會注意到編輯區域應該有自訂UI

```
Please note this is compatible to AEM Guides version 4.2 and AEM Guides cloud version 2303 (March)
```


## 引用

您也可能有興趣參加以下主題的專家會議： [Webeditor專家會議](https://experienceleague.adobe.com/docs/experience-manager-guides-learn/tutorials/knowledge-base/expert-session/webbased-authoring-jan2023.html?lang=en)