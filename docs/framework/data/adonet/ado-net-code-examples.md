---
title: "ADO.NET のコード例 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c119657a-9ce6-4940-91e4-ac1d5f0d9584
caps.latest.revision: 7
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 7
---
# ADO.NET のコード例
このトピックにリストされたコードは、次の ADO.NET テクノロジを使用してデータベースからデータを取得する方法を示しています。  
  
-   ADO.NET データ プロバイダー:   
  
    -   [SqlClient](#_SqlClient) (`System.Data.SqlClient`)  
  
    -   [OleDb](#_OleDb) (`System.Data.OleDb`)  
  
    -   [Odbc](#_Odbc) (`System.Data.Odbc`)  
  
    -   [OracleClient](#_OracleClient) (`System.Data.OracleClient`)  
  
-   ADO.NET Entity Framework:  
  
    -   [LINQ to Entities](#_LINQ)  
  
    -   [型指定された ObjectQuery](#_QBM)  
  
    -   [EntityClient](#_EntityClient) (`System.Data.EntityClient`)  
  
-   [LINQ to SQL](#_LINQ2SQL)  
  
## <a name="adonet-data-provider-examples"></a>ADO.NET データ プロバイダーの例  
 以下に示した各コードは、ADO.NET データ プロバイダーを使用してデータベースからデータを取得する方法を示しています。 データは `DataReader` で返されます。 詳細については、次を参照してください。 [DataReader によるデータの取得](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md)します。  
  
<a name="_SqlClient"></a>   
### <a name="sqlclient"></a>SqlClient  
 このコード例は、Microsoft `Northwind` の [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] サンプル データベースに接続できることを前提としています。 このコードを作成、 <xref:System.Data.SqlClient.SqlCommand> Products テーブルから行を選択するを追加する、 <xref:System.Data.SqlClient.SqlParameter>を指定したパラメーター値では、この場合は 5 よりも大きな UnitPrice を持つ行に結果を制限します。 <xref:System.Data.SqlClient.SqlConnection>内に開かれ、`using`によってリソースが閉じられ、破棄、コードが終了したときに、ブロックします。 コードを使用してコマンドを実行する、 <xref:System.Data.SqlClient.SqlDataReader>、し、コンソール ウィンドウに結果を表示します。  
  
  [DataWorks SampleApp.SqlClient#1](../CodeSnippet/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient#1)]  
  
 [[Top]](#_TOP)  
  
<a name="_OleDb"></a>   
### <a name="oledb"></a>OleDb  
 このコード例は、Microsoft Access の Northwind サンプル データベースに接続できることを前提としています。 このコードを作成、 <xref:System.Data.OleDb.OleDbCommand> Products テーブルから行を選択するを追加する、 <xref:System.Data.OleDb.OleDbParameter>を指定したパラメーター値では、この場合は 5 よりも大きな UnitPrice を持つ行に結果を制限します。 <xref:System.Data.OleDb.OleDbConnection>内に開かれ、`using`によってリソースが閉じられ、破棄、コードが終了したときに、ブロックします。 コードを使用してコマンドを実行する、 <xref:System.Data.OleDb.OleDbDataReader>、し、コンソール ウィンドウに結果を表示します。  
  
  [DataWorks SampleApp.OleDb#1](../CodeSnippet/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb#1)]  
  
 [[Top]](#_TOP)  
  
<a name="_Odbc"></a>   
### <a name="odbc"></a>Odbc  
 このコード例は、Microsoft Access の Northwind サンプル データベースに接続できることを前提としています。 このコードを作成、 <xref:System.Data.Odbc.OdbcCommand> Products テーブルから行を選択するを追加する、 <xref:System.Data.Odbc.OdbcParameter>を指定したパラメーター値では、この場合は 5 よりも大きな UnitPrice を持つ行に結果を制限します。 <xref:System.Data.Odbc.OdbcConnection>内に開かれ、`using`によってリソースが閉じられ、破棄、コードが終了したときに、ブロックします。 使用してコマンドを実行、 <xref:System.Data.Odbc.OdbcDataReader>、し、コンソール ウィンドウに結果を表示します。  
  
<!-- TODO: review snippet reference  [!CODE [DataWorksSampleApp.Odbc#1](DataWorksSampleApp.Odbc#1)]  -->  
  
 [[Top]](#_TOP)  
  
<a name="_OracleClient"></a>   
### <a name="oracleclient"></a>OracleClient  
 このコード例では、Oracle サーバー上の DEMO.CUSTOMER との接続を前提としています。 また、System.Data.OracleClient.dll への参照を追加する必要があります。 コード内のデータを返す、 <xref:System.Data.OracleClient.OracleDataReader>します。  
  
  [DataWorks SampleApp.Oracle#1](../CodeSnippet/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle#1)]  
  
 [[Top]](#_TOP)  
  
## <a name="entity-framework-examples"></a>Entity Framework の例  
 以下に示した各コードは、エンティティ データ モデル (EDM) のエンティティを照会して、データ ソースからデータを取得する方法を示しています。 これらの例を使用して、 [Northwind モデル](http://msdn.microsoft.com/ja-jp/74521f8c-e974-48cb-8858-c08deff52638)します。 詳細については、次を参照してください。 [Entity Framework の概要](../../../../docs/framework/data/adonet/ef/overview.md)します。  
  
<a name="_LINQ"></a>   
### <a name="linq-to-entities"></a>LINQ to Entities  
 この例のコードは LINQ クエリを使用してデータをカテゴリ オブジェクトとして返します。これは、CategoryID および CategoryName プロパティのみを含んでいる匿名型として射影されます。 詳細については、次を参照してください。 [LINQ to Entities の概要](http://msdn.microsoft.com/ja-jp/86d87a27-c17a-45ac-b28d-72c8500333c6)します。  
  
```  
Option Explicit On  
Option Strict On  
  
Imports System  
Imports System.Linq  
Imports System.Data.Objects  
Imports NorthwindModel  
  
Class LinqSample  
    Public Shared Sub ExecuteQuery()  
        Using context As NorthwindEntities = New NorthwindEntities()  
            Try  
                Dim query = From category In context.Categories _  
                            Select New With _  
                            { _  
                                .categoryID = category.CategoryID, _  
                                .categoryName = category.CategoryName _  
                            }  
  
                For Each categoryInfo In query  
                    Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _  
                        categoryInfo.categoryID, categoryInfo.categoryName)  
                Next  
            Catch ex As Exception  
                Console.WriteLine(ex.Message)  
            End Try  
        End Using  
    End Sub  
End Class  
```  
  
 C# の場合:  
  
```  
using System;  
using System.Linq;  
using System.Data.Objects;  
using NorthwindModel;  
  
class LinqSample  
{  
    public static void ExecuteQuery()  
    {  
        using (NorthwindEntities context = new NorthwindEntities())  
        {  
            try  
            {  
                var query = from category in context.Categories  
                            select new  
                            {  
                                categoryID = category.CategoryID,  
                                categoryName = category.CategoryName  
                            };  
  
                foreach (var categoryInfo in query)  
                {  
                    Console.WriteLine("\t{0}\t{1}",  
                        categoryInfo.categoryID, categoryInfo.categoryName);  
                }  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine(ex.Message);  
            }  
        }  
    }  
}  
```  
  
 [[Top]](#_TOP)  
  
<a name="_QBM"></a>   
### <a name="typed-objectquery"></a>型指定された ObjectQuery  
 この例のコードを使用して、 <xref:System.Data.Objects.ObjectQuery%601>をカテゴリ オブジェクトとしてデータを返します。 詳細については、次を参照してください。[オブジェクト クエリ](http://msdn.microsoft.com/ja-jp/0768033c-876f-471d-85d5-264884349276)します。  
  
```  
Option Explicit On  
Option Strict On  
  
Imports System  
Imports System.Data.Objects  
Imports NorthwindModel  
  
Class ObjectQuerySample  
    Public Shared Sub ExecuteQuery()  
        Using context As NorthwindEntities = New NorthwindEntities()  
            Dim categoryQuery As ObjectQuery(Of Categories) = context.Categories  
  
            For Each category As Categories In _  
                categoryQuery.Execute(MergeOption.AppendOnly)  
                Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _  
                    category.CategoryID, category.CategoryName)  
            Next  
        End Using  
    End Sub  
End Class  
```  
  
 C# の場合:  
  
```  
using System;  
using System.Data.Objects;  
using NorthwindModel;  
  
class ObjectQuerySample  
{  
    public static void ExecuteQuery()  
    {  
        using (NorthwindEntities context = new NorthwindEntities())  
        {  
            ObjectQuery<Categories> categoryQuery = context.Categories;  
  
            foreach (Categories category in   
                categoryQuery.Execute(MergeOption.AppendOnly))  
            {  
                Console.WriteLine("\t{0}\t{1}",  
                    category.CategoryID, category.CategoryName);  
            }  
        }  
    }  
}  
```  
  
 [[Top]](#_TOP)  
  
<a name="_EntityClient"></a>   
### <a name="entityclient"></a>EntityClient  
 この例のコードを使用して、 <xref:System.Data.EntityClient.EntityCommand> Entity SQL クエリを実行します。 このクエリは、カテゴリ エンティティ型のインスタンスを示すレコードのリストを返します。 <xref:System.Data.EntityClient.EntityDataReader>結果セット内のデータ レコードにアクセスするために使用します。 詳細については、次を参照してください。 [Entity Framework 用の EntityClient プロバイダー](../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)します。  
  
```  
Option Explicit On  
Option Strict On  
  
Imports System  
Imports System.Data  
Imports System.Data.Common  
Imports System.Data.EntityClient  
Imports NorthwindModel  
  
Class EntityClientSample  
    Public Shared Sub ExecuteQuery()  
        Dim queryString As String = _  
            "SELECT c.CategoryID, c.CategoryName " & _  
                "FROM NorthwindEntities.Categories AS c"  
  
        Using conn As EntityConnection = _  
            New EntityConnection("name=NorthwindEntities")  
  
            Try  
                conn.Open()  
                Using query As EntityCommand = _  
                New EntityCommand(queryString, conn)  
                    Using rdr As DbDataReader = _  
                        query.ExecuteReader(CommandBehavior.SequentialAccess)  
                        While rdr.Read()  
                            Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _  
                                              rdr(0), rdr(1))  
                        End While  
                    End Using  
                End Using  
            Catch ex As Exception  
                Console.WriteLine(ex.Message)  
            End Try  
        End Using   
    End Sub  
End Class  
```  
  
 C# の場合:  
  
```  
using System;  
using System.Data;  
using System.Data.Common;  
using System.Data.EntityClient;  
using NorthwindModel;  
  
class EntityClientSample  
{  
    public static void ExecuteQuery()  
    {  
        string queryString =  
            @"SELECT c.CategoryID, c.CategoryName   
                FROM NorthwindEntities.Categories AS c";  
  
        using (EntityConnection conn =  
            new EntityConnection("name=NorthwindEntities"))  
        {  
            try  
            {  
                conn.Open();  
                using (EntityCommand query = new EntityCommand(queryString, conn))  
                {  
                    using (DbDataReader rdr =   
                        query.ExecuteReader(CommandBehavior.SequentialAccess))  
                    {  
                        while (rdr.Read())  
                        {  
                            Console.WriteLine("\t{0}\t{1}", rdr[0], rdr[1]);  
                        }  
                    }  
                }  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine(ex.Message);  
            }  
        }  
    }  
}  
```  
  
 [[Top]](#_TOP)  
  
<a name="_LINQ2SQL"></a>   
## <a name="linq-to-sql"></a>LINQ to SQL  
 この例のコードは LINQ クエリを使用してデータをカテゴリ オブジェクトとして返します。これは、CategoryID および CategoryName プロパティのみを含んでいる匿名型として射影されます。 この例は Northwind データ コンテキストを基にしています。 詳細については、次を参照してください。[概要](../../../../docs/framework/data/adonet/sql/linq/getting-started.md)します。  
  
```  
Option Explicit On  
Option Strict On  
  
Imports System  
Imports System.Collections.Generic  
Imports System.Linq  
Imports System.Text  
Imports Northwind  
  
Class LinqSqlSample  
    Public Shared Sub ExecuteQuery()  
        Using db As NorthwindDataContext = New NorthwindDataContext()  
            Try  
                Dim query = From category In db.Categories _  
                                Select New With _  
                                { _  
                                    .categoryID = category.CategoryID, _  
                                    .categoryName = category.CategoryName _  
                                }  
  
                For Each categoryInfo In query  
                    Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _  
                            categoryInfo.categoryID, categoryInfo.categoryName)  
                Next  
            Catch ex As Exception  
                Console.WriteLine(ex.Message)  
            End Try  
            End Using   
    End Sub  
End Class  
```  
  
 C# の場合:  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using Northwind;  
  
    class LinqSqlSample  
    {  
        public static void ExecuteQuery()  
        {  
            using (NorthwindDataContext db = new NorthwindDataContext())  
            {  
                try  
                {  
                    var query = from category in db.Categories  
                                select new  
                                {  
                                    categoryID = category.CategoryID,  
                                    categoryName = category.CategoryName  
                                };  
  
                    foreach (var categoryInfo in query)  
                    {  
                        Console.WriteLine("vbTab {0} vbTab {1}",  
                            categoryInfo.categoryID, categoryInfo.categoryName);  
                    }  
                }  
                catch (Exception ex)  
                {  
                    Console.WriteLine(ex.Message);  
                }  
            }  
        }  
    }  
```  
  
 [[Top]](#_TOP)  
  
## <a name="see-also"></a>関連項目  
 [ADO.NET の概要](../../../../docs/framework/data/adonet/ado-net-overview.md)   
 [取得して、ADO.NET でのデータを変更します。](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)   
 [データ アプリケーションの作成](../Topic/Creating%20Data%20Applications.md)   
 [Entity Data Model (Entity Framework Tasks) のクエリを実行します。](http://msdn.microsoft.com/ja-jp/187f1caa-e4d3-4e31-bd99-5d5c2b329c77)   
 [方法: 匿名型のオブジェクトを返すクエリの実行](http://msdn.microsoft.com/ja-jp/3b264025-e911-4d73-90ce-992d2b9d189d)   
 [ADO.NET マネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)