---
title: "スキーマの制限 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# スキーマの制限
**GetSchema** メソッドの 2 番目のオプション パラメーターは、返されるスキーマ情報の量を制限するために使用される制限で、文字列の配列として **GetSchema** メソッドに渡されます。  配列での位置により、渡すことができる値が決定します。これは、制限の番号に相当します。  
  
 たとえば、次の表は、.NET Framework Data Provider for SQL Server を使用して、"Tables" スキーマ コレクションによりサポートされる制限を示しています。  SQL Server スキーマ コレクションの追加の制限をこのトピックの終わりに示します。  
  
|制限の名前|パラメーター名|制限の既定値|制限の番号|  
|-----------|-------------|------------|-----------|  
|Catalog|@Catalog|TABLE\_CATALOG|1|  
|オーナー|@Owner|TABLE\_SCHEMA|2|  
|テーブル|@Name|TABLE\_NAME|3|  
|TableType|@TableType|TABLE\_TYPE|4|  
  
## 制限値の指定  
 "Tables" スキーマ コレクションの制限の 1 つを使用するには、4 つの要素を使って文字列の配列を作成してから、制限の番号と一致する要素内に値を配置します。  たとえば、**GetSchema** メソッドにより返されるテーブルを、"Sales" スキーマ内のテーブルのみに制限するには、**GetSchema** メソッドに渡す前に、配列の 2 番目の要素を "Sales" に設定します。  
  
> [!NOTE]
>  `SqlClient` と `OracleClient` の制限のコレクションには、追加の `ParameterName` 列があります。  制限の既定の列は、下位互換性のために存在してはいますが、現在は無視されています。  制限の値を指定する場合、文字列置換ではなく、パラメーター付きのクエリを使って、SQL への注入攻撃のリスクを最小限にする必要があります。  
  
> [!NOTE]
>  配列内の要素数は、指定したスキーマ コレクションでサポートされる制限数以下にする必要があります。そうでない場合、<xref:System.ArgumentException> がスローされます。  制限は最大数よりも小さい場合があります。  指定されていない制限は、null \(無制限\) と見なされます。  
  
 .NET Framework マネージ プロバイダーでは、"Restrictions" という制限のスキーマ コレクションの名前を指定して **GetSchema** メソッドを呼び出すことにより、サポートされる制限の一覧を特定します。  これにより、コレクション名の一覧、制限の名前、既定の制限値、および制限の番号と共に、<xref:System.Data.DataTable> が返されます。  
  
### 例  
 .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> クラスの <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> メソッドを使って、**AdventureWorks** サンプル データベースに含まれるすべてのテーブルに関するスキーマ情報を取得し、返される情報を "Sales" スキーマ内のテーブルのみに制限する方法について、いくつかの例を次に示します。  
  
 \[Visual Basic\]  
  
```  
Imports System.Data.SqlClient  
  
Module Module1  
Sub Main()  
  Dim connectionString As String = _  
    "Data Source=(local);Database=AdventureWorks;" & _  
       "Integrated Security=true;";  
  
  Dim restrictions(3) As String  
  Using connection As New SqlConnection(connectionString)  
    connection.Open()  
  
    'Specify the restrictions.  
    restrictions(1) = "Sales"  
    Dim table As DataTable = connection.GetSchema("Tables", _  
       restrictions)  
  
    ' Display the contents of the table.  
      For Each row As DataRow In table.Rows  
         For Each col As DataColumn In table.Columns  
            Console.WriteLine("{0} = {1}", col.ColumnName, row(col))  
         Next  
         Console.WriteLine("============================")  
      Next  
    Console.WriteLine("Press any key to continue.")  
    Console.ReadKey()  
  End Using  
End Sub  
End Module  
```  
  
 \[C\#\]  
  
```  
using System;  
using System.Data;  
using System.Data.SqlClient;  
  
class Program  
{  
  static void Main()  
  {  
    string connectionString =   
       "Data Source=(local);Database=AdventureWorks;" +  
       "Integrated Security=true;";  
    using (SqlConnection connection =  
       new SqlConnection(connectionString))  
    {  
        connection.Open();  
  
        // Specify the restrictions.  
        string[] restrictions = new string[4];  
        restrictions[1] = "Sales";  
        System.Data.DataTable table = connection.GetSchema(  
          "Tables", restrictions);  
  
        // Display the contents of the table.  
        foreach (System.Data.DataRow row in table.Rows)  
        {  
            foreach (System.Data.DataColumn col in table.Columns)  
            {  
                Console.WriteLine("{0} = {1}",   
                  col.ColumnName, row[col]);  
            }  
            Console.WriteLine("============================");  
        }  
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
  
## SQL Server スキーマの制限  
 次の表に、SQL Server スキーマ コレクションの制限を示します。  
  
### Users  
  
|制限の名前|パラメーター名|制限の既定値|制限の番号|  
|-----------|-------------|------------|-----------|  
|User\_Name|@Name|name|1|  
  
### Databases  
  
|制限の名前|パラメーター名|制限の既定値|制限の番号|  
|-----------|-------------|------------|-----------|  
|名前|@Name|名前|1|  
  
### \[テーブル\]  
  
|制限の名前|パラメーター名|制限の既定値|制限の番号|  
|-----------|-------------|------------|-----------|  
|Catalog|@Catalog|TABLE\_CATALOG|1|  
|オーナー|@Owner|TABLE\_SCHEMA|2|  
|テーブル|@Name|TABLE\_NAME|3|  
|TableType|@TableType|TABLE\_TYPE|4|  
  
### 列  
  
|制限の名前|パラメーター名|制限の既定値|制限の番号|  
|-----------|-------------|------------|-----------|  
|Catalog|@Catalog|TABLE\_CATALOG|1|  
|オーナー|@Owner|TABLE\_SCHEMA|2|  
|テーブル|@Table|TABLE\_NAME|3|  
|Column|@Column|COLUMN\_NAME|4|  
  
### StructuredTypeMembers  
  
|制限の名前|パラメーター名|制限の既定値|制限の番号|  
|-----------|-------------|------------|-----------|  
|Catalog|@Catalog|TABLE\_CATALOG|1|  
|オーナー|@Owner|TABLE\_SCHEMA|2|  
|テーブル|@Table|TABLE\_NAME|3|  
|Column|@Column|COLUMN\_NAME|4|  
  
### ビュー  
  
|制限の名前|パラメーター名|制限の既定値|制限の番号|  
|-----------|-------------|------------|-----------|  
|Catalog|@Catalog|TABLE\_CATALOG|1|  
|オーナー|@Owner|TABLE\_SCHEMA|2|  
|テーブル|@Table|TABLE\_NAME|3|  
  
### ViewColumns  
  
|制限の名前|パラメーター名|制限の既定値|制限の番号|  
|-----------|-------------|------------|-----------|  
|Catalog|@Catalog|VIEW\_CATALOG|1|  
|オーナー|@Owner|VIEW\_SCHEMA|2|  
|テーブル|@Table|VIEW\_NAME|3|  
|Column|@Column|COLUMN\_NAME|4|  
  
### ProcedureParameters  
  
|制限の名前|パラメーター名|制限の既定値|制限の番号|  
|-----------|-------------|------------|-----------|  
|Catalog|@Catalog|SPECIFIC\_CATALOG|1|  
|オーナー|@Owner|SPECIFIC\_SCHEMA|2|  
|名前|@Name|SPECIFIC\_NAME|3|  
|パラメーター|@Parameter|PARAMETER\_NAME|4|  
  
### 手順  
  
|制限の名前|パラメーター名|制限の既定値|制限の番号|  
|-----------|-------------|------------|-----------|  
|Catalog|@Catalog|SPECIFIC\_CATALOG|1|  
|オーナー|@Owner|SPECIFIC\_SCHEMA|2|  
|名前|@Name|SPECIFIC\_NAME|3|  
|種類|@Type|ROUTINE\_TYPE|4|  
  
### IndexColumns  
  
|制限の名前|パラメーター名|制限の既定値|制限の番号|  
|-----------|-------------|------------|-----------|  
|Catalog|@Catalog|db\_name\(\)|1|  
|オーナー|@Owner|user\_name\(\)|2|  
|テーブル|@Table|o.  name|3|  
|ConstraintName|@ConstraintName|x.  name|4|  
|Column|@Column|c.  name|5|  
  
### Indexes  
  
|制限の名前|パラメーター名|制限の既定値|制限の番号|  
|-----------|-------------|------------|-----------|  
|Catalog|@Catalog|db\_name\(\)|1|  
|オーナー|@Owner|user\_name\(\)|2|  
|テーブル|@Table|o.  name|3|  
  
### UserDefinedTypes  
  
|制限の名前|パラメーター名|制限の既定値|制限の番号|  
|-----------|-------------|------------|-----------|  
|assembly\_name|@AssemblyName|assemblies.  name|1|  
|udt\_name|@UDTName|types.assembly\_class|2|  
  
### ForeignKeys  
  
|制限の名前|パラメーター名|制限の既定値|制限の番号|  
|-----------|-------------|------------|-----------|  
|Catalog|@Catalog|CONSTRAINT\_CATALOG|1|  
|オーナー|@Owner|CONSTRAINT\_SCHEMA|2|  
|テーブル|@Table|TABLE\_NAME|3|  
|名前|@Name|CONSTRAINT\_NAME|4|  
  
## SQL Server 2008 スキーマの制限  
 次の表に、SQL Server 2008 スキーマ コレクションの制限を示します。  これらの制限は、.NET Framework 3.5 SP1 および SQL Server 2008 以降で有効です。  これらの制限は、以前のバージョンの .NET Framework および SQL Server ではサポートされません。  
  
### ColumnSetColumns  
  
|制限の名前|パラメーター名|制限の既定値|制限の番号|  
|-----------|-------------|------------|-----------|  
|Catalog|@Catalog|TABLE\_CATALOG|1|  
|オーナー|@Owner|TABLE\_SCHEMA|2|  
|テーブル|@Table|TABLE\_NAME|3|  
  
### AllColumns  
  
|制限の名前|パラメーター名|制限の既定値|制限の番号|  
|-----------|-------------|------------|-----------|  
|Catalog|@Catalog|TABLE\_CATALOG|1|  
|オーナー|@Owner|TABLE\_SCHEMA|2|  
|テーブル|@Table|TABLE\_NAME|3|  
|Column|@Column|COLUMN\_NAME|4|  
  
## 参照  
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)