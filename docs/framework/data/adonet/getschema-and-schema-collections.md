---
title: GetSchema およびスキーマ コレクション
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ab93b89-1221-427c-84ad-04803b3c64b4
ms.openlocfilehash: 1694a6de515e5326264f345f50d0730fe2a62e4f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="getschema-and-schema-collections"></a><span data-ttu-id="6c116-102">GetSchema およびスキーマ コレクション</span><span class="sxs-lookup"><span data-stu-id="6c116-102">GetSchema and Schema Collections</span></span>
<span data-ttu-id="6c116-103">**接続**各 .NET Framework マネージ プロバイダーの実装のクラス、 **GetSchema**メソッドが現在接続されているデータベースに関するスキーマ情報を取得するために使用し、返されるスキーマ情報、 **GetSchema**メソッドは、の形式では、<xref:System.Data.DataTable>です。</span><span class="sxs-lookup"><span data-stu-id="6c116-103">The **Connection** classes in each of the .NET Framework managed providers implement a **GetSchema** method which is used to retrieve schema information about the database that is currently connected, and the schema information returned from the **GetSchema** method comes in the form of a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="6c116-104">**GetSchema**メソッドが戻るには、スキーマ コレクションを指定し、返される情報の量を制限するための省略可能なパラメーターを提供するオーバー ロードされたメソッドです。</span><span class="sxs-lookup"><span data-stu-id="6c116-104">The **GetSchema** method is an overloaded method that provides optional parameters for specifying the schema collection to return, and restricting the amount of information returned.</span></span>  
  
## <a name="specifying-the-schema-collections"></a><span data-ttu-id="6c116-105">スキーマ コレクションの指定</span><span class="sxs-lookup"><span data-stu-id="6c116-105">Specifying the Schema Collections</span></span>  
 <span data-ttu-id="6c116-106">最初の省略可能なパラメーター、 **GetSchema**メソッドは、文字列として指定されるコレクションの名前。</span><span class="sxs-lookup"><span data-stu-id="6c116-106">The first optional parameter of the **GetSchema** method is the collection name which is specified as a string.</span></span> <span data-ttu-id="6c116-107">スキーマ コレクションには 2 種類あります。すべてのプロバイダーに共通している一般的なスキーマ コレクションと、各プロバイダーによって固有のスキーマ コレクションです。</span><span class="sxs-lookup"><span data-stu-id="6c116-107">There are two types of schema collections: common schema collections that are common to all providers, and specific schema collections which are specific to each provider.</span></span>  
  
 <span data-ttu-id="6c116-108">呼び出すことによってサポートされるスキーマ コレクションの一覧を特定の .NET Framework マネージ プロバイダーを照会することができます、 **GetSchema**メソッド引数のない、またはスキーマ コレクション名に"metadatacollections を指定して"います。</span><span class="sxs-lookup"><span data-stu-id="6c116-108">You can query a .NET Framework managed provider to determine the list of supported schema collections by calling the **GetSchema** method with no arguments, or with the schema collection name "MetaDataCollections".</span></span> <span data-ttu-id="6c116-109">これにより、サポートされるスキーマ コレクションの一覧、それぞれがサポートする制限数、および使用する識別子部分の数と共に、<xref:System.Data.DataTable> が返されます。</span><span class="sxs-lookup"><span data-stu-id="6c116-109">This will return a <xref:System.Data.DataTable> with a list of the supported schema collections, the number of restrictions that they each support, and the number of identifier parts that they use.</span></span>  
  
### <a name="retrieving-schema-collections-example"></a><span data-ttu-id="6c116-110">スキーマ コレクションの取得例</span><span class="sxs-lookup"><span data-stu-id="6c116-110">Retrieving Schema Collections Example</span></span>  
 <span data-ttu-id="6c116-111">次の例を使用する方法を示します、<xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>の .NET Framework Data Provider for SQL Server メソッド<xref:System.Data.SqlClient.SqlConnection>に関する、すべてのテーブルに含まれているスキーマ情報を取得するクラス、 **AdventureWorks**サンプル データベース。</span><span class="sxs-lookup"><span data-stu-id="6c116-111">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database:</span></span>  
  
```vb  
Imports System.Data.SqlClient  
  
Module Module1  
   Sub Main()  
      Dim connectionString As String = GetConnectionString()  
      Using connection As New SqlConnection(connectionString)  
         'Connect to the database then retrieve the schema information.  
         connection.Open()  
         Dim table As DataTable = connection.GetSchema("Tables")  
  
         ' Display the contents of the table.  
         DisplayData(table)  
         Console.WriteLine("Press any key to continue.")  
         Console.ReadKey()  
      End Using  
   End Sub  
  
   Private Function GetConnectionString() As String  
      ' To avoid storing the connection string in your code,    
      ' you can retrieve it from a configuration file.  
      Return "Data Source=(local);Database=AdventureWorks;" _  
         & "Integrated Security=true;"  
   End Function  
  
   Private Sub DisplayData(ByVal table As DataTable)  
      For Each row As DataRow In table.Rows  
         For Each col As DataColumn In table.Columns  
            Console.WriteLine("{0} = {1}", col.ColumnName, row(col))  
         Next  
         Console.WriteLine("============================")  
      Next  
   End Sub  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
  
class Program  
{  
  static void Main()  
  {  
  string connectionString = GetConnectionString();  
  using (SqlConnection connection = new SqlConnection(connectionString))  
  {  
   // Connect to the database then retrieve the schema information.  
   connection.Open();  
   DataTable table = connection.GetSchema("Tables");  
  
   // Display the contents of the table.  
   DisplayData(table);  
   Console.WriteLine("Press any key to continue.");  
   Console.ReadKey();  
   }  
 }  
  
  private static string GetConnectionString()  
  {  
   // To avoid storing the connection string in your code,  
   // you can retrieve it from a configuration file.  
   return "Data Source=(local);Database=AdventureWorks;" +  
      "Integrated Security=true;";  
  }  
  
  private static void DisplayData(System.Data.DataTable table)  
  {  
     foreach (System.Data.DataRow row in table.Rows)  
     {  
        foreach (System.Data.DataColumn col in table.Columns)  
        {  
           Console.WriteLine("{0} = {1}", col.ColumnName, row[col]);  
        }  
     Console.WriteLine("============================");  
     }  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="6c116-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="6c116-112">See Also</span></span>  
 [<span data-ttu-id="6c116-113">データベース スキーマ情報の取得</span><span class="sxs-lookup"><span data-stu-id="6c116-113">Retrieving Database Schema Information</span></span>](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [<span data-ttu-id="6c116-114">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="6c116-114">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
