---
title: "DataView イベントの処理"
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
ms.assetid: e5675663-fc91-4e0d-87a9-481b25b64c0f
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2abade8bbbf5ab8a9d2cf146271e89703ec34cb9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="handling-dataview-events"></a>DataView イベントの処理
<xref:System.Data.DataView.ListChanged> の <xref:System.Data.DataView> イベントを使用して、ビューが更新されているかどうかを確認できます。 基になるテーブルの行の追加、削除、または変更や、このスキーマの列の追加または削除、親子のリレーションシップの変更など、これらの更新を行うとこのイベントが発生します。 **ListChanged**イベントもユーザーに通知を表示している行のリストが新しい並べ替え順序またはフィルターの適用により大幅に変更します。  
  
 **ListChanged**イベントを実装して、 **ListChangedEventHandler**の委任、<xref:System.ComponentModel>入力名前空間として受け取り、<xref:System.ComponentModel.ListChangedEventArgs>オブジェクト。 使用して変更の種類が発生したかを決定できます、<xref:System.ComponentModel.ListChangedType>の列挙値に、 **ListChangedType**のプロパティ、 **ListChangedEventArgs**オブジェクト。 追加変更、削除、または、行を移動追加または削除された行の新しいインデックスと、削除された行の古いインデックスにアクセスできますを使用して、 **NewIndex**のプロパティ、 **ListChangedEventArgs**オブジェクト。 移動先の行の場合、移動された行の古いインデックス アクセスできるを使用して、 **OldIndex**のプロパティ、 **ListChangedEventArgs**オブジェクト。  
  
 **DataViewManager**も公開、 **ListChanged**テーブルが追加または削除された場合、またはに、変更を加えた場合に通知するイベント、**リレーション**のコレクション、基になる**データセット**です。  
  
 次のコード例は、追加する方法を示します、 **ListChanged**イベント ハンドラー。  
  
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
  
## <a name="see-also"></a>関連項目  
 <xref:System.Data.DataView>  
 <xref:System.ComponentModel.ListChangedEventHandler>  
 [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
