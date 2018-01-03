---
title: "DataRow の削除"
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
ms.assetid: c34f531d-4b9b-4071-b2d7-342c402aa586
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 7f20fdebe101665e681597db0c55b7ced7853f9d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="datarow-deletion"></a>DataRow の削除
削除に使用できる 2 つの方法がある、<xref:System.Data.DataRow>オブジェクトから、<xref:System.Data.DataTable>オブジェクト:**削除**のメソッド、<xref:System.Data.DataRowCollection>オブジェクト、および<xref:System.Data.DataRow.Delete%2A>のメソッド、 **DataRow**オブジェクト。 一方、<xref:System.Data.DataRowCollection.Remove%2A>メソッドの削除、 **DataRow**から、 **DataRowCollection**、<xref:System.Data.DataRow.Delete%2A>メソッドは削除対象の行をマークするだけです。 アプリケーションを呼び出すときに実際の削除が発生した、 **AcceptChanges**メソッドです。 <xref:System.Data.DataRow.Delete%2A> を使用すると、行を実際に削除する前に、削除対象としてどの行がマークされているかをプログラムによってチェックできます。 削除対象としてマークされている行の <xref:System.Data.DataRow.RowState%2A> プロパティは、<xref:System.Data.DataRow.Delete%2A> に設定されています。  
  
 <xref:System.Data.DataRow.Delete%2A> オブジェクトを反復処理している間は、foreach ループで <xref:System.Data.DataRowCollection.Remove%2A> も <xref:System.Data.DataRowCollection> も呼び出すことはできません。 <xref:System.Data.DataRow.Delete%2A> または <xref:System.Data.DataRowCollection.Remove%2A> はコレクションの状態を変更します。  
  
 使用する場合、<xref:System.Data.DataSet>または**DataTable**と組み合わせて、 **DataAdapter**とを使用して、リレーショナル データ ソース、**削除**のメソッド、 **DataRow**行を削除します。 **削除**メソッドとして行をマーク**Deleted**で、**データセット**または**DataTable**は削除されません。 代わりに、 **DataAdapter**としてマークされている行を検出する**Deleted**を実行してその**DeleteCommand**データ ソースの行を削除するメソッドをします。 行、完全に削除できますを使用して、 **AcceptChanges**メソッドです。 使用する場合**削除**行を削除する、行は、テーブルから完全に削除されるが、 **DataAdapter**データ ソースの行は削除されません。  
  
 **削除**のメソッド、 **DataRowCollection**は、 **DataRow**を引数として、次の例に示すように、コレクションから削除します。  
  
```vb  
workTable.Rows.Remove(workRow)  
```  
  
```csharp  
workTable.Rows.Remove(workRow);  
```  
  
 これに対し、次の例を呼び出す方法、**削除**メソッドを**DataRow**を変更するその**RowState**に**Deleted**.  
  
```vb  
workRow.Delete  
```  
  
```csharp  
workRow.Delete();  
```  
  
 行が削除対象としてマークしを呼び出す場合、 **AcceptChanges**のメソッド、 **DataTable**から、行が削除されるオブジェクト、 **DataTable**です。 呼び出す場合とは異なり、 **RejectChanges**、 **RowState**としてマークされる前に元に戻します、行の**Deleted**です。  
  
> [!NOTE]
>  場合、 **RowState**の**DataRow**は**Added**、つまり直前が追加されたテーブル、およびとしてマークされます**Deleted**はテーブルから削除します。  
  
## <a name="see-also"></a>参照  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataRowCollection>  
 <xref:System.Data.DataTable>  
 [DataTable 内のデータの操作](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
