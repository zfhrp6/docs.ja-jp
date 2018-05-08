---
title: '方法 : SolidColorBrush の色または不透明度をアニメーション化する'
ms.date: 03/30/2017
helpviewer_keywords:
- SolidColorBrush [WPF], animating color of
- colors [WPF], animating
- opacity [WPF], animating
- animation [WPF], color of SolidColorBrush
- animation [WPF], opacity of SolidColorBrush
- SolidColorBrush [WPF], animating opacity of
ms.assetid: d9154354-843f-4713-bad1-35bb0ba6eaeb
ms.openlocfilehash: 2457bdb794d81e7c482f735cad4ade34564328e2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-animate-the-color-or-opacity-of-a-solidcolorbrush"></a>方法 : SolidColorBrush の色または不透明度をアニメーション化する
この例は、アニメーション化する方法を示しています、<xref:System.Windows.Media.SolidColorBrush.Color%2A>と<xref:System.Windows.Media.Brush.Opacity%2A>の<xref:System.Windows.Media.SolidColorBrush>です。  
  
## <a name="example"></a>例  
 次の例は、アニメーション化する 3 つのアニメーションを使用して、<xref:System.Windows.Media.SolidColorBrush.Color%2A>と<xref:System.Windows.Media.Brush.Opacity%2A>の<xref:System.Windows.Media.SolidColorBrush>です。  
  
-   最初のアニメーション、 <xref:System.Windows.Media.Animation.ColorAnimation>、ブラシの色を変更<xref:System.Windows.Media.Colors.Gray%2A>マウスが四角形に入ったとき。  
  
-   次のアニメーション別<xref:System.Windows.Media.Animation.ColorAnimation>、ブラシの色を変更<xref:System.Windows.Media.Colors.Orange%2A>マウスが四角形を離れるときにします。  
  
-   最後のアニメーション、<xref:System.Windows.Media.Animation.DoubleAnimation>マウスの左ボタンが押されたときに、0.0 ブラシの不透明度を変更します。  
  
 [!code-csharp[brushanimations_snip#SolidColorBrushAnimationExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushanimations_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushanimationexample)]  
  
 完全なサンプルは、さまざまな種類のブラシをアニメーション化する方法を表示するには、次を参照してください。、[ブラシ サンプル](http://go.microsoft.com/fwlink/?LinkID=159973)です。 アニメーションの詳細については、次を参照してください。、[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)です。  
  
 この例のコードを使用して他のアニメーション例と一貫性を保つのため、<xref:System.Windows.Media.Animation.Storyboard>アニメーションを適用するオブジェクト。 ただし、コード内の 1 つのアニメーションを適用するときに使いやすく、<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>メソッドを使用してではなく、<xref:System.Windows.Media.Animation.Storyboard>です。 例については、「[ストーリーボードを使用せずにプロパティをアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [ストーリーボードの概要](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [ブラシのサンプル](http://go.microsoft.com/fwlink/?LinkID=159973)
