---
title: "DataSet のイベント処理 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 54edefe0-bc38-419b-b486-3d8a0c356f13
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# DataSet のイベント処理
<xref:System.Data.DataSet> オブジェクトには、<xref:System.ComponentModel.MarshalByValueComponent.Disposed>、<xref:System.Data.DataSet.Initialized>、<xref:System.Data.DataSet.MergeFailed> という 3 つのイベントがあります。  
  
## MergeFailed イベント  
 `DataSet` オブジェクトのイベントの中で最も使用頻度が高いイベントは、マージしようとしている `MergeFailed` オブジェクトのスキーマが競合する場合に発生する `DataSet` です。 この状況は、ターゲットとソースの <xref:System.Data.DataRow> が同じ主キー値を持ち、なおかつ、<xref:System.Data.DataSet.EnforceConstraints%2A> プロパティが `true` に設定されている場合に発生します。 たとえば、マージ対象のテーブルの主キーの列が 2 つの `DataSet` オブジェクトのテーブル間で同じ場合、例外がスローされ、`MergeFailed` イベントが発生します。<xref:System.Data.MergeFailedEventArgs> イベントに渡される `MergeFailed` オブジェクトには、2 つの <xref:System.Data.MergeFailedEventArgs.Conflict%2A> オブジェクト間のスキーマで発生した競合を示す `DataSet` プロパティ、および競合が発生したテーブルの名前を示す <xref:System.Data.MergeFailedEventArgs.Table%2A> プロパティがあります。  
  
 次のコードは、`MergeFailed` イベントのイベント ハンドラーを追加する方法を示しています。  
  
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
  
## Initialized イベント  
 <xref:System.Data.DataSet.Initialized> イベントは、`DataSet` のコンストラクターによって `DataSet` の新しいインスタンスが初期化された後に発生します。  
  
 <xref:System.Data.DataSet.IsInitialized%2A> プロパティは、`true` の初期化が完了した場合に `DataSet` を返します。それ以外の場合は `false` を返します。 この値は、<xref:System.Data.DataSet.BeginInit%2A> の初期化を開始する `DataSet` メソッドによって <xref:System.Data.DataSet.IsInitialized%2A> が `false` に設定されます。 また、<xref:System.Data.DataSet.EndInit%2A> の初期化を終了する `DataSet` メソッドによって `true` に設定されます。 これらのメソッドは、別のコンポーネントによって使用されている [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] を初期化する目的で、`DataSet` のデザイン環境によって使用されます。 通常、コード内で直接使用することはありません。  
  
## Disposed イベント  
 `DataSet` は、<xref:System.ComponentModel.MarshalByValueComponent> メソッドおよび <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> イベントの両方を公開する <xref:System.ComponentModel.MarshalByValueComponent.Disposed> クラスから派生しています。<xref:System.ComponentModel.MarshalByValueComponent.Disposed>イベントでは、コンポーネントが破棄されたことを伝えるイベントを待機するためのイベント ハンドラーを追加します。<xref:System.ComponentModel.MarshalByValueComponent.Disposed> の `DataSet` イベントを使用することで、<xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> メソッドが呼び出されたときにコードを実行できます。<xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> は、<xref:System.ComponentModel.MarshalByValueComponent> で使用したリソースを解放します。  
  
> [!NOTE]
>  `DataSet` オブジェクトと `DataTable` オブジェクトは <xref:System.ComponentModel.MarshalByValueComponent> から継承し、リモート処理用の <xref:System.Runtime.Serialization.ISerializable> インターフェイスをサポートします。 これらは、リモート処理ができる唯一の ADO.NET オブジェクトです。 詳細については、「[Remote Objects](http://msdn.microsoft.com/ja-jp/515686e6-0a8d-42f7-8188-73abede57c58)」を参照してください。  
  
 `DataSet` の使用時に使用できるその他のイベントについては、「[DataTable イベントの処理](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)」および「[DataAdapter のイベント処理](../../../../../docs/framework/data/adonet/handling-dataadapter-events.md)」を参照してください。  
  
## 参照  
 [DataSets、DataTables、および DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [データの検証](../Topic/Validating%20Data.md)   
 [ADO.NET でのデータの取得および変更](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)   
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)