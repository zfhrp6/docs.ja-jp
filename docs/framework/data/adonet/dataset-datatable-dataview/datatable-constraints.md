---
title: "DataTable の制約"
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
ms.assetid: 27c9f2fd-f64d-4b4e-bbf6-1d24f47067cb
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 3767467024d6c0d0dfbf1be8829d77ba3f7fa439
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="datatable-constraints"></a>DataTable の制約
制約を使用すると、データの整合性を維持するために <xref:System.Data.DataTable> のデータを強制的に制限できます。 制約は、1 つの列または関連付けられた複数の列に対して自動的に適用される規則であり、行の値がなんらかの方法で変更されたときに実行されるアクションを決定します。 制約が適用時に、`System.Data.DataSet.EnforceConstraints`のプロパティ、<xref:System.Data.DataSet>は**true**です。 `EnforceConstraints` プロパティの設定方法のコード例については、<xref:System.Data.DataSet.EnforceConstraints%2A> のリファレンス トピックを参照してください。  
  
 ADO.NET には、<xref:System.Data.ForeignKeyConstraint> と <xref:System.Data.UniqueConstraint> の 2 種類の制約があります。 既定では、両方の制約が自動的に作成を追加して 2 つ以上のテーブル間のリレーションシップを作成するときに、<xref:System.Data.DataRelation>を**データセット**です。 指定してこの動作を無効にするただし、 **createConstraints** = **false**リレーションシップを作成するときにします。  
  
## <a name="foreignkeyconstraint"></a>ForeignKeyConstraint  
 A **ForeignKeyConstraint**更新および削除を関連テーブルを反映する方法に関する規則が適用されます。 たとえば、1 つのテーブルの行の値が更新または削除すると同じ値もで使用される 1 つか複数の関連するテーブル、 **ForeignKeyConstraint**関連テーブルでの動作を決定します。  
  
 <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A>と<xref:System.Data.ForeignKeyConstraint.UpdateRule%2A>のプロパティ、 **ForeignKeyConstraint**ユーザーを削除するか、関連テーブルの行を更新しようとしたときに実行されるアクションを定義します。 次の表に、さまざまな設定に使用できる、 **DeleteRule**と**UpdateRule**のプロパティ、 **ForeignKeyConstraint**です。  
  
|規則の設定|説明|  
|------------------|-----------------|  
|**Cascade**|関連付けられている行を削除または更新します。|  
|**SetNull**|関連付けられている行の値を設定**DBNull**です。|  
|**SetDefault**|関連付けられている行の値を既定値に設定します。|  
|**None**|関連付けられている行に対してアクションは実行しません。 既定値です。|  
  
 A **ForeignKeyConstraint**制限することができますへの変更の反映させたり、関連列です。 設定されたプロパティによって、 **ForeignKeyConstraint** 、列の場合、 **EnforceConstraints**のプロパティ、**データセット**は**true**、親の行で特定の操作を実行すると、例外。 たとえば場合、 **DeleteRule**のプロパティ、 **ForeignKeyConstraint**は**None**子行がある場合、親の行を削除できません。  
  
 1 つの列間または配列を使用して列の間の外部キー制約を作成することができます、 **ForeignKeyConstraint**コンス トラクターです。 その結果を渡す**ForeignKeyConstraint**オブジェクトを**追加**メソッド テーブルの**制約**プロパティとは、 **ConstraintCollection**. いくつかのオーバー ロードにコンス トラクターの引数を渡すことも、**追加**のメソッド、 **ConstraintCollection**を作成する、 **ForeignKeyConstraint**です。  
  
 作成するときに、 **ForeignKeyConstraint**を渡すことができます、 **DeleteRule**と**UpdateRule**するか、引数としてコンス トラクターに値としてのプロパティとして設定できます、次の例 (ここで、 **DeleteRule**に値が設定されている**None**)。  
  
```vb  
Dim custOrderFK As ForeignKeyConstraint = New ForeignKeyConstraint("CustOrderFK", _  
  custDS.Tables("CustTable").Columns("CustomerID"), _  
  custDS.Tables("OrdersTable").Columns("CustomerID"))  
custOrderFK.DeleteRule = Rule.None    
' Cannot delete a customer value that has associated existing orders.  
custDS.Tables("OrdersTable").Constraints.Add(custOrderFK)  
```  
  
```csharp  
ForeignKeyConstraint custOrderFK = new ForeignKeyConstraint("CustOrderFK",  
  custDS.Tables["CustTable"].Columns["CustomerID"],   
  custDS.Tables["OrdersTable"].Columns["CustomerID"]);  
custOrderFK.DeleteRule = Rule.None;    
// Cannot delete a customer value that has associated existing orders.  
custDS.Tables["OrdersTable"].Constraints.Add(custOrderFK);  
```  
  
### <a name="acceptrejectrule"></a>AcceptRejectRule  
 使用して行への変更を受け入れることができます、 **AcceptChanges**メソッドまたは取り消しを使用して、 **RejectChanges**のメソッド、**データセット**、 **DataTable**、または**DataRow**です。 ときに、**データセット**が含まれています**ForeignKeyConstraints**、起動、 **AcceptChanges**または**RejectChanges** を強制する方法**AcceptRejectRule**です。 **AcceptRejectRule**のプロパティ、 **ForeignKeyConstraint**子に対して実行されるアクションを決定するときに行**AcceptChanges**または**RejectChanges**は親の行で呼び出されます。  
  
 次の表に、利用可能な設定、 **AcceptRejectRule**です。  
  
|規則の設定|説明|  
|------------------|-----------------|  
|**Cascade**|子の行への変更を受け入れるかまたは拒否します。|  
|**None**|子の行に対してアクションは実行しません。 既定値です。|  
  
### <a name="example"></a>例  
 次の例では、<xref:System.Data.ForeignKeyConstraint> を作成し、<xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A> を含む複数のプロパティを設定して、<xref:System.Data.ConstraintCollection> オブジェクトの <xref:System.Data.DataTable> に追加します。  
  
 [!code-csharp[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/CS/source.cs#1)]
 [!code-vb[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/VB/source.vb#1)]  
  
## <a name="uniqueconstraint"></a>UniqueConstraint  
 **UniqueConstraint**オブジェクト、1 つの列または列の配列のいずれかに割り当てることができます、 **DataTable**、指定された列または列のすべてのデータが行ごとに一意であることを確認します。 使用して、列または列の配列に対する unique 制約を作成することができます、 **UniqueConstraint**コンス トラクターです。 その結果を渡す**UniqueConstraint**オブジェクトを**追加**メソッド テーブルの**制約**プロパティとは、 **ConstraintCollection**. いくつかのオーバー ロードにコンス トラクターの引数を渡すことも、**追加**のメソッド、 **ConstraintCollection**を作成する、 **UniqueConstraint**です。 作成するときに、 **UniqueConstraint**または複数の列のことができます必要に応じて指定するかどうか、列が主キー。  
  
 設定して、列の unique 制約を作成することも、 **Unique**する列のプロパティ**true**です。 または、設定、 **Unique**に単一の列のプロパティ**false**が存在している既存の unique 制約を削除します。 1 つの列 (または複数の列) をテーブルの主キーとして定義すると、指定した列 (または複数の列) の UNIQUE 制約が自動的に作成されます。 列を削除する場合、 **PrimaryKey**のプロパティ、 **DataTable**、 **UniqueConstraint**を削除します。  
  
 次の例を作成、 **UniqueConstraint**の 2 つの列に対して、 **DataTable**です。  
  
```vb  
Dim custTable As DataTable = custDS.Tables("Customers")  
Dim custUnique As UniqueConstraint = _  
    New UniqueConstraint(New DataColumn()   {custTable.Columns("CustomerID"), _  
    custTable.Columns("CompanyName")})  
custDS.Tables("Customers").Constraints.Add(custUnique)  
```  
  
```csharp  
DataTable custTable = custDS.Tables["Customers"];  
UniqueConstraint custUnique = new UniqueConstraint(new DataColumn[]   
    {custTable.Columns["CustomerID"],   
    custTable.Columns["CompanyName"]});  
custDS.Tables["Customers"].Constraints.Add(custUnique);  
```  
  
## <a name="see-also"></a>参照  
 <xref:System.Data.DataRelation>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.ForeignKeyConstraint>  
 <xref:System.Data.UniqueConstraint>  
 [DataTable スキーマの定義](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [DataSet、DataTable、および DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
