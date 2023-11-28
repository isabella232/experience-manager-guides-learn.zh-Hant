---
sidebar_position: 3
source-git-commit: 42052b37724f97e34ab007db4cc3d9f9524ad3a2
workflow-type: tm+mt
source-wordcount: '62'
ht-degree: 0%

---


# 文字欄位和文字區域

若要以文字作為輸入，我們使用元件、文字欄位和文字區域。
JUI中的文字區域元件代表html `<textarea/>`.

```js title="textArea.js"
const textAreaJSON =  {
    "component": "textarea", //tells the component name
    "id": "input_name", // can be used to give a unique identifier to a component
    "data": "@name", // the variable storing the inputted text
    "on-keyup": {
        "name": "submitName",
        "eventArgs": {
            "keys": [
            "ENTER"
            ]
        }
    },
},
```

此處， `on-keyup` 是叫用控制器中命令的語法。
這會產生textArea，按下ENTER即可呼叫事件 `submitName`

演算後的文字區域看起來像這樣：

![text-area](./imgs/text_area.png "文字區域")
