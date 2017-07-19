---
title: "方法: ビュー内のデータを並べ替える | Microsoft Docs"
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
  - "データ バインディング, グループ化 (ビューのデータを)"
  - "データ バインディング, 並べ替え (ビューのデータを)"
  - "グループ化 (ビューのデータを)"
  - "並べ替え (ビューのデータを)"
  - "ビュー, グループ化 (データを)"
  - "ビュー, 並べ替え (データの)"
ms.assetid: f4c43578-01b7-4774-a953-acb95a13b94a
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# 方法: ビュー内のデータを並べ替える
この例では、ビュー内のデータを並べ替える方法を示します。  
  
## 使用例  
 簡単な <xref:System.Windows.Controls.ListBox> と <xref:System.Windows.Controls.Button> を作成する例を次に示します。  
  
 [!code-xml[ListBoxSort_snip#HowTo](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml#howto)]  
  
 ボタンの <xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベント ハンドラーには、<xref:System.Windows.Controls.ListBox> 内の項目を降順に並べ替えるロジックが含まれています。  この方法が可能なのは、こうして <xref:System.Windows.Controls.ListBox> に項目を追加すると <xref:System.Windows.Controls.ListBox> の <xref:System.Windows.Controls.ItemCollection> に項目が追加され、<xref:System.Windows.Controls.ItemCollection> は <xref:System.Windows.Data.CollectionView> クラスから派生しているためです。  <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> プロパティを使用してコレクションに <xref:System.Windows.Controls.ListBox> をバインドしている場合も、同じ手法を使用して並べ替えることができます。  
  
 [!code-csharp[ListBoxSort_snip#HowToCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml.cs#howtocode)]
 [!code-vb[ListBoxSort_snip#HowToCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxSort_snip/visualbasic/window1.xaml.vb#howtocode)]  
  
 ビュー オブジェクトに対する参照がある限り、同じ手法を使用して、他のコレクション ビューのコンテンツも並べ替えることができます。  ビューを取得する方法の例については、「[データ コレクションの既定のビューを取得する](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md)」を参照してください。  別の例については、「[ヘッダーがクリックされたときに GridView 列を並べ替える](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)」を参照してください。  ビューの詳細については、「[データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)」の「コレクションへのバインド」を参照してください。  
  
 並べ替えロジックに [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] を適用する方法の例については、「[XAML でビューを使用してデータの並べ替えおよびグループ化を行う](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Data.ListCollectionView.CustomSort%2A>   
 [ヘッダーがクリックされたときに GridView 列を並べ替える](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)   
 [データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [ビュー内のデータをフィルター処理する](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)   
 [方法のトピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)