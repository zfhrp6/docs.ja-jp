---
title: "DataView イベントの処理 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e5675663-fc91-4e0d-87a9-481b25b64c0f
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# DataView イベントの処理
<xref:System.Data.DataView> の <xref:System.Data.DataView.ListChanged> イベントを使用して、ビューが更新されているかどうかを確認できます。  基になるテーブルの行の追加、削除、または変更や、このスキーマの列の追加または削除、親子のリレーションシップの変更など、これらの更新を行うとこのイベントが発生します。  さらに、現在表示されている行のリストが新しい並べ替え順序またはフィルターの適用により大幅に変更された場合、**ListChanged** イベントはそのことも通知します。  
  
 **ListChanged** イベントは、<xref:System.ComponentModel> 名前空間の **ListChangedEventHandler** デリゲートを実装し、<xref:System.ComponentModel.ListChangedEventArgs> オブジェクトを入力として受け取ります。  発生した変更の内容を確認するには、**ListChangedEventArgs** オブジェクトの **ListChangedType** プロパティの <xref:System.ComponentModel.ListChangedType> 列挙値を使用します。  行の追加、削除、または移動による変更の場合、追加された行または移動された行の新しいインデックスと削除された行の古いインデックスには、**ListChangedEventArgs** オブジェクトの **NewIndex** プロパティを使用してアクセスできます。  移動された行の場合、移動前の古いインデックスにアクセスするには **ListChangedEventArgs** オブジェクトの **OldIndex** プロパティを使用します。  
  
 **DataViewManager** は、さらにテーブルが追加または削除された場合に、または基になる **DataSet** の **Relations** コレクションが変更された場合に、そのことを通知するために **ListChanged** イベントを公開します。  
  
 **ListChanged** イベント ハンドラーを追加する方法を次のコード サンプルに示します。  
  
```vb  
AddHandler custView.ListChanged, _  
  New System.ComponentModel.ListChangedEventHandler( _  
  AddressOf OnListChanged)  
  
Private Shared Sub OnListChanged( _  
  sender As Object, args As System.ComponentModel.ListChangedEventArgs)  
  Console.WriteLine("ListChanged:")  
  Console.WriteLine(vbTab & "    Type = " & _  
    System.Enum.GetName(args.ListChangedType.GetType(), _  
    args.ListChangedType))  
  Console.WriteLine(vbTab & "OldIndex = " & args.OldIndex)  
  Console.WriteLine(vbTab & "NewIndex = " & args.NewIndex)  
End Sub  
  
```  
  
```csharp  
custView.ListChanged  += new   
  System.ComponentModel.ListChangedEventHandler(OnListChanged);  
  
protected static void OnListChanged(object sender,   
  System.ComponentModel.ListChangedEventArgs args)  
{  
  Console.WriteLine("ListChanged:");  
  Console.WriteLine("\t    Type = " + args.ListChangedType);  
  Console.WriteLine("\tOldIndex = " + args.OldIndex);  
  Console.WriteLine("\tNewIndex = " + args.NewIndex);  
}  
```  
  
## 参照  
 <xref:System.Data.DataView>   
 <xref:System.ComponentModel.ListChangedEventHandler>   
 [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)