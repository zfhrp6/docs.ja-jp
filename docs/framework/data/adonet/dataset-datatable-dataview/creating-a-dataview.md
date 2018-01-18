---
title: "DataView の作成"
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
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 1a8529c317025dbabd9c7467557b244b2f452a77
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="creating-a-dataview"></a>DataView の作成
<xref:System.Data.DataView> は 2 とおりの方法で作成できます。 使用することができます、 **DataView**コンス トラクターを作成できますへの参照、<xref:System.Data.DataTable.DefaultView%2A>のプロパティ、<xref:System.Data.DataTable>です。 **DataView**コンス トラクターは空、またはいずれかがかかることができます、 **DataTable**引数を 1 つとして、または**DataTable**フィルター条件、並べ替え基準、および行と共に状態フィルター。 使用する追加の引数の詳細については、 **DataView**を参照してください[並べ替え/フィルター データ](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)です。  
  
 のインデックス、 **DataView**ときにも組み込まれて、 **DataView**が作成されるときのいずれかと、**並べ替え**、 **RowFilter**、または**RowStateFilter**プロパティが変更されると、最適なパフォーマンスを実現するには、最初の並べ替え順序を指定するかを作成するときに、コンス トラクターの引数としてフィルター条件を**DataView**です。 作成する、 **DataView**並べ替えまたはフィルターの条件を指定しを設定せず、**並べ替え**、 **RowFilter**、または**RowStateFilter**プロパティが、その後、インデックスの構築には、少なくとも 2 回: したらときに、 **DataView**作成されると、再度並べ替えまたはフィルターのプロパティのいずれかが変更されました。  
  
 作成する場合、 **DataView**を任意の引数を受け取らないコンス トラクターを使用していないことができますを使用する、 **DataView**を設定するまで、**テーブル**プロパティ.  
  
 次のコード例を作成する方法を示しています、 **DataView**を使用して、 **DataView**コンス トラクターです。 A **RowFilter**、**並べ替え**列、および**DataViewRowState**と共に提供される、 **DataTable**です。  
  
```vb  
Dim custDV As DataView = New DataView(custDS.Tables("Customers"), _  
    "Country = 'USA'", _  
    "ContactName", _  
    DataViewRowState.CurrentRows)  
```  
  
```csharp  
DataView custDV = new DataView(custDS.Tables["Customers"],   
    "Country = 'USA'",   
    "ContactName",   
    DataViewRowState.CurrentRows);  
```  
  
 次のコード例は、既定値への参照を取得する方法を示します**DataView**の**DataTable**を使用して、 **DefaultView**テーブルのプロパティです。  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## <a name="see-also"></a>参照  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [データの並べ替えとフィルター処理](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)  
 [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
