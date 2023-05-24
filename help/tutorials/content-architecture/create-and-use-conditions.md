---
title: 建立及使用條件
description: 瞭解如何建立條件，然後在中設定條件式內容產生 [!DNL AEM Guides]
role: User
exl-id: a86007e3-48d1-458b-84a7-b683e113e5b2
source-git-commit: b5e64512956f0a7f33c2021bc431d69239f2a088
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# 建立和使用條件並產生條件輸出

**使用案例**

* 作者可以對內容片段設定條件，以便控制該內容是否顯示在輸出中。

* 作者可以在發佈時選擇顯示/隱藏不同的條件。

* 例如，作者可以在內容中新增屬性為1.0版和2.0版，並使用條件來包括1.0版的1.0版和排除2.0版。

**步驟 1**

在中定義與檔案相關的條件 [!UICONTROL 資料夾設定檔]：請參閱區段 **設定全域或資料夾層級設定檔的條件屬性** 在 [安裝及設定指南的第64頁](https://helpx.adobe.com/content/dam/help/en/xml-documentation-solution/3-8/XML-Documentation-for-Adobe-Experience-Manager_Installation-Configuration-Guide_EN.pdf)

![在資料夾設定檔中設定條件](assets/conditions-in-profiles.png)

**步驟2**

選取 **[!UICONTROL 資料夾設定檔]** 中的步驟1所定義 **使用者偏好設定** 在XML編輯器中：請參閱區段 **使用者偏好設定** 在 [使用手冊第39頁](https://helpx.adobe.com/content/dam/help/en/xml-documentation-solution/3-8/XML-Documentation-for-Adobe-Experience-Manager_User-Guide_EN.pdf)


**步驟3**

使用條件來條件化內容的區段：請參閱區段 **條件** 在 [使用手冊第81頁](https://helpx.adobe.com/content/dam/help/en/xml-documentation-solution/3-8/XML-Documentation-for-Adobe-Experience-Manager_User-Guide_EN.pdf)

![在網頁編輯器中使用條件](assets/conditions-in-web-editor.png)

**步驟4**

在對應層級定義條件預設集，以選擇要在輸出中啟用哪些條件：請參閱區段 **使用條件預設集** 在 [使用手冊第184頁](https://helpx.adobe.com/content/dam/help/en/xml-documentation-solution/3-8/XML-Documentation-for-Adobe-Experience-Manager_User-Guide_EN.pdf)
