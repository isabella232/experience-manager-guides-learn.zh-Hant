---
title: 設定資料來源聯結器
description: 瞭解如何設定資料來源聯結器
source-git-commit: bb04590ccb08cde0826dcb60c664f47d7305c9d1
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 1%

---


# 設定資料來源聯結器

AEM Guides為JIRA和SQL (MySQL、PostgreSQL、SQL Server、SQLite)資料庫提供現成的聯結器。 您也可以擴充預設介面來新增其他聯結器。 以下設定可協助您輕鬆新增各種資料來源。 新增後，您可以在網頁編輯器中檢視資料來源。

執行以下步驟來設定資料來源聯結器，然後從Web編輯器使用它：

## 設定聯結器

您可以上傳JSON檔案來設定現成可用的聯結器。 您可以使用下列範例安裝檔案來設定Jira和SQL (MySQL、PostgreSQL、SQL Server、SQLite)資料庫的聯結器。

Jira使用使用者名稱和密碼進行基本驗證的設定檔範例：

```
{
	"connectorClazz": "com.adobe.guides.konnect.definitions.ootb.connector.rest.JiraConnector",
	"configName": "Jira",
	"templateFolders": ["/content/dam/dita-templates/konnect/jira"],
	"connectionConfig": {
		"configClazz": "com.adobe.guides.konnect.definitions.ootb.config.rest.BasicAuthRestConfig",
		"configData": {
			"username": "jirausername",
			"password": "jirapassword",
			"url": "https://jira.corp.adobe.com/rest/api/latest/search"
		}
	}
}
```

例如，另存為 `jira.json`.

使用Token進行Jira基本驗證的設定檔範例：

```
{
	"connectorClazz": "com.adobe.guides.konnect.definitions.ootb.connector.rest.JiraConnector",
	"configName": "Jira",
	"templateFolders": ["/content/dam/dita-templates/konnect/jira"],
	"connectionConfig": {
		"configClazz": "com.adobe.guides.konnect.definitions.ootb.config.rest.BasicAuthRestConfig",
		"configData": {
			"token": "jiraauthtoken",
			"url": "https://jira.corp.adobe.com/rest/api/latest/search"
		}
	}
}
```

例如，另存為 `jira.json`.

Jira基本驗證的設定檔範例，其中包含具有「Basic」關鍵字的Token：

```
{
	"connectorClazz": "com.adobe.guides.konnect.definitions.ootb.connector.rest.JiraConnector",
	"configName": "Jira",
	"templateFolders": ["/content/dam/dita-templates/konnect/jira"],
	"connectionConfig": {
		"configClazz": "com.adobe.guides.konnect.definitions.ootb.config.rest.BasicAuthRestConfig",
		"configData": {
			"token": "Basic jiraauthtoken",
			"url": "https://jira.corp.adobe.com/rest/api/latest/search"
		}
	}
}
```

例如，另存為 `jira.json`.

MySql基本驗證的範例安裝檔案：

```
{
	"connectorClazz": "com.adobe.guides.konnect.definitions.ootb.connector.sql.MySqlConnector",
	"configName": "MySQL",
	"templateFolders": ["/content/dam/dita-templates/konnect/sql"],
	"connectionConfig": {
		"configClazz": "com.adobe.guides.konnect.definitions.ootb.config.sql.UserPassSqlConfig",
		"configData": {
			"username": "admin",
			"password": "admin",
			"driver": "com.mysql.jdbc.Driver",
			"connectionString": "jdbc:mysql://host.corp.adobe.com:3306/plm"
		}
	}
}
```

例如，另存為 `mysql.json`.

PostgreSQL基本驗證的設定檔範例：

```
{
	"connectorClazz": "com.adobe.guides.konnect.definitions.ootb.connector.sql.PostgreSqlConnector",
	"configName": "PostgreSQL",
	"templateFolders": ["/content/dam/dita-templates/konnect/sql"],
	"connectionConfig": {
		"configClazz": "com.adobe.guides.konnect.definitions.ootb.config.sql.UserPassSqlConfig",
		"configData": {
			"username": "admin",
			"password": "admin",
			"driver": "org.postgresql.Driver",
			"connectionString": "jdbc:postgresql://host:port/database"
		}
	}
}
```

例如，另存為 `postgres.json`.

MS SQL Server基本驗證的安裝檔案範例：

```
{
	"connectorClazz": "com.adobe.guides.konnect.definitions.ootb.connector.sql.MsSqlServerConnector",
	"configName": "MSSQLServer",
	"templateFolders": ["/content/dam/dita-templates/konnect/sql"],
	"connectionConfig": {
		"configClazz": "com.adobe.guides.konnect.definitions.ootb.config.sql.UserPassSqlConfig",
		"configData": {
			"username": "admin",
			"password": "admin",
			"driver": "com.microsoft.sqlserver.jdbc.SQLServerDriver",
			"connectionString": "jdbc:sqlserver://10.10.10.10\\SQLEXPRESS01:1433;database=TutorialDB;encrypt=false;trustServerCertificate=true"
		}
	}
}
```

例如，另存為 `mssqlserver.json`.

SQLite基本驗證的範例安裝檔案：

```
{
	"connectorClazz": "com.adobe.guides.konnect.definitions.ootb.connector.sql.SqliteConnector",
	"configName": "SQLiteServer",
	"templateFolders": ["/content/dam/dita-templates/konnect/sql"],
	"connectionConfig": {
		"configClazz": "com.adobe.guides.konnect.definitions.ootb.config.sql.UserPassSqlConfig",
		"configData": {
			"username": "admin",
			"password": "admin",
			"driver": "org.sqlite.JDBC",
			"connectionString": "jdbc:sqlite:sample.db"
		}
	}
}
```

例如，另存為 `sqqlite.json`.

### 自訂聯結器設定

AEM Guides可讓您自訂設定檔案中的某些值，以符合使用者的需求。

| 屬性名稱 | 說明 |
|---|---|
| configname | 使用者可以指定組態名稱，以協助識別聯結器 |
| templateFolders | 將從其中擷取範本的資料夾清單 |

其他欄位是根據選取用來執行聯結器的設定類別自訂。

## 將檔案上傳至AEM中的位置

將檔案上傳到AEM Assets中的某個位置。

例如 `/var/dxml/konnect/jira.json`

## 使用REST API建立設定

您可以使用REST API註冊設定。 如需詳細資訊，請檢視 *REST API可註冊資料來源聯結器* Adobe Experience Manager Guides的API參考資料中的區段。

設定資料來源後，聯結器會列在網頁編輯器的「資料來源」面板下。 然後，您可以連線至資料來源，並將內容片段插入主題中。 如需詳細資訊，請檢視 [從您的資料來源插入內容片段](../user-guide/web-editor-content-snippet.md).

