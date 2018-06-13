---
title: 主キーの定義
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2ea85959-e763-4669-8bd9-46a9dab894bd
ms.openlocfilehash: 21d63aa33e20019f8392b81fb69881296a52cb26
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32757581"
---
# <a name="defining-primary-keys"></a>主キーの定義
通常、データベース テーブルには、テーブル内の各行を一意に識別する単一の列または複数の列があります。 行を識別するこのような列を、主キーと呼びます。  
  
 1 つを指定すると<xref:System.Data.DataColumn>として、<xref:System.Data.DataTable.PrimaryKey%2A>の<xref:System.Data.DataTable>、テーブルが自動的に設定、<xref:System.Data.DataColumn.AllowDBNull%2A>する列のプロパティ**false**と<xref:System.Data.DataColumn.Unique%2A>プロパティを**true**です。 複数列プライマリ キーの場合のみ、 **AllowDBNull**プロパティに設定されて自動的に**false**です。  
  
 **PrimaryKey**のプロパティ、 <xref:System.Data.DataTable> 1 つ以上の配列をその値として受け取る**DataColumn**オブジェクトを次の例に示すようにします。 最初の例は、1 つの列を主キーとして定義しています。  
  
```vb  
workTable.PrimaryKey = New DataColumn() {workTable.Columns("CustID")}  
  
' Or  
  
Dim columns(1) As DataColumn  
columns(0) = workTable.Columns("CustID")  
workTable.PrimaryKey = columns  
```  
  
```csharp  
workTable.PrimaryKey = new DataColumn[] {workTable.Columns["CustID"]};  
  
// Or  
  
DataColumn[] columns = new DataColumn[1];  
columns[0] = workTable.Columns["CustID"];  
workTable.PrimaryKey = columns;  
```  
  
 2 つの列を主キーとして定義する例を次に示します。  
  
```vb  
workTable.PrimaryKey = New DataColumn() {workTable.Columns("CustLName"), _  
                                         workTable.Columns("CustFName")}  
  
' Or  
  
Dim keyColumn(2) As DataColumn  
keyColumn(0) = workTable.Columns("CustLName")  
keyColumn(1) = workTable.Columns("CustFName")  
workTable.PrimaryKey = keyColumn  
```  
  
```csharp  
workTable.PrimaryKey = new DataColumn[] {workTable.Columns["CustLName"],   
                                         workTable.Columns["CustFName"]};  
  
// Or  
  
DataColumn[] keyColumn = new DataColumn[2];  
keyColumn[0] = workTable.Columns["CustLName"];  
keyColumn[1] = workTable.Columns["CustFName"];  
workTable.PrimaryKey = keyColumn;  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Data.DataTable>  
 [DataTable スキーマの定義](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
