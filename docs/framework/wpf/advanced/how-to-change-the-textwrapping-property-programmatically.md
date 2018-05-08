---
title: '方法 : TextWrapping プロパティをプログラムにより変更する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- documents [WPF], changing TextWrapping property programmatically
- TextWrapping property [WPF], changing programmatically
ms.assetid: 30d25554-4c82-4df9-a8d6-35683a4a13bb
ms.openlocfilehash: 1b0f039f0484d1d1e73c3c12af06e0faffbce1cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-change-the-textwrapping-property-programmatically"></a>方法 : TextWrapping プロパティをプログラムにより変更する
## <a name="example"></a>例  
 次のコード例の値を変更する方法を示しています、<xref:System.Windows.Controls.TextBlock.TextWrapping%2A>プロパティ プログラムでします。  
  
 次の 3 つ<xref:System.Windows.Controls.Button>内の要素を配置している、<xref:System.Windows.Controls.StackPanel>内の要素[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]です。 各<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベントを<xref:System.Windows.Controls.Button>をイベント ハンドラーのコードに対応しています。 イベント ハンドラーと同じ名前を使用して、<xref:System.Windows.Controls.TextBlock.TextWrapping%2A>値に適用されます`txt2`ボタンがクリックされたときにします。 内のテキストも、 `txt1` (、<xref:System.Windows.Controls.TextBlock>に表示されていない、 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]) プロパティに変更を反映するように更新されます。  
  
 [!code-xaml[TextWrapProperty#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextWrapProperty/VisualBasic/Pane1.xaml#1)]  
  
 [!code-csharp[TextWrapProperty#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextWrapProperty/CSharp/Window1.xaml.cs#2)]
 [!code-vb[TextWrapProperty#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextWrapProperty/VisualBasic/Pane1.xaml.vb#2)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Controls.TextBlock.TextWrapping%2A>  
 <xref:System.Windows.TextWrapping>
