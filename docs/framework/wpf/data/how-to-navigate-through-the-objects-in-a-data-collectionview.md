---
title: "方法 : データ CollectionView のオブジェクト間を移動する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CollectionView, 移動 (オブジェクト間を)"
  - "データ バインディング, 移動 (データ CollectionView のオブジェクト間を)"
  - "移動 (データ CollectionView のオブジェクト間を)"
ms.assetid: fcd37590-bce1-4ac9-8b74-3b96c7458b8a
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : データ CollectionView のオブジェクト間を移動する
ビューを使用すれば、同じデータ コレクションを、並べ替え、フィルター処理、またはグループ化するによってさまざまな方法で表示できます。  ビューでは現在のレコード ポインターの概念を用いており、このポインターは移動できます。  この例では、現在のオブジェクトを取得する方法と、<xref:System.Windows.Data.CollectionView> クラスにある機能を使用してデータ コレクション内のオブジェクト間を移動する方法を示します。  
  
## 使用例  
 この例では、`myCollectionView` は、連結コレクションのビューである <xref:System.Windows.Data.CollectionView> オブジェクトです。  
  
 次の例では、`OnButton` がアプリケーションの \[`Previous`\] ボタンと \[`Next`\] ボタン用のイベント ハンドラーで、これらのボタンを使用してユーザーがデータ コレクション内を移動できます。  <xref:System.Windows.Data.CollectionView.IsCurrentBeforeFirst%2A> と <xref:System.Windows.Data.CollectionView.IsCurrentAfterLast%2A> プロパティが <xref:System.Windows.Data.CollectionView.MoveCurrentToFirst%2A> と <xref:System.Windows.Data.CollectionView.MoveCurrentToLast%2A> が必要に応じて呼び出せるように、カレント レコード ポインターが最初とリストの末尾のそれぞれに達したかどうかを報告します。  
  
 ビューの <xref:System.Windows.Data.CollectionView.CurrentItem%2A> プロパティは、コレクションの現在の順序項目を返すために、`Order` としてキャストされます。  
  
 [!code-csharp[CollectionView#OnButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#onbutton)]
 [!code-vb[CollectionView#OnButton](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#onbutton)]  
  
## 参照  
 [データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [ビュー内のデータの並べ替え](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)   
 [ビュー内のデータをフィルター処理する](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)   
 [XAML でビューを使用してデータの並べ替えおよびグループ化を行う](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)   
 [方法のトピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)