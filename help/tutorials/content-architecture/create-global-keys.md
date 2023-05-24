---
title: 建立全域索引鍵
description: 如何建立要在組織內容中使用的全域金鑰
role: Admin
exl-id: b8e3a6d2-ea82-4fdb-bd16-3f4b6594af52
source-git-commit: b5e64512956f0a7f33c2021bc431d69239f2a088
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---

# 建立全域索引鍵

組織應使用索引鍵，以防止有許多地方都使用某些可重複且常見的文字（例如產品名稱或產品推介），但這些文字很容易變更。 對此類可重複使用的文字使用索引鍵，可讓您透過在單一位置（例如索引鍵值）進行變更，將更新推送到多個位置。

## 步驟1：建立全域地圖以儲存金鑰

建立地圖並新增 [!UICONTROL keyref] 元素加入。

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE map PUBLIC "-//OASIS//DTD DITA Map//EN" "technicalContent/dtd/map.dtd">
<mapid="map.ditamap_ffbdbf06-8658-4311-ad84-1c631bba904f">
  <title>global-keys-map</title>
  <keydefkeys="adobe">
    <topicmeta>
      <linktext>Adobe Systems</linktext>
    </topicmeta>
  </keydef>
  <keydefkeys="AEM">
    <topicmeta>
      <linktext>Adobe Experience Manager</linktext>
    </topicmeta>
  </keydef>
</map>
```

您在此處定義了兩個定義（如上所示），並提供 [!UICONTROL keyref] 作為 _AEM_ 的 _Adobe Experience Manager_ 文字。

## 步驟2：將此地圖新增至您的出版物地圖

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE map PUBLIC "-//OASIS//DTD DITA Map//EN" "technicalContent/dtd/map.dtd">
<mapid="map.ditamap_cbf4a96d-e382-4e8c-8830-bcc093fe6638">
  <title>sample-map</title>
  <topicrefhref="sample-topic-using-the-keys.dita"type="topic">
  </topicref>
  <maprefformat="ditamap"href="global-keys-map.ditamap"type="map">
  </mapref>
</map>
```

## 步驟3：使用索引鍵來參照全域索引鍵對映中定義的變數

+ 編輯主題並使用 [!UICONTROL keyref].
+ 如熒幕擷圖所示，將顯示一個小視窗，您可在其中選擇關鍵字。 當您新增「keyword」元素時，就會顯示這個專案。
   ![插入元素](assets/insert_element.png)
   ![索引鍵參考](assets/key_ref.png)

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE topic PUBLIC "-//OASIS//DTD DITA Topic//EN" "technicalContent/dtd/topic.dtd">
<topicid="topic.dita_31b00e61-04b5-4193-af7a-68503e88b087">
  <title>sample-topic-using-the-keys</title>
  <shortdesc></shortdesc>
  <body>
    <p>This is a sample topic using the keys defined in the global map</p>
    <p>here i am using the key definition for AEM :<keywordkeyref="AEM"></keyword></p>
  </body>
</topic>
```
