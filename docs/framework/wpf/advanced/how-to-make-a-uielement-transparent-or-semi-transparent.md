---
title: '方法 : UIElement を透明または半透明にする'
ms.date: 03/30/2017
helpviewer_keywords:
- UIElements [WPF], transparency
- opacity [WPF], of UIElements
- transparency of UIElements [WPF]
- UIElements [WPF], opacity
ms.assetid: a49fc8d6-7b32-4f28-9122-39b632a19b4b
ms.openlocfilehash: 7bf79848edb84a5bd93d1196fbe0b3196d159ff3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-make-a-uielement-transparent-or-semi-transparent"></a>方法 : UIElement を透明または半透明にする
この例では、作成、<xref:System.Windows.UIElement>透明または半透明です。 設定する要素を透明または半透明にその<xref:System.Windows.UIElement.Opacity%2A>プロパティです。 値`0.0`要素は完全に透明で、値の中に、`1.0`要素を完全に不透明になります。 値`0.5`により要素 50% 不透明で、やなどです。 要素の<xref:System.Windows.UIElement.Opacity%2A>に設定されている`1.0`既定です。  
  
## <a name="example"></a>例  
 次の例のセット、<xref:System.Windows.UIElement.Opacity%2A>するボタンの`0.25`、作成とその内容 (この場合、ボタンのテキスト) を 25% 不透明です。  
  
 [!code-xaml[brushsamples_snip#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#2)]  
  
 [!code-csharp[brushsamples_procedural_snip#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#2)]  
  
 要素の内容が自分<xref:System.Windows.UIElement.Opacity%2A>、それらの値の設定を含む要素が乗算<xref:System.Windows.UIElement.Opacity%2A>です。  
  
 次の例では、ボタンの<xref:System.Windows.UIElement.Opacity%2A>に`0.25`、および<xref:System.Windows.UIElement.Opacity%2A>の<xref:System.Windows.Controls.Image> をクリックしてに含まれているコントロール`0.5`です。 その結果、イメージが 12.5% 不透明度が表示されます: 0.125 = 0.25 * 0.5 です。  
  
 [!code-xaml[brushsamples_snip#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#3)]  
  
 [!code-csharp[brushsamples_procedural_snip#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#3)]  
  
 要素の不透明度を制御する別の方法がの不透明度を設定するには、<xref:System.Windows.Media.Brush>要素を描画します。 この方法が選択的に、要素の各部分の不透明度を変更することができ、使用する要素の場合よりパフォーマンス上の利点を提供<xref:System.Windows.UIElement.Opacity%2A>プロパティです。 次の例のセット、<xref:System.Windows.Media.Brush.Opacity%2A>の<xref:System.Windows.Media.SolidColorBrush>ボタンの描画に使用される<xref:System.Windows.Controls.Control.Background%2A>に設定されている`0.25`です。 その結果、ブラシの背景が 25% 不透明で残ります内容 (ボタンのテキスト) 100% の不透明度。  
  
 [!code-xaml[brushsamples_snip#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#4)]  
  
 [!code-csharp[brushsamples_procedural_snip#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#4)]  
  
 ブラシ内の個々 の色の不透明度を制御することもできます。 詳細については、色、ブラシを参照してください。[純色、グラデーションの概要でペイント](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)です。 要素の不透明度をアニメーション化する方法を示す例は、次を参照してください。[要素またはブラシの不透明度をアニメーション化](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-the-opacity-of-an-element-or-brush.md)です。
