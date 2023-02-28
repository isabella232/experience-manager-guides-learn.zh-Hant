---
title: 產生後的工作流程
description: 以範例概述產生貼文工作流程
source-git-commit: 447cd512d1b6cdce3bd1ddded1575dab87daa04a
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 0%

---


# AEM指南發佈 — 產生後續工作流程

AEM指南可讓您彈性指定輸出後產生工作流程。 您可以對使用AEM參考線產生的輸出執行一些後置處理工作。
例如，您可能想要在PDF輸出上設定某些屬性，或在產生輸出後，您可能想要傳送電子郵件給一組使用者。


## 運用後續產生工作流程的步驟為何

### 建立工作流程程式

建立基於Java或ECMA的工作流進程，該進程對生成的輸出執行操作。 例如，將一些元資料從源複製到生成的內容或操作生成輸出的元資料。
- 我們將舉例，說明如何使用ECMA指令碼建立此類程式（您可以參考附加的套件）
- 有關基於Java的工作流進程，請參閱「*自訂輸出後產生工作流程*「 [安裝及設定指南](https://helpx.adobe.com/content/dam/help/en/xml-documentation-solution/4-2/Adobe-Experience-Manager-Guides_UUID_Installation-Configuration-Guide_EN.pdf#page=119)


### 建立工作流模型

使用您在上一步驟中建立的自訂工作流程程式，建立工作流程模型並將該程式步驟新增至該工作流程程式。
- 您還需要添加強制流程步驟「*最後生成後*」，作為工作流程的最後一步。

請參閱以下顯示的工作流模型範例：

![後置生成工作流模型](../assets/workflows/pgwf-workflow-model.png)


### 在地圖上使用此產生貼文的工作流程

後續產生工作流程是屬性，可在AEM Guides發佈機制內的任何輸出預設集上設定。 範例:

![輸出預設集上的後置生成工作流](../assets/workflows/pgwf-preset-settings.png)


假定已建立選定模型。


### 測試

現在，您可以使用此預設集執行發佈，並驗證處理步驟輸出


## 範例

如需參考，您可以使用以下套件，並透過套件管理程式進行安裝，以測試範例產生後工作流程(*如上螢幕截圖所述*)

[基於ECMA的後生成工作流模型示例](../assets/workflows/sample-pgwf-ecma-test-wfmetadata.zip)
