---
title: "DataTable の編集"
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
ms.assetid: f08008a9-042e-4de9-94f3-4f0e502b1eb5
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d33bd8900c48222142a46ed2c5bd64412d2eaab5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="datatable-edits"></a><span data-ttu-id="38dc2-102">DataTable の編集</span><span class="sxs-lookup"><span data-stu-id="38dc2-102">DataTable Edits</span></span>
<span data-ttu-id="38dc2-103"><xref:System.Data.DataRow> 内の列値を変更すると、その変更はすぐに行の現在の状態に反映されます。</span><span class="sxs-lookup"><span data-stu-id="38dc2-103">When you make changes to column values in a <xref:System.Data.DataRow>, the changes are immediately placed in the current state of the row.</span></span> <span data-ttu-id="38dc2-104"><xref:System.Data.DataRowState>に設定されているし、 **Modified**、変更が受け入れられますまたは拒否を使用して、<xref:System.Data.DataRow.AcceptChanges%2A>または<xref:System.Data.DataRow.RejectChanges%2A>のメソッド、 **DataRow**です。</span><span class="sxs-lookup"><span data-stu-id="38dc2-104">The <xref:System.Data.DataRowState> is then set to **Modified**, and the changes are accepted or rejected using the <xref:System.Data.DataRow.AcceptChanges%2A> or <xref:System.Data.DataRow.RejectChanges%2A> methods of the **DataRow**.</span></span> <span data-ttu-id="38dc2-105">**DataRow**を編集しているときに、行の状態を中断するのに使用できる 3 つのメソッドも提供します。</span><span class="sxs-lookup"><span data-stu-id="38dc2-105">The **DataRow** also provides three methods that you can use to suspend the state of the row while you are editing it.</span></span> <span data-ttu-id="38dc2-106">これらのメソッドとは、<xref:System.Data.DataRow.BeginEdit%2A>、<xref:System.Data.DataRow.EndEdit%2A> および <xref:System.Data.DataRow.CancelEdit%2A> です。</span><span class="sxs-lookup"><span data-stu-id="38dc2-106">These methods are <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A>, and <xref:System.Data.DataRow.CancelEdit%2A>.</span></span>  
  
 <span data-ttu-id="38dc2-107">列の値を変更する場合、 **DataRow**を直接、 **DataRow**を使用して列の値を管理、**現在**、**既定**、および**元**行のバージョン。</span><span class="sxs-lookup"><span data-stu-id="38dc2-107">When you modify column values in a **DataRow** directly, the **DataRow** manages the column values using the **Current**, **Default**, and **Original** row versions.</span></span> <span data-ttu-id="38dc2-108">これらの行バージョンに加えて、 **BeginEdit**、 **EndEdit**、および**CancelEdit**メソッドが 4 番目の行バージョンを使用する: **Proposed**です。</span><span class="sxs-lookup"><span data-stu-id="38dc2-108">In addition to these row versions, the **BeginEdit**, **EndEdit**, and **CancelEdit** methods use a fourth row version: **Proposed**.</span></span> <span data-ttu-id="38dc2-109">行のバージョンの詳細については、次を参照してください。[行の状態と行のバージョン](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)します。</span><span class="sxs-lookup"><span data-stu-id="38dc2-109">For more information about row versions, see [Row States and Row Versions](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="38dc2-110">**Proposed**呼び出しによって開始編集操作中に行バージョンが存在する**BeginEdit**を使用するか終了して**EndEdit**または**CancelEdit、**または呼び出すことによって**AcceptChanges**または**RejectChanges**です。</span><span class="sxs-lookup"><span data-stu-id="38dc2-110">The **Proposed** row version exists during an edit operation that begins by calling **BeginEdit** and that ends either by using **EndEdit** or **CancelEdit,** or by calling **AcceptChanges** or **RejectChanges**.</span></span>  
  
 <span data-ttu-id="38dc2-111">編集操作中に適用できます検証ロジックの個々 の列を評価することによって、 **ProposedValue**で、 **ColumnChanged**のイベント、 **DataTable**です。</span><span class="sxs-lookup"><span data-stu-id="38dc2-111">During the edit operation, you can apply validation logic to individual columns by evaluating the **ProposedValue** in the **ColumnChanged** event of the **DataTable**.</span></span> <span data-ttu-id="38dc2-112">**ColumnChanged**イベントを保持**DataColumnChangeEventArgs**に変更されている列と参照を保持する、 **ProposedValue**です。</span><span class="sxs-lookup"><span data-stu-id="38dc2-112">The **ColumnChanged** event holds **DataColumnChangeEventArgs** that keep a reference to the column that is changing and to the **ProposedValue**.</span></span> <span data-ttu-id="38dc2-113">提示された値を評価した後で、値を変更するか、または編集をキャンセルできます。</span><span class="sxs-lookup"><span data-stu-id="38dc2-113">After you evaluate the proposed value, you can either modify it or cancel the edit.</span></span> <span data-ttu-id="38dc2-114">うち、行が移動、編集が終了したときに、 **Proposed**状態です。</span><span class="sxs-lookup"><span data-stu-id="38dc2-114">When the edit is ended, the row moves out of the **Proposed** state.</span></span>  
  
 <span data-ttu-id="38dc2-115">編集内容を確認するには呼び出すことによって**EndEdit**、呼び出すことによって、それらをキャンセルできます**CancelEdit**です。</span><span class="sxs-lookup"><span data-stu-id="38dc2-115">You can confirm edits by calling **EndEdit**, or you can cancel them by calling **CancelEdit**.</span></span> <span data-ttu-id="38dc2-116">注意してください**EndEdit**が、編集内容を確認して、**データセット**までの変更を実際には受け入れません**AcceptChanges**と呼びます。</span><span class="sxs-lookup"><span data-stu-id="38dc2-116">Note that while **EndEdit** does confirm your edits, the **DataSet** does not actually accept the changes until **AcceptChanges** is called.</span></span> <span data-ttu-id="38dc2-117">なおを呼び出す場合**AcceptChanges**と編集を終了する前に**EndEdit**または**CancelEdit**、編集が終了し、 **Proposed**両方の行の値を受け入れる、**現在**と**元**行のバージョン。</span><span class="sxs-lookup"><span data-stu-id="38dc2-117">Note also that if you call **AcceptChanges** before you have ended the edit with **EndEdit** or **CancelEdit**, the edit is ended and the **Proposed** row values are accepted for both the **Current** and **Original** row versions.</span></span> <span data-ttu-id="38dc2-118">同様でを呼び出す**RejectChanges**編集を終了し、破棄、**現在**と**提案済み**行のバージョン。</span><span class="sxs-lookup"><span data-stu-id="38dc2-118">In the same manner, calling **RejectChanges** ends the edit and discards the **Current** and **Proposed** row versions.</span></span> <span data-ttu-id="38dc2-119">呼び出す**EndEdit**または**CancelEdit**呼び出した後**AcceptChanges**または**RejectChanges**編集が既にあるため影響を与えません終了しました。</span><span class="sxs-lookup"><span data-stu-id="38dc2-119">Calling **EndEdit** or **CancelEdit** after calling **AcceptChanges** or **RejectChanges** has no effect because the edit has already ended.</span></span>  
  
 <span data-ttu-id="38dc2-120">次の例を使用する方法を示します**BeginEdit**で**EndEdit**と**CancelEdit**です。</span><span class="sxs-lookup"><span data-stu-id="38dc2-120">The following example demonstrates how to use **BeginEdit** with **EndEdit** and **CancelEdit**.</span></span> <span data-ttu-id="38dc2-121">例もチェック、 **ProposedValue**で、 **ColumnChanged**イベントし、編集をキャンセルするかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="38dc2-121">The example also checks the **ProposedValue** in the **ColumnChanged** event and decides whether to cancel the edit.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="38dc2-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="38dc2-122">See Also</span></span>  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataRowVersion>  
 [<span data-ttu-id="38dc2-123">DataTable 内のデータを操作します。</span><span class="sxs-lookup"><span data-stu-id="38dc2-123">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [<span data-ttu-id="38dc2-124">DataTable イベントの処理</span><span class="sxs-lookup"><span data-stu-id="38dc2-124">Handling DataTable Events</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 [<span data-ttu-id="38dc2-125">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="38dc2-125">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
