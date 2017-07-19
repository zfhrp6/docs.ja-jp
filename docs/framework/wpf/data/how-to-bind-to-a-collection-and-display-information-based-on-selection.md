---
title: "方法 : コレクションにバインドして選択に基づく情報を表示する | Microsoft Docs"
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
  - "データ バインディング, バインド (コレクションに)"
  - "データ バインディング, 作成 (データ コレクションのビューを)"
  - "データ バインディング, 選択 (ビューのデータを)"
  - "データ コレクション, 選択 (ビューのデータを)"
ms.assetid: 952a7d76-dd29-49e5-86f5-32c4530e70eb
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : コレクションにバインドして選択に基づく情報を表示する
簡単なマスター詳細シナリオには、<xref:System.Windows.Controls.ListBox> のようなデータ バインドされた <xref:System.Windows.Controls.ItemsControl> があります。  ユーザー選択に基づいて、選択された項目に関する情報をさらに表示します。  このシナリオを実装する方法を次の例に示します。  
  
## 使用例  
 この例では、`People` は `Person` クラスの <xref:System.Collections.ObjectModel.ObservableCollection%601> です。  この `Person` クラスには、`FirstName`、`LastName`、および `HomeTown` という 3 つのプロパティが含まれ、すべて `string` 型です。  
  
 [!code-xml[CollectionBinding#Source](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#source)]  
[!code-xml[CollectionBinding#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#ui)]  
  
 <xref:System.Windows.Controls.ContentControl> は、`Person` の情報の提示方法を定義する、次のような <xref:System.Windows.DataTemplate> を使用します。  
  
 [!code-xml[CollectionBinding#DetailTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#detailtemplate)]  
  
 この例が生成するスクリーンショットを次に示します。  <xref:System.Windows.Controls.ContentControl> は、選択されている人の他のプロパティを示します。  
  
 ![コレクションへのバインディング](../../../../docs/framework/wpf/data/media/databinding-collectionbindingsample.png "DataBinding\_CollectionBindingSample")  
  
 この例では、次の 2 つの点に注意する必要があります。  
  
1.  <xref:System.Windows.Controls.ListBox> と <xref:System.Windows.Controls.ContentControl> は、同じソースにバインドしています。  どちらのコントロールもコレクション オブジェクト全体にバインドしているので、どちらのバインディングの <xref:System.Windows.Data.Binding.Path%2A> プロパティも指定されていません。  
  
2.  この例が動作するには、<xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> プロパティを `true` に設定する必要があります。  このプロパティを設定すると、選択されている項目は常に <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A> として設定されます。  または、<xref:System.Windows.Controls.ListBox> が <xref:System.Windows.Data.CollectionViewSource> からデータを取得する場合は、選択と現在の項目が自動的に同期されます。  
  
 `Person` クラスが次のように `ToString` メソッドをオーバーライドすることに注意してください。  既定では、<xref:System.Windows.Controls.ListBox> は `ToString` を呼び出して、バインドされたコレクション内の各オブジェクトの文字列表現を表示します。  これにより、各 `Person` は <xref:System.Windows.Controls.ListBox> の名前として表示されます。  
  
 [!code-csharp[CollectionBinding#ToString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Data.cs#tostring)]
 [!code-vb[CollectionBinding#ToString](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionBinding/VisualBasic/Person.vb#tostring)]  
  
## 参照  
 [階層データでマスター詳細パターンを使用する](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md)   
 [階層 XML データでマスター詳細パターンを使用する](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)   
 [データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [データ テンプレートの概要](../../../../docs/framework/wpf/data/data-templating-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)