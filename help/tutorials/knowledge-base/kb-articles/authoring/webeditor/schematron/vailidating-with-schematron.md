---
title: 韋貝迪托的圖式支援
description: 在Webeditor中與Schematron合作
source-git-commit: 2a036ec628424f0dedfdb69a5e860906ca100cc6
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---


# 控制Web編輯器內容的品質

本文概述AEM指南網頁編輯器中的驗證可能性。
通過設計Web編輯器，可利用系統中的DITA架構設定來強制用戶建立DITA相容內容。 借此，系統中儲存的所有內容都經過結構化、可重複使用且有效的DITA內容。

除了支援DITA規則外，Web編輯器還支援基於「*捨馬特龍*」規則。

&quot;*捨馬特龍*「」是指用於定義XML檔案測試的基於規則的驗證語言。 您可以導入Schematron檔案，也可以在Web編輯器中編輯它們。 使用「架構」檔案，您可以定義特定規則，然後驗證DITA主題或地圖的規則。 方案規則通過施加定義為規則的限制來確保XML結構的一致性。 這些限制是由擁有內容質量和一致性的中小企業推動的。

    注意：Web編輯器支援ISO架構。


## 了解&quot;圖式&quot;在網頁編輯器中的作用

### 配置架構規則

請參閱 [使用手冊](https://helpx.adobe.com/content/dam/help/en/xml-documentation-solution/4-2/Adobe-Experience-Manager-Guides_UUID_User-Guide_EN.pdf#page=148)


### 對檔案儲存強制執行驗證規則

Webeditor設定允許超級用戶設定Schematron規則/檔案，這些規則/檔案將在用戶每次更新內容時執行。 如需更多詳細資訊，請參閱 [使用手冊](https://helpx.adobe.com/content/dam/help/en/xml-documentation-solution/4-2/Adobe-Experience-Manager-Guides_UUID_User-Guide_EN.pdf#page=58)

![從網頁編輯器設定設定規則](../../../assets/authoring/schematron-editorsettings-validation-tab.png)


### 可以手動運行驗證嗎？

可以，作為建立內容時的作者/用戶，可以在webeditor中使用「架構」面板來上載架構檔案，並對在編輯器中開啟的檔案運行驗證。

    為了讓此功能發揮作用，資料夾配置檔案管理員必須允許所有用戶在「驗證」面板中添加Schemtron檔案。 請參閱編輯器設定（上方提供的螢幕擷圖）

![選擇架構檔案](../../../assets/authoring/schematron-rightpanel-validation-addsch.png)
![執行驗證](../../../assets/authoring/schematron-rightpanel-validation-runsch.png)


### 支援的規則

目前版本的AEM指南僅支援使用「斷言」型規則進行驗證。 (請參閱 [資產與報告](https://schematron.com/document/205.html))尚不支援任何以「報表」為基礎的規則。


### Schematron規則的示例和更多幫助

#### 範例使用案例

- 檢查連結是否為外部連結，以及連結是否具有範圍「外部」

   ```
   <sch:pattern>
       <sch:rule context="xref[contains(@href, 'http') or contains(@href, 'https')]">
           <sch:assert test="@scope = 'external' and @format = 'html'">
               All external xref links must be with scope='external' and format='html'
           </sch:assert>
       </sch:rule>
   </sch:pattern>
   ```

- 檢查地圖中是否至少有一個「topicref」，或「ul」下是否至少有一個「li」

   ```
   <sch:pattern>
       <sch:rule context="map">
           <sch:assert test="count(topicref) > 0">
               There should be atleast one topicref in map
           </sch:assert>
       </sch:rule>
   
       <sch:rule context="ul">
           <sch:assert test="count(li) > 1" >
               A list must have more than one item.
           </sch:assert>
       </sch:rule>
   </sch:pattern>
   ```

- 「indexterm」元素應一律顯示在「prolog」中

   ```
   <sch:pattern>
       <sch:rule context="*[contains(@class, ' topic/indexterm ')]">
           <sch:assert test="ancestor::node()/local-name() = 'prolog'">
               The indexterm element should be in a prolog.
           </sch:assert>
       </sch:rule>
   </sch:pattern>
   ```

#### 資源

- 了解  [Schematron基本介紹](https://da2022.xatapult.com/#what-is-schematron)
- 關於 [圖式中的斷言規則](https://www.xml.com/pub/a/2003/11/12/schematron.html#Assertions)
- [示例架構檔案](../../../assets/authoring/sample_schematron.sch)