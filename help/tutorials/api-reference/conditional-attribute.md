---
title: 使用條件屬性的REST API
description: 瞭解如何使用條件屬性的REST API
source-git-commit: fad5049962f258bbe59c7d172436d82b3d6cd68f
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 2%

---


# 使用條件屬性的REST API {#id175UB30E05Z}

下列REST API可讓您在資料夾設定檔中新增條件屬性。

## 在資料夾層級的設定檔中新增條件屬性

將條件屬性新增至指定資料夾層級設定檔的POST方法。

**請求 URL**:\
http://*&lt;aem-guides-server>*： *&lt;port-number>*/bin/fmdita/folderprofiles

**參數**:\
|名稱|型別|必要|說明| --------------------------- |`:operation`|字串|是|要呼叫的作業名稱。 此引數的值為 ``ADDATTRIBUTEPROFILES``. <br> **注意：** 值不區分大小寫。| |`profilename`|字串|是|必須新增條件屬性的資料夾層級設定檔的顯示名稱。| |`conditionalprofiles`|JSON陣列|是|由條件屬性名稱和值組成的JSON陣列。 下列範常式式碼片段顯示具有兩個屬性的JSON陣列 —  `platform` 和 `product` 指派了多個值。|

```JSON
[  {    name: "platform",    
        values: [       
                {value: "win", label: "Windows"},       
                {value: "mac", label: "Mac OS"}    
                ]},
                {    
                    name: "product",    
                    values: [      
                        {value: "aem_1", label: "AEM 6.1"},     
                        {value: "aem_4,  label: "AEM 6.4"}  
                        ]  
                }]
```

**回應值**：\
傳回HTTP 200 \(Successful\)回應。

