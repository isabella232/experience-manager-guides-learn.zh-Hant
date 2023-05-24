---
title: Webeditor中的Schematron支援
description: 在Webeditor中使用Schematron
exl-id: 3e61432f-d81e-446e-b0ad-560f5b9fa91a
source-git-commit: f3c8ec973d3a6369d6135a33f61584c8bf7d083d
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# 在Web編輯器中控制內容品質

本文概述AEM Guides網頁編輯器中的驗證可能性。
透過設計Web編輯器，利用系統中的DITA架構設定來強制使用者建立符合DITA規範的內容。 這樣，儲存在系統中的所有內容都會結構化、可重複使用且有效的DITA內容。

除了支援DITA規則外，網頁編輯器也支援根據&quot;*結構描述*」規則。

&quot;*結構描述*」是指用於定義XML檔案測試的規則型驗證語言。 您可以匯入Schematron檔案，也可以在Web編輯器中編輯它們。 使用「Schematron」檔案，您可以定義特定規則，然後針對DITA主題或地圖驗證這些規則。 Schematron規則可以強制實施定義為規則的限制，以確保XML結構的一致性。 這些限制是由擁有內容品質和一致性的SME所驅動。

    注意：網頁編輯器支援ISO架構。


## 瞭解「Schematron」在Web編輯器中的運作方式

### 設定結構描述規則

請參閱以下連結中的「支援Schematron檔案」一節： [使用手冊](https://helpx.adobe.com/content/dam/help/en/xml-documentation-solution/4-2/Adobe-Experience-Manager-Guides_UUID_User-Guide_EN.pdf#page=148)


### 在檔案儲存時強制執行驗證規則

Webeditor設定可讓超級使用者設定每次使用者更新內容時所執行的Schematron規則/檔案。 如需更多詳細資訊，請參閱中的「驗證」一節。 [使用手冊](https://helpx.adobe.com/content/dam/help/en/xml-documentation-solution/4-2/Adobe-Experience-Manager-Guides_UUID_User-Guide_EN.pdf#page=58)

![從網頁編輯器設定設定規則](../../../assets/authoring/schematron-editorsettings-validation-tab.png)


### 您可以手動執行驗證嗎？

可以，作為作者/使用者，在建立內容時，您可以使用Webeditor中的Schematron面板來上傳Schematron檔案，並對在編輯器中開啟的檔案執行驗證。

    為了讓此功能發揮作用，資料夾設定檔管理員必須允許所有使用者在驗證面板中新增結構描述檔案。 請參閱編輯器設定（上方提供的熒幕擷圖）

![選擇結構描述檔案](../../../assets/authoring/schematron-rightpanel-validation-addsch.png)
![執行驗證](../../../assets/authoring/schematron-rightpanel-validation-runsch.png)


### 支援的規則

目前版本的AEM Guides僅支援使用「判斷提示」型規則進行驗證。 (請參閱 [資產vs報表](https://schematron.com/document/205.html))尚不支援任何以「報表」為基礎的規則。


### 有關Schematron規則的範例和更多說明

#### 範例使用案例

- 檢查連結是否為外部連結，以及連結的範圍是否為「外部」

   ```
   <sch:pattern>
       <sch:rule context="xref[contains(@href, 'http') or contains(@href, 'https')]">
           <sch:assert test="@scope = 'external' and @format = 'html'">
               All external xref links must be with scope='external' and format='html'
           </sch:assert>
       </sch:rule>
   </sch:pattern>
   ```

- 檢查地圖中是否至少有一個&quot;topicref&quot;，或在&quot;ul&quot;底下是否至少有一個&quot;li&quot;

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

- 「indexterm」元素應一律存在於「prolog」中

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

- 瞭解  [結構描述基礎知識](https://da2022.xatapult.com/#what-is-schematron)
- 更多關於 [結構描述中的判斷提示規則](https://www.xml.com/pub/a/2003/11/12/schematron.html#Assertions)
- [範例結構描述檔案](../../../assets/authoring/sample_schematron.sch)
