---
title: 建立、 改變和移除預存程序 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- stored procedures [SMO]
ms.assetid: 2a072f9c-8f11-4364-ab71-3990735a8d66
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fe7fb603ae3b0f3550d63d4c9b886934b31a28ba
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48074498"
---
# <a name="creating-altering-and-removing-stored-procedures"></a>建立、改變和移除預存程序
  在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]管理物件 (SMO) 預存程序由<xref:Microsoft.SqlServer.Management.Smo.StoredProcedure>物件。  
  
 建立<xref:Microsoft.SqlServer.Management.Smo.StoredProcedure>在 SMO 中的物件需要設定<xref:Microsoft.SqlServer.Management.Smo.StoredProcedure.TextBody%2A>屬性設[!INCLUDE[tsql](../../../includes/tsql-md.md)]定義預存程序的指令碼。 參數需要\@前置詞，且必須建立使用的個別<xref:Microsoft.SqlServer.Management.Smo.StoredProcedureParameter>物件以及加入至<xref:Microsoft.SqlServer.Management.Smo.StoredProcedureParameter>的集合<xref:Microsoft.SqlServer.Management.Smo.StoredProcedure>物件。  
  
## <a name="example"></a>範例  
 如果要使用所提供的任何程式碼範例，您必須選擇建立應用程式用的程式設計環境、程式設計範本，及程式設計語言。 如需詳細資訊，請參閱[Visual Studio.NET 中建立 Visual Basic SMO Project](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)或是[建立 Visual C&#35; Visual Studio.NET 中的 SMO 專案](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)。  
  
## <a name="creating-altering-and-removing-a-stored-procedure-in-visual-basic"></a>在 Visual Basic 中建立、改變和移除預存程序  
 此程式碼範例示範如何建立預存程序[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)]資料庫。 以下範例在給定員工識別碼時會傳回員工的姓。 預存程序需要一個輸入參數來指定員工識別碼，以及一個輸出參數來傳回員工的姓氏。  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBStoredProcs1](SMO How to#SMO_VBStoredProcs1)]  -->  
  
## <a name="creating-altering-and-removing-a-stored-procedure-in-visual-c"></a>在 Visual C# 中建立、改變和移除預存程序  
 此程式碼範例示範如何建立預存程序[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)]資料庫。 以下範例在給定員工識別碼 (`BusinessEntityID`) 時會傳回員工的姓氏。 預存程序需要一個輸入參數來指定員工識別碼，以及一個輸出參數來傳回員工的姓氏。  
  
```  
{  
            //Connect to the local, default instance of SQL Server.   
            Server srv;  
            srv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database db;  
            db = srv.Databases["AdventureWorks2012"];  
            //Define a StoredProcedure object variable by supplying the parent database and name arguments in the constructor.   
            StoredProcedure sp;  
            sp = new StoredProcedure(db, "GetLastNameByBusinessEntityID");  
            //Set the TextMode property to false and then set the other object properties.   
            sp.TextMode = false;  
            sp.AnsiNullsStatus = false;  
            sp.QuotedIdentifierStatus = false;  
            //Add two parameters.   
            StoredProcedureParameter param;  
            param = new StoredProcedureParameter(sp, "@empval", DataType.Int);  
            sp.Parameters.Add(param);  
            StoredProcedureParameter param2;  
            param2 = new StoredProcedureParameter(sp, "@retval", DataType.NVarChar(50));  
            param2.IsOutputParameter = true;  
            sp.Parameters.Add(param2);  
            //Set the TextBody property to define the stored procedure.   
            string stmt;  
            stmt = " SELECT @retval = (SELECT LastName FROM Person.Person,HumanResources.Employee WHERE Person.Person.BusinessEntityID = HumanResources.Employee.BusinessentityID AND HumanResources.Employee.BusinessEntityID = @empval )";  
            sp.TextBody = stmt;  
            //Create the stored procedure on the instance of SQL Server.   
            sp.Create();  
            //Modify a property and run the Alter method to make the change on the instance of SQL Server.   
            sp.QuotedIdentifierStatus = true;  
            sp.Alter();  
            //Remove the stored procedure.   
            sp.Drop();  
        }  
```  
  
## <a name="creating-altering-and-removing-a-stored-procedure-in-powershell"></a>在 PowerShell 中建立、改變和移除預存程序  
 此程式碼範例示範如何建立預存程序[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)]資料庫。 以下範例在給定員工識別碼 (`BusinessEntityID`) 時會傳回員工的姓氏。 預存程序需要一個輸入參數來指定員工識別碼，以及一個輸出參數來傳回員工的姓氏。  
  
```  
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = get-item Adventureworks2012  
  
# Define a StoredProcedure object variable by supplying the parent database and name arguments in the constructor.   
$sp  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.StoredProcedure `  
-argumentlist $db, "GetLastNameByBusinessEntityID"  
  
#Set the TextMode property to false and then set the other object properties.   
$sp.TextMode = $false  
$sp.AnsiNullsStatus = $false  
$sp.QuotedIdentifierStatus = $false  
  
# Add two parameters  
$type = [Microsoft.SqlServer.Management.SMO.Datatype]::Int  
$param  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.StoredProcedureParameter `  
-argumentlist $sp,"@empval",$type  
$sp.Parameters.Add($param)  
  
$type = [Microsoft.SqlServer.Management.SMO.DataType]::NVarChar(50)  
$param2  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.StoredProcedureParameter `  
-argumentlist $sp,"@retval",$type  
$param2.IsOutputParameter = $true  
$sp.Parameters.Add($param2)  
  
#Set the TextBody property to define the stored procedure.   
$sp.TextBody =  " SELECT @retval = (SELECT LastName FROM Person.Person,HumanResources.Employee WHERE Person.Person.BusinessEntityID = HumanResources.Employee.BusinessentityID AND HumanResources.Employee.BusinessEntityID = @empval )"  
  
# Create the stored procedure on the instance of SQL Server.   
$sp.Create()  
  
# Modify a property and run the Alter method to make the change on the instance of SQL Server.   
$sp.QuotedIdentifierStatus = $true  
$sp.Alter()  
  
#Remove the stored procedure.   
$sp.Drop()  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure>  
  
  
