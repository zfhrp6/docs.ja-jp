---
title: '方法: ビュー内のデータを並べ替える'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], sorting data in views
- data binding [WPF], grouping data in views
- grouping data in views [WPF]
- views [WPF], sorting data
- views [WPF], grouping data
- sorting data in views [WPF]
ms.assetid: f4c43578-01b7-4774-a953-acb95a13b94a
ms.openlocfilehash: 5c79261983fcf6200120bcfbf180d155aca3c3c9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556758"
---
# <a name="how-to-sort-data-in-a-view"></a>方法: ビュー内のデータを並べ替える
この例では、ビュー内のデータを並べ替える方法について説明します。  
  
## <a name="example"></a>例  
 次の例では、単純な<xref:System.Windows.Controls.ListBox>と<xref:System.Windows.Controls.Button>:  
  
 [!code-xaml[ListBoxSort_snip#HowTo](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml#howto)]  
  
 <xref:System.Windows.Controls.Primitives.ButtonBase.Click>ボタンのイベント ハンドラーには内の項目の並べ替えにロジックが含まれています、<xref:System.Windows.Controls.ListBox>降順でします。 これを行うために項目を追加する、<xref:System.Windows.Controls.ListBox>にこのように追加、<xref:System.Windows.Controls.ItemCollection>の<xref:System.Windows.Controls.ListBox>、および<xref:System.Windows.Controls.ItemCollection>から派生した、<xref:System.Windows.Data.CollectionView>クラスです。 バインドする場合、<xref:System.Windows.Controls.ListBox>を使用してコレクションに、<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>プロパティを並べ替えるには同じ手法を使用することができます。  
  
 [!code-csharp[ListBoxSort_snip#HowToCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml.cs#howtocode)]
 [!code-vb[ListBoxSort_snip#HowToCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxSort_snip/visualbasic/window1.xaml.vb#howtocode)]  
  
 ビュー オブジェクトへの参照がある限り、他のコレクション ビューの内容を並べ替えるには同じ手法を使用できます。 ビューを取得する方法の例は、次を参照してください。[データ コレクションの既定のビューを取得する](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md)です。 別の例では、次を参照してください。 [、GridView 列のヘッダーがクリックされたときの並べ替え](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)です。 ビューの詳細についてでのコレクションにバインディングを参照してください。[データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)です。  
  
 並べ替えのロジックを適用する方法の例については[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]を参照してください[並べ替えとグループを使用して XAML でのビュー データ](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Data.ListCollectionView.CustomSort%2A>  
 [ヘッダーがクリックされたときに GridView 列を並べ替える](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)  
 [データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [ビュー内のデータをフィルター処理する](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)  
 [方法トピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
