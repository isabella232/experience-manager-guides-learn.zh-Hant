---
sidebar_position: 2
source-git-commit: 42052b37724f97e34ab007db4cc3d9f9524ad3a2
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 1%

---


# 安裝和使用AEM Guides擴充功能套件

擴充功能可讓您自訂您的AEM Guides應用程式，以更符合您的需求。 AEM Guides v4.3以上（內部部署）和2310 （雲端）支援此擴充功能架構。

## 要求

此封裝需要 [Git雜湊](https://github.com/git-guides/install-git) 和npm

## 安裝

啟動AEM Guides框架安裝的最簡單方式是透過cli

```bash
npx @adobe/create-guides-extension
```

## 新增自訂程式碼

1. 為您要在中擴充的每個元件新增程式碼檔案 `src/` 目錄。 已經為您新增了一些範例檔案。
2. 現在位於 `index.ts` 檔案位於 `src/` 目錄：
   - 匯入 `.ts` 包含您要在組建中新增的自訂專案的檔案。
   - 將匯入新增至 `window.extension`
   - 註冊自訂元件的 `id` 和對應的匯入目標 `tcx extensions`
   - 請參閱範例 [index.ts](../../../src/index.ts)

## 建立自訂程式碼

- 執行 `npm run build` 在根目錄中。 目錄中會有3個檔案， `dist/`：
   - `build.css`
   - `guides-extension.js`
   - `guides-extension.umd.cjs`

![建置輸出](./../imgs/build_output.png)

## 將自訂新增至AEM

- 前往 `CRXDE` `crx/de/index.jsp#/`
- 在 `apps` 資料夾，建立型別的新節點 `cq:ClientLibraryFolder`

![檔案夾結構](./../imgs/crxde_folder_structure.png)

- 在 `properties` 在節點中，選取 `Multi` 新增以下屬性Name： `categories`
型別： `String []`
值： `apps.fmdita.review_overrides`， `apps.fmdita.xml_editor.page_overrides`

![資料夾屬性](./../imgs/crxde_folder_properties.png)

- 若要新增內建js，請建立新檔案，例如： `tcx1.js` 在上述建立的節點中。 在這裡，從新增程式碼 `dist/guides-extension.umd.cjs` 或 `dist/guides-extension.js`. 現在建立新檔案 `js.txt`，接著新增js檔案名稱，在此案例中會是：

```t
#base=.
tcx1.js
```

- 若要新增內建的css，請建立新檔案，例如： `tcx1.css` 在上述建立的節點中。 在這裡，從新增程式碼 `dist/build.css`. 現在建立新檔案 `css.txt`，接著新增css檔案的名稱，在此案例中會是：

```t
#base=.
tcx1.css
```

- 執行 `shift + refresh` 以載入包含自訂內容的應用程式！

## 疑難排解

檢查上述所有步驟是否正確執行。
將程式碼新增至tcx.js後，請務必執行強制重新整理(shift+refresh)。
現在開啟AEM，按一下滑鼠右鍵，然後按一下 `Inspect`
前往「來源」並搜尋您的 `[node_name].js` （例如： extensions.js）檔案。 執行Control / Cmd + D以搜尋您的檔案。 如果 `.js` 存在與您貼入之JS程式碼相同的檔案 `dist/guides-extension.umd.cjs` 或 `dist/guides-extension.js`，您的設定已完成
