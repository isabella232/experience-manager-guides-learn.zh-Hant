---
title: 後期生成工作流
description: 後期生成工作流的一個示例概述
exl-id: e19fdc0b-0ec6-46ce-81ed-e9490d12c029
source-git-commit: 3cfa0a58c5681668fbb3c97dcbe1e8f7e32335fc
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 0%

---

# 指AEM南發佈 — 後期生成工作流

指AEM南使您可以靈活地指定輸出後生成工作流。 您可以對使用「參考線」生成的輸出執行一些後處理AEM任務。
例如，您可能希望在PDF輸出上設定某些屬性，或者在生成輸出後，可能希望向一組用戶發送電子郵件。


## 利用後代工作流涉及哪些步驟

### 建立工作流進程

建立基於Java或ECMA的工作流進程，該工作流進程對生成的輸出執行操作。 例如，將某些元資料從源複製到生成的內容或操作生成的輸出的元資料。
- 我們將舉一個示例，說明如何使用ECMA指令碼建立此過程（您可以引用附加的包）
- 有關基於Java的工作流進程，請參閱「」一節&#x200B;*自定義輸出後生成工作流*「 」 [安裝及設定指南](https://helpx.adobe.com/content/dam/help/en/xml-documentation-solution/4-2/Adobe-Experience-Manager-Guides_UUID_Installation-Configuration-Guide_EN.pdf#page=119)


### 建立工作流模型

使用您在上一步中建立的自定義工作流進程，建立工作流模型並將該進程步驟添加到該工作流模型中。
- 您還需要添加強制流程步驟&#39;&#39;*完成後期生成*」作為工作流的最後一步。

請參閱下面所示的示例工作流模型：

![後代工作流模型](../assets/workflows/pgwf-workflow-model.png)


### 在地圖上使用此後期生成工作流

後期生成工作流是一個屬性，可在「參考線」發佈機制內的任何輸AEM出預設上配置。 範例:

![「輸出預設」上的後期生成工作流](../assets/workflows/pgwf-preset-settings.png)


假定已建立選定模型。


### 測試

現在，您可以使用此預設運行發佈並驗證流程步驟輸出


## 範例

為了供您參考，您可以使用下面的軟體包並通過軟體包管理器安裝它，以test示例後生成工作流(*如上所述*)

[基於ECMA的後生成工作流模型](../assets/workflows/sample-pgwf-ecma-test-wfmetadata.zip)
