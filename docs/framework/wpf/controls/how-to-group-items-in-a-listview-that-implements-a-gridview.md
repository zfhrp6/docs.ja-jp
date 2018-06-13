---
title: '方法 : GridView を実装する ListView の項目をグループ化する'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], grouping items with GridViews
- grouping items in ListViews implementing GridViews [WPF]
- GridView controls [WPF], grouping items
ms.assetid: eebef25b-ddc6-424e-a66d-ea228d1bf33d
ms.openlocfilehash: 76074449d4ea1454689c51ecad54d7c495f00872
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33551909"
---
# <a name="how-to-group-items-in-a-listview-that-implements-a-gridview"></a>方法 : GridView を実装する ListView の項目をグループ化する
この例は、グループ内の項目を表示する方法を示します、<xref:System.Windows.Controls.GridView>の表示モード、<xref:System.Windows.Controls.ListView>コントロール。  
  
## <a name="example"></a>例  
 内の項目のグループを表示する、 <xref:System.Windows.Controls.ListView>、定義、<xref:System.Windows.Data.CollectionViewSource>です。 次の例は、<xref:System.Windows.Data.CollectionViewSource>の値に基づいてデータ項目をグループ化、`Catalog`データ フィールドです。  
  
 [!code-xaml[GridViewWithGroups#GroupingCollectionViewSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#groupingcollectionviewsource)]  
  
 次の例のセット、<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>の<xref:System.Windows.Controls.ListView>を<xref:System.Windows.Data.CollectionViewSource>前の例を定義します。 また、<xref:System.Windows.Controls.ItemsControl.GroupStyle%2A>を実装する、<xref:System.Windows.Controls.Expander>コントロール。  
  
 [!code-xaml[GridViewWithGroups#ListViewGroups](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewgroups)]  
[!code-xaml[GridViewWithGroups#ListViewEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewend)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [方法トピック](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [ListView の概要](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [GridView の概要](../../../../docs/framework/wpf/controls/gridview-overview.md)
