---
title: "DataTable の編集 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f08008a9-042e-4de9-94f3-4f0e502b1eb5
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# DataTable の編集
<xref:System.Data.DataRow> 内の列値を変更すると、その変更はすぐに行の現在の状態に反映されます。  次に、<xref:System.Data.DataRowState> が **Modified** に設定され、**DataRow** の <xref:System.Data.DataRow.AcceptChanges%2A> メソッドまたは <xref:System.Data.DataRow.RejectChanges%2A> メソッドを使用して変更が受け入れられるかまたは拒否されます。  **DataRow** は、行の編集中に、その行の状態を保留にしておくために使用できる 3 つのメソッドも提供します。  これらのメソッドとは、<xref:System.Data.DataRow.BeginEdit%2A>、<xref:System.Data.DataRow.EndEdit%2A> および <xref:System.Data.DataRow.CancelEdit%2A> です。  
  
 **DataRow** の列値が直接変更されると、**DataRow** は、**Current**、**Default**、**Original** の各行バージョンを使用して列値を管理します。  **BeginEdit**、**EndEdit**、**CancelEdit** の各メソッドでは、これらの行バージョンに加えて、4 番目の行バージョン **Proposed** を使用します。  行バージョンの詳細については、「[行の状態とバージョン](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)」を参照してください。  
  
 **Proposed** 行バージョンは、編集操作中に存在するバージョンです。編集操作は、**BeginEdit** への呼び出しによって開始し、**EndEdit** または **CancelEdit** の使用あるいは **AcceptChanges** または **RejectChanges** の呼び出しによって終了します。  
  
 編集操作中に、**DataTable** の **ColumnChanged** イベントで **ProposedValue** を評価することにより、個々の列に検証ロジックを適用できます。  **ColumnChanged** イベントは、変更されている列への参照および **ProposedValue** への参照を維持する **DataColumnChangeEventArgs** を保持します。  提示された値を評価した後で、値を変更するか、または編集をキャンセルできます。  編集が終了すると、行は **Proposed** 状態ではなくなります。  
  
 **EndEdit** を呼び出すと編集内容を確定でき、**CancelEdit** を呼び出すと編集内容をキャンセルできます。  **EndEdit** は編集内容を確定しますが、**DataSet** は **AcceptChanges** が呼び出されるまでは実際には変更を受け入れません。  また、**EndEdit** または **CancelEdit** を使用して編集を終了する前に **AcceptChanges** を呼び出した場合は、編集が終了し、**Proposed** 行値が **Current** 行バージョンと **Original** 行バージョンの両方に受け入れられます。  同様に、**RejectChanges** を呼び出した場合も編集が終了し、**Current** 行バージョンと **Proposed** 行バージョンの両方が破棄されます。  **AcceptChanges** または **RejectChanges** を呼び出した後で **EndEdit** または **CancelEdit** を呼び出しても、編集が既に終了しているため、その呼び出しは無効になります。  
  
 **BeginEdit**、**EndEdit**、および **CancelEdit** を使用する方法を次の例に示します。  この例では、**ColumnChanged** イベントで **ProposedValue** をチェックして、編集をキャンセルするかどうかを決定しています。  
  
```vb  
Dim workTable As DataTable = New DataTable  
workTable.Columns.Add("LastName", Type.GetType("System.String"))  
  
AddHandler workTable.ColumnChanged, _  
  New DataColumnChangeEventHandler(AddressOf OnColumnChanged)  
  
Dim workRow As DataRow = workTable.NewRow()  
workRow(0) = "Smith"  
workTable.Rows.Add(workRow)  
  
workRow.BeginEdit()  
' Causes the ColumnChanged event to write a message and cancel the edit.  
workRow(0) = ""       
workRow.EndEdit()  
  
' Displays "Smith, New".  
Console.WriteLine("{0}, {1}", workRow(0), workRow.RowState)  
  
Private Shared Sub OnColumnChanged( _  
  sender As Object, args As DataColumnChangeEventArgs)  
  If args.Column.ColumnName = "LastName" Then  
    If args.ProposedValue.ToString() = "" Then  
      Console.WriteLine("Last Name cannot be blank.  Edit canceled.")  
      args.Row.CancelEdit()  
    End If  
  End If  
End Sub  
  
```  
  
```csharp  
DataTable workTable  = new DataTable();  
workTable.Columns.Add("LastName", typeof(String));  
  
workTable.ColumnChanged +=   
  new DataColumnChangeEventHandler(OnColumnChanged);  
  
DataRow workRow = workTable.NewRow();  
workRow[0] = "Smith";  
workTable.Rows.Add(workRow);  
  
workRow.BeginEdit();  
// Causes the ColumnChanged event to write a message and cancel the edit.  
workRow[0] = "";       
workRow.EndEdit();  
  
// Displays "Smith, New".  
Console.WriteLine("{0}, {1}", workRow[0], workRow.RowState);    
  
protected static void OnColumnChanged(  
  Object sender, DataColumnChangeEventArgs args)  
{  
  if (args.Column.ColumnName == "LastName")  
    if (args.ProposedValue.ToString() == "")  
    {  
      Console.WriteLine("Last Name cannot be blank. Edit canceled.");  
      args.Row.CancelEdit();  
    }  
}  
```  
  
## 参照  
 <xref:System.Data.DataRow>   
 <xref:System.Data.DataTable>   
 <xref:System.Data.DataRowVersion>   
 [DataTable 内のデータの操作](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)   
 [DataTable イベントの処理](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)