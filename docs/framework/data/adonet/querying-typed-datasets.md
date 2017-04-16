---
title: "Querying Typed DataSets | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ad712fa1-2baf-462a-b163-574cce6d376a
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Querying Typed DataSets
アプリケーションのデザイン時に <xref:System.Data.DataSet> のスキーマがわかっている場合は、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] を使用するときに、型指定された <xref:System.Data.DataSet> を用いることをお勧めします。  型指定された <xref:System.Data.DataSet> とは、<xref:System.Data.DataSet> から派生するクラスのことです。  したがって、型指定されたデータセットは <xref:System.Data.DataSet> のすべてのメソッド、イベント、およびプロパティを継承します。  さらに、型指定された <xref:System.Data.DataSet> には、厳密に型指定されたメソッド、イベント、およびプロパティが用意されています。  つまり、コレクションベースのメソッドを使用せずに名前でテーブルおよび列にアクセスできます。  これによりクエリが簡素化され、読みやすくなります。  詳細については、「[型指定された DataSet](../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)」を参照してください。  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] は、型指定された <xref:System.Data.DataSet> に対するクエリもサポートしています。  型指定された <xref:System.Data.DataSet> を使用した場合、ジェネリック メソッドの <xref:System.Data.DataRowExtensions.Field%2A> または <xref:System.Data.DataRowExtensions.SetField%2A> を使って列データにアクセスする必要はありません。  <xref:System.Data.DataSet> に型情報が含まれているため、プロパティ名をコンパイル時に利用できます。[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] では、列の値に適切な型としてアクセスすることが可能となるため、型の不一致エラーは実行時ではなくコードのコンパイル時にキャッチされます。  
  
 型指定された <xref:System.Data.DataSet> に対してクエリを実行するには、[!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)] のデータセット デザイナーを使用してあらかじめクラスを生成しておく必要があります。  詳細については、「[方法 : 型指定されたデータセットを作成する](../Topic/Create%20and%20configure%20datasets%20in%20Visual%20Studio.md)」を参照してください。  
  
## 例  
 次の例では、型指定された <xref:System.Data.DataSet> に対してクエリを実行しています。  
  
```csharp  
var query = from o in orders  
            where o.OnlineOrderFlag == true  
            select new { o.SalesOrderID,  
                         o.OrderDate,  
                         o.SalesOrderNumber };  
  
foreach(var order in query)   
{  
    Console.WriteLine("{0}\t{1:d}\t{2}",   
order.SalesOrderID,   
order.OrderDate,   
order.SalesOrderNumber);  
}  
```  
  
```vb  
Dim orders = ds.Tables("SalesOrderHeader")  
  
Dim query = _  
       From o In orders _  
       Where o.OnlineOrderFlag = True _  
       Select New {SalesOrderID := o.SalesOrderID, _  
                   OrderDate := o.OrderDate, _  
                   SalesOrderNumber := o.SalesOrderNumber}  
  
For Each Dim onlineOrder In query  
 Console.WriteLine("{0}\t{1:d}\t{2}", _  
 onlineOrder.SalesOrderID, _  
 onlineOrder.OrderDate, _  
 onlineOrder.SalesOrderNumber)  
Next  
```  
  
## 参照  
 [Querying DataSets](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)   
 [Cross\-Table Queries](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)   
 [Single\-Table Queries](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)