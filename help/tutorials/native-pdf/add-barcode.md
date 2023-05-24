---
title: 原生PDF發佈功能 |新增條碼
description: 瞭解如何新增條碼。
source-git-commit: 6cea7a92eed8f7b1d4a0763baae65ccccd71790e
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 2%

---

# 將條碼新增至PDF輸出

條碼可用來包含易於機器處理的資訊。 同樣地，QR碼也用於讀者可以用行動裝置開啟的連結。

本教學課程可協助您在PDF輸出的每個頁面上方新增條碼。

## 產生條碼的步驟

若要產生條碼，請執行下列步驟：

### 將資源ID新增至DITA map

將資源ID元素新增至DITA map。 資源ID會作為產生條碼的主要輸入。

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE map PUBLIC "-//OASIS//DTD DITA Map//EN" "technicalContent/dtd/map.dtd">
<map id="GUID-3c330691-4dac-4020-904a-d2d6246aeeb1-en">
  <title>Barcode Sample</title>
  <topicmeta>
    <resourceid id="7a5bda1c-b1db-4fd8-8763-a731e2e8abba">
    </resourceid>
  </topicmeta>
  <topicref href="GUID-139f6c64-bea3-4f17-8b22-ee131557e249-en.dita" type="topic">
  </topicref>
</map>  
```

您也可以在編寫模式下編輯資源ID。

<img src="./assets/barcode-map.png" alt="具條碼的範例輸出" width="700">


### 在範本標題中新增條碼預留位置

修改 `Common.plt` 中的檔案 **基本** 範本以在專案標題後新增條碼。

```html
...
  <div data-region="header">
    <p class="chapter-header"><span data-field="project-title" data-format="default">Project Title</span> </p>
    <p><span class="barcode" data-field="metadata" data-format="default" data-subtype="//resourceid/@id">Resource ID (barcode)</span></p>
  </div>
} 
...
```


### 更新範本的CSS以演算條碼值

修改 `content.css` 在產生PDF期間呈現條碼的檔案。 支援各種條碼型別，例如「qrcode」和「pdf417」。  如需詳細資訊，請參閱 [條碼型別](#barcode-types).



```css
...
.barcode {
  -ro-replacedelement: barcode;
  -ro-barcode-type: code128;
}
...
```

執行完上述步驟後，即可使用條碼產生PDF輸出。

以下熒幕擷圖顯示PDF輸出中的範例條碼。

<img src="./assets/barcode-output-sample.png" alt="具條碼的範例輸出" width="700">


## 條碼型別 {#barcode-types}

| 類型 | CSS屬性 | 其他屬性 |
| ------------------------------- | ----------------------- | -------------------------- |
| QR碼 | qrcode |  |
| PDF417 | pdf417 |  |
| DataMatrix | data-matrix |  |
| Aztec代碼 | aztec-code |  |
| 格點矩陣 | 格點矩陣 |  |
| Maxicode | maxicode mode-4 |  |
| Micro QR | microqr |  |
| 程式碼1 | code-one |  |
| 程式碼區塊F | codablockf |  |
| GS1資料庫有限公司 | 資料庫限制 |  |
| GS1資料庫全方向 | 資料庫全方向 |  |
| EAN-13 | ean-13 |  |
| GS1-128 (EAN-128) | code128 | -ro-barcode-encoding： gs1； |
| ITF-14 | itf14 |  |
| UPC-A | upc-a |  |
| 代碼128 | code128 |  |
| 交錯式2/5 | code2of5交錯 |  |
| POSTNET | postnet |  |
| 荷蘭文Post Kixcode | kixcode |  |
| 韓國郵政 | 韓國 — 郵政 |  |
| 德國郵遞區號 | dp-leitcode |  |
| 澳洲郵政 | auspost |  |
| Logmars | logmars |  |
| Pharmacode | pharmacode |  |
| USPS OneCode （智慧型郵件） | usps-onecode |  |


