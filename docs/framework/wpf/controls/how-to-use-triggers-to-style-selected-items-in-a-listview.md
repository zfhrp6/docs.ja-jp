---
title: '方法 : トリガーを使用して、ListView で選択された項目のスタイルを設定する'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], styling
ms.assetid: 1e2bdce0-afe8-4507-9b18-f33de43de25a
ms.openlocfilehash: 1741ce84fab1639409a7c834845573239c51cc35
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33554912"
---
# <a name="how-to-use-triggers-to-style-selected-items-in-a-listview"></a>方法 : トリガーを使用して、ListView で選択された項目のスタイルを設定する
この例は、定義する方法を示します<xref:System.Windows.Style.Triggers%2A>の<xref:System.Windows.Controls.ListViewItem>コントロールできるように時のプロパティの値、 <xref:System.Windows.Controls.ListViewItem> 、変更、<xref:System.Windows.Style>の<xref:System.Windows.Controls.ListViewItem>対応する変更点です。  
  
## <a name="example"></a>例  
 場合は、<xref:System.Windows.Style>の<xref:System.Windows.Controls.ListViewItem>プロパティの変更に応答を変更するには、定義<xref:System.Windows.Style.Triggers%2A>の<xref:System.Windows.Style>を変更します。  
  
 次の例では定義、<xref:System.Windows.Trigger>が設定された、<xref:System.Windows.Controls.Control.Foreground%2A>プロパティを<xref:System.Windows.Media.Brushes.Blue%2A>し、変更、<xref:System.Windows.FrameworkElement.Cursor%2A>を表示する、<xref:System.Windows.Input.CursorType.Hand>ときに、<xref:System.Windows.UIElement.IsMouseOver%2A>プロパティに対する変更を`true`です。  
  
 [!code-xaml[ListViewChkBox#ListViewItemTriggersStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersstart)]  
[!code-xaml[ListViewChkBox#Trigger](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#trigger)]  
[!code-xaml[ListViewChkBox#ListViewItemTriggersEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersend)]  
  
 次の例では定義、<xref:System.Windows.MultiTrigger>が設定された、<xref:System.Windows.Controls.Control.Foreground%2A>のプロパティ、<xref:System.Windows.Controls.ListViewItem>に<xref:System.Windows.Media.Brushes.Yellow%2A>ときに、<xref:System.Windows.Controls.ListViewItem>選択された項目し、キーボード フォーカスがあります。  
  
 [!code-xaml[ListViewChkBox#ListViewItemTriggersStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersstart)]  
[!code-xaml[ListViewChkBox#MultiTrigger](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#multitrigger)]  
[!code-xaml[ListViewChkBox#ListViewItemTriggersEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersend)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Controls.Control>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [方法トピック](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [ListView の概要](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [GridView の概要](../../../../docs/framework/wpf/controls/gridview-overview.md)
