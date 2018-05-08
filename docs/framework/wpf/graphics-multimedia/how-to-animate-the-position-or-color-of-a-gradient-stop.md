---
title: '方法 : グラデーション ストップの位置または色をアニメーション化する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- position [WPF], animating
- animation [WPF], position of GradientStop objects
- GradientStop objects [WPF], animating color of
- colors [WPF], animating
- animation [WPF], color of GradientStop objects
- GradientStop objects [WPF], animating position of
ms.assetid: 6f5b8b47-6c32-4b8e-98ee-fdf6515ec843
ms.openlocfilehash: 2eb528127c8aa66976788ec1f4e5362ca3a1ef26
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-animate-the-position-or-color-of-a-gradient-stop"></a>方法 : グラデーション ストップの位置または色をアニメーション化する
この例は、アニメーション化する方法を示しています、<xref:System.Windows.Media.GradientStop.Color%2A>と<xref:System.Windows.Media.GradientStop.Offset%2A>の<xref:System.Windows.Media.GradientStop>オブジェクト。  
  
## <a name="example"></a>例  
 次の例の内側の 3 つのグラデーションの分岐点をアニメーション化、<xref:System.Windows.Media.LinearGradientBrush>です。 この例では、別のグラデーションの分岐点をアニメーション化の 3 つのアニメーションでは。  
  
-   最初のアニメーション、 <xref:System.Windows.Media.Animation.DoubleAnimation>、最初にグラデーション終了位置のアニメーション化<xref:System.Windows.Media.GradientStop.Offset%2A>0.0 ~ 1.0 から 0.0 に戻ります。 その結果、最初の色、グラデーションのシフト左側にある四角形の右側に、左側に戻ります。  
  
-   2 番目のアニメーション、 <xref:System.Windows.Media.Animation.ColorAnimation>、2 番目のグラデーションのアニメーション化<xref:System.Windows.Media.GradientStop.Color%2A>から<xref:System.Windows.Media.Colors.Purple%2A>に<xref:System.Windows.Media.Colors.Yellow%2A>に戻ると<xref:System.Windows.Media.Colors.Purple%2A>です。 その結果、黄色および紫へ、グラデーションの中間色を紫から変更します。  
  
-   3 番目のアニメーションでは、別<xref:System.Windows.Media.Animation.ColorAnimation>、3 番目のグラデーション ストップの不透明度をアニメーション化<xref:System.Windows.Media.GradientStop.Color%2A>-1 でし、バックアップします。 結果として、3 番目の色、グラデーションはフェードアウトし、し、再び不透明になります。  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/GradientStopAnimationExample.cs#graphicsmmgradientanimationexampleswholepage)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/gradientstopanimationexample.vb#graphicsmmgradientanimationexampleswholepage)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/GradientStopAnimationExample.xaml#graphicsmmgradientanimationexampleswholepage)]  
  
 この例を使用しますが、 <xref:System.Windows.Media.LinearGradientBrush>、プロセスは、アニメーション化する同じ<xref:System.Windows.Media.GradientStop>の内部オブジェクト、<xref:System.Windows.Media.RadialGradientBrush>です。  
  
 その他の例では、次を参照してください。、[ブラシ サンプル](http://go.microsoft.com/fwlink/?LinkID=159973)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Media.GradientStop>  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [ストーリーボードの概要](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
