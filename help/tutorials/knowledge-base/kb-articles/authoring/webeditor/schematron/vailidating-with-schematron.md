---
title: 韋貝多的圖式支援
description: 在Webeditor中與Schematron一起工作
exl-id: 3e61432f-d81e-446e-b0ad-560f5b9fa91a
source-git-commit: f3c8ec973d3a6369d6135a33f61584c8bf7d083d
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# 控制Web編輯器內的內容質量

本文概述了指南Web編輯器AEM中的驗證可能性。
通過設計Web編輯器，可利用系統中的DITA架構設定來強制用戶建立符合DITA的內容。 由此，系統中儲存的所有內容都是結構化、可重用和有效的DITA內容。

除了支援DITA規則外，Web編輯器還支援基於「 」的內容驗證&#x200B;*捨馬特龍*」規則。

&quot;*捨馬特龍*「」是指用於定義XML檔案test的基於規則的驗證語言。 您可以導入Schematron檔案，也可以在Web編輯器中編輯這些檔案。 使用「架構」檔案，您可以定義某些規則，然後為DITA主題或映射驗證它們。 Schematron規則通過施加定義為規則的限制來保證XML結構的一致性。 這些限制是由擁有內容質量和一致性的中小企業推動的。

    注：Web編輯器支援ISO架構。


## 網路編輯中&quot;圖式論&quot;的作用

### 配置架構規則

請參閱中的「Support for Schematron files」（支援Schematron檔案）一節 [使用手冊](https://helpx.adobe.com/content/dam/help/en/xml-documentation-solution/4-2/Adobe-Experience-Manager-Guides_UUID_User-Guide_EN.pdf#page=148)


### 在檔案保存時強制執行驗證規則

Webeditor設定允許超級用戶設定每次用戶更新內容時將執行的Schematron規則/檔案。 有關詳細資訊，請參閱中的「驗證」部分 [使用手冊](https://helpx.adobe.com/content/dam/help/en/xml-documentation-solution/4-2/Adobe-Experience-Manager-Guides_UUID_User-Guide_EN.pdf#page=58)

![從Web編輯器設定設定規則](../../../assets/authoring/schematron-editorsettings-validation-tab.png)


### 是否可以手動運行驗證？

是，在建立內容時，作為作者/用戶，您可以在webeditor中使用「架構」面板上載架構檔案並對在編輯器中開啟的檔案運行驗證。

    要使此操作正常，資料夾配置檔案管理員必須允許所有用戶在「驗證」面板中添加Schetron檔案。 請參閱編輯器設定（上面提供的螢幕截圖）

![選擇Schematron檔案](../../../assets/authoring/schematron-rightpanel-validation-addsch.png)
![運行驗證](../../../assets/authoring/schematron-rightpanel-validation-runsch.png)


### 支援的規則

當前版本的AEM指南僅支援使用基於「斷言」的規則進行驗證。 （請參見） [資產與報表](https://schematron.com/document/205.html))任何基於「報告」的規則都不受支援。


### 關於Schematron規則的示例和更多幫助

#### 示例使用案例

- 檢查連結是否為外部連結，以及其範圍是否為「外部」

   ```
   <sch:pattern>
       <sch:rule context="xref[contains(@href, 'http') or contains(@href, 'https')]">
           <sch:assert test="@scope = 'external' and @format = 'html'">
               All external xref links must be with scope='external' and format='html'
           </sch:assert>
       </sch:rule>
   </sch:pattern>
   ```

- 檢查地圖中是否有至少一個「topicref」，或「ul」下是否有至少一個「li」

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

- &quot;indexterm&quot;元素應始終出現在&quot;prolog&quot;中

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

- 理解  [圖式基礎](https://da2022.xatapult.com/#what-is-schematron)
- 有關 [圖式的斷言規則](https://www.xml.com/pub/a/2003/11/12/schematron.html#Assertions)
- [示例Schematron檔案](../../../assets/authoring/sample_schematron.sch)
