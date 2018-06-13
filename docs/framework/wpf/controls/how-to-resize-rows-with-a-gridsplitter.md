---
title: '方法 : GridSplitter を使用して行のサイズを変更する'
ms.date: 03/30/2017
helpviewer_keywords:
- resizing grid rows [WPF]
- grid rows [WPF], resizing
- GridSplitter control [WPF], resizing grid rows
ms.assetid: 2413a9f2-1d81-46ed-95cb-95ec8233eea2
ms.openlocfilehash: 9bd7b073237fa995ac67fe23b616cd54980fbec9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33554886"
---
# <a name="how-to-resize-rows-with-a-gridsplitter"></a>方法 : GridSplitter を使用して行のサイズを変更する
この例は、水平方向の使用方法を示しています。<xref:System.Windows.Controls.GridSplitter>の 2 つの行の間の領域を再配布する、<xref:System.Windows.Controls.Grid>の寸法を変更することなく、<xref:System.Windows.Controls.Grid>です。  
  
## <a name="example"></a>例  
 **行の端に重なって表示される GridSplitter を作成する方法**  
  
 指定する、<xref:System.Windows.Controls.GridSplitter>で隣接する行のサイズを変更する、 <xref:System.Windows.Controls.Grid>、設定されて、<xref:System.Windows.Controls.Grid.Row%2A>のサイズを変更する行の 1 つにプロパティを接続します。 場合、<xref:System.Windows.Controls.Grid>が 1 つ以上の列は、設定、<xref:System.Windows.Controls.Grid.ColumnSpan%2A>添付プロパティの列の数を指定します。 設定して、<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>に<xref:System.Windows.VerticalAlignment.Top>または<xref:System.Windows.VerticalAlignment.Bottom>(どの設定は整列する 2 つの行のサイズを変更する)。 最後に、設定、<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>プロパティを<xref:System.Windows.HorizontalAlignment.Stretch>です。  
  
 次の例は、水平方向を定義する方法を示しています。<xref:System.Windows.Controls.GridSplitter>隣接する行のサイズを変更します。  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterRowOverlay](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterrowoverlay)]  
  
 A<xref:System.Windows.Controls.GridSplitter>独自の行を占有しないで他のコントロールによって隠される可能性があります、<xref:System.Windows.Controls.Grid>です。 この問題の詳しい回避方法については、[GridSplitter を表示されるようにする](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md)を参照してください。  
  
 **行を占有する GridSplitter を作成する方法**  
  
 指定する、<xref:System.Windows.Controls.GridSplitter>内の行を占有する、 <xref:System.Windows.Controls.Grid>、設定、<xref:System.Windows.Controls.Grid.Row%2A>のサイズを変更する行の 1 つにプロパティを接続します。 場合、<xref:System.Windows.Controls.Grid>が 1 つ以上の列は、設定、<xref:System.Windows.Controls.Grid.ColumnSpan%2A>添付プロパティを列の数にします。 設定して、<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>に<xref:System.Windows.VerticalAlignment.Center>、設定されて、<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>プロパティを<xref:System.Windows.HorizontalAlignment.Stretch>、設定と、<xref:System.Windows.Controls.RowDefinition.Height%2A>を含む行の<xref:System.Windows.Controls.GridSplitter>に<xref:System.Windows.GridLength.Auto%2A>です。  
  
 次の例は、水平方向を定義する方法を示しています。<xref:System.Windows.Controls.GridSplitter>する行を占有し、その両側に行のサイズを変更します。  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterEntireRowPart1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirerowpart1)]  
[!code-xaml[GridSplitterRowColumn#GridSplitterEntireRowPart2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirerowpart2)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Controls.GridSplitter>  
 [データ バインドに関する「方法」トピック](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)
