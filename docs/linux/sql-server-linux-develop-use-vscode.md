---
title: 使用 Visual Studio Code 的 mssql 擴充功能適用於 SQL Server |Microsoft Docs
description: 本教學課程會示範如何使用適用於 VS Code 的 mssql 擴充功能。 此延伸模組可讓您編輯，然後在 VS Code 中執行 TRANSACT-SQL 指令碼。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/17/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 9766ee75-32d3-4045-82a6-4c7968bdbaa6
ms.custom: sql-linux
ms.openlocfilehash: b1ae9056ecbaf158b275798d69d691ae64e6ef06
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/06/2018
ms.locfileid: "51033625"
---
# <a name="use-visual-studio-code-to-create-and-run-transact-sql-scripts-for-sql-server"></a>使用 Visual Studio Code 來建立和執行 SQL Server 的 TRANSACT-SQL 指令碼

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

本文示範如何使用**mssql** Visual Studio Code （VS Code），開發 SQL Server 資料庫的擴充功能。

Visual Studio Code 是適用於 Linux、 macOS 和支援擴充功能的 Windows 圖形化的程式碼編輯器。 [**mssql** VS Code 擴充功能] 可讓您連接到 SQL Server，使用 TRANSACT-SQL (T-SQL)、 查詢和檢視結果。

## <a name="install-vs-code"></a>安裝 VS Code
1. 如果尚未安裝 VS Code[下載並安裝 VS Code]您的電腦上。

2. 啟動 VS Code。

## <a name="install-the-mssql-extension"></a>安裝 mssql 擴充功能
下列步驟說明如何安裝 mssql 擴充功能。 

1. 按**CTRL + SHIFT + P** (或**F1**) 若要開啟命令選擇區 VS Code 中。 

2. 選取 [安裝擴充功能] 並輸入 **mssql**。
   > [!TIP] 
   > 對於 macOS， **CMD**機碼相當於**CTRL** Linux 和 Windows 上的索引鍵。

2. 按一下 安裝 **mssql**。 
   
   <img src="./media/sql-server-linux-develop-use-vscode/vscode-extension.png" alt="Install the extension" style="width: 600px;"/>

3. 安裝 **Mssql** 延伸模組最多需要一分鐘。 請等候提示，告訴您已成功安裝。

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-install-success-notification.png" alt="Installation success notification" style="width: 600px;"/>

   > [!NOTE]
   > 若使用的是 MacOS，則必須先安裝 OpenSSL。 這是讓 mssql  延伸模組使用 .Net Core 的必要條件。 請遵循 [.Net Core 指示] 的 **安裝必要條件** 中的步驟。 或者，您也可以在您的 macOS 終端機中執行下列命令。
   >
   >   ```bash
   >   brew update
   >   brew install openssl
   >   ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
   >   ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
   >   ```
   
   > [!NOTE]
   > Windows 8.1、 Windows Server 2012 或較低版本，您必須下載並安裝[Windows 10 通用 C 執行階段]。 下載並開啟 zip 檔案。 然後執行安裝程式 （.msu 檔案） 目標設為目前的 OS 設定。

## <a name="create-or-open-a-sql-file"></a>建立或開啟 SQL 檔案

**Mssql**擴充功能可讓 mssql 命令和 T-SQL IntelliSense 在編輯器中將語言模式設定為當**SQL**。

1. 按下**CTRL + N**。 Visual Studio Code 預設會開啟新的 「 純文字 」 檔案。 

2. 按下**CTRL + K、 M**並將語言模式變更為**SQL**。 

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-language-mode.png" alt="SQL language mode" style="width: 500px;" />

3. 或者，開啟現有的檔案副檔名為.sql 檔案。 將語言模式會自動**SQL**具有.sql 副檔名的檔案。  

## <a name="connect-to-sql-server"></a>連接至 SQL Server

下列步驟示範如何連接到 SQL Server 以 VS Code。

1. 在 VS Code 中，按 **CTRL+SHIFT+P** (或 **F1**) 開啟 [命令選擇區]。

2. 型別**sql**以顯示 mssql 命令。

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-commands.png" alt="mssql commands" style="width: 500px;" />
   

3. 選取  **MS SQL： 連接**命令。 您只需鍵入**sqlcon**然後按**ENTER**。

4. 選取 **建立連線設定檔**。 這會建立您的 SQL Server 執行個體的連線設定檔。

5. 遵循提示來指定新連線設定檔的連線屬性。 指定每個值之後，請按 **ENTER** 繼續。 

   下表介紹連線設定檔屬性。

   | 設定 | 描述 |
   |-----|-----|
   | **伺服器名稱** | SQL Server 執行個體名稱。 本教學課程中，使用**localhost**連接到本機電腦上的 SQL Server 執行個體。 如果連接到遠端 SQL Server，請輸入目標 SQL Server 電腦或其 IP 位址的名稱。 如果您需要指定您的 SQL Server 執行個體的連接埠，請使用逗號來分隔的名稱。 例如針對本機伺服器連接埠 1401年上執行您會輸入**localhost，1401年**。 |
   | **[選用]資料庫名稱** | 您想要使用的資料庫。 基於本教學課程的詳細資訊，未指定資料庫，然後按**ENTER**以繼續。 |
   | **使用者名稱** | 輸入資料庫伺服器上具有存取權的使用者名稱。 本教學課程中，使用預設值**SA**在 SQL Server 安裝期間建立的帳戶。 |
   | **密碼 (SQL 登入)** | 請輸入指定之使用者的密碼。 | 
   | **儲存密碼嗎？** | 若要儲存密碼，請輸入**是**。 否則請輸入**否**，此後每次使用連線設定檔時，系統都會提示您輸入密碼。 |
   | **[選用] 輸入此設定檔的名稱** | 連線設定檔名稱。 例如，您可將設定檔命名為**本機主機設定檔**。 

   > [!Tip] 
   > 您可以建立和編輯使用者設定檔 (settings.json) 中的連線設定檔。 開啟選取的設定檔**喜好設定**，然後**使用者設定**VS Code 功能表。 如需詳細資訊，請參閱 [管理連線設定檔]。

6. 按 **ESC** 鍵關閉資訊訊息，通知您已建立並連線設定檔。

   > [!TIP]
   > 如果連接失敗，第一次嘗試診斷問題中的錯誤訊息從**輸出**VS Code 中的面板 (選取**輸出**上**檢視**功能表)。 然後檢閱[連線疑難排解建議]。

7. 在狀態列中確認您的連線。

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-connection-status.png" alt="Connection status" style="width: 500px;" />

## <a name="create-a-database"></a>建立資料庫

1. 在編輯器中，輸入**sql**以顯示可編輯的程式碼片段的清單。 

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-sql-snippets.png" alt="SQL snippets" style="width: 500px;" />

2. 選取  **sqlCreateDatabase**。

3. 在片段中，輸入**TutorialDB**的資料庫名稱。

   ```sql
   USE master
   GO
   IF NOT EXISTS (
      SELECT name
      FROM sys.databases
      WHERE name = N'TutorialDB'
   )
   CREATE DATABASE [TutorialDB]
   GO
   ```
   
4. 按下**CTRL + SHIFT + E**執行 TRANSACT-SQL 命令。 在查詢視窗中檢視結果。

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-create-database-messages.png" alt="create database messages" style="width: 500px;" />

   > [!TIP]
   > 您可以自訂快速鍵繫結 mssql 延伸模組命令。 請參閱[自訂快速鍵]。

## <a name="create-a-table"></a>建立資料表

1. 移除 [編輯器] 視窗中的內容。

2. 按下**F1**顯示命令選擇區。

3.  在命令選擇區輸入 **sql** 以顯示 SQL 命令，或輸入 **sqluse** 以顯示 **MS SQL:Use Database** 命令。

4. 按一下  **MS sql: use-cdata 資料庫**，然後選取**TutorialDB**資料庫。 這是在上一節中建立新資料庫變更的內容。

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-use-database.png" alt="use database" style="width: 500px;" />

3. 在編輯器中，輸入**sql** 以顯示程式碼片段，然後選取 **sqlCreateTable** 並按 **Enter**。

4. 在程式碼片段中，輸入 **Employees** 作為資料表名稱。

5. 按 **Tab 鍵**，然後輸入 **dbo** 作為結構描述名稱。

   > [!NOTE]
   > 之後加入程式碼片段，您必須輸入的資料表和結構描述名稱，而不需要變更焦點從 VS Code 編輯器。

6. 變更的資料行名稱**Column1**要**名稱**並**Column2**至**位置**。

   ```sql
   -- Create a new table called 'Employees' in schema 'dbo'
   -- Drop the table if it already exists
   IF OBJECT_ID('dbo.Employees', 'U') IS NOT NULL
   DROP TABLE dbo.Employees
   GO
   -- Create the table in the specified schema
   CREATE TABLE dbo.Employees
   (
      EmployeesId        INT    NOT NULL   PRIMARY KEY, -- primary key column
      Name      [NVARCHAR](50)  NOT NULL,
      Location   [NVARCHAR](50)  NOT NULL
   );
   GO
   ```

7. 按下**CTRL + SHIFT + E**來建立資料表。

## <a name="insert-and-query"></a>插入和查詢

1. 加入下列陳述式以新增四個資料列至 **Employees** 資料表。 然後選取所有資料列。

   ```sql
   -- Insert rows into table 'Employees'
   INSERT INTO Employees
      ([EmployeesId],[Name],[Location])
   VALUES
      ( 1, N'Jared', N'Australia'),
      ( 2, N'Nikita', N'India'),
      ( 3, N'Tom', N'Germany'),
      ( 4, N'Jake', N'United States')   
   GO   
   -- Query the total count of employees
   SELECT COUNT(*) as EmployeeCount FROM dbo.Employees;
   -- Query all employee information
   SELECT e.EmployeesId, e.Name, e.Location 
   FROM dbo.Employees as e
   GO
   ```

   > [!TIP]
   > 雖然您輸入時，使用 T-SQL IntelliSense 的協助。
   >   <img src="./media/sql-server-linux-develop-use-vscode/vscode-intellisense.png" alt="TSQL IntelliSense" style="width: 500px;" />

2. 按下**CTRL + SHIFT + E**以執行命令。 這兩個結果集顯示在**結果**視窗。 

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-result-grid.png" alt="Results" style="width: 300px;" />

## <a name="view-and-save-the-result"></a>檢視及儲存結果

1. 在 **檢視**功能表上，選取**切換編輯器群組配置**切換至垂直或水平分割配置。

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-toggle-split.png" alt="Vertical split" style="width: 500px;" />

2. 按一下 **結果**並**訊息**摺疊和展開 面板 中的面板標頭。

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-toggle-messages-pannel.png" alt="Toggle Messages" style="width: 500px;" />

   > [!TIP]
   > 您可以自訂 mssql 擴充功能的預設行為。 請參閱[自訂延伸模組選項]。

2. 按一下第二個結果方格放大，以最大化格線圖示。

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-maximize-grid.png" alt="Maximize grid" style="width: 500px;" />

   > [!NOTE]
   > 當您的 T-SQL 指令碼有兩個或多個結果方格時，會顯示最大化 圖示。

3. 滑鼠右鍵點選方格開啟 [方格] 內容功能表。 

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-grid-context-menu.png" alt="Context menu" style="width: 500px;" />

4. 選取 **選取所有**。

5. 開啟 [方格] 內容功能表，然後選取 **儲存為 JSON** 將結果儲存為 .json 檔案。

6. 指定 JSON 檔案的檔案名稱。 本教學課程中，輸入**employees.json**。

7. 請確認 JSON 檔案已經儲存，並在 VS Code 中開啟。

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-save-as-json.png" alt="Save as Json" style="width: 500px;" />

## <a name="next-steps"></a>後續步驟

在真實世界案例中，您所建立的指令碼，可能會先儲存之後再執行 (無論用於系統管理或做為更大型的開發專案的一部分)。 在此情況下，您可以使用 **.sql** 為副檔名的方式儲存指令碼。

如果您不熟悉 T-SQL，請參閱[教學課程：撰寫 Transact-SQL 陳述式]和 [Transact-SQL 參考 (Database Engine)]。

如需有關使用或促成 mssql 擴充功能的詳細資訊，請參閱 < [mssql 擴充功能專案 wiki]。

如需有關使用 VS Code 的詳細資訊，請參閱[Visual Studio Code 文件](https://code.visualstudio.com/docs)。

[**mssql** VS Code 擴充功能]:https://aka.ms/mssql-marketplace
[下載並安裝 VS Code]:https://code.visualstudio.com/Download
[.Net Core 指示]:https://www.microsoft.com/net/core
[管理連線設定檔]:https://github.com/Microsoft/vscode-mssql/wiki/manage-connection-profiles
[連線疑難排解建議]:./sql-server-linux-troubleshooting-guide.md#connection
[自訂快速鍵]:https://github.com/Microsoft/vscode-mssql/wiki/customize-shortcuts
[教學課程：撰寫 Transact-SQL 陳述式]:https://msdn.microsoft.com/library/ms365303.aspx
[Transact-SQL 參考 (Database Engine)]:https://msdn.microsoft.com/library/bb510741.aspx
[Visual Studio Code documentation]:https://code.visualstudio.com/docs
[Windows 10 通用 C 執行階段]:https://github.com/Microsoft/vscode-mssql/wiki/windows10-universal-c-runtime-requirement
[自訂延伸模組選項]: https://github.com/Microsoft/vscode-mssql/wiki/customize-options
[mssql 擴充功能專案 wiki]: https://github.com/Microsoft/vscode-mssql/wiki
