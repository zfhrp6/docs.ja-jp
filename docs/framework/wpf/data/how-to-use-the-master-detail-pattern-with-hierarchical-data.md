---
title: '方法 : 階層データでマスター詳細パターンを使用する'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: 11429b9e-058d-4084-bfb6-2cf209c8ddf7
ms.openlocfilehash: 46733b462861bdac3381cdacb8f2fbe0536d12eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-data"></a>方法 : 階層データでマスター詳細パターンを使用する
この例では、マスター/詳細シナリオを実装する方法を示します。  
  
## <a name="example"></a>例  
 この例では`LeagueList`のコレクションは、`Leagues`です。 各`League`が、`Name`およびのコレクションの`Divisions`、および各`Division`名は、一連の`Teams`します。 各`Team`team 名前が指定されています。  
  
 [!code-xaml[MasterDetail#HowTo1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto1)]  
[!code-xaml[MasterDetail#HowTo2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto2)]  
  
 次に示すのは、この例のスクリーンショットです。 `Divisions` <xref:System.Windows.Controls.ListBox>の選択項目が自動的に追跡、 `Leagues` <xref:System.Windows.Controls.ListBox>し、対応するデータを表示します。 `Teams` <xref:System.Windows.Controls.ListBox>他の 2 つの選択項目を追跡<xref:System.Windows.Controls.ListBox>コントロール。  
  
 ![マスター&#45;詳細の例](../../../../docs/framework/wpf/data/media/databindingmasterdetailsample.png "DataBindingMasterDetailSample")  
  
 この例では注意する 2 つの点は次のとおりです。  
  
1.  3 つ<xref:System.Windows.Controls.ListBox>コントロールを同じソースにバインドします。 設定する、<xref:System.Windows.Data.Binding.Path%2A>するデータのレベルを指定するバインドのプロパティ、<xref:System.Windows.Controls.ListBox>を表示します。  
  
2.  設定する必要があります、<xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A>プロパティを`true`上、<xref:System.Windows.Controls.ListBox>コントロールを追跡して、選択します。 このプロパティを設定すると、選択した項目として常に設定されている、<xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>です。 また場合、<xref:System.Windows.Controls.ListBox>からデータを取得、 <xref:System.Windows.Data.CollectionViewSource>、選択範囲と通貨を自動的に同期します。  
  
 使用しているときに、手法は若干異なります[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]データ。 例については、次を参照してください。[階層の XML データを、マスター/詳細形式のパターンを使用して](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.HierarchicalDataTemplate>  
 [コレクションにバインドして選択に基づく情報を表示する](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md)  
 [データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [データ テンプレートの概要](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [方法トピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
