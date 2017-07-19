---
title: "DataRow の削除 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c34f531d-4b9b-4071-b2d7-342c402aa586
caps.latest.revision: 5
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 5
---
# DataRow の削除
<xref:System.Data.DataTable> オブジェクトから <xref:System.Data.DataRow> オブジェクトを削除するには、<xref:System.Data.DataRowCollection> オブジェクトの **Remove** メソッドと **DataRow** オブジェクトの <xref:System.Data.DataRow.Delete%2A> メソッドの 2 つのメソッドを使用できます。  <xref:System.Data.DataRowCollection.Remove%2A> メソッドが **DataRowCollection** から **DataRow** を削除するのに対し、<xref:System.Data.DataRow.Delete%2A> メソッドは削除対象の行をマークするだけです。  実際の削除は、アプリケーションが **AcceptChanges** メソッドを呼び出すと実行されます。  <xref:System.Data.DataRow.Delete%2A> を使用すると、行を実際に削除する前に、削除対象としてどの行がマークされているかをプログラムによってチェックできます。  削除対象としてマークされている行の <xref:System.Data.DataRow.RowState%2A> プロパティは、<xref:System.Data.DataRow.Delete%2A> に設定されています。  
  
 <xref:System.Data.DataRowCollection> オブジェクトを反復処理している間は、foreach ループで <xref:System.Data.DataRow.Delete%2A> も <xref:System.Data.DataRowCollection.Remove%2A> も呼び出すことはできません。  <xref:System.Data.DataRow.Delete%2A> または <xref:System.Data.DataRowCollection.Remove%2A> はコレクションの状態を変更します。  
  
 **DataAdapter** およびリレーショナル データ ソースに関連して <xref:System.Data.DataSet> または **DataTable** を使用するときは、**DataRow** の **Delete** メソッドを使用して行を削除します。  **Delete** メソッドは、**DataSet** または **DataTable** の行を **Deleted** としてマークしますが、その行を削除しません。  代わりに、**DataAdapter** が **Deleted** としてマークされた行を検出したときに **DeleteCommand** メソッドを実行して、データ ソースの該当する行を削除します。  その後、**AcceptChanges** メソッドを使用して、その行を永続的に削除できます。  **Remove** を使用して行を削除すると、行はテーブルから完全に削除されますが、**DataAdapter** はデータ ソースの該当する行を削除しません。  
  
 **DataRowCollection** の **Remove** メソッドが **DataRow** を引数として受け取り、その行をコレクションから削除する例を次に示します。  
  
```vb  
workTable.Rows.Remove(workRow)  
  
```  
  
```csharp  
workTable.Rows.Remove(workRow);  
```  
  
 これに対して、**DataRow** の **Delete** メソッドを呼び出して、該当する行の **RowState** を **Deleted** に変更する例を次に示します。  
  
```vb  
workRow.Delete  
  
```  
  
```csharp  
workRow.Delete();  
```  
  
 行を削除対象としてマークしてから **DataTable** オブジェクトの **AcceptChanges** メソッドを呼び出すと、その行が **DataTable** から削除されます。  これに対して、**RejectChanges** を呼び出すと、行の **RowState** はその行が **Deleted** としてマークされる前の状態に戻ります。  
  
> [!NOTE]
>  **DataRow** の **RowState** が **Added** である場合、つまりテーブルに行が追加された直後の状態の場合に、その行を **Deleted** としてマークすると、その行はテーブルから削除されます。  
  
## 参照  
 <xref:System.Data.DataRow>   
 <xref:System.Data.DataRowCollection>   
 <xref:System.Data.DataTable>   
 [DataTable 内のデータの操作](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)