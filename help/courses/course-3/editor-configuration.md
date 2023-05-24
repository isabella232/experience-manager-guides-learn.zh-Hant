---
title: AEM Guides編輯器設定
description: 為AEM Guides設定編輯器
exl-id: 437d9598-4afc-431f-81bd-6762e22656b7
source-git-commit: 67ba514616a0bf4449aeda035161d1caae0c3f50
workflow-type: tm+mt
source-wordcount: '780'
ht-degree: 0%

---

# XML編輯器設定

如果您在限制性的環境中工作，您可以透過自訂特定資料夾設定檔中的編輯器設定，選擇作者能夠檢視的功能。 套用此資料夾描述檔可以變更編輯器本身的外觀、CSS範本、可用的代碼片段以及內容版本標籤。

檔案中提供您可選擇用於本課程的範例檔案 [xmleditorconfiguration.zip](assets/xmleditorconfiguration.zip).

>[!VIDEO](https://video.tv.adobe.com/v/342762?quality=12&learn=on)

## 自訂預設編輯器UI設定

您一律可以將預設UI設定下載到本機系統，在您選擇的文字編輯器中對其進行變更，然後再次上傳。

1. 在導覽畫面中，按一下 [!UICONTROL **工具**] 圖示。

   ![工具圖示](images/reuse/tools-icon.png)

1. 選取 **指南** 在左側面板。

1. 按一下 [!UICONTROL **資料夾設定檔**] 圖磚。

   ![資料夾設定檔](images/reuse/folder-profiles-tile.png)

1. 選取資料夾設定檔。

1. 按一下 [!UICONTROL **XML編輯器設定**] 標籤。

1. 按一下 [!UICONTROL **下載**] 預設。

   ![下載預設值](images/lesson-4/download-default.png)

您現在可以在文字編輯器中開啟及修改內容。 此 _AEM Guides安裝與設定_ 指南包含如何移除、自訂函式或將其新增到UI設定的範例。

## 上傳修改過的XML編輯器UI設定

自訂UI設定後，您可以上傳它。 請注意，組態檔範例 _ui-config-restricted-editor.json_ 隨附本課程的一組支援主題。

1. 在「資料夾描述檔」中，按一下 [!UICONTROL **XML編輯器設定**] 標籤。

1. 在XML編輯器UI設定下，按一下 [!UICONTROL **上傳**].

   ![上傳](images/lesson-4/upload.png)

1. 按兩下您修改過的UI設定的檔案，或這裡所示的提供範例檔案。

   ![範例設定檔](images/lesson-4/sample-config-file.png)

1. 按一下 [!UICONTROL **儲存**] 在熒幕的左上角。

您已成功上傳修改過的UI設定。

## 自訂CSS範本版面

和UI設定一樣，您可以下載CSS範本版面。 您可以在文字編輯器中開啟該主題，並進行修改以在上傳之前自訂主題的外觀。

1. 在導覽畫面中，按一下 [!UICONTROL **工具**] 圖示。

   ![工具圖示](images/reuse/tools-icon.png)

1. 選取 **指南** 在左側面板。

1. 按一下 [!UICONTROL **資料夾設定檔**] 圖磚。

   ![資料夾設定檔](images/reuse/folder-profiles-tile.png)

1. 選取資料夾設定檔。

1. 按一下 [!UICONTROL **XML編輯器設定**] 標籤。

1. 在「CSS範本配置」下，按一下 [!UICONTROL **下載**].

   ![下載CSS](images/lesson-4/download-css.png)

您現在可以在文字編輯器中修改及儲存CSS內容。

## 上傳修改過的CSS範本版面

自訂CSS範本佈局後，您可以上傳它。 請注意，範例檔案 _css-layout-ONLY-draft-comment-change.css_ 隨附本課程的一組支援主題。 此檔案僅包含「草稿註解變更」，而 _css-layout-draft-comment-change.css_ 是整個檔案，僅供您測試或檢閱之用。

1. 在「資料夾描述檔」中，按一下 [!UICONTROL **XML編輯器設定**] 標籤。

1. 在「CSS範本配置」下，按一下 [!UICONTROL **上傳**].

   ![上傳 CSS](images/lesson-4/upload-css.png)

1. 連按兩下檔案，以取得您自己的自訂CSS版面配置或此處顯示的提供範例檔案。

   ![範例CSS檔案](images/lesson-4/sample-css-file.png)

1. 按一下 [!UICONTROL **儲存**] 在熒幕的左上角。
您已成功上傳自訂的CSS範本版面。

## 編輯XML編輯器代碼片段

程式碼片段是可重複使用的內容片段，可以特定於產品或群組。 請注意，範常式式碼片段會隨本課程的支援檔案一起提供。

1. 在導覽畫面中，按一下 [!UICONTROL **工具**] 圖示。

   ![工具圖示](images/reuse/tools-icon.png)

1. 選取 **指南** 在左側面板。

1. 按一下 [!UICONTROL **資料夾設定檔**] 圖磚。

   ![資料夾設定檔](images/reuse/folder-profiles-tile.png)

1. 選取資料夾設定檔。

1. 按一下 [!UICONTROL **XML編輯器設定**] 標籤。

1. 在「XML編輯器代碼片段」底下，按一下 **上傳**.

   ![上傳代碼片段](images/lesson-4/upload-snippets.png)

1. 選擇您自己的代碼片段或使用提供的範例。

   ![範常式式碼片段](images/lesson-4/sample-snippet.png)

1. 按一下 [!UICONTROL **儲存**] 在熒幕的左上角。

您已成功將新的代碼片段新增至編輯器。

## 自訂XML內容版本標籤

依預設，作者可以建立自己選擇的標籤，並將其與主題檔案相關聯。 這可能會導致同一標籤上的不同變化。 為避免標籤不一致，您也可以從預先定義的標籤清單中選擇。

1. 在導覽畫面中，按一下 [!UICONTROL **工具**] 圖示。

   ![工具圖示](images/reuse/tools-icon.png)

1. 選取 **指南** 在左側面板。

1. 按一下 [!UICONTROL **資料夾設定檔**] 圖磚。

   ![資料夾設定檔](images/reuse/folder-profiles-tile.png)

1. 選取資料夾設定檔。

1. 按一下 [!UICONTROL **XML編輯器設定**] 標籤。

1. 在「XML內容版本標籤」下，按一下 [!UICONTROL **下載**].

   ![下載標籤](images/lesson-4/download-labels.png)

您現在已準備好視需要自訂標籤。

## 上傳XML內容版本標籤

下載並修改標籤後，您就可以上傳XML內容版本標籤主題。 您可以選擇使用範例檔案 _labels.json_，並提供本課程的一組支援主題。

1. 在「資料夾描述檔」中，按一下 [!UICONTROL **XML編輯器設定**] 標籤。

1. 在「XML內容版本標籤」下，按一下 [!UICONTROL **上傳**].

   ![上傳標籤](images/lesson-4/upload-labels.png)

1. 連按兩下檔案以取得您自己的自訂標籤或此處顯示的提供範例檔案。

   ![範例標籤檔案](images/lesson-4/sample-labels-file.png)

1. 按一下 [!UICONTROL **儲存**] 在熒幕的左上角。

您已成功上傳自訂XML內容版本標籤。
