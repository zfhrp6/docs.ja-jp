---
title: "DataSet のイベント処理"
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
ms.assetid: 54edefe0-bc38-419b-b486-3d8a0c356f13
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6c87e805bd710b49ce805af8223cddb5c7036c50
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="handling-dataset-events"></a><span data-ttu-id="53186-102">DataSet のイベント処理</span><span class="sxs-lookup"><span data-stu-id="53186-102">Handling DataSet Events</span></span>
<span data-ttu-id="53186-103"><xref:System.Data.DataSet> オブジェクトには、 <xref:System.ComponentModel.MarshalByValueComponent.Disposed>、 <xref:System.Data.DataSet.Initialized>、 <xref:System.Data.DataSet.MergeFailed>という 3 つのイベントがあります。</span><span class="sxs-lookup"><span data-stu-id="53186-103">The <xref:System.Data.DataSet> object provides three events: <xref:System.ComponentModel.MarshalByValueComponent.Disposed>, <xref:System.Data.DataSet.Initialized>, and <xref:System.Data.DataSet.MergeFailed>.</span></span>  
  
## <a name="the-mergefailed-event"></a><span data-ttu-id="53186-104">MergeFailed イベント</span><span class="sxs-lookup"><span data-stu-id="53186-104">The MergeFailed Event</span></span>  
 <span data-ttu-id="53186-105">`DataSet` オブジェクトのイベントの中で最も使用頻度が高いイベントは、マージしようとしている `MergeFailed`オブジェクトのスキーマが競合する場合に発生する `DataSet` です。</span><span class="sxs-lookup"><span data-stu-id="53186-105">The most commonly used event of the `DataSet` object is `MergeFailed`, which is raised when the schema of the `DataSet` objects being merged are in conflict.</span></span> <span data-ttu-id="53186-106">この状況は、ターゲットとソースの <xref:System.Data.DataRow> が同じ主キー値を持ち、なおかつ、 <xref:System.Data.DataSet.EnforceConstraints%2A> プロパティが `true`に設定されている場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="53186-106">This occurs when a target and source <xref:System.Data.DataRow> have the same primary key value, and the <xref:System.Data.DataSet.EnforceConstraints%2A> property is set to `true`.</span></span> <span data-ttu-id="53186-107">たとえば、マージ対象のテーブルの主キーの列が 2 つの `DataSet` オブジェクトのテーブル間で同じ場合、例外がスローされ、 `MergeFailed` イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="53186-107">For example, if the primary key columns of a table being merged are the same between the tables in the two `DataSet` objects, an exception is thrown and the `MergeFailed` event is raised.</span></span> <span data-ttu-id="53186-108"><xref:System.Data.MergeFailedEventArgs> イベントに渡される `MergeFailed` オブジェクトには、2 つの <xref:System.Data.MergeFailedEventArgs.Conflict%2A> オブジェクト間のスキーマで発生した競合を示す `DataSet` プロパティ、および競合が発生したテーブルの名前を示す <xref:System.Data.MergeFailedEventArgs.Table%2A> プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="53186-108">The <xref:System.Data.MergeFailedEventArgs> object passed to the `MergeFailed` event have a <xref:System.Data.MergeFailedEventArgs.Conflict%2A> property that identifies the conflict in schema between the two `DataSet` objects, and a <xref:System.Data.MergeFailedEventArgs.Table%2A> property that identifies the name of the table in conflict.</span></span>  
  
 <span data-ttu-id="53186-109">次のコードは、`MergeFailed` イベントのイベント ハンドラーを追加する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="53186-109">The following code fragment demonstrates how to add an event handler for the `MergeFailed` event.</span></span>  
  
```vb  
AddHandler workDS.MergeFailed, New MergeFailedEventHandler( _  
  AddressOf DataSetMergeFailed)  
  
Private Shared Sub DataSetMergeFailed(  _  
  sender As Object,args As MergeFailedEventArgs)  
  Console.WriteLine("Merge failed for table " & args.Table.TableName)  
  Console.WriteLine("Conflict = " & args.Conflict)  
End Sub  
```  
  
```csharp  
workDS.MergeFailed += new MergeFailedEventHandler(DataSetMergeFailed);  
  
private static void DataSetMergeFailed(  
  object sender, MergeFailedEventArgs args)  
{  
  Console.WriteLine("Merge failed for table " + args.Table.TableName);  
  Console.WriteLine("Conflict = " + args.Conflict);  
}  
```  
  
## <a name="the-initialized-event"></a><span data-ttu-id="53186-110">Initialized イベント</span><span class="sxs-lookup"><span data-stu-id="53186-110">The Initialized Event</span></span>  
 <span data-ttu-id="53186-111"><xref:System.Data.DataSet.Initialized> イベントは、 `DataSet` のコンストラクターによって `DataSet`の新しいインスタンスが初期化された後に発生します。</span><span class="sxs-lookup"><span data-stu-id="53186-111">The <xref:System.Data.DataSet.Initialized> event occurs after the `DataSet` constructor initializes a new instance of the `DataSet`.</span></span>  
  
 <span data-ttu-id="53186-112"><xref:System.Data.DataSet.IsInitialized%2A> プロパティは、 `true` の初期化が完了した場合に `DataSet` を返します。それ以外の場合は `false`を返します。</span><span class="sxs-lookup"><span data-stu-id="53186-112">The <xref:System.Data.DataSet.IsInitialized%2A> property returns `true` if the `DataSet` has completed initialization; otherwise it returns `false`.</span></span> <span data-ttu-id="53186-113">この値は、 <xref:System.Data.DataSet.BeginInit%2A> の初期化を開始する `DataSet`メソッドによって <xref:System.Data.DataSet.IsInitialized%2A> が `false`に設定されます。</span><span class="sxs-lookup"><span data-stu-id="53186-113">The <xref:System.Data.DataSet.BeginInit%2A> method, which begins the initialization of a `DataSet`, sets <xref:System.Data.DataSet.IsInitialized%2A> to `false`.</span></span> <span data-ttu-id="53186-114">また、 <xref:System.Data.DataSet.EndInit%2A> の初期化を終了する `DataSet`メソッドによって `true`に設定されます。</span><span class="sxs-lookup"><span data-stu-id="53186-114">The <xref:System.Data.DataSet.EndInit%2A> method, which ends the initialization of the `DataSet`, sets it to `true`.</span></span> <span data-ttu-id="53186-115">これらのメソッドは、別のコンポーネントによって使用されている [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] を初期化する目的で、 `DataSet` のデザイン環境によって使用されます。</span><span class="sxs-lookup"><span data-stu-id="53186-115">These methods are used by the [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] design environment to initialize a `DataSet` that is being used by another component.</span></span> <span data-ttu-id="53186-116">通常、コード内で直接使用することはありません。</span><span class="sxs-lookup"><span data-stu-id="53186-116">You will not commonly use them in your code.</span></span>  
  
## <a name="the-disposed-event"></a><span data-ttu-id="53186-117">Disposed イベント</span><span class="sxs-lookup"><span data-stu-id="53186-117">The Disposed Event</span></span>  
 <span data-ttu-id="53186-118">`DataSet` は、 <xref:System.ComponentModel.MarshalByValueComponent> メソッドおよび <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> イベントの両方を公開する <xref:System.ComponentModel.MarshalByValueComponent.Disposed> クラスから派生しています。</span><span class="sxs-lookup"><span data-stu-id="53186-118">`DataSet` is derived from the <xref:System.ComponentModel.MarshalByValueComponent> class, which exposes both the <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> method and the <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event.</span></span> <span data-ttu-id="53186-119"><xref:System.ComponentModel.MarshalByValueComponent.Disposed>イベントは、コンポーネントで破棄されたイベントを待機するイベント ハンドラーを追加します。</span><span class="sxs-lookup"><span data-stu-id="53186-119">The <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event adds an event handler to listen to the disposed event on the component.</span></span> <span data-ttu-id="53186-120">使用することができます、<xref:System.ComponentModel.MarshalByValueComponent.Disposed>のイベント、`DataSet`を実行する場合は、ときにコード、<xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A>メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="53186-120">You can use the <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event of a `DataSet` if you want to execute code when the <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> method is called.</span></span> <span data-ttu-id="53186-121"><xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A>によって使用されるリソースを解放、<xref:System.ComponentModel.MarshalByValueComponent>です。</span><span class="sxs-lookup"><span data-stu-id="53186-121"><xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> releases the resources used by the <xref:System.ComponentModel.MarshalByValueComponent>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="53186-122">`DataSet`と`DataTable`オブジェクトから継承<xref:System.ComponentModel.MarshalByValueComponent>をサポートし、<xref:System.Runtime.Serialization.ISerializable>リモート処理用のインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="53186-122">The `DataSet` and `DataTable` objects inherit from <xref:System.ComponentModel.MarshalByValueComponent> and support the <xref:System.Runtime.Serialization.ISerializable> interface for remoting.</span></span> <span data-ttu-id="53186-123">これらは、リモート処理ができる唯一の ADO.NET オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="53186-123">These are the only ADO.NET objects that can be remoted.</span></span> <span data-ttu-id="53186-124">詳細については、「 [Remote Objects](http://msdn.microsoft.com/en-us/515686e6-0a8d-42f7-8188-73abede57c58)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="53186-124">For more information, see [Remote Objects](http://msdn.microsoft.com/en-us/515686e6-0a8d-42f7-8188-73abede57c58).</span></span>  
  
 <span data-ttu-id="53186-125">使用するときに使用可能なその他のイベントについては、`DataSet`を参照してください[DataTable イベントの処理](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)と[DataAdapter イベントの処理](../../../../../docs/framework/data/adonet/handling-dataadapter-events.md)です。</span><span class="sxs-lookup"><span data-stu-id="53186-125">For information about other events available when working with a `DataSet`, see [Handling DataTable Events](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md) and [Handling DataAdapter Events](../../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53186-126">参照</span><span class="sxs-lookup"><span data-stu-id="53186-126">See Also</span></span>  
 [<span data-ttu-id="53186-127">DataSet、DataTable、および DataView</span><span class="sxs-lookup"><span data-stu-id="53186-127">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="53186-128">データの検証</span><span class="sxs-lookup"><span data-stu-id="53186-128">Validating Data</span></span>](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)  
 [<span data-ttu-id="53186-129">ADO.NET でのデータの取得および変更</span><span class="sxs-lookup"><span data-stu-id="53186-129">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="53186-130">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="53186-130">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
