---
title: 支援Schematron檔案
description: 瞭解如何使用架構驗證您的主題
exl-id: e5912fa1-af26-42f4-b5e5-a6d2afd45bc8
source-git-commit: f6794078e760565f5934faf63a7cbfb919acce90
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 0%

---

# 支援Schematron檔案

「Schematron」是指用來定義XML檔案測試的規則型驗證語言。 網頁編輯器支援Schematron檔案。 您可以匯入Schematron檔案，也可以在Web編輯器中編輯它們。 您可以使用Schematron檔案定義特定規則，然後針對DITA主題或地圖驗證這些規則。

>[!NOTE]
>
> 網頁編輯器支援ISO結構描述。


## 匯入Schematron檔案

執行以下步驟來匯入Schematron檔案：

![](images/scematron-panel-add.png){width="300" align="left"}

1. 導覽至所需的資料夾（您要上傳檔案的位置），位置在： *存放庫檢視*.
1. 按一下 **選項** 圖示以開啟內容功能表並選擇 **上傳資產**.
1. 在 **上傳資產** 對話方塊中，您可以變更目的地資料夾 **選取資產資料夾** 欄位。
1. 按一下 **選擇檔案** 並瀏覽以選取Schematron檔案。 您可以選取一或多個「結構描述」檔案，然後按一下 **上傳**.

## 使用Schematron驗證DITA主題或地圖

匯入Schematron檔案後，您可以在Web編輯器中編輯它們。 您可以使用Schematron檔案來驗證主題或DITA map。 例如，您可以為DITA map或主題建立下列規則：

* 已為DITA map定義標題。
* 已新增特定長度的簡短說明。
* 地圖中應至少有一個topicref。

在Web編輯器中開啟主題時，「結構描述驗證」面板會出現在右側。 執行以下步驟來新增和驗證主題或具有Schematron檔案的對應：
![](images/schematron-validate.png){width="300" align="left"}

1. 按一下「結構描述」圖示()以開啟「結構描述」面板。
1. 使用「新增Schematron檔案」來新增Schematron檔案。
1. 如果Schematron檔案沒有錯誤，則會新增該檔案並列在「驗證」面板中。 針對包含錯誤的Schematron檔案顯示錯誤訊息。
   >[!NOTE]
   >
   >您可以使用Schematron檔案名稱附近的十字圖示來移除它。
1. 按一下使用結構描述進行驗證，以驗證主題。

   * 如果主題未破壞任何規則，則會顯示檔案的驗證成功訊息。
   * 如果主題破壞規則，例如，如果它不包含標題並為上述給定結構描述進行驗證，則會顯示驗證錯誤。

1. 按一下錯誤訊息，以反白顯示開啟的主題/地圖中包含錯誤的元素。

網頁編輯器中的Schematron支援可協助您根據一組規則來驗證檔案，並維護主題間的一致性和正確性。

## 使用判斷提示和報表陳述式來檢查規則{#schematron-assert-report}

AEM Guides也支援Schematron中的assert和report陳述式。 這些陳述式可協助您驗證DITA主題。

### Assert陳述式

當測試陳述式評估為false時，判斷提示陳述式會產生訊息。 例如，如果您希望標題為粗體，可以為其定義判斷提示陳述式。

```XML
<sch:rule context="title"> 
    <sch:assert test = "b"> Title should be bold </sch:assert>
  </sch:rule>
```

使用Schematron驗證DITA主題時，會出現標題未加粗的主題訊息。

### 報告陳述式

當測試陳述式評估為true時，報表陳述式會產生訊息。 例如，如果您希望簡短說明小於或等於150個字元，可以定義報表陳述式，以檢查簡短說明超過150個字元的主題。
當您使用Schematron驗證DITA主題時，您會得到報告陳述式評估為true的規則的完整報告。 因此，您會收到一則簡短說明超過150個字元的主題訊息。


```XML
<sch:rule context="shortdesc"> 
        <sch:let name="characters" value="string-length(.)"/> 
        <sch:report test="$characters &gt; 150">  
        The short description has <sch:value-of select="$characters"/> characters. It should contain more than 150 characters.      
        </sch:report>   
    </sch:rule> 
```

>[!NOTE]
>
> 撰寫Schematron規則時只使用Xpath 2.0運算式。

## 使用規則運算式{#schematron-regex-espressions}

您也可以使用Regex運算式定義具有matches()函式的規則，然後使用Schematron檔案執行驗證。

例如，如果標題只包含一個單字，您可以使用它來顯示訊息。

```XML
<assert test="not(matches(.,'^\w+$'))"> 
No one word titles.
</assert>  
```


## 定義抽象模式{#schematron-abstract-patterns}

AEM Gudies也支援Schematron中的抽象模式。 您可以定義一般抽象模式，以重複使用這些抽象模式。  您可以建立指定實際模式的預留位置引數。


使用抽象模式可減少規則的重複，並更容易管理和更新驗證邏輯，藉此簡化您的Schematron結構描述。 它也可以讓您的結構描述更易於理解，因為您可以在可在整個結構描述中重複使用的單一抽象模式中定義複雜的驗證邏輯。


例如，下列XML程式碼會建立抽象模式，然後實際模式會使用ID來參照它。

```XML
<sch:pattern abstract="true" id="LimitNoOfWords"> 

<sch:rule context="$parentElement"> 

<sch:let name="words" value="string-length(.)"/> 

<sch:assert test="$words &lt; $maxWords"> 

You have <sch:value-of select="$words"/> letters. This should be lesser than <sch:value-of select="$maxWords"/>. 

</sch:assert>  

<sch:assert test="$words &gt; $minWords"> 

You have <sch:value-of select="$words"/> letters. This should be greater than <sch:value-of select="$minWords"/>. 

</sch:assert>  

</sch:rule> 

</sch:pattern> 

<sch:pattern is-a="LimitNoOfWords" id="extend-LimitNoOfWords"> 

<sch:param name="parentElement" value="title"/> 

<param name="minWords" value="1"/> 

<param name="maxWords" value="8"/> 

</sch:pattern> 
```
