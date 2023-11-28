---
sidebar_position: 4
source-git-commit: 0f20681fa4de859053c8d2baae0e53f347ce5859
workflow-type: tm+mt
source-wordcount: '50'
ht-degree: 2%

---


# 圖示

若要顯示圖示，請使用元件「圖示」。
JUI中的文字區域元件代表html `<icon/>`.

圖示位於 [Adobe頻譜圖示](https://spectrum.adobe.com/page/icons/) 與我們的應用程式相容。

```js title="icon.js"
const iconJSON =  {
    "component": "icon", //tells the component name
    "icon": "info", // name of the icon to be used
    "size": "S", // size of the icon
    "title": "Information" // tooltip corresponding to the icon.
},
```

圖示也可以新增到按鈕中。

演算後的圖示看起來像這樣：

![圖示](./imgs/info_icon.png "圖示")
