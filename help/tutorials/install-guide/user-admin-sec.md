---
title: 用戶管理和安全
description: 瞭解用戶管理和安全工作原理
source-git-commit: 801c306fa120e7889d4b9428fd5bee2849bf1956
workflow-type: tm+mt
source-wordcount: '742'
ht-degree: 10%

---


# 用戶管理和安全 {#id181AED00G5Z}

要訪問和配置指南中AEM的功能，您需要建立用戶。 然後，可以為這些用戶分配訪問指南中所有或特定功AEM能的權限。 瞭解如何配置和維護用戶授權，並瞭解身份驗證和授權在中的工作原理AEM。

文檔中的以AEM下主題將幫助您瞭解用戶管理和與安全相關的概念和功能：

- [中的用戶和組AEM](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/security.html#UsersandGroupsinAEM)

- [權AEM限](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/security.html#PermissionsinAEM)

- [管理用戶和組](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/security.html#ManagingUsersandGroups)

- [管理權限](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/security.html#ManagingPermissions)


## 輔助線建立的AEM用戶組 {#id181TF0K0MHT}

指AEM南提供了三個現成的組來管理DITA項目中的不同任務。 這些組包括： *作者*。 *審閱者*, *出版商*。 根據用戶所關聯的組，允許用戶執行特定任務。 例如，發佈任務只能由發佈者執行，而不能由作者或審閱者執行。 同樣，作者可以建立新主題，而審閱者只能審閱主題。

>[!TIP]
>
> 查看 *權限* 最佳實踐指南中有關設定用戶權限的最佳實踐部分。

下表列出了可執行這些任務的各種任務和組：

| 任務 | 作者 | 檢閱者 | 出版商 |
|----|-------|---------|----------|
| 建立DITA主題 | 是 |   | 是 |
| 建立DITA映射 | 是 |   | 是 |
| 映射集合 | 是 |   | 是 |
| 建立審閱任務 | 是 |   | 是 |
| 審閱主題[1](#fntarg_1) | 是 | 是 | 是 |
| 密鑰解析 | 是 |   | 是 |
| 在FrameMaker中開啟 | 是 |   | 是 |
| 簽出/簽入 | 是 |   | 是 |
| 編輯主題 | 是 |   | 是 |
| 移動主題 | 是 |   | 是 |
| 編輯主題屬性 | 是 |   | 是 |
| 複製 | 是 |   | 是 |
| 刪除 | 是 |   | 是 |
| 共用 | 是 |   | 是 |
| **文檔狀態** |
| 建立/編輯文檔狀態配置檔案 |   |   | 是 |
| 更改文檔狀態[2](#fntarg_2) | 是 | 是 | 是 |
| **DITA映射控制台\（輸出預設頁籤\）中提供的功能** |
| 產生 |   |   | 是 |
| 編輯 |   |   | 是 |
| 複製 |   |   | 是 |
| 建立 |   |   | 是 |
| 刪除預設集 |   |   | 是 |
| **DITA映射控制台\（輸出頁籤\）中提供的功能** |
| 查看生成的輸出 | 是 |   | 是 |
| **DITA映射控制台\（主題頁籤\）中提供的功能** |
| 建立審閱任務 | 是 |   | 是 |
| 編輯 | 是 |   | 是 |
| **DITA映射控制台\（基線頁籤\）中提供的功能** |
| 建立 |   |   | 是 |
| 編輯 |   |   | 是 |
| 複製 |   |   | 是 |
| 移除 |   |   | 是 |
| DITA映射控制台\（報告頁籤\） | 是 |   | 是 |
| **DITA映射控制台\（條件預設\）中提供的功能** |
| 建立/編輯條件預設 |   |   | 是 |

## 有關用戶組的附加說明

以下清單包含一些與用戶組和相應權限相關的建議和點：

- 如果希望用戶啟動翻譯或審閱工作流，請確保該用戶是 *出版商* 和 *項目管理員組*。

- 用戶必須具有在需要處理的源語言資料夾和目標語言資料夾上可用的讀取、建立、刪除和修改權限。

- 如果建立項目，則您是項目的所有者 *出版商* 權限。 項目中的其他用戶若要能夠查看其團隊成員、建立任務或建立工作流，必須具有對的讀取訪問權限 `/home/users` 和 `/home/groups` 節點。 提供讀訪問權限的一種方法 `/home/users` 和 `/home/groups` 節點通過授予對 `projects-users` 組。

- *審閱者* 可以從Project控制台或收件箱通知連結訪問和添加有關正在審閱的主題的審閱注釋。 此外，此訪問僅在查看任務開啟之前可用。

- 預設情況下， *出版商* 在DAM中授予對以下資料夾的訪問權限和權限：

   - ``/var/dxml``–\> 讀取和寫入

   - `/content/dam/fmdita-outputs` –\> 讀取和寫入

   - `/content/output/sites` –\> 讀取和寫入

   如果您使用的是除上述預設發佈位置之外的任何其他位置，則必須為發佈者授予明確的讀和寫權限。

- 所有用戶 *作者*。 *審閱者*, *出版商* 組對DAM中的所有內容都具有讀權限。

- 必須通過用戶管理頁將資料夾級權限分配給用戶。

- 如果希望用戶能夠在DAM上執行搜索操作，則請使用戶成為 *大壩用戶* 組。

- 如果要向任何用戶授予管理權限，可以通過通過標準組(如 *管理員*。 *項目管理員*&#x200B;或OSGI配置\（Felix控制台\）。

- 要授予用戶更改文檔狀態的權限，請確保在文檔狀態配置檔案的狀態轉換部分添加用戶。

[1](#fnsrc_1) 如果 *作者* 和 *出版商* 邀請您進行審閱。[2](#fnsrc_2) 取決於在文檔狀態配置檔案中授予用戶的權限。
