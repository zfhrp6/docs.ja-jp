---
title: "型指定された DataSet のクエリ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: ad712fa1-2baf-462a-b163-574cce6d376a
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: bd78b4f47d7f48d7b4cbacdf53140758a05b7869
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="querying-typed-datasets"></a>型指定された DataSet のクエリ
アプリケーションのデザイン時に <xref:System.Data.DataSet> のスキーマがわかっている場合は、<xref:System.Data.DataSet> を使用するときに、型指定された [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] を用いることをお勧めします。 型指定された<xref:System.Data.DataSet>から派生したクラスには、<xref:System.Data.DataSet>です。 したがって、型指定されたデータセットは <xref:System.Data.DataSet> のすべてのメソッド、イベント、およびプロパティを継承します。 さらに、型指定された<xref:System.Data.DataSet>厳密に型指定されたメソッド、イベント、およびプロパティを提供します。 つまり、コレクションベースのメソッドを使用せずに名前でテーブルおよび列にアクセスできます。 これによりクエリが簡素化され、読みやすくなります。 詳細については、次を参照してください。[型指定されたデータセット](../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)です。  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]型指定されたに対するクエリもサポート<xref:System.Data.DataSet>です。 型指定された<xref:System.Data.DataSet>、ジェネリックを使用する必要はありません<xref:System.Data.DataRowExtensions.Field%2A>メソッドまたは<xref:System.Data.DataRowExtensions.SetField%2A>列データにアクセスするメソッド。  型情報が含まれているために、プロパティ名はコンパイル時に使用できる、<xref:System.Data.DataSet>です。 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]実行時の代わりに、コードがコンパイルされるときに、型の不一致エラーがキャッチできるように、適切な型として列の値へのアクセスを提供します。  
  
 型指定された <xref:System.Data.DataSet> に対してクエリを実行するには、[!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)] のデータセット デザイナーを使用してあらかじめクラスを生成しておく必要があります。  詳細については、[データセットの作成と構成](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio)に関するページを参照してください。  
  
## <a name="example"></a>例  
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
  
## <a name="see-also"></a>関連項目  
 [Dataset のクエリ](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 [テーブルにまたがるクエリ](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)  
 [単一テーブルのクエリ](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)
