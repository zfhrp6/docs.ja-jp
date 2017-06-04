---
title: "How to: Implement CopyToDataTable&lt;T&gt; Where the Generic Type T Is Not a DataRow | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b27b52cf-6172-485f-a75c-70ff9c5a2bd4
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# How to: Implement CopyToDataTable&lt;T&gt; Where the Generic Type T Is Not a DataRow
データ バインドには、しばしば <xref:System.Data.DataTable> オブジェクトが使用されます。  <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> メソッドは、クエリの結果を受け取り、そのデータを <xref:System.Data.DataTable> にコピーします。これをデータ バインドに利用できます。  ただし、<xref:System.Data.DataTableExtensions.CopyToDataTable%2A> メソッドは、ジェネリック パラメーター `T` が <xref:System.Data.DataRow> 型である <xref:System.Collections.Generic.IEnumerable%601> ソースに対してのみ作用します。  有用ではありますが、一連のスカラー型、匿名型を射影するクエリ、またはテーブルの結合を実行するクエリからは、テーブルを作成できません。  
  
 このトピックでは、<xref:System.Data.DataRow> 型以外のジェネリック パラメーター `T` を受け取る 2 つのカスタム `CopyToDataTable<T>` 拡張メソッドを実装する方法について説明します。  <xref:System.Collections.Generic.IEnumerable%601> ソースから <xref:System.Data.DataTable> を作成するロジックは、`ObjectShredder<T>` クラスに存在し、オーバーロードされた 2 つの `CopyToDataTable<T>` 拡張メソッドにラップされています。  `ObjectShredder<T>` クラスの `Shred` メソッドは、データが格納された <xref:System.Data.DataTable> を返し、<xref:System.Collections.Generic.IEnumerable%601> ソース、<xref:System.Data.DataTable>、および <xref:System.Data.LoadOption> 列挙型の 3 つの入力パラメーターを受け取ります。  返される <xref:System.Data.DataTable> の最初のスキーマは、`T` 型のスキーマに基づきます。  既存のテーブルを入力として指定する場合は、そのスキーマが、`T` 型のスキーマと矛盾がないようにする必要があります。  返されたテーブルでは、`T` 型のパブリック プロパティおよびパブリック フィールドが、それぞれ <xref:System.Data.DataColumn> に変換されます。  `T` から派生した型がソース シーケンスに含まれている場合は、返されるテーブルのスキーマが、あらゆる追加パブリック プロパティまたは追加パブリック フィールドに展開されます。  
  
 カスタム `CopyToDataTable<T>` メソッドの使用例については、「[Creating a DataTable From a Query](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md)」を参照してください。  
  
### カスタム CopyToDataTable\<T\> メソッドをアプリケーションに実装するには  
  
1.  `ObjectShredder<T>` クラスを実装して、<xref:System.Collections.Generic.IEnumerable%601> ソースから <xref:System.Data.DataTable> を作成します。  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#objectshredderclass)]
     [!code-vb[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#objectshredderclass)]  
  
2.  カスタム `CopyToDataTable<T>` 拡張メソッドをクラスに実装します。  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#customcopytodatatablemethods)]
     [!code-vb[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#customcopytodatatablemethods)]  
  
3.  `ObjectShredder<T>` クラスおよび `CopyToDataTable<T>` 拡張メソッドをアプリケーションに追加します。  
  
    ```vb  
    Module Module1  
        Sub Main()  
        ' Your application code using CopyToDataTable<T>.  
        End Sub  
    End Module  
  
    Public Module CustomLINQtoDataSetMethods  
    …  
    End Module  
  
    Public Class ObjectShredder(Of T)  
    …  
    End Class  
    ```  
  
4.  ```c#  
    class Program  
    {  
            static void Main(string[] args)  
            {  
               // Your application code using CopyToDataTable<T>.  
            }  
    }  
    public static class CustomLINQtoDataSetMethods  
    {  
    …  
    }  
    public class ObjectShredder<T>  
    {  
    …  
    }  
    ```  
  
## 参照  
 [Creating a DataTable From a Query](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md)   
 [Programming Guide](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)