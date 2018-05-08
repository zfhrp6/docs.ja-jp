---
title: '方法 : 変換の原点を相対値で指定する'
ms.date: 03/30/2017
helpviewer_keywords:
- origins of Transforms [WPF]
- Transforms [WPF], origins of
- graphics [WPF], origins of Transforms
ms.assetid: f4dbc29d-93c7-41cd-96d8-5cfd8624b470
ms.openlocfilehash: ff263af8fbedeec483eee213c07dd4ec169805de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-specify-the-origin-of-a-transform-by-using-relative-values"></a>方法 : 変換の原点を相対値で指定する
この例の原点を指定する相対値を使用する方法を示しています、<xref:System.Windows.UIElement.RenderTransform%2A>に適用されている、<xref:System.Windows.FrameworkElement>です。  
  
 回転、拡大縮小、または傾斜するときに、<xref:System.Windows.FrameworkElement>を使用して、<xref:System.Windows.UIElement.RenderTransform%2A>プロパティ、既定の設定では、要素の左上隅に変換が適用されます。 要素の中心から回転、拡大縮小、または傾斜させる場合は、要素の中心に変換の中心を設定して補正することができます。 ただし、そのソリューションでは、要素のサイズがわかっている必要があります。 設定する要素の中心に、変換を適用する簡単な方法は、その<xref:System.Windows.UIElement.RenderTransformOrigin%2A>プロパティを (0.5, 0.5) 変換自体の中央値を設定する代わりにします。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Media.RotateTransform>回転、<xref:System.Windows.Controls.Button>時計回りに 45 度回転します。 この例では中心を指定していないので、ボタンは、左上隅の点 (0, 0) の周りを回転します。 <xref:System.Windows.Media.RotateTransform>に適用される、<xref:System.Windows.UIElement.RenderTransform%2A>プロパティです。  
  
 次の図は、それに続く例の変換結果を示しています。  
  
 ![RenderTransform を使用して変換されたボタン](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")  
RenderTransform プロパティを使用して時計回りに 45 度回転  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample1)]  
  
 次の例を使用しても、<xref:System.Windows.Media.RotateTransform>回転、 <xref:System.Windows.Controls.Button> 45 度時計回り。 ただし、この例の設定、<xref:System.Windows.UIElement.RenderTransformOrigin%2A>するボタンの (0.5, 0.5) です。 その結果、回転は、左上隅ではなくボタンの中心に適用されています。  
  
 次の図は、それに続く例の変換結果を示しています。  
  
 ![中心の周りで変換されたボタン](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")  
RenderTransformOrigin が (0.5, 0.5) の RenderTransform を使用した 45 度の回転  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample2)]  
  
 変換の詳細については<xref:System.Windows.FrameworkElement>、オブジェクトを参照してください、[変換の概要](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Media.Transform>  
 [変換の概要](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [方法トピック](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
