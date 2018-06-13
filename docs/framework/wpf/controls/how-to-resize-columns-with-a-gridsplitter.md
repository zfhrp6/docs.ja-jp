---
title: '方法 : GridSplitter を使用して列のサイズを変更する'
ms.date: 03/30/2017
helpviewer_keywords:
- grid columns [WPF], resizing
- GridSplitter control [WPF], resizing grid columns
- resizing grid columns [WPF]
ms.assetid: 47b20fe6-7adc-4aa6-9693-b4e184eef74b
ms.openlocfilehash: b4652c06cfe6f048f6c75a11b9447d70d6820e4f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556151"
---
# <a name="how-to-resize-columns-with-a-gridsplitter"></a>方法 : GridSplitter を使用して列のサイズを変更する
この例は、垂直方向を作成する方法を示します<xref:System.Windows.Controls.GridSplitter>で 2 つの列間のスペースを再配布するために、<xref:System.Windows.Controls.Grid>の寸法を変更することがなく、<xref:System.Windows.Controls.Grid>です。  
  
## <a name="example"></a>例  
 **列の端に重なって表示される GridSplitter を作成する方法**  
  
 指定する、<xref:System.Windows.Controls.GridSplitter>内の隣接する列のサイズを変更する、 <xref:System.Windows.Controls.Grid>、設定、<xref:System.Windows.Controls.Grid.Column%2A>にサイズを変更する列の 1 つの添付プロパティ。 場合、 <xref:System.Windows.Controls.Grid> 1 つ以上の行がある設定、<xref:System.Windows.Controls.Grid.RowSpan%2A>行の数にプロパティをアタッチします。 設定して、<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>プロパティを<xref:System.Windows.HorizontalAlignment.Left>または<xref:System.Windows.HorizontalAlignment.Right>(どの設定は整列する 2 つの列のサイズを変更する)。 最後に、設定、<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>プロパティを<xref:System.Windows.VerticalAlignment.Stretch>です。  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterColumnOverlay](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplittercolumnoverlay)]  
  
 A<xref:System.Windows.Controls.GridSplitter>独自の列を持たない他のコントロールによって隠される可能性があります、<xref:System.Windows.Controls.Grid>です。 この問題の詳しい回避方法については、[GridSplitter を表示されるようにする](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md)を参照してください。  
  
 **列を占有する GridSplitter を作成する方法**  
  
 指定する、<xref:System.Windows.Controls.GridSplitter>内の列を占有する、 <xref:System.Windows.Controls.Grid>、設定、<xref:System.Windows.Controls.Grid.Column%2A>にサイズを変更する列の 1 つの添付プロパティ。 グリッドに複数の行がある場合は、設定、<xref:System.Windows.Controls.Grid.RowSpan%2A>行の数にプロパティをアタッチします。 設定して、<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>に<xref:System.Windows.HorizontalAlignment.Center>、設定されて、<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>プロパティを<xref:System.Windows.VerticalAlignment.Stretch>、設定と、<xref:System.Windows.Controls.ColumnDefinition.Width%2A>を含む列の<xref:System.Windows.Controls.GridSplitter>に<xref:System.Windows.GridLength.Auto%2A>です。  
  
 次の例は、垂直方向を定義する方法を示しています。<xref:System.Windows.Controls.GridSplitter>する列を占有し、そのいずれかの側の列のサイズを変更します。  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterEntireColumnPart1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirecolumnpart1)]  
[!code-xaml[GridSplitterRowColumn#GridSplitterEntireColumnPart2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirecolumnpart2)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Controls.GridSplitter>  
 [データ バインドに関する「方法」トピック](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)
