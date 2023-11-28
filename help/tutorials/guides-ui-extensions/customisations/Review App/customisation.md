---
source-git-commit: 42052b37724f97e34ab007db4cc3d9f9524ad3a2
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---
# 自訂稽核應用程式

為了方便自訂檢閱應用程式，我們提供了一些鉤點，詳見以下說明：

## Review-Comment

- id： `review_comment`
- 勾點： `this.updateExtraProps`：

如討論內容 [此處](../../aem_guides_framework/basic_customisation.md)，自訂期間新增的任何新屬性都會遵循 `this.model.extraProps`. 方法 `updateExtraProps` 可讓您新增屬性至稽核註解，並處理伺服器上新增屬性的更新及儲存。

### 使用範例

舉例來說，您想要新增欄位 `commentRationale` 和 `severity` 加入您的註解。
讓我們更新 `commentRationale` 到「這是一個重要的句子」。 和 `severity` 變為「嚴重」。
您可以使用語法來達成此目的：

```typescript
 this.updateExtraProps(
        {'commentRationale': 'This is an important sentence.',
        'severity': 'CRITICAL'}
      )
```

上述程式碼片段會處理值的更新及儲存。 可藉由定義檢視在UI上呈現儲存的值。

```JSON
{
    "component" : "label",
    "label": "@extraProps.commentRationale"
}
```

## 內嵌稽核面板

- id： `inline_review_panel`

1. 勾點： `onNewCommentEvent`
勾點 `onNewCommentEvent` 可讓您擲回事件，或針對新評論或回覆事件呼叫方法。
在中收到的引數 `onNewCommentEvent` 包括：
   - 事件：已傳送的評論/回覆事件。
   - newComment：布林值如果傳送的事件是新評論事件，例如 `highlight`， `insertion`， `deletion`， `sticky note comment`
   - newReply：布林值如果傳送的事件是新回覆事件。

2. 勾點： `sendExtraProps`

如果您想要延伸 `event` 並傳送 `extraProps` 從內嵌稽核面板。 我們將在下方說明這兩個鉤點的用途。

### 內嵌稽核面板範例

假設我們要傳送額外的prop， `userInfo`，每次傳送新評論或回覆時。 現在，這將透過內嵌稽核面板完成，但我們沒有新產生註解的commentId參考，因此為了實現這一點，我們可以編寫以下程式碼。

```typescript
    onNewCommentEvent(args){
      const events = _.get(args, "events")
      const currTopicIndex = tcx.model.getValue(tcx.model.KEYS.REVIEW_CURR_TOPIC) || this.model.currTopicIndex || "0"
      const event = _.get(_.get(events, currTopicIndex), '0')
      const newComment = _.get(args, 'newComment')
      const newReply = _.get(args, 'newReply')
      if ((newComment || newReply) && event) {
        this.next('setUserInfo', event)
      }
    },
```

在上述程式碼片段中，我們正在檢查已傳送事件是否為新註解或回覆。 如果出現新的評論或回覆，我們會呼叫方法 `setUserInfo`

```typescript
    setUserInfo(event) {
      this.loader?.getUserInfo(event.user).subscribe(userData => {
        const extraProps = {
          "userFirstName": userData?.givenName || '',
          "userLastName": userData?.familyName || '',
          "userTitle": userData?.title || '',
          "userJobTitle": userData?.jobTitle || '',
          'userEmail': userData?.email || '',
        }
        const data = {... event, extraProps}
        this.sendExtraProps(
          data
        )
      })
    },
```

在上述方法中，我們將擴充事件以傳送extraProp，包括使用者的名字、電子郵件、標題等。 以此方式擴充事件可確保以正確的commentId傳送extraProp，確保將其附加到正確的註解。

勾點 `updateExtraProps` 本身會呼叫勾點 `sendExtraProps`，那什麼時候該使用什麼？

我們使用 `updateExtraProps` 在 `review_comment` 控制器，已經有註解的 `id` 因此，您只需提及 `extraProps.`

此 `inline_review_panel` 但是無法存取評論的id，因此每當您需要從內嵌稽核面板傳送事件時， `sendExtraProps` 會派上用場。
