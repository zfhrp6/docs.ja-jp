---
title: "AcceptChange と RejectChange"
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
ms.assetid: e2d1a6fe-31f9-4b83-9728-06c406a3394e
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 72868cb81c8abb988dd765f4b3ed68bf3c4a71da
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="acceptchanges-and-rejectchanges"></a>AcceptChange と RejectChange
内のデータに加えられた変更の精度を確認した後、<xref:System.Data.DataTable>を使用して変更を受け入れることができます、<xref:System.Data.DataRow.AcceptChanges%2A>のメソッド、 <xref:System.Data.DataRow>、 <xref:System.Data.DataTable>、または<xref:System.Data.DataSet>、セットは、**現在**行値を**元**設定は、値を**RowState**プロパティを**Unchanged**です。 いずれかをクリアして承認または拒否する変更**RowError**情報と設定、 **HasErrors**プロパティを**false**です。 変更を受け入れるかまたは拒否した場合、データ ソース内で実行中の更新操作にも影響することがあります。 詳細については、次を参照してください。 [Dataadapter によるデータ ソースを更新](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)です。  
  
 外部キー制約が存在しない場合、 **DataTable**、変更が受理されるかを使用して拒否された**AcceptChanges**と**RejectChanges** の子の行に反映されます**DataRow**によると、 **ForeignKeyConstraint.AcceptRejectRule**です。 詳細については、次を参照してください。 [DataTable の制約](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md)です。  
  
 行にエラーがあるかどうかをチェックし、必要に応じてエラーを解決し、エラーを解決できない場合にはその行を拒否する例を次に示します。 解決エラー、メモ、 **RowError**値が空の文字列にリセット原因、 **HasErrors**設定するプロパティを**false**です。 エラーのあるすべての行が解決済みまたは拒否されると、ときに**AcceptChanges**全体のすべての変更を受け入れるために呼び出される**DataTable**です。  
  
```vb  
If workTable.HasErrors Then  
  Dim errRow As DataRow  
  
  For Each errRow in workTable.GetErrors()  
  
    If errRow.RowError = "Total cannot exceed 1000." Then  
      errRow("Total") = 1000  
      errRow.RowError = ""    ' Clear the error.  
    Else  
      errRow.RejectChanges()  
    End If  
  Next  
End If  
  
workTable.AcceptChanges()  
```  
  
```csharp  
if (workTable.HasErrors)  
{  
  
  foreach (DataRow errRow in workTable.GetErrors())  
  {  
    if (errRow.RowError == "Total cannot exceed 1000.")  
    {  
      errRow["Total"] = 1000;  
      errRow.RowError = "";    // Clear the error.  
    }  
    else  
      errRow.RejectChanges();  
  }  
}  
  
workTable.AcceptChanges();  
```  
  
## <a name="see-also"></a>参照  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 [DataTable 内のデータの操作](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
