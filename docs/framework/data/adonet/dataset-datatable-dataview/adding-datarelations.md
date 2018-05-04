---
title: DataRelation の追加
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a4a564fb-c1c4-4135-b6c2-b030e51195e4
ms.openlocfilehash: 451ee0eee466efca86345ea7112e9b178a2c66e2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="adding-datarelations"></a>DataRelation の追加
複数の <xref:System.Data.DataSet> オブジェクトを含む <xref:System.Data.DataTable> では、<xref:System.Data.DataRelation> オブジェクトを使用して 1 つのテーブルを別のテーブルに関連付けたり、テーブル間を移動したり、関連付けたテーブルから子または親の行を戻したりできます。  
  
 作成に必要な引数、 **DataRelation**の名前は、 **DataRelation**作成されており、1 つ以上の配列<xref:System.Data.DataColumn>親と子として機能する列への参照リレーションシップの列です。 作成した後、 **DataRelation**テーブル間を移動して値の取得に使用することができます。  
  
 追加する、 **DataRelation**を<xref:System.Data.DataSet>追加すると、既定では、<xref:System.Data.UniqueConstraint>親テーブルに、<xref:System.Data.ForeignKeyConstraint>する子テーブルにします。 これらの既定の制約の詳細については、次を参照してください。 [DataTable の制約](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md)です。  
  
 次のコード例を作成、 **DataRelation** 2 つを使用して<xref:System.Data.DataTable>内のオブジェクト、<xref:System.Data.DataSet>です。 各<xref:System.Data.DataTable>という名前の列を含む**CustID**、2 つの間のリンクとして機能する<xref:System.Data.DataTable>オブジェクト。 この例は、1 つを追加**DataRelation**に、**リレーション**のコレクション、<xref:System.Data.DataSet>です。 この例の最初の引数の名前を指定する、 **DataRelation**作成中です。 2 番目の引数は、親を設定します。 **DataColumn** 3 番目の引数、子の設定と**DataColumn**です。  
  
```vb  
customerOrders.Relations.Add("CustOrders", _  
  customerOrders.Tables("Customers").Columns("CustID"), _  
  customerOrders.Tables("Orders").Columns("CustID"))  
```  
  
```csharp  
customerOrders.Relations.Add("CustOrders",  
  customerOrders.Tables["Customers"].Columns["CustID"],  
  customerOrders.Tables["Orders"].Columns["CustID"]);  
```  
  
 A **DataRelation**も、**入れ子になった**プロパティに設定すると**true**、親テーブルから関連する行の入れ子にする子テーブルの行が使用して XML 要素として書き込まれるときに<xref:System.Data.DataSet.WriteXml%2A>です。 詳しくは、「[DataSet での XML の使用](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [DataSet、DataTable、および DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
