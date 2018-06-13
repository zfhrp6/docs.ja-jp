---
title: DataTable へのデータの追加
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d6aa8474-7bde-48f7-949d-20dc38a1625b
ms.openlocfilehash: c58f64dba0bceb4a35c67e16193a6627837436e0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32767129"
---
# <a name="adding-data-to-a-datatable"></a>DataTable へのデータの追加
<xref:System.Data.DataTable> を作成し、列と制約を使用してそのテーブルの構造を定義した後で、テーブルに新しいデータ行を追加できます。 新しい行を追加するには、新しい変数を <xref:System.Data.DataRow> 型として宣言します。 新しい**DataRow**を呼び出すと、オブジェクトが返されます、<xref:System.Data.DataTable.NewRow%2A>メソッドです。 **DataTable**を作成し、 **DataRow**オブジェクトに基づいて、テーブルの構造によって定義された、<xref:System.Data.DataColumnCollection>です。  
  
 次の例は、呼び出すことによって、新しい行を作成する方法を示します、 **NewRow**メソッドです。  
  
```vb  
Dim workRow As DataRow = workTable.NewRow()  
```  
  
```csharp  
DataRow workRow = workTable.NewRow();  
```  
  
 その後でインデックスまたは列名を使用して、新しく追加した行を操作する例を次に示します。  
  
```vb  
workRow("CustLName") = "Smith"  
workRow(1) = "Smith"  
```  
  
```csharp  
workRow["CustLName"] = "Smith";  
workRow[1] = "Smith";  
```  
  
 データは、新しい行に挿入した後、**追加**メソッドを使用して、行を追加、 <xref:System.Data.DataRowCollection>、次のコードに示すです。  
  
```vb  
workTable.Rows.Add(workRow)  
```  
  
```csharp  
workTable.Rows.Add(workRow);  
```  
  
 呼び出すことも、**追加**として型指定された値の配列を渡すことによって、新しい行を追加するメソッドを<xref:System.Object>次の例で示すように、します。  
  
```vb  
workTable.Rows.Add(new Object() {1, "Smith"})  
```  
  
```csharp  
workTable.Rows.Add(new Object[] {1, "Smith"});  
```  
  
 型の値の配列を渡す**オブジェクト**を**追加**メソッドがテーブル内の新しい行を作成し、列の値をオブジェクト配列内の値に設定します。 配列内の値は、テーブル内での列の順序に基づいて、列に順次的に割り当てられます。  
  
 次の例では、10 個の行を追加、新しく作成した**顧客**テーブル。  
  
```vb  
Dim workRow As DataRow  
Dim i As Integer  
  
For i = 0 To 9  
  workRow = workTable.NewRow()  
  workRow(0) = i  
  workRow(1) = "CustName" & I.ToString()  
  workTable.Rows.Add(workRow)  
Next  
```  
  
```csharp  
DataRow workRow;  
  
for (int i = 0; i <= 9; i++)   
{  
  workRow = workTable.NewRow();  
  workRow[0] = i;  
  workRow[1] = "CustName" + i.ToString();  
  workTable.Rows.Add(workRow);  
}  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataRowCollection>  
 <xref:System.Data.DataTable>  
 [DataTable 内のデータの操作](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
