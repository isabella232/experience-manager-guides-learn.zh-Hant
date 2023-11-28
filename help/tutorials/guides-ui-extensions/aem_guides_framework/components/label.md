---
sidebar_position: 2
source-git-commit: 0f20681fa4de859053c8d2baae0e53f347ce5859
workflow-type: tm+mt
source-wordcount: '44'
ht-degree: 2%

---


# 標籤

若要顯示任何文字或字串，我們會使用元件label。
JUI中的label元件代表html `<label/>`.

以下是新增靜態標籤的範例

```js title="staticLabel.js"
const staticLabelJSON =  {
    "component": "label", //tells the component name
    "label": "This is an example label", // the string to be displayed
}
```

JSON下方會顯示動態字串：

```js title="dynamicLabel.js"
const labelJSON =  {
    "component": "label", //tells the component name
    "label": "@name", // the variable storing the text to be displayed
},
```

轉譯的標籤看起來像這樣：

![標籤](./imgs/label.png "標籤")