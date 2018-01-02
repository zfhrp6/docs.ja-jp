---
title: "DataTable 内のデータの表示"
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
ms.assetid: 1d26e0fb-f6e0-4afa-9a9c-b8d55b8f20dc
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: ab7a60b4195f3d8976a61e3909682b3748e30341
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="viewing-data-in-a-datatable"></a>DataTable 内のデータの表示
内容にアクセスすることができます、<xref:System.Data.DataTable>を使用して、**行**と**列**のコレクション、 **DataTable**です。 使用することも、<xref:System.Data.DataTable.Select%2A>内のデータのサブセットを返すメソッド、 **DataTable**のような検索条件の基準に従って並べ替え順序、および行の状態。 また、使用することができます、<xref:System.Data.DataRowCollection.Find%2A>のメソッド、 **DataRowCollection**主キーの値を使用して特定の行を検索するとき。  
  
 **選択**のメソッド、 **DataTable**オブジェクトのセットを返します<xref:System.Data.DataRow>指定した条件に一致するオブジェクト。 **選択**は、フィルター式、並べ替え式の省略可能な引数を受け取り、 **DataViewRowState**です。 フィルター式に基づいて返される行を識別する**DataColumn**などの値`LastName = 'Smith'`です。 並べ替え式は、列の並べ替えについての標準 SQL 規則に基づく `LastName ASC, FirstName ASC` などの式です。 式の作成に関する規則は、次を参照してください。、<xref:System.Data.DataColumn.Expression%2A>のプロパティ、 **DataColumn**クラスです。  
  
> [!TIP]
>  呼び出しの数を実行している場合、**選択**のメソッド、 **DataTable**、最初に作成することでパフォーマンスを向上させることができますできます、<xref:System.Data.DataView>の**DataTable**です。 作成する、 **DataView**テーブルの行のインデックスを作成します。 **選択**メソッド、インデックス、除去クエリ結果を生成する時間を大幅に削減します。 作成する方法について、 **DataView**の**DataTable**を参照してください[Dataview](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)です。  
  
 **選択**メソッドに基づいて、表示または操作する行のバージョンを決定する<xref:System.Data.DataViewRowState>です。 次の表に、考えられる**DataViewRowState**列挙値。  
  
|DataViewRowState の値|説明|  
|----------------------------|-----------------|  
|**CurrentRows**|変更されていない行、追加された行、および変更された行を含む現在の行。|  
|**削除**|削除された行。|  
|**ModifiedCurrent**|元のデータを変更した後のバージョンである、現在のバージョン。 (を参照してください**ModifiedOriginal**)。|  
|**ModifiedOriginal**|変更されたすべての行の元のバージョン。 現在のバージョンが利用可能なを使用して**ModifiedCurrent**です。|  
|**追加**|新しい行。|  
|**None**|なし。|  
|**OriginalRows**|変更されていない行および削除された行を含む元の行。|  
|**変更されません。**|変更されていない行。|  
  
 次の例で、**データセット**オブジェクトはフィルター処理のみを使用する行が**DataViewRowState**に設定されている**CurrentRows**です。  
  
```vb  
Dim column As DataColumn  
Dim row As DataRow  
  
Dim currentRows() As DataRow = _  
    workTable.Select(Nothing, Nothing, DataViewRowState.CurrentRows)  
  
If (currentRows.Length < 1 ) Then  
  Console.WriteLine("No Current Rows Found")  
Else  
  For Each column in workTable.Columns  
    Console.Write(vbTab & column.ColumnName)  
  Next  
  
  Console.WriteLine(vbTab & "RowState")  
  
  For Each row In currentRows  
    For Each column In workTable.Columns  
      Console.Write(vbTab & row(column).ToString())  
    Next  
  
    Dim rowState As String = _  
        System.Enum.GetName(row.RowState.GetType(), row.RowState)  
    Console.WriteLine(vbTab & rowState)  
  Next  
End If  
```  
  
```csharp  
DataRow[] currentRows = workTable.Select(  
    null, null, DataViewRowState.CurrentRows);  
  
if (currentRows.Length < 1 )  
  Console.WriteLine("No Current Rows Found");  
else  
{  
  foreach (DataColumn column in workTable.Columns)  
    Console.Write("\t{0}", column.ColumnName);  
  
  Console.WriteLine("\tRowState");  
  
  foreach (DataRow row in currentRows)  
  {  
    foreach (DataColumn column in workTable.Columns)  
      Console.Write("\t{0}", row[column]);  
  
    Console.WriteLine("\t" + row.RowState);  
  }  
}  
```  
  
 **選択**が異なると行を返すメソッドを使用できます**RowState**値またはフィールド値。 次の例を返します、 **DataRow**が削除されているし、他を返すすべての行を参照する配列**DataRow**順に、すべての行を参照している配列**CustLName**、場所、 **CustID**列が 5 より大きい。 内の情報を表示する方法については、 **Deleted**行を参照してください[行の状態と行のバージョン](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)します。  
  
```vb  
' Retrieve all deleted rows.  
Dim deletedRows() As DataRow = workTable.Select(Nothing, Nothing, DataViewRowState.Deleted)  
  
' Retrieve rows where CustID > 5, and order by CustLName.  
Dim custRows() As DataRow = workTable.Select( _  
    "CustID > 5", "CustLName ASC")  
```  
  
```csharp  
// Retrieve all deleted rows.  
DataRow[] deletedRows = workTable.Select(  
    null, null, DataViewRowState.Deleted);  
  
// Retrieve rows where CustID > 5, and order by CustLName.  
DataRow[] custRows = workTable.Select("CustID > 5", "CustLName ASC");  
```  
  
## <a name="see-also"></a>参照  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataViewRowState>  
 [DataTable 内のデータの操作](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [行の状態とバージョン](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
