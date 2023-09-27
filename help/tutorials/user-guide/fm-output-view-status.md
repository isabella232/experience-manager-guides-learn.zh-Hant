---
title: 檢視輸出產生工作的狀態
description: 檢視FrameMaker檔案的輸出產生佇列。 瞭解如何檢視輸出產生任務的狀態。
exl-id: 6fdaa547-8446-4ce5-95c3-a63d9c1f27d2
source-git-commit: 8504a0a52d381044bf1f0d6e7de3585ebecf3a7b
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%

---

# 檢視輸出產生工作的狀態 {#viewing_output_history}

當您啟動FrameMaker檔案的輸出產生任務後，AEM Guides會將此任務傳送至輸出產生佇列。 此佇列會即時更新，顯示佇列中每個輸出產生工作的狀態。

執行以下步驟來檢視輸出產生佇列：

1. 在Assets UI中，導覽至並按一下FrameMaker檔案，以檢查輸出產生狀態。

1. 按一下「輸出」。

   ![](images/output-queued-fm.png){width="800" align="left"}

1. 「輸出」頁面分為兩個部分：

   - **佇列輸出：**

     列出等待產生或正在產生程式中的輸出。 您也可以找到用於已排入佇列之任務的輸出產生設定或預設集、型別、啟動任務的使用者、任務已排入佇列後的時間以及目前狀態。

   - **產生的輸出**

     列出已完成的輸出工作。 同樣地，此處顯示的資訊與「佇列輸出」區段類似，只是輸出產生時間有差異。

     在此清單中，您可能會有成功執行或失敗的工作。 對於已成功完成的工作，發佈程式會建立記錄檔\(logs.txt\)，按一下「產生時間」欄中的連結即可存取該記錄檔。


**父級主題：**[&#x200B;產生FrameMaker檔案的輸出](fm-output-generatation.md)
