---
sidebar_position: 8
source-git-commit: f00c135222adf57a418b4885cff2f3f036ea07ff
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---


# 範例

在此套件中，我們也提供了一些自訂範例(位於 `guides_extension/src`) 。 以下為各範本的簡短說明。

1. [內容功能表](./../../src/file_options.ts)
在此範例中，我們已自訂 `file_options` 快顯選單，以移除 `Delete` 和 `Edit` 選項，並取代 `Duplicate` 選項搭配 `Download` 選項。

2. [左側面板](../../src/left_panel_container.ts)
在此範例中，我們已自訂 `left tab panel` 以擁有另一個`tab` 標題為&quot;TEST EXTENSION&quot;，以及 `tab panel` 具有標籤： `Test Tab Panel`

3. [右側面板](../../src/right_panel_container.ts)
在此範例中，我們已自訂 `right tab panel` 以擁有另一個 `tab` 標題為&quot;TEST EXTENSION&quot;，以及 `tab panel` 具有標籤： `New Tab Panel`

4. [存放庫面板](../../src/repository_panel.ts)

5. [工具列](../../src/toolbar.ts)
在此範例中，我們已取代 `Insert Element`， `Insert Paragraph`， `Insert Numbered List`， `Insert Bulleted List` 按鈕與單一 `More Insert Options` 包含所有這些專案的按鈕。

[檢閱應用程式範例]

1. [註解工具箱](../../src/review_app_examples/annotation_extension.ts)
在此範例中，我們已將另一個按鈕新增到註釋工具箱，以在AEM中開啟目前的稽核主題。

2. [評論內容](../../src/review_app_examples/review_comment.ts)
在此範例中，我們已新增以使用者資訊（包含評論者的全名和標題）取代使用者名稱、新增唯一評論ID、mailTo圖示，以及新增用於提及評論嚴重性和理由的輸入欄位。
我們也新增了 `accept with modification` XMLEditor側上開啟對話方塊之註釋上的按鈕。

3. [評論回覆](../../src/review_app_examples/comment_reply.ts)
在此範例中，我們已新增以使用者資訊取代使用者名稱（包含評論者的完整名稱和標題），並在評論標題中新增mailTo圖示。

4. [內嵌檢閱面板](../../src/review_app_examples/inline_review_panel.ts)
在此檔案中，我們會計算並指派唯一註解ID，如中所述 `Review Comment` 和 `Comment Reply` 範例。
   - 此 `setCommentId` 方法會根據註解計數，為每個註解設定唯一的註解ID。

   - 此 `setUserInfo` 使用每個註解的完整名稱和標題來設定userInfo的值。

   - 此 `onNewCommentEvent` 確保 `setUserInfo` 每個新註解或回覆都會呼叫方法。

   - 此 `updatedProcessComments` 函式會針對每個新註解事件執行，並確保 `setCommentId` 如果收到新的評論事件，則會呼叫。

5. [主題評論面板](../../src/review_app_examples/topic_reviews.ts)：此檔案會擴充 [內嵌檢閱面板](../../src/review_app_examples/inline_review_panel.ts) 因此新增的自訂功能也可在檢閱應用程式端運作。

6. [接受並修改對話方塊](../../src/review_app_examples/accept_with_modification_dialog.ts)
這是將新Widget新增至應用程式的範例。 在此處，我們已建立新的對話方塊，其中包含兩個輸入文字欄位： `Revised Text` 和 `Adjudicator Comment Rationale`

![接受並修改對話方塊](./imgs/accept_with_modification_dialogue.png)

以下是自訂前後的檢閱面板：

![檢閱面板；](./imgs/review_panel.png)
![接受並修改對話方塊](./imgs/customised_review_panel.png)
