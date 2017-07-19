---
title: "DataTable 内のデータの表示 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d26e0fb-f6e0-4afa-9a9c-b8d55b8f20dc
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# DataTable 内のデータの表示
<xref:System.Data.DataTable> の内容には、**DataTable** の **Rows** コレクションと **Columns** コレクションを使用してアクセスできます。  また、<xref:System.Data.DataTable.Select%2A> メソッドを使用すると、検索条件、並べ替え順序、行の状態などの基準に基づいて **DataTable** 内のデータのサブセットを返すことができます。  さらに、主キー値を使用して特定の行を検索するときは、**DataRowCollection** の <xref:System.Data.DataRowCollection.Find%2A> メソッドを使用できます。  
  
 **DataTable** オブジェクトの **Select** メソッドは、指定された基準と一致する <xref:System.Data.DataRow> オブジェクトのセットを返します。  **Select** は、フィルター式、並べ替え式、および **DataViewRowState** のオプション引数を受け取ります。  フィルター式は、**DataColumn** 値に基づいて返す行を識別する `LastName = 'Smith'` などの式です。  並べ替え式は、列の並べ替えについての標準 SQL 規則に基づく `LastName ASC, FirstName ASC` などの式です。  式の記述の規則については、**DataColumn** クラスの <xref:System.Data.DataColumn.Expression%2A> プロパティのトピックを参照してください。  
  
> [!TIP]
>  **DataTable** の **Select** メソッドへの呼び出しを多数実行する場合は、最初に **DataTable** の <xref:System.Data.DataView> を作成することにより、パフォーマンスを向上させることができます。  **DataView** を作成すると、テーブルの行にインデックスが付けられます。  **Select** メソッドがこのインデックスを使用すると、クエリ結果を生成するまでの時間が大幅に減少します。  **DataTable** の **DataView** を作成する方法については、「[DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)」を参照してください。  
  
 **Select** メソッドは、<xref:System.Data.DataViewRowState> に基づいて、表示または操作する行のバージョンを判断します。  有効な **DataViewRowState** 列挙値の説明を次の表に示します。  
  
|DataViewRowState の値|説明|  
|-------------------------|--------|  
|**CurrentRows**|変更されていない行、追加された行、および変更された行を含む現在の行。|  
|**Deleted**|削除された行。|  
|**ModifiedCurrent**|元のデータを変更した後のバージョンである、現在のバージョン。  **ModifiedOriginal** を参照してください。|  
|**ModifiedOriginal**|変更されたすべての行の元のバージョン。  現在のバージョンは、**ModifiedCurrent**. を使用して取得できます。|  
|**Added**|新しい行。|  
|**なし**|なし。|  
|**OriginalRows**|変更されていない行および削除された行を含む元の行。|  
|**Unchanged**|変更されていない行。|  
  
 **DataSet** オブジェクトをフィルター処理して、**DataViewRowState** が **CurrentRows** に設定されている行だけを操作できるようにする例を次に示します。  
  
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
  
 **Select** メソッドを使用して、異なる **RowState** 値またはフィールド値を持つ行を返すこともできます。  削除されたすべての行を参照する **DataRow** 配列を返し、また、**CustLName** を基準にして並べ替えた **CustID** 列が 5 より大きいすべての行を参照する、別の **DataRow** 配列も返す例を次に示します。  **Deleted** 行の情報を表示する方法については、「[行の状態とバージョン](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)」を参照してください。  
  
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
  
## 参照  
 <xref:System.Data.DataRow>   
 <xref:System.Data.DataSet>   
 <xref:System.Data.DataTable>   
 <xref:System.Data.DataViewRowState>   
 [DataTable 内のデータの操作](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)   
 [行の状態とバージョン](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)