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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: bf3b02227de5068a031cedb73269148c7d5262a0
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
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
  
## <a name="see-also"></a>参照  
 <xref:System.Data.DataView>  
 <xref:System.ComponentModel.ListChangedEventHandler>  
 [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
