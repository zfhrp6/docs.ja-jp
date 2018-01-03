---
title: "DataView の変更"
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
ms.assetid: 697a3991-b660-4a5a-8a54-1a2304ff158e
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 921707b07f1e8c8a9208df7de74512325f3027d2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="modifying-dataviews"></a>DataView の変更
<xref:System.Data.DataView> を使用して、データ行を基になるテーブルに追加、削除、または変更できます。 使用する機能、 **DataView**基になるテーブル内のデータを変更するのには 3 つのブール型プロパティのいずれかの設定によって制御されます、 **DataView**です。 この 3 つのプロパティとは、<xref:System.Data.DataView.AllowNew%2A>、<xref:System.Data.DataView.AllowEdit%2A> および <xref:System.Data.DataView.AllowDelete%2A> です。 設定されている**true**既定です。  
  
 場合**AllowNew**は**true**、使用することができます、<xref:System.Data.DataView.AddNew%2A>のメソッド、 **DataView**を新規作成する<xref:System.Data.DataRowView>です。 新しい行がないことが実際には、基になる追加<xref:System.Data.DataTable>まで、<xref:System.Data.DataRowView.EndEdit%2A>のメソッド、 **DataRowView**と呼びます。 場合、<xref:System.Data.DataRowView.CancelEdit%2A>のメソッド、 **DataRowView**が呼び出されると、新しい行が破棄されます。 1 つだけを編集できることにも注意してください**DataRowView**一度にです。 呼び出す場合は、 **AddNew**または**BeginEdit**のメソッド、 **DataRowView**保留中の行が存在する間**EndEdit**で暗黙的に呼び出されると、保留中の行。 ときに**EndEdit**が呼び出されると、変更は適用、基になる**DataTable**でき、後でコミットされたかを使用して拒否された、 **AcceptChanges**または**RejectChanges**のメソッド、 **DataTable**、**データセット**、または**DataRow**オブジェクト。 場合**AllowNew**は**false**、呼び出した場合、例外がスローされます、 **AddNew**のメソッド、 **DataRowView**です。  
  
 場合**AllowEdit**は**true**の内容を変更することができます、 **DataRow**を介して、 **DataRowView**です。 使用して基になる行への変更を確認する**DataRowView.EndEdit**を使用して変更を拒否または**DataRowView.CancelEdit**です。 一度に編集できるのは 1 行だけです。 呼び出す場合は、 **AddNew**または**BeginEdit**のメソッド、 **DataRowView**保留中の行が存在する間**EndEdit**で暗黙的に呼び出される保留中の行。 ときに**EndEdit**が呼び出されるで提案された変更を配置している、**現在**行バージョンの基になる**DataRow**でき、後でコミットされたか、を使用して拒否されました。**AcceptChanges**または**RejectChanges**のメソッド、 **DataTable**、**データセット**、または**DataRow**オブジェクト。 場合**AllowEdit**は**false**、内の値を変更しようとする場合、例外がスローされます、 **DataView**です。  
  
 既存**DataRowView**が編集中、基になるイベント**DataTable**提案された変更をまだ生成されます。 呼び出す場合**EndEdit**または**CancelEdit**で、基になる**DataRow**、保留中の変更を適用またはかどうかに関係なくキャンセルは**EndEdit**または**CancelEdit**で呼び出されると、 **DataRowView**です。  
  
 場合**AllowDelete**は**true**から行を削除することができます、 **DataView**を使用して、**削除**のメソッド、 **DataView**または**DataRowView**オブジェクト、および行が削除されている場合、基になるから**DataTable**です。 後でコミットまたはを使用して削除を拒否する**AcceptChanges**または**RejectChanges**それぞれします。 場合**AllowDelete**は**false**、呼び出した場合、例外がスローされます、**削除**のメソッド、 **DataView**または**DataRowView**です。  
  
 次のコード例を使用して無効になります、 **DataView**に削除の行の行を新しい行を使用して基になるテーブルを追加、 **DataView**です。  
  
```vb  
Dim custTable As DataTable = custDS.Tables("Customers")  
Dim custView As DataView = custTable.DefaultView  
custView.Sort = "CompanyName"  
  
custView.AllowDelete = False  
  
Dim newDRV As DataRowView = custView.AddNew()  
newDRV("CustomerID") = "ABCDE"  
newDRV("CompanyName") = "ABC Products"  
newDRV.EndEdit()  
```  
  
```csharp  
DataTable custTable = custDS.Tables["Customers"];  
DataView custView = custTable.DefaultView;  
custView.Sort = "CompanyName";  
  
custView.AllowDelete = false;  
  
DataRowView newDRV = custView.AddNew();  
newDRV["CustomerID"] = "ABCDE";  
newDRV["CompanyName"] = "ABC Products";  
newDRV.EndEdit();  
```  
  
## <a name="see-also"></a>参照  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 <xref:System.Data.DataRowView>  
 [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
