---
title: '方法 : コレクションにバインドして選択に基づく情報を表示する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data collections [WPF], selecting data for views
- data binding [WPF], creating views of data collections
- data binding [WPF], selecting data for views
- data binding [WPF], binding to collections
ms.assetid: 952a7d76-dd29-49e5-86f5-32c4530e70eb
ms.openlocfilehash: 154f4b9b6024d064e73d64c44e2398a5da47052c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557410"
---
# <a name="how-to-bind-to-a-collection-and-display-information-based-on-selection"></a>方法 : コレクションにバインドして選択に基づく情報を表示する
マスター/詳細形式の単純なシナリオでデータ バインドがある<xref:System.Windows.Controls.ItemsControl>など、<xref:System.Windows.Controls.ListBox>です。 詳細については、選択した項目を表示するユーザーの選択に基づいて、です。 この例では、このシナリオを実装する方法を示します。  
  
## <a name="example"></a>例  
 この例では`People`は、<xref:System.Collections.ObjectModel.ObservableCollection%601>の`Person`クラスです。 これは、`Person`クラスには、3 つのプロパティが含まれています: `FirstName`、 `LastName`、および`HomeTown`、すべての種類の`string`します。  
  
 [!code-xaml[CollectionBinding#Source](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#source)]  
[!code-xaml[CollectionBinding#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#ui)]  
  
 <xref:System.Windows.Controls.ContentControl> 、次を使用して<xref:System.Windows.DataTemplate>を定義する方法の詳細について、`Person`が表示されます。  
  
 [!code-xaml[CollectionBinding#DetailTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#detailtemplate)]  
  
 この例の生成のスクリーン ショットを次に示します。 <xref:System.Windows.Controls.ContentControl>選択されているユーザーの他のプロパティを示しています。  
  
 ![コレクションへのバインド](../../../../docs/framework/wpf/data/media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")  
  
 この例では注意する 2 つの点は次のとおりです。  
  
1.  <xref:System.Windows.Controls.ListBox>と<xref:System.Windows.Controls.ContentControl>同じソースにバインドします。 <xref:System.Windows.Data.Binding.Path%2A>コレクション オブジェクト全体に両方のコントロールをバインドするため、どちらのバインディングのプロパティが指定されていません。  
  
2.  設定する必要があります、<xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A>プロパティを`true`これを行います。 このプロパティを設定すると、選択した項目として常に設定されている、<xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>です。 また場合、<xref:System.Windows.Controls.ListBox>からデータを取得、 <xref:System.Windows.Data.CollectionViewSource>、選択範囲と通貨を自動的に同期します。  
  
 なお、`Person`クラスのオーバーライド、`ToString`メソッドは次のようです。 既定では、<xref:System.Windows.Controls.ListBox>呼び出し`ToString`し、バインドされたコレクションの各オブジェクトの文字列表現を表示します。 その理由は各`Person`の最初の名前として表示されます、<xref:System.Windows.Controls.ListBox>です。  
  
 [!code-csharp[CollectionBinding#ToString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Data.cs#tostring)]
 [!code-vb[CollectionBinding#ToString](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionBinding/VisualBasic/Person.vb#tostring)]  
  
## <a name="see-also"></a>関連項目  
 [階層データでマスター詳細パターンを使用する](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md)  
 [階層 XML データでマスター詳細パターンを使用する](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)  
 [データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [データ テンプレートの概要](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [方法トピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
