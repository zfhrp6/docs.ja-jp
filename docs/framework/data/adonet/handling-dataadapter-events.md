---
title: DataAdapter のイベント処理
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 11515b25-ee49-4b1d-9294-a142147c1ec5
ms.openlocfilehash: f2b07b8d42069fa98ba51dea75f9695e7adce0b0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32759154"
---
# <a name="handling-dataadapter-events"></a><span data-ttu-id="428d5-102">DataAdapter のイベント処理</span><span class="sxs-lookup"><span data-stu-id="428d5-102">Handling DataAdapter Events</span></span>
<span data-ttu-id="428d5-103">ADO.NET <xref:System.Data.Common.DataAdapter> は、データ ソースのデータに対して行われた変更に応答するときに使用できる 3 つのイベントを公開します。</span><span class="sxs-lookup"><span data-stu-id="428d5-103">The ADO.NET <xref:System.Data.Common.DataAdapter> exposes three events that you can use to respond to changes made to data at the data source.</span></span> <span data-ttu-id="428d5-104">`DataAdapter` のイベントを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="428d5-104">The following table shows the `DataAdapter` events.</span></span>  
  
|<span data-ttu-id="428d5-105">Event</span><span class="sxs-lookup"><span data-stu-id="428d5-105">Event</span></span>|<span data-ttu-id="428d5-106">説明</span><span class="sxs-lookup"><span data-stu-id="428d5-106">Description</span></span>|  
|-----------|-----------------|  
|`RowUpdating`|<span data-ttu-id="428d5-107">行に対する UPDATE、INSERT、または DELETE の各操作が (`Update` メソッドの 1 つの呼び出しによって) 開始しようとしています。</span><span class="sxs-lookup"><span data-stu-id="428d5-107">An UPDATE, INSERT, or DELETE operation on a row (by a call to one of the `Update` methods) is about to begin.</span></span>|  
|`RowUpdated`|<span data-ttu-id="428d5-108">行に対する UPDATE、INSERT、DELETE の各操作が (`Update` メソッドの 1 つの呼び出しによって) 完了しました。</span><span class="sxs-lookup"><span data-stu-id="428d5-108">An UPDATE, INSERT, or DELETE operation on a row (by a call to one of the `Update` methods) is complete.</span></span>|  
|`FillError`|<span data-ttu-id="428d5-109">`Fill` 操作中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="428d5-109">An error has occurred during a `Fill` operation.</span></span>|  
  
## <a name="rowupdating-and-rowupdated"></a><span data-ttu-id="428d5-110">RowUpdating と RowUpdated</span><span class="sxs-lookup"><span data-stu-id="428d5-110">RowUpdating and RowUpdated</span></span>  
 <span data-ttu-id="428d5-111">`RowUpdating` は、<xref:System.Data.DataSet> 側で生じた行に対する更新が、データ ソース側で処理される前に発生します。</span><span class="sxs-lookup"><span data-stu-id="428d5-111">`RowUpdating` is raised before any update to a row from the <xref:System.Data.DataSet> has been processed at the data source.</span></span> <span data-ttu-id="428d5-112">`RowUpdated` は、`DataSet` 側で生じた行に対する更新が、データ ソース側で処理された後で発生します。</span><span class="sxs-lookup"><span data-stu-id="428d5-112">`RowUpdated` is raised after any update to a row from the `DataSet` has been processed at the data source.</span></span> <span data-ttu-id="428d5-113">したがって、更新が始まる前に `RowUpdating` を使用して更新の動作を変更することで、更新発生時に行う追加の処理の提供、更新行への参照の保存、現在の更新のキャンセル、後で処理するバッチ処理のための更新スケジュールなどを提供できます。</span><span class="sxs-lookup"><span data-stu-id="428d5-113">As a result, you can use `RowUpdating` to modify update behavior before it happens, to provide additional handling when an update will occur, to retain a reference to an updated row, to cancel the current update and schedule it for a batch process to be processed later, and so on.</span></span> <span data-ttu-id="428d5-114">`RowUpdated` は、更新中に発生するエラーや例外の応答に便利です。</span><span class="sxs-lookup"><span data-stu-id="428d5-114">`RowUpdated` is useful for responding to errors and exceptions that occur during the update.</span></span> <span data-ttu-id="428d5-115">`DataSet` にエラー情報や再試行ロジックなどを追加できます。</span><span class="sxs-lookup"><span data-stu-id="428d5-115">You can add error information to the `DataSet`, as well as retry logic, and so on.</span></span>  
  
 <span data-ttu-id="428d5-116"><xref:System.Data.Common.RowUpdatingEventArgs> イベントおよび <xref:System.Data.Common.RowUpdatedEventArgs> イベントに渡される `RowUpdating` 引数および `RowUpdated` 引数には、更新を実行するために使用される `Command` オブジェクトを参照する `Command` プロパティ、更新情報を格納する `Row` オブジェクトを参照する `DataRow` プロパティ、どのタイプの更新を実行するかを示す `StatementType` プロパティ、適用可能な場合は `TableMapping`、および、操作の `Status` などがあります。</span><span class="sxs-lookup"><span data-stu-id="428d5-116">The <xref:System.Data.Common.RowUpdatingEventArgs> and <xref:System.Data.Common.RowUpdatedEventArgs> arguments passed to the `RowUpdating` and `RowUpdated` events include the following: a `Command` property that references the `Command` object being used to perform the update; a `Row` property that references the `DataRow` object containing the updated information; a `StatementType` property for what type of update is being performed; the `TableMapping`, if applicable; and the `Status` of the operation.</span></span>  
  
 <span data-ttu-id="428d5-117">`Status` プロパティを使用すると、操作中にエラーが発生したかどうかを確認したり、必要に応じて現在の行および結果行に対するアクションを制御したりできます。</span><span class="sxs-lookup"><span data-stu-id="428d5-117">You can use the `Status` property to determine if an error has occurred during the operation and, if desired, to control the actions against the current and resulting rows.</span></span> <span data-ttu-id="428d5-118">イベントが発生すると、`Status` プロパティは `Continue` または `ErrorsOccurred` のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="428d5-118">When the event occurs, the `Status` property equals either `Continue` or `ErrorsOccurred`.</span></span> <span data-ttu-id="428d5-119">次の表では、更新の後続のアクションを制御するために `Status` プロパティに設定できる値を示しています。</span><span class="sxs-lookup"><span data-stu-id="428d5-119">The following table shows the values to which you can set the `Status` property in order to control later actions during the update.</span></span>  
  
|<span data-ttu-id="428d5-120">状態</span><span class="sxs-lookup"><span data-stu-id="428d5-120">Status</span></span>|<span data-ttu-id="428d5-121">説明</span><span class="sxs-lookup"><span data-stu-id="428d5-121">Description</span></span>|  
|------------|-----------------|  
|`Continue`|<span data-ttu-id="428d5-122">更新操作を続行します。</span><span class="sxs-lookup"><span data-stu-id="428d5-122">Continue the update operation.</span></span>|  
|`ErrorsOccurred`|<span data-ttu-id="428d5-123">更新操作を中止し、例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="428d5-123">Abort the update operation and throw an exception.</span></span>|  
|`SkipCurrentRow`|<span data-ttu-id="428d5-124">現在の行を無視し、更新操作を続行します。</span><span class="sxs-lookup"><span data-stu-id="428d5-124">Ignore the current row and continue the update operation.</span></span>|  
|`SkipAllRemainingRows`|<span data-ttu-id="428d5-125">更新操作を中止しますが、例外はスローしません。</span><span class="sxs-lookup"><span data-stu-id="428d5-125">Abort the update operation but do not throw an exception.</span></span>|  
  
 <span data-ttu-id="428d5-126">`Status` プロパティを `ErrorsOccurred` に設定すると、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="428d5-126">Setting the `Status` property to `ErrorsOccurred` causes an exception to be thrown.</span></span> <span data-ttu-id="428d5-127">`Errors` プロパティを例外として設定することで、どの例外をスローするかを制御できます。</span><span class="sxs-lookup"><span data-stu-id="428d5-127">You can control which exception is thrown by setting the `Errors` property to the desired exception.</span></span> <span data-ttu-id="428d5-128">`Status` に他の値を使用すると、例外はスローされません。</span><span class="sxs-lookup"><span data-stu-id="428d5-128">Using one of the other values for `Status` prevents an exception from being thrown.</span></span>  
  
 <span data-ttu-id="428d5-129">`ContinueUpdateOnError` プロパティを使用して更新行に関するエラーを処理することもできます。</span><span class="sxs-lookup"><span data-stu-id="428d5-129">You can also use the `ContinueUpdateOnError` property to handle errors for updated rows.</span></span> <span data-ttu-id="428d5-130">`DataAdapter.ContinueUpdateOnError` を `true` に設定すると、行を更新した結果、例外がスローされようとしているときに、例外のテキストをその行の `RowError` 情報の中に格納し、例外をスローせずに処理を続行できます。</span><span class="sxs-lookup"><span data-stu-id="428d5-130">If `DataAdapter.ContinueUpdateOnError` is `true`, when an update to a row results in an exception being thrown, the text of the exception is placed into the `RowError` information of the particular row, and processing continues without throwing an exception.</span></span> <span data-ttu-id="428d5-131">これにより、`Update` が完了した時点でエラーに応答できるようになります。これに対して `RowUpdated` イベントを使用すると、エラーが発生した時点でエラーに応答できます。</span><span class="sxs-lookup"><span data-stu-id="428d5-131">This enables you to respond to errors when the `Update` is complete, in contrast to the `RowUpdated` event, which enables you to respond to errors when the error is encountered.</span></span>  
  
 <span data-ttu-id="428d5-132">イベント ハンドラーを追加および削除する方法を次のコード サンプルに示します。</span><span class="sxs-lookup"><span data-stu-id="428d5-132">The following code sample shows how to both add and remove event handlers.</span></span> <span data-ttu-id="428d5-133">`RowUpdating` イベント ハンドラーは、削除されたすべてのレコードのログをタイムスタンプと共に記録します。</span><span class="sxs-lookup"><span data-stu-id="428d5-133">The `RowUpdating` event handler writes a log of all deleted records with a time stamp.</span></span> <span data-ttu-id="428d5-134">`RowUpdated`イベント ハンドラーの追加エラー情報を`RowError`内の行のプロパティ、 `DataSet`、例外を抑制し、処理を続行 (の動作をミラーリング`ContinueUpdateOnError`  =  `true`)。</span><span class="sxs-lookup"><span data-stu-id="428d5-134">The `RowUpdated` event handler adds error information to the `RowError` property of the row in the `DataSet`, suppresses the exception, and continues processing (mirroring the behavior of `ContinueUpdateOnError` = `true`).</span></span>  
  
```vb  
' Assumes that connection is a valid SqlConnection object.  
Dim custAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers", connection)  
  
' Add handlers.  
AddHandler custAdapter.RowUpdating, New SqlRowUpdatingEventHandler( _  
  AddressOf OnRowUpdating)  
AddHandler custAdapter.RowUpdated, New SqlRowUpdatedEventHandler(  
  AddressOf OnRowUpdated)  
  
' Set DataAdapter command properties, fill DataSet, and modify DataSet.  
  
custAdapter.Update(custDS, "Customers")  
  
' Remove handlers.  
RemoveHandler custAdapter.RowUpdating, _  
  New SqlRowUpdatingEventHandler(AddressOf OnRowUpdating)  
RemoveHandler custAdapter.RowUpdated, _  
  New SqlRowUpdatedEventHandler(AddressOf OnRowUpdated)  
  
Private Shared Sub OnRowUpdating(sender As Object, _  
  args As SqlRowUpdatingEventArgs)  
  If args.StatementType = StatementType.Delete Then  
    Dim tw As System.IO.TextWriter = _  
  System.IO.File.AppendText("Deletes.log")  
    tw.WriteLine( _  
      "{0}: Customer {1} Deleted.", DateTime.Now, args.Row(_  
      "CustomerID", DataRowVersion.Original))  
    tw.Close()  
  End If  
End Sub  
  
Private Shared Sub OnRowUpdated( _  
  sender As Object, args As SqlRowUpdatedEventArgs)  
  If args.Status = UpdateStatus.ErrorsOccurred  
    args.Status = UpdateStatus.SkipCurrentRow  
    args.Row.RowError = args.Errors.Message  
  End If  
End Sub  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection object.  
SqlDataAdapter custAdapter = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers", connection);  
  
// Add handlers.  
custAdapter.RowUpdating += new SqlRowUpdatingEventHandler(OnRowUpdating);  
custAdapter.RowUpdated += new SqlRowUpdatedEventHandler(OnRowUpdated);  
  
// Set DataAdapter command properties, fill DataSet, modify DataSet.  
  
custAdapter.Update(custDS, "Customers");  
  
// Remove handlers.  
custAdapter.RowUpdating -= new SqlRowUpdatingEventHandler(OnRowUpdating);  
custAdapter.RowUpdated -= new SqlRowUpdatedEventHandler(OnRowUpdated);  
  
protected static void OnRowUpdating(  
  object sender, SqlRowUpdatingEventArgs args)  
{  
  if (args.StatementType == StatementType.Delete)  
  {  
    System.IO.TextWriter tw = System.IO.File.AppendText("Deletes.log");  
    tw.WriteLine(  
      "{0}: Customer {1} Deleted.", DateTime.Now,   
       args.Row["CustomerID", DataRowVersion.Original]);  
    tw.Close();  
  }  
}  
  
protected static void OnRowUpdated(  
  object sender, SqlRowUpdatedEventArgs args)  
{  
  if (args.Status == UpdateStatus.ErrorsOccurred)  
  {  
    args.Row.RowError = args.Errors.Message;  
    args.Status = UpdateStatus.SkipCurrentRow;  
  }  
}  
```  
  
## <a name="fillerror"></a><span data-ttu-id="428d5-135">FillError</span><span class="sxs-lookup"><span data-stu-id="428d5-135">FillError</span></span>  
 <span data-ttu-id="428d5-136">`DataAdapter` は、`FillError` 操作中にエラーが発生すると `Fill` イベントを発行します。</span><span class="sxs-lookup"><span data-stu-id="428d5-136">The `DataAdapter` issues the `FillError` event when an error occurs during a `Fill` operation.</span></span> <span data-ttu-id="428d5-137">このタイプのエラーは通常、追加する行のデータを .NET Framework 型に変換したときに、有効桁を消失してしまった場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="428d5-137">This type of error commonly occurs when the data in the row being added could not be converted to a .NET Framework type without some loss of precision.</span></span>  
  
 <span data-ttu-id="428d5-138">`Fill` 操作中にエラーが発生した場合、現在の行は `DataTable` に追加されません。</span><span class="sxs-lookup"><span data-stu-id="428d5-138">If an error occurs during a `Fill` operation, the current row is not added to the `DataTable`.</span></span> <span data-ttu-id="428d5-139">`FillError` イベントを使用すると、エラーを解決してその行を追加するか、または除外された行を無視し、`Fill` 操作を続行できます。</span><span class="sxs-lookup"><span data-stu-id="428d5-139">The `FillError` event enables you to resolve the error and add the row, or to ignore the excluded row and continue the `Fill` operation.</span></span>  
  
 <span data-ttu-id="428d5-140">`FillErrorEventArgs` イベントに渡す `FillError` には、エラーに応答してエラーを解決できるいくつかのプロパティを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="428d5-140">The `FillErrorEventArgs` passed to the `FillError` event can contain several properties that enable you to respond to and resolve errors.</span></span> <span data-ttu-id="428d5-141">`FillErrorEventArgs` オブジェクトのプロパティを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="428d5-141">The following table shows the properties of the `FillErrorEventArgs` object.</span></span>  
  
|<span data-ttu-id="428d5-142">プロパティ</span><span class="sxs-lookup"><span data-stu-id="428d5-142">Property</span></span>|<span data-ttu-id="428d5-143">説明</span><span class="sxs-lookup"><span data-stu-id="428d5-143">Description</span></span>|  
|--------------|-----------------|  
|`Errors`|<span data-ttu-id="428d5-144">発生した `Exception`。</span><span class="sxs-lookup"><span data-stu-id="428d5-144">The `Exception` that occurred.</span></span>|  
|`DataTable`|<span data-ttu-id="428d5-145">エラー発生時にデータを格納しようとしていた `DataTable` オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="428d5-145">The `DataTable` object being filled when the error occurred.</span></span>|  
|`Values`|<span data-ttu-id="428d5-146">エラー発生時に追加しようとしていた行の値を保持しているオブジェクトの配列。</span><span class="sxs-lookup"><span data-stu-id="428d5-146">An array of objects that contains the values of the row being added when the error occurred.</span></span> <span data-ttu-id="428d5-147">`Values` 配列の序数参照は、追加しようとしていた行の列の序数参照に対応します。</span><span class="sxs-lookup"><span data-stu-id="428d5-147">The ordinal references of the `Values` array correspond to the ordinal references of the columns of the row being added.</span></span> <span data-ttu-id="428d5-148">たとえば、`Values[0]` は、行の第 1 列として追加しようとした値です。</span><span class="sxs-lookup"><span data-stu-id="428d5-148">For example, `Values[0]` is the value that was being added as the first column of the row.</span></span>|  
|`Continue`|<span data-ttu-id="428d5-149">例外をスローするかどうかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="428d5-149">Allows you to choose whether or not to throw an exception.</span></span> <span data-ttu-id="428d5-150">`Continue` プロパティを `false` に設定すると、エラーが発生したときに現在の `Fill` 操作を停止し、例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="428d5-150">Setting the `Continue` property to `false` will halt the current `Fill` operation, and an exception will be thrown.</span></span> <span data-ttu-id="428d5-151">`Continue` を `true` に設定すると、エラーに関係なく `Fill` 操作を続行します。</span><span class="sxs-lookup"><span data-stu-id="428d5-151">Setting `Continue` to `true` continues the `Fill` operation despite the error.</span></span>|  
  
 <span data-ttu-id="428d5-152">次のコード例では、`FillError` の `DataAdapter` イベントにイベント ハンドラーを追加しています。</span><span class="sxs-lookup"><span data-stu-id="428d5-152">The following code example adds an event handler for the `FillError` event of the `DataAdapter`.</span></span> <span data-ttu-id="428d5-153">この `FillError` イベント コードの例は、有効桁の消失が発生したかどうかを確認し、例外に応答する機会を与えます。</span><span class="sxs-lookup"><span data-stu-id="428d5-153">In the `FillError` event code, the example determines if there is the potential for precision loss, providing the opportunity to respond to the exception.</span></span>  
  
```vb  
AddHandler adapter.FillError, New FillErrorEventHandler( _  
  AddressOf FillError)  
  
Dim dataSet As DataSet = New DataSet  
adapter.Fill(dataSet, "ThisTable")  
  
Private Shared Sub FillError(sender As Object, _  
  args As FillErrorEventArgs)  
  If args.Errors.GetType() Is Type.GetType("System.OverflowException") Then  
    ' Code to handle precision loss.  
    ' Add a row to table using the values from the first two columns.  
    DataRow myRow = args.DataTable.Rows.Add(New Object() _  
      {args.Values(0), args.Values(1), DBNull.Value})  
    ' Set the RowError containing the value for the third column.  
    args.RowError = _  
      "OverflowException encountered. Value from data source: " & _  
      args.Values(2)  
    args.Continue = True  
  End If  
End Sub  
```  
  
```csharp  
adapter.FillError += new FillErrorEventHandler(FillError);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, "ThisTable");  
  
protected static void FillError(object sender, FillErrorEventArgs args)  
{  
  if (args.Errors.GetType() == typeof(System.OverflowException))  
  {  
    // Code to handle precision loss.  
    //Add a row to table using the values from the first two columns.  
    DataRow myRow = args.DataTable.Rows.Add(new object[]  
       {args.Values[0], args.Values[1], DBNull.Value});  
    //Set the RowError containing the value for the third column.  
    args.RowError =   
       "OverflowException Encountered. Value from data source: " +  
       args.Values[2];  
    args.Continue = true;  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="428d5-154">関連項目</span><span class="sxs-lookup"><span data-stu-id="428d5-154">See Also</span></span>  
 [<span data-ttu-id="428d5-155">DataAdapter と DataReader</span><span class="sxs-lookup"><span data-stu-id="428d5-155">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="428d5-156">DataSet のイベント処理</span><span class="sxs-lookup"><span data-stu-id="428d5-156">Handling DataSet Events</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md)  
 [<span data-ttu-id="428d5-157">DataTable イベントの処理</span><span class="sxs-lookup"><span data-stu-id="428d5-157">Handling DataTable Events</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 [<span data-ttu-id="428d5-158">イベント</span><span class="sxs-lookup"><span data-stu-id="428d5-158">Events</span></span>](../../../../docs/standard/events/index.md)  
 [<span data-ttu-id="428d5-159">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="428d5-159">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
