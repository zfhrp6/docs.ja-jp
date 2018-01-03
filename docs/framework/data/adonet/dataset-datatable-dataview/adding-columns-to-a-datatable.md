---
title: "DataTable への列の追加"
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
ms.assetid: e85c4a0e-4f3f-458c-b58b-0ddbc06bf974
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 423b9ed389a5a3750c8e9b0339e0887d6b650741
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="adding-columns-to-a-datatable"></a>DataTable への列の追加
A<xref:System.Data.DataTable>のコレクションを格納<xref:System.Data.DataColumn>によって参照されるオブジェクト、**列**テーブルのプロパティです。 この列のコレクションと制約によって、テーブルのスキーマ (構造) が定義されます。  
  
 作成する**DataColumn**を使用してテーブル内のオブジェクト、 **DataColumn**コンス トラクター、または呼び出すことによって、**追加**のメソッド、**列**これは、テーブルのプロパティ、<xref:System.Data.DataColumnCollection>です。 **追加**メソッドは省略可能なを受け取ります**ColumnName**、 **DataType**、および**式**引数新たに作成および**DataColumn**コレクションのメンバーとして。 指定することも、既存**DataColumn**オブジェクトし、コレクションに追加しを追加の参照を返します**DataColumn**要求されている場合。 **DataTable**オブジェクトがすべてのデータ ソースに固有ではないのデータ型を指定するときに .NET Framework の型が使用される、 **DataColumn**です。  
  
 次の例では、次の 4 つの列を**DataTable**です。  
  
```vb  
Dim workTable As DataTable = New DataTable("Customers")  
  
Dim workCol As DataColumn = workTable.Columns.Add( _  
    "CustID", Type.GetType("System.Int32"))  
workCol.AllowDBNull = false  
workCol.Unique = true  
  
workTable.Columns.Add("CustLName", Type.GetType("System.String"))  
workTable.Columns.Add("CustFName", Type.GetType("System.String"))  
workTable.Columns.Add("Purchases", Type.GetType("System.Double"))  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
  
DataColumn workCol = workTable.Columns.Add("CustID", typeof(Int32));  
workCol.AllowDBNull = false;  
workCol.Unique = true;  
  
workTable.Columns.Add("CustLName", typeof(String));  
workTable.Columns.Add("CustFName", typeof(String));  
workTable.Columns.Add("Purchases", typeof(Double));  
```  
  
 例では、ことに注意してプロパティを**CustID**列は許可しないように設定**DBNull**値とを一意になる値を制限します。 ただし、定義した場合、 **CustID**列、テーブルの主キー列として、 **AllowDBNull**プロパティに自動的に設定する**false**と、 **Unique**プロパティに自動的に設定する**true**です。 詳細については、次を参照してください。[主キーを定義する](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md)です。  
  
> [!CAUTION]
>  列が列の増分の既定の名前を指定された列の列名が指定されない場合*N、* "Column1"から始めて、これが追加されたときに、 **DataColumnCollection**です。 名前付け規則を回避することをお勧め"列*N*"の既存の既定の列名と競合があります、名前を指定するために、列名を指定するときに、 **DataColumnCollection**です。 指定した名前が既に存在する場合は、例外がスローされます。  
  
 <xref:System.Xml.Linq.XElement> を、<xref:System.Data.DataColumn.DataType%2A> 内の <xref:System.Data.DataColumn> の <xref:System.Data.DataTable> として使用すると、データを読み取るときに XML シリアル化が機能しません。 たとえば、<xref:System.Xml.XmlDocument> メソッドを使用して `DataTable.WriteXml` を書き込むと、XML へのシリアル化で <xref:System.Xml.Linq.XElement> に親ノードが追加されます。 この問題に対処するには、<xref:System.Data.SqlTypes.SqlXml> の代わりに <xref:System.Xml.Linq.XElement> 型を使用します。 `ReadXml` および `WriteXml` は、<xref:System.Data.SqlTypes.SqlXml> で適切に機能します。  
  
## <a name="see-also"></a>参照  
 <xref:System.Data.DataColumn>  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataTable>  
 [DataTable スキーマの定義](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
