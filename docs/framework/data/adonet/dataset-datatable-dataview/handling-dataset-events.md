---
title: DataSet のイベント処理
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54edefe0-bc38-419b-b486-3d8a0c356f13
ms.openlocfilehash: 486f38e2900eb85dbffbb4f9a9d0e6753267e32b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758322"
---
# <a name="handling-dataset-events"></a>DataSet のイベント処理
<xref:System.Data.DataSet> オブジェクトには、 <xref:System.ComponentModel.MarshalByValueComponent.Disposed>、 <xref:System.Data.DataSet.Initialized>、 <xref:System.Data.DataSet.MergeFailed>という 3 つのイベントがあります。  
  
## <a name="the-mergefailed-event"></a>MergeFailed イベント  
 `DataSet` オブジェクトのイベントの中で最も使用頻度が高いイベントは、マージしようとしている `MergeFailed`オブジェクトのスキーマが競合する場合に発生する `DataSet` です。 この状況は、ターゲットとソースの <xref:System.Data.DataRow> が同じ主キー値を持ち、なおかつ、 <xref:System.Data.DataSet.EnforceConstraints%2A> プロパティが `true`に設定されている場合に発生します。 たとえば、マージ対象のテーブルの主キーの列が 2 つの `DataSet` オブジェクトのテーブル間で同じ場合、例外がスローされ、 `MergeFailed` イベントが発生します。 <xref:System.Data.MergeFailedEventArgs> イベントに渡される `MergeFailed` オブジェクトには、2 つの <xref:System.Data.MergeFailedEventArgs.Conflict%2A> オブジェクト間のスキーマで発生した競合を示す `DataSet` プロパティ、および競合が発生したテーブルの名前を示す <xref:System.Data.MergeFailedEventArgs.Table%2A> プロパティがあります。  
  
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
  
## <a name="the-initialized-event"></a>Initialized イベント  
 <xref:System.Data.DataSet.Initialized> イベントは、 `DataSet` のコンストラクターによって `DataSet`の新しいインスタンスが初期化された後に発生します。  
  
 <xref:System.Data.DataSet.IsInitialized%2A> プロパティは、 `true` の初期化が完了した場合に `DataSet` を返します。それ以外の場合は `false`を返します。 この値は、 <xref:System.Data.DataSet.BeginInit%2A> の初期化を開始する `DataSet`メソッドによって <xref:System.Data.DataSet.IsInitialized%2A> が `false`に設定されます。 また、 <xref:System.Data.DataSet.EndInit%2A> の初期化を終了する `DataSet`メソッドによって `true`に設定されます。 これらのメソッドは、Visual Studio のデザイン環境が初期化に使用される、`DataSet`他のコンポーネントで使用されています。 通常、コード内で直接使用することはありません。  
  
## <a name="the-disposed-event"></a>Disposed イベント  
 `DataSet` は、 <xref:System.ComponentModel.MarshalByValueComponent> メソッドおよび <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> イベントの両方を公開する <xref:System.ComponentModel.MarshalByValueComponent.Disposed> クラスから派生しています。 <xref:System.ComponentModel.MarshalByValueComponent.Disposed>イベントは、コンポーネントで破棄されたイベントを待機するイベント ハンドラーを追加します。 使用することができます、<xref:System.ComponentModel.MarshalByValueComponent.Disposed>のイベント、`DataSet`を実行する場合は、ときにコード、<xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A>メソッドが呼び出されます。 <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> によって使用されるリソースを解放、<xref:System.ComponentModel.MarshalByValueComponent>です。  
  
> [!NOTE]
>  `DataSet`と`DataTable`オブジェクトから継承<xref:System.ComponentModel.MarshalByValueComponent>をサポートし、<xref:System.Runtime.Serialization.ISerializable>リモート処理用のインターフェイスです。 これらは、リモート処理ができる唯一の ADO.NET オブジェクトです。 詳細については、次を参照してください。[リモート オブジェクト](http://msdn.microsoft.com/library/515686e6-0a8d-42f7-8188-73abede57c58)です。  
  
 使用するときに使用可能なその他のイベントについては、`DataSet`を参照してください[DataTable イベントの処理](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)と[DataAdapter イベントの処理](../../../../../docs/framework/data/adonet/handling-dataadapter-events.md)です。  
  
## <a name="see-also"></a>関連項目  
 [DataSet、DataTable、および DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [データの検証](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)  
 [ADO.NET でのデータの取得および変更](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
