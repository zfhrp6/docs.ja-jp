---
title: '方法 : グリッドを使用して標準 UI ダイアログ ボックスをビルドする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dialog boxes [WPF], creating
- Grid control [WPF], creating [WPF], dialog box
ms.assetid: d6ac3d51-844b-4d29-96d8-81a696a7b960
ms.openlocfilehash: d0b24e320c2a341b069e1c9c3e8b6d5e93076733
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33551883"
---
# <a name="how-to-build-a-standard-ui-dialog-box-by-using-grid"></a>方法 : グリッドを使用して標準 UI ダイアログ ボックスをビルドする
この例は、標準的なを作成する方法を示します[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] ダイアログ ボックスを使用して、<xref:System.Windows.Controls.Grid>要素。  
  
## <a name="example"></a>例  
 次の例のようなダイアログ ボックスの作成、**実行** ダイアログ ボックスで、[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]オペレーティング システムです。  
  
 例は、作成、<xref:System.Windows.Controls.Grid>を使用して、<xref:System.Windows.Controls.ColumnDefinition>と<xref:System.Windows.Controls.RowDefinition>5 つの列と 4 つの行を定義するクラス。  
  
 例では、追加し、配置、 <xref:System.Windows.Controls.Image>、 `RunIcon.png`、ダイアログ ボックスにある画像を表すです。 最初の列との行で、イメージが格納される、 <xref:System.Windows.Controls.Grid> (左上隅)。  
  
 この例を次に、追加、<xref:System.Windows.Controls.TextBlock>を最初の列は、最初の行の残りの列にまたがる要素。 追加別<xref:System.Windows.Controls.TextBlock>要素を表すため、最初の列に 2 番目の行を**開く**テキスト ボックス。 A<xref:System.Windows.Controls.TextBlock>次のように、データ エントリの領域を表します。  
  
 最後に、この例で 3 つの追加<xref:System.Windows.Controls.Button>を表す要素が、最後の行を**OK**、**キャンセル**と**参照**イベント。  
  
 [!code-csharp[GridRunDialog#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Controls.Grid>  
 <xref:System.Windows.GridUnitType>  
 [パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [方法トピック](../../../../docs/framework/wpf/controls/grid-how-to-topics.md)
