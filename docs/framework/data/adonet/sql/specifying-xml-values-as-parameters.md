---
title: パラメーターとしての XML 値の指定
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2c4d08b8-fc29-4614-97fa-29c8ff7ca5b3
ms.openlocfilehash: c963b3e08eba7776a0ed579017f1e84828794379
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355299"
---
# <a name="specifying-xml-values-as-parameters"></a><span data-ttu-id="1369b-102">パラメーターとしての XML 値の指定</span><span class="sxs-lookup"><span data-stu-id="1369b-102">Specifying XML Values as Parameters</span></span>
<span data-ttu-id="1369b-103">開発者がのインスタンスを使用してその値を指定できますクエリには、その値は、XML 文字列パラメーターが必要とする場合、 **SqlXml**データ型。</span><span class="sxs-lookup"><span data-stu-id="1369b-103">If a query requires a parameter whose value is an XML string, developers can supply that value using an instance of the **SqlXml** data type.</span></span> <span data-ttu-id="1369b-104">実際にはありませんテクニックです。SQL Server の XML 列では、他のデータ型とまったく同じ方法でパラメーター値をそのまま使用します。</span><span class="sxs-lookup"><span data-stu-id="1369b-104">There really are no tricks; XML columns in SQL Server accept parameter values in exactly the same way as other data types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1369b-105">例</span><span class="sxs-lookup"><span data-stu-id="1369b-105">Example</span></span>  
 <span data-ttu-id="1369b-106">次のコンソール アプリケーションで新しいテーブルを作成する、 **AdventureWorks**データベース。</span><span class="sxs-lookup"><span data-stu-id="1369b-106">The following console application creates a new table in the **AdventureWorks** database.</span></span> <span data-ttu-id="1369b-107">新しいテーブルには、という名前の列が含まれています。 **SalesID**とという XML 列を**SalesInfo**です。</span><span class="sxs-lookup"><span data-stu-id="1369b-107">The new table includes a column named **SalesID** and an XML column named **SalesInfo**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1369b-108">**AdventureWorks**既定では、SQL Server をインストールするときにサンプル データベースはインストールされません。</span><span class="sxs-lookup"><span data-stu-id="1369b-108">The **AdventureWorks** sample database is not installed by default when you install SQL Server.</span></span> <span data-ttu-id="1369b-109">SQL Server Setup を実行してインストールします。</span><span class="sxs-lookup"><span data-stu-id="1369b-109">You can install it by running SQL Server Setup.</span></span>  
  
 <span data-ttu-id="1369b-110">この例では、新しいテーブルに行を挿入するために <xref:System.Data.SqlClient.SqlCommand> オブジェクトを準備します。</span><span class="sxs-lookup"><span data-stu-id="1369b-110">The example prepares a <xref:System.Data.SqlClient.SqlCommand> object to insert a row in the new table.</span></span> <span data-ttu-id="1369b-111">保存されたファイルに必要な XML データを提供する、 **SalesInfo**列です。</span><span class="sxs-lookup"><span data-stu-id="1369b-111">A saved file provides the XML data needed for the **SalesInfo** column.</span></span>  
  
 <span data-ttu-id="1369b-112">この例を実行させるために必要なファイルを作成するには、プロジェクトと同じフォルダー内に新しいテキスト ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="1369b-112">To create the file needed for the example to run, create a new text file in the same folder as your project.</span></span> <span data-ttu-id="1369b-113">ファイルに MyTestStoreData.xml という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="1369b-113">Name the file MyTestStoreData.xml.</span></span> <span data-ttu-id="1369b-114">ファイルをメモ帳で開き、次のテキストをコピーして貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="1369b-114">Open the file in Notepad and copy and paste the following text:</span></span>  
  
```xml  
<StoreSurvey xmlns="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/StoreSurvey">  
  <AnnualSales>300000</AnnualSales>  
  <AnnualRevenue>30000</AnnualRevenue>  
  <BankName>International Bank</BankName>  
  <BusinessType>BM</BusinessType>  
  <YearOpened>1970</YearOpened>  
  <Specialty>Road</Specialty>  
  <SquareFeet>7000</SquareFeet>  
  <Brands>3</Brands>  
  <Internet>T1</Internet>  
  <NumberEmployees>2</NumberEmployees>  
</StoreSurvey>  
```  
  
```vb  
Imports System  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports System.Xml  
  
Module Module1  
    Sub Main()  
  
        Using connection As SqlConnection = New SqlConnection(GetConnectionString())  
        connection.Open()  
  
        ' Create a sample table (dropping first if it already  
        ' exists.)  
        Dim commandNewTable As String = _  
         "IF EXISTS (SELECT * FROM dbo.sysobjects " & _  
         "WHERE id = object_id(N'[dbo].[XmlDataTypeSample]') " & _  
         "AND OBJECTPROPERTY(id, N'IsUserTable') = 1) " & _  
         "DROP TABLE [dbo].[XmlDataTypeSample];" & _  
         "CREATE TABLE [dbo].[XmlDataTypeSample](" & _  
         "[SalesID] [int] IDENTITY(1,1) NOT NULL, " & _  
         "[SalesInfo] [xml])"  
  
        Dim commandAdd As New _  
         SqlCommand(commandNewTable, connection)  
        commandAdd.ExecuteNonQuery()  
  
        Dim commandText As String = _  
         "INSERT INTO [dbo].[XmlDataTypeSample] " & _  
           "([SalesInfo] ) " & _  
           "VALUES(@xmlParameter )"  
  
        Dim command As New SqlCommand(commandText, connection)  
  
        ' Read the saved XML document as a   
        ' SqlXml-data typed variable.  
        Dim newXml As SqlXml = _  
         New SqlXml(New XmlTextReader("MyTestStoreData.xml"))  
  
        ' Supply the SqlXml value for the value of the parameter.  
        command.Parameters.AddWithValue("@xmlParameter", newXml)  
  
        Dim result As Integer = command.ExecuteNonQuery()  
        Console.WriteLine(result & " row was added.")  
        Console.WriteLine("Press Enter to continue.")  
        Console.ReadLine()  
    End Using  
End Sub  
  
    Private Function GetConnectionString() As String  
        ' To avoid storing the connection string in your code,              
        ' you can retrieve it from a configuration file.   
        Return "Data Source=(local);Integrated Security=SSPI;" & _  
          "Initial Catalog=AdventureWorks"  
    End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
using System.Xml;  
using System.Data.SqlTypes;  
  
class Class1  
{  
    static void Main()  
    {  
        using (SqlConnection connection = new SqlConnection(GetConnectionString()))  
       {  
        connection.Open();  
        //  Create a sample table (dropping first if it already  
        //  exists.)  
  
        string commandNewTable =   
            "IF EXISTS (SELECT * FROM dbo.sysobjects " +   
            "WHERE id = " +  
                  "object_id(N'[dbo].[XmlDataTypeSample]') " +   
            "AND OBJECTPROPERTY(id, N'IsUserTable') = 1) " +   
            "DROP TABLE [dbo].[XmlDataTypeSample];" +   
            "CREATE TABLE [dbo].[XmlDataTypeSample](" +   
            "[SalesID] [int] IDENTITY(1,1) NOT NULL, " +   
            "[SalesInfo] [xml])";  
        SqlCommand commandAdd =   
                   new SqlCommand(commandNewTable, connection);  
        commandAdd.ExecuteNonQuery();  
        string commandText =   
            "INSERT INTO [dbo].[XmlDataTypeSample] " +   
            "([SalesInfo] ) " +   
            "VALUES(@xmlParameter )";  
        SqlCommand command =   
                  new SqlCommand(commandText, connection);  
  
        //  Read the saved XML document as a   
        //  SqlXml-data typed variable.  
        SqlXml newXml =   
            new SqlXml(new XmlTextReader("MyTestStoreData.xml"));  
  
        //  Supply the SqlXml value for the value of the parameter.  
        command.Parameters.AddWithValue("@xmlParameter", newXml);  
  
        int result = command.ExecuteNonQuery();  
        Console.WriteLine(result + " row was added.");  
        Console.WriteLine("Press Enter to continue.");  
        Console.ReadLine();  
    }  
  }  
  
    private static string GetConnectionString()  
    {  
        // To avoid storing the connection string in your code,              
        // you can retrieve it from a configuration file.   
        return "Data Source=(local);Integrated Security=true;" +  
        "Initial Catalog=AdventureWorks; ";  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="1369b-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="1369b-115">See Also</span></span>  
 <xref:System.Data.SqlTypes.SqlXml>  
 [<span data-ttu-id="1369b-116">SQL Server における XML データ</span><span class="sxs-lookup"><span data-stu-id="1369b-116">XML Data in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/xml-data-in-sql-server.md)  
 [<span data-ttu-id="1369b-117">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="1369b-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
