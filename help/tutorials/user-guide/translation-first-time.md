---
title: 內容翻譯的最佳實務
description: 了解內容翻譯的最佳實務
source-git-commit: 7cd719921e68ac1763d09d9665d912e3697e5849
workflow-type: tm+mt
source-wordcount: '1237'
ht-degree: 1%

---


# 內容翻譯的最佳實務 {#id1678G0S702F}

翻譯內容時，請考量下列幾點：

- 資料夾和檔案名稱必須符合檔案命名標準，例如：不應有空格、撇號、大括弧、等號、特殊或非ASCII字元。

- 如果您翻譯不同語言的內容，則必須建立與每種語言對應的資料夾。 這些語言資料夾中的每一個都會包含與該語言對應的內容。 例如，您可以使用語言標誌(如 `de` 德語， `fr` 法語等。 或者，您可以使用語言和地區指示符(如 `fr-FR` 法文或 `fr-CA` 在加拿大用的法文。
- 目標語言還應根據其實例上的目標語言資料夾選擇實際區域設定。
- 雲配置應與源資料夾的配置相同，且一個資料夾中只應有一個雲配置。 如果您想使用多個翻譯連接器，可在/conf下建立多個資料夾。
- 資料夾中的檔案不應超過1000個。
- 確保負責啟動翻譯流程的用戶具有對源語言資料夾和目標語言資料夾的讀取、修改、建立和刪除權限。
- 由於翻譯內容需要建立翻譯專案，因此使用者必須擁有在AEM中建立專案的存取權。
- 如果要將「條件預設集」與地圖搭配使用，則必須先建立條件預設集，然後再開始翻譯程式。 由於地圖的翻譯版本中也捆綁了「條件預設集」，因此在開始翻譯過程之前請建立預設集，以確保這些預設集在翻譯版本中可用。
- 內容轉譯程式必須從DITA映射主控台(而非AEM Assets UI)啟動。
- 如果您要透過人工翻譯來翻譯內容，則不得使用元件型DITA翻譯工作流程。 但是，必須將此選項用於機器翻譯。
- 不需要本地化的全球使用內容和媒體，應該不要放在語言副本中。
- 所有必須本地化的通用內容都應保留在語言資料夾下的通用資料夾中。

下圖顯示全域使用內容和三個語言副本時，AEM中的資料夾結構範例。

![](images/aem-directory_structure.png)

## 配置翻譯服務

執行以下步驟來配置要使用的人工或機器翻譯服務：

1. 在「資產」UI中，選取來源語言資料夾。

1. 開啟資料夾屬性，然後前往 **Cloud Services** 標籤。

1. 在 **Cloud Services** 頁簽，配置要使用的翻譯服務。

   您可以配置基於機器或人的翻譯。

   確保一個資料夾中只有一個翻譯連接器的配置。 如果有多個翻譯連接器，可在/conf下建立多個資料夾。 啟動翻譯過程之前，源語言資料夾必須選擇雲配置。

   >[!NOTE]
   >
   > 請參閱 [配置翻譯整合框架](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/administering/reusing-content/translation/integration-framework.html?lang=en) 如需與協力廠商翻譯服務整合的詳細資訊，請參閱AEM檔案。

1. 按一下 **儲存並關閉** 保存更新的資料夾屬性。


>[!TIP]
>
> 請參閱 *翻譯* 內容轉譯最佳實務指南的一節。

## 建立新的翻譯專案

執行下列步驟以建立翻譯專案：

>[!NOTE]
>
> 在執行此程式中的步驟之前，請確定您已建立所需的語言根和目標資料夾，如 [內容翻譯的最佳實務](#id1678G0S702F).

1. 在資產UI中，按一下DITA對應檔案。

1. 按一下 **翻譯** 標籤。

1. 從 **目標語言** 清單中，選擇要翻譯項目的地區，然後按一下 **完成**.

   畫面會顯示主題和相關資產的摘要和詳細資訊。

   >[!IMPORTANT]
   >
   > 此 **目標語言** 僅顯示與源語言並行建立語言資料夾的語言。 也不會顯示在任何其他級別建立的語言資料夾，例如從源語言資料夾向下的一個級別。 確保在與源語言資料夾相同的級別建立所有目標語言資料夾。

1. 選取要傳送以供翻譯的主題。

   您也可以使用下列主題篩選選項：

   >[!NOTE]
   >
   > 套用必要的篩選器後，按一下 **完成** ，以根據您的選擇篩選主題。

   - **翻譯狀態**:選擇以根據主題的翻譯狀態篩選主題。 可用選項包括：不同步、缺少副本、正在進行和同步。
   - **搜尋**:輸入要在主題標題中搜索的一個或多個術語。
   - **來源類型**:選擇根據主題的檔案類型篩選主題。 可用選項包括：全部、DITA、DITA映射、資源。
   - **源版本修改時間**:選擇根據修改日期和時間篩選主題。 在指定日期和時間之後修改的所有主題都顯示在清單中。
   - **基線**:按一下「使用基線」(Use Baseline)，然後選擇在映射上建立的基線。 所有屬於所選基線的檔案都顯示在「翻譯」頁中。 您可以從基線中選擇所需的檔案，然後繼續翻譯過程。 翻譯內容後，即可匯出翻譯的基線。 如需匯出已轉譯基線的詳細資訊，請參閱 [導出轉換的基線](generate-output-use-baseline-for-publishing.md#id196SE600GHS).
1. 按一下 **建立/更新語言副本** 的下方。

1. 從 **專案** 清單，選擇 **建立新的翻譯專案**.

   >[!NOTE]
   >
   > 如果您已有翻譯專案，則可將主題新增至該專案。 選擇 **新增至現有翻譯專案** 選項 **專案** 列出並從中選擇專案 **現有翻譯專案** 清單。

1. 在「專 **案標題** 」欄位中，輸入專案標題。

1. 選取 **包含DITA映射** 選項，以傳送對應以供翻譯。
1. 按一下 **開始** 建立新翻譯專案。

   系統會使用所選主題版本建立新的翻譯專案。 此時會顯示快顯訊息，確認已建立翻譯專案。 翻譯專案中提供所有目標語言副本後，您就會在收件匣中收到通知。 翻譯專案中的目標語言副本區域一旦可用，您就可以開始翻譯工作。


## 開始翻譯工作 {#id225IK030OE8}

執行下列步驟以開始翻譯工作：

1. 在 **專案** 主控台，導覽至您為本地化建立的專案資料夾。

1. 按一下本地化專案以開啟詳細資訊頁面。

1. 按一下 **翻譯工作** 拼貼，然後選取 **開始** 從清單開始翻譯工作流程。

   >[!NOTE]
   >
   > 如果您使用人文翻譯服務，則需要匯出內容以進行翻譯。 取得翻譯的內容後，您就需要將其匯回翻譯專案。

1. 若要檢視翻譯工作的狀態，請按一下 **翻譯工作** 方塊。


翻譯完成後，翻譯工作的狀態會變更為 *準備審核*. 若要完成翻譯程式，您必須從專案主控台的「翻譯工作」方塊接受翻譯的復本和資產中繼資料。

>[!NOTE]
>
> 如果您拒絕翻譯工作中一個或多個主題的翻譯，則 **進行中** 所有已拒絕主題的翻譯狀態都回復為原始狀態。 根據最新的翻譯狀態檢查並還原所引用主題的狀態。 此外，即使目標項目中的翻譯被拒絕，也不會刪除在目標項目中建立的翻譯檔案。

**上層主題：**[&#x200B;翻譯內容](translation.md)
