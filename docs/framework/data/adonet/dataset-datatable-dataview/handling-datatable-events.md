---
title: "DataTable イベントの処理"
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
ms.assetid: 62f404a5-13ea-4b93-a29f-55b74a16c9d3
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: f7ab9d1043fdd1d4d78ec09390f227f297e471c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="handling-datatable-events"></a><span data-ttu-id="8d331-102">DataTable イベントの処理</span><span class="sxs-lookup"><span data-stu-id="8d331-102">Handling DataTable Events</span></span>
<span data-ttu-id="8d331-103"><xref:System.Data.DataTable> オブジェクトは、アプリケーションが処理できる一連のイベントを提供します。</span><span class="sxs-lookup"><span data-stu-id="8d331-103">The <xref:System.Data.DataTable> object provides a series of events that can be processed by an application.</span></span> <span data-ttu-id="8d331-104">`DataTable` のイベントを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="8d331-104">The following table describes `DataTable` events.</span></span>  
  
|<span data-ttu-id="8d331-105">Event</span><span class="sxs-lookup"><span data-stu-id="8d331-105">Event</span></span>|<span data-ttu-id="8d331-106">説明</span><span class="sxs-lookup"><span data-stu-id="8d331-106">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Data.DataTable.Initialized>|<span data-ttu-id="8d331-107"><xref:System.Data.DataTable.EndInit%2A> の `DataTable` メソッドが呼び出された後に発生します。</span><span class="sxs-lookup"><span data-stu-id="8d331-107">Occurs after the <xref:System.Data.DataTable.EndInit%2A> method of a `DataTable` is called.</span></span> <span data-ttu-id="8d331-108">このイベントは、主にデザイン時のシナリオをサポートすることを目的としています。</span><span class="sxs-lookup"><span data-stu-id="8d331-108">This event is intended primarily to support design-time scenarios.</span></span>|  
|<xref:System.Data.DataTable.ColumnChanged>|<span data-ttu-id="8d331-109"><xref:System.Data.DataColumn> で値が正常に変更された後に発生します。</span><span class="sxs-lookup"><span data-stu-id="8d331-109">Occurs after a value has been successfully changed in a <xref:System.Data.DataColumn>.</span></span>|  
|<xref:System.Data.DataTable.ColumnChanging>|<span data-ttu-id="8d331-110">`DataColumn` に対して値が送信されたときに発生します。</span><span class="sxs-lookup"><span data-stu-id="8d331-110">Occurs when a value has been submitted for a `DataColumn`.</span></span>|  
|<xref:System.Data.DataTable.RowChanged>|<span data-ttu-id="8d331-111">`DataColumn` 値または <xref:System.Data.DataRow.RowState%2A> の <xref:System.Data.DataRow> の `DataTable` が正常に変更された後で発生します。</span><span class="sxs-lookup"><span data-stu-id="8d331-111">Occurs after a `DataColumn` value or the <xref:System.Data.DataRow.RowState%2A> of a <xref:System.Data.DataRow> in the `DataTable` has been changed successfully.</span></span>|  
|<xref:System.Data.DataTable.RowChanging>|<span data-ttu-id="8d331-112">`DataColumn` 値または `RowState` の `DataRow` の `DataTable` に対して変更が送信されたときに発生します。</span><span class="sxs-lookup"><span data-stu-id="8d331-112">Occurs when a change has been submitted for a `DataColumn` value or the `RowState` of a `DataRow` in the `DataTable`.</span></span>|  
|<xref:System.Data.DataTable.RowDeleted>|<span data-ttu-id="8d331-113">`DataRow` の `DataTable` が `Deleted` としてマークされた後に発生します。</span><span class="sxs-lookup"><span data-stu-id="8d331-113">Occurs after a `DataRow` in the `DataTable` has been marked as `Deleted`.</span></span>|  
|<xref:System.Data.DataTable.RowDeleting>|<span data-ttu-id="8d331-114">`DataRow` の `DataTable` が `Deleted` としてマークされる前に発生します。</span><span class="sxs-lookup"><span data-stu-id="8d331-114">Occurs before a `DataRow` in the `DataTable` is marked as `Deleted`.</span></span>|  
|<xref:System.Data.DataTable.TableCleared>|<span data-ttu-id="8d331-115"><xref:System.Data.DataTable.Clear%2A> の `DataTable` メソッドがすべての `DataRow` を正常にクリアした後で発生します。</span><span class="sxs-lookup"><span data-stu-id="8d331-115">Occurs after a call to the <xref:System.Data.DataTable.Clear%2A> method of the `DataTable` has successfully cleared every `DataRow`.</span></span>|  
|<xref:System.Data.DataTable.TableClearing>|<span data-ttu-id="8d331-116">`Clear` メソッドが呼び出された後、`Clear` 操作が開始される前に発生します。</span><span class="sxs-lookup"><span data-stu-id="8d331-116">Occurs after the `Clear` method is called but before the `Clear` operation begins.</span></span>|  
|<xref:System.Data.DataTable.TableNewRow>|<span data-ttu-id="8d331-117">`DataRow` の `NewRow` メソッドの呼び出しにより、新しい `DataTable` が作成された後で発生します。</span><span class="sxs-lookup"><span data-stu-id="8d331-117">Occurs after a new `DataRow` is created by a call to the `NewRow` method of the `DataTable`.</span></span>|  
|<xref:System.ComponentModel.MarshalByValueComponent.Disposed>|<span data-ttu-id="8d331-118">`DataTable` が破棄 (`Disposed`) されたときに発生します。</span><span class="sxs-lookup"><span data-stu-id="8d331-118">Occurs when the `DataTable` is `Disposed`.</span></span> <span data-ttu-id="8d331-119">このプロパティは、<xref:System.ComponentModel.MarshalByValueComponent> から継承されています。</span><span class="sxs-lookup"><span data-stu-id="8d331-119">Inherited from <xref:System.ComponentModel.MarshalByValueComponent>.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="8d331-120">行の追加または削除を行う操作の多くは、`ColumnChanged` イベントも `ColumnChanging` イベントも生成しません。</span><span class="sxs-lookup"><span data-stu-id="8d331-120">Most operations that add or delete rows do not raise the `ColumnChanged` and `ColumnChanging` events.</span></span> <span data-ttu-id="8d331-121">ただし、`ReadXml` メソッドでは、`ColumnChanged` が `ColumnChanging` または `XmlReadMode` (読み込む XML ドキュメントが `DiffGram` の場合) に設定されていない限り、`Auto` イベントおよび `DiffGram` イベントが生成されます。</span><span class="sxs-lookup"><span data-stu-id="8d331-121">However, the `ReadXml` method does raise `ColumnChanged` and `ColumnChanging` events, unless the `XmlReadMode` is set to `DiffGram` or is set to `Auto` when the XML document being read is a `DiffGram`.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="8d331-122">`DataSet` イベントの生成元の `RowChanged` でデータが変更されると、データが破損する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8d331-122">Data corruption can occur if data is modified in a `DataSet` from which the `RowChanged` event is raised.</span></span> <span data-ttu-id="8d331-123">このようなデータの破損が起きた場合、例外は発生しません。</span><span class="sxs-lookup"><span data-stu-id="8d331-123">No exception will be raised if such data corruption occurs.</span></span>  
  
## <a name="additional-related-events"></a><span data-ttu-id="8d331-124">その他の関連イベント</span><span class="sxs-lookup"><span data-stu-id="8d331-124">Additional Related Events</span></span>  
 <span data-ttu-id="8d331-125"><xref:System.Data.DataTable.Constraints%2A> プロパティは <xref:System.Data.ConstraintCollection> インスタンスを保持します。</span><span class="sxs-lookup"><span data-stu-id="8d331-125">The <xref:System.Data.DataTable.Constraints%2A> property holds a <xref:System.Data.ConstraintCollection> instance.</span></span> <span data-ttu-id="8d331-126"><xref:System.Data.ConstraintCollection> クラスは、<xref:System.Data.ConstraintCollection.CollectionChanged> イベントを公開します。</span><span class="sxs-lookup"><span data-stu-id="8d331-126">The <xref:System.Data.ConstraintCollection> class exposes a <xref:System.Data.ConstraintCollection.CollectionChanged> event.</span></span> <span data-ttu-id="8d331-127">このイベントは、`ConstraintCollection` に対して制約の追加、変更、または削除が実行されたときに発生します。</span><span class="sxs-lookup"><span data-stu-id="8d331-127">This event fires when a constraint is added, modified, or removed from the `ConstraintCollection`.</span></span>  
  
 <span data-ttu-id="8d331-128"><xref:System.Data.DataTable.Columns%2A> プロパティは <xref:System.Data.DataColumnCollection> インスタンスを保持します。</span><span class="sxs-lookup"><span data-stu-id="8d331-128">The <xref:System.Data.DataTable.Columns%2A> property holds a <xref:System.Data.DataColumnCollection> instance.</span></span> <span data-ttu-id="8d331-129">`DataColumnCollection` クラスは、<xref:System.Data.DataColumnCollection.CollectionChanged> イベントを公開します。</span><span class="sxs-lookup"><span data-stu-id="8d331-129">The `DataColumnCollection` class exposes a <xref:System.Data.DataColumnCollection.CollectionChanged> event.</span></span> <span data-ttu-id="8d331-130">このイベントは、`DataColumn` が追加、変更、または `DataColumnCollection` から削除されたときに発生します。</span><span class="sxs-lookup"><span data-stu-id="8d331-130">This event fires when a `DataColumn` is added, modified, or removed from the `DataColumnCollection`.</span></span> <span data-ttu-id="8d331-131">イベントの発生を伴う変更には、名前の変更、型の変更、式の変更、列の序数位置の変更などがあります。</span><span class="sxs-lookup"><span data-stu-id="8d331-131">Modifications that cause the event to fire include changes to the name, type, expression or ordinal position of a column.</span></span>  
  
 <span data-ttu-id="8d331-132"><xref:System.Data.DataSet.Tables%2A> の <xref:System.Data.DataSet> プロパティは <xref:System.Data.DataTableCollection> インスタンスを保持します。</span><span class="sxs-lookup"><span data-stu-id="8d331-132">The <xref:System.Data.DataSet.Tables%2A> property of a <xref:System.Data.DataSet> holds a <xref:System.Data.DataTableCollection> instance.</span></span> <span data-ttu-id="8d331-133">`DataTableCollection` クラスは、`CollectionChanged` イベントと `CollectionChanging` イベントの両方を公開します。</span><span class="sxs-lookup"><span data-stu-id="8d331-133">The `DataTableCollection` class exposes both a `CollectionChanged` and a `CollectionChanging` event.</span></span> <span data-ttu-id="8d331-134">これらのイベントは、`DataTable` に対して、`DataSet` の追加、変更、または削除が実行されたときに発生します。</span><span class="sxs-lookup"><span data-stu-id="8d331-134">These events fire when a `DataTable` is added to or removed from the `DataSet`.</span></span>  
  
 <span data-ttu-id="8d331-135">`DataRows` への変更によって、関連する <xref:System.Data.DataView> のイベントがトリガーされる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="8d331-135">Changes to `DataRows` can also trigger events for an associated <xref:System.Data.DataView>.</span></span> <span data-ttu-id="8d331-136">`DataView` クラスは、<xref:System.Data.DataView.ListChanged> 値が変更されたとき、または、ビューの構成や並べ替え順が変更されたときに発生する `DataColumn` イベントを公開します。</span><span class="sxs-lookup"><span data-stu-id="8d331-136">The `DataView` class exposes a <xref:System.Data.DataView.ListChanged> event that fires when a `DataColumn` value changes or when the composition or sort order of the view changes.</span></span> <span data-ttu-id="8d331-137"><xref:System.Data.DataRowView> クラスは、関連する <xref:System.Data.DataRowView.PropertyChanged> 値が変更されたときに発生する `DataColumn` イベントを公開します。</span><span class="sxs-lookup"><span data-stu-id="8d331-137">The <xref:System.Data.DataRowView> class exposes a <xref:System.Data.DataRowView.PropertyChanged> event that fires when an associated `DataColumn` value changes.</span></span>  
  
## <a name="sequence-of-operations"></a><span data-ttu-id="8d331-138">操作の順序</span><span class="sxs-lookup"><span data-stu-id="8d331-138">Sequence of Operations</span></span>  
 <span data-ttu-id="8d331-139">`DataRow` が追加、変更、または削除されたときに発生する操作の順序について説明します。</span><span class="sxs-lookup"><span data-stu-id="8d331-139">Here is the sequence of operations that occur when a `DataRow` is added, modified, or deleted:</span></span>  
  
1.  <span data-ttu-id="8d331-140">提示されたレコードを作成し、変更を適用します。</span><span class="sxs-lookup"><span data-stu-id="8d331-140">Create the proposed record and apply any changes.</span></span>  
  
2.  <span data-ttu-id="8d331-141">式以外の列の制約をチェックします。</span><span class="sxs-lookup"><span data-stu-id="8d331-141">Check constraints for non-expression columns.</span></span>  
  
3.  <span data-ttu-id="8d331-142">適宜 `RowChanging` イベントまたは `RowDeleting` イベントを発生させます。</span><span class="sxs-lookup"><span data-stu-id="8d331-142">Raise the `RowChanging` or `RowDeleting` events as applicable.</span></span>  
  
4.  <span data-ttu-id="8d331-143">提示されたレコードを現在のレコードとして設定します。</span><span class="sxs-lookup"><span data-stu-id="8d331-143">Set the proposed record to be the current record.</span></span>  
  
5.  <span data-ttu-id="8d331-144">関連するインデックスをすべて更新します。</span><span class="sxs-lookup"><span data-stu-id="8d331-144">Update any associated indexes.</span></span>  
  
6.  <span data-ttu-id="8d331-145">関連する `ListChanged` オブジェクトの `DataView` イベントおよび関連する `PropertyChanged` オブジェクトの `DataRowView` イベントを発生させます。</span><span class="sxs-lookup"><span data-stu-id="8d331-145">Raise `ListChanged` events for associated `DataView` objects and `PropertyChanged` events for associated `DataRowView` objects.</span></span>  
  
7.  <span data-ttu-id="8d331-146">すべての式列を評価します。ただし、これらの列に対する制約のチェックは、この段階では行われません。</span><span class="sxs-lookup"><span data-stu-id="8d331-146">Evaluate all expression columns, but delay checking any constraints on these columns.</span></span>  
  
8.  <span data-ttu-id="8d331-147">式列の評価によって影響を受ける、関連する `ListChanged` オブジェクトの `DataView` イベントおよび関連する `PropertyChanged` オブジェクトの `DataRowView` イベントを発生させます。</span><span class="sxs-lookup"><span data-stu-id="8d331-147">Raise `ListChanged` events for associated `DataView` objects and `PropertyChanged` events for associated `DataRowView` objects affected by the expression column evaluations.</span></span>  
  
9. <span data-ttu-id="8d331-148">適宜 `RowChanged` イベントまたは `RowDeleted` イベントを発生させます。</span><span class="sxs-lookup"><span data-stu-id="8d331-148">Raise `RowChanged` or `RowDeleted` events as applicable.</span></span>  
  
10. <span data-ttu-id="8d331-149">式列の制約をチェックします。</span><span class="sxs-lookup"><span data-stu-id="8d331-149">Check constraints on expression columns.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8d331-150">式列に対する変更で `DataTable` のイベントが発生することはありません。</span><span class="sxs-lookup"><span data-stu-id="8d331-150">Changes to expression columns never raise `DataTable` events.</span></span> <span data-ttu-id="8d331-151">式列に対する変更で発生するのは、`DataView` と `DataRowView` のイベントだけです。</span><span class="sxs-lookup"><span data-stu-id="8d331-151">Changes to expression columns only raise `DataView` and `DataRowView` events.</span></span> <span data-ttu-id="8d331-152">式列には他の複数の列に対する依存関係が存在することもあるため、1 回の `DataRow` 操作で複数回、評価される場合もあります。</span><span class="sxs-lookup"><span data-stu-id="8d331-152">Expression columns can have dependencies on multiple other columns, and can be evaluated multiple times during a single `DataRow` operation.</span></span> <span data-ttu-id="8d331-153">イベントは式が評価されるたびに発生するため、式列が変更された場合、1 回の `DataRow` 操作で複数の `ListChanged` イベントおよび `PropertyChanged` イベントが発生し、同じ式列に対して複数のイベントが発生する場合もあります。</span><span class="sxs-lookup"><span data-stu-id="8d331-153">Each expression evaluation raises events, and a single `DataRow` operation can raise multiple `ListChanged` and `PropertyChanged` events when expression columns are affected, possibly including multiple events for the same expression column.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="8d331-154"><xref:System.NullReferenceException> を `RowChanged` イベント ハンドラー内でスローしないでください。</span><span class="sxs-lookup"><span data-stu-id="8d331-154">Do not throw a <xref:System.NullReferenceException> within the `RowChanged` event handler.</span></span> <span data-ttu-id="8d331-155"><xref:System.NullReferenceException> が `RowChanged` の `DataTable` イベント内でスローされると、`DataTable` が破損します。</span><span class="sxs-lookup"><span data-stu-id="8d331-155">If a <xref:System.NullReferenceException> is thrown within the `RowChanged` event of a `DataTable`, then the `DataTable` will be corrupted.</span></span>  
  
### <a name="example"></a><span data-ttu-id="8d331-156">例</span><span class="sxs-lookup"><span data-stu-id="8d331-156">Example</span></span>  
 <span data-ttu-id="8d331-157">次の例では、`RowChanged`、`RowChanging`、`RowDeleted`、`RowDeleting`、`ColumnChanged`、`ColumnChanging`、`TableNewRow`、`TableCleared`、`TableClearing` の各イベントについてイベント ハンドラーを作成しています。</span><span class="sxs-lookup"><span data-stu-id="8d331-157">The following example demonstrates how to create event handlers for the `RowChanged`, `RowChanging`, `RowDeleted`, `RowDeleting`, `ColumnChanged`, `ColumnChanging`, `TableNewRow`, `TableCleared`, and `TableClearing` events.</span></span> <span data-ttu-id="8d331-158">イベントが発生すると、各イベント ハンドラーによって、出力結果がコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="8d331-158">Each event handler displays output in the console window when it is fired.</span></span>  
  
 [!code-csharp[DataWorks DataTable.Events#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.Events/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.Events#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.Events/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="8d331-159">参照</span><span class="sxs-lookup"><span data-stu-id="8d331-159">See Also</span></span>  
 [<span data-ttu-id="8d331-160">DataTable 内のデータの操作</span><span class="sxs-lookup"><span data-stu-id="8d331-160">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [<span data-ttu-id="8d331-161">DataAdapter のイベント処理</span><span class="sxs-lookup"><span data-stu-id="8d331-161">Handling DataAdapter Events</span></span>](../../../../../docs/framework/data/adonet/handling-dataadapter-events.md)  
 [<span data-ttu-id="8d331-162">DataSet のイベント処理</span><span class="sxs-lookup"><span data-stu-id="8d331-162">Handling DataSet Events</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md)  
 [<span data-ttu-id="8d331-163">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="8d331-163">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
