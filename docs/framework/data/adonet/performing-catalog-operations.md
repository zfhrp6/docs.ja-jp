---
title: カタログ操作の実行
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e60f542f-6271-495b-a9e4-48553481c2a3
ms.openlocfilehash: c1d8b9dd579cae7f4868058343c034caf17c5fff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33362065"
---
# <a name="performing-catalog-operations"></a><span data-ttu-id="7ee86-102">カタログ操作の実行</span><span class="sxs-lookup"><span data-stu-id="7ee86-102">Performing Catalog Operations</span></span>
<span data-ttu-id="7ee86-103">データベースまたは、CREATE TABLE または CREATE PROCEDURE ステートメントなどのカタログを変更するコマンドを実行するには、作成、**コマンド**オブジェクト、適切な SQL ステートメントを使用して、**接続**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="7ee86-103">To execute a command to modify a database or catalog, such as the CREATE TABLE or CREATE PROCEDURE statement, create a **Command** object using the appropriate SQL statements and a **Connection** object.</span></span> <span data-ttu-id="7ee86-104">コマンドを実行、 **ExecuteNonQuery**のメソッド、**コマンド**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="7ee86-104">Execute the command with the **ExecuteNonQuery** method of the **Command** object.</span></span>  
  
 <span data-ttu-id="7ee86-105">Microsoft SQL Server データベースにストアド プロシージャを作成するコード サンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="7ee86-105">The following code example creates a stored procedure in a Microsoft SQL Server database.</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim queryString As String = "CREATE PROCEDURE InsertCategory " & _  
    "@CategoryName nchar(15), " & _  
    "@Identity int OUT " & _  
    "AS " & _  
    "INSERT INTO Categories (CategoryName) VALUES(@CategoryName) " & _  
    "SET @Identity = @@Identity " & _  
    "RETURN @@ROWCOUNT"  
  
Dim command As SqlCommand = New SqlCommand(queryString, connection)  
command.ExecuteNonQuery()  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
string queryString = "CREATE PROCEDURE InsertCategory  " +   
    "@CategoryName nchar(15), " +  
    "@Identity int OUT " +  
    "AS " +   
    "INSERT INTO Categories (CategoryName) VALUES(@CategoryName) " +   
    "SET @Identity = @@Identity " +  
    "RETURN @@ROWCOUNT";  
  
SqlCommand command = new SqlCommand(queryString, connection);  
command.ExecuteNonQuery();  
```  
  
## <a name="see-also"></a><span data-ttu-id="7ee86-106">関連項目</span><span class="sxs-lookup"><span data-stu-id="7ee86-106">See Also</span></span>  
 [<span data-ttu-id="7ee86-107">コマンドを使用したデータ変更</span><span class="sxs-lookup"><span data-stu-id="7ee86-107">Using Commands to Modify Data</span></span>](../../../../docs/framework/data/adonet/using-commands-to-modify-data.md)  
 [<span data-ttu-id="7ee86-108">コマンドおよびパラメーター</span><span class="sxs-lookup"><span data-stu-id="7ee86-108">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="7ee86-109">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="7ee86-109">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
