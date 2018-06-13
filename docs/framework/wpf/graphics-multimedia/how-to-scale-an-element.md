---
title: '方法 : 要素をスケーリングする'
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], elements
- graphics [WPF], scaling elements
ms.assetid: 18158d94-bbe7-4f6a-814e-84d27fa748bf
ms.openlocfilehash: f39bb4408e5b61912da30088de7c9f62587bc278
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562168"
---
# <a name="how-to-scale-an-element"></a>方法 : 要素をスケーリングする
この例を使用する方法を示しています、<xref:System.Windows.Media.ScaleTransform>要素のスケールを設定します。  
  
 使用して、<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>と<xref:System.Windows.Media.ScaleTransform.ScaleY%2A>プロパティを指定する場合の係数して要素のサイズを変更します。 たとえば、 <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> 1.5 の値が元の幅の 150% に要素を拡大します。 A<xref:System.Windows.Media.ScaleTransform.ScaleY%2A>値 0.5 は 50%、要素の高さを縮小します。  
  
 使用して、<xref:System.Windows.Media.ScaleTransform.CenterX%2A>と<xref:System.Windows.Media.ScaleTransform.CenterY%2A>プロパティをスケール操作の中心であるポイントを指定します。 既定では、<xref:System.Windows.Media.ScaleTransform>四角形の左上隅に対応するポイント (0, 0) で中央揃えされます。 これは、要素の移動とも適用すると、サイズが大きくなるように見えるので、<xref:System.Windows.Media.Transform>オブジェクトが存在する座標空間を変更します。  
  
 次の例では、 <xref:System.Windows.Media.ScaleTransform> 50 での 50 のサイズを 2 倍に<xref:System.Windows.Shapes.Rectangle>です。 <xref:System.Windows.Media.ScaleTransform>両方の値を 0 (既定値) を持つ<xref:System.Windows.Media.ScaleTransform.CenterX%2A>と<xref:System.Windows.Media.ScaleTransform.CenterY%2A>です。  
  
## <a name="example"></a>例  
 [!code-xaml[transformsSample#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#21)]  
  
 通常、設定<xref:System.Windows.Media.ScaleTransform.CenterX%2A>と<xref:System.Windows.Media.ScaleTransform.CenterY%2A>のスケールが設定されるオブジェクトの中心に: (<xref:System.Windows.FrameworkElement.Width%2A>/2、  <xref:System.Windows.FrameworkElement.Height%2A> /2)。  
  
 次の例に示します別<xref:System.Windows.Shapes.Rectangle>が 2 倍の大きさです。 ただし、この<xref:System.Windows.Media.ScaleTransform>両方に対して 25 の値を持つ<xref:System.Windows.Media.ScaleTransform.CenterX%2A>と<xref:System.Windows.Media.ScaleTransform.CenterY%2A>、四角形の中心に対応します。  
  
 [!code-xaml[transformsSample#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#22)]  
  
 次の図は、2 つの差<xref:System.Windows.Media.ScaleTransform>操作します。 点線は、拡大/縮小する前の四角形のサイズと位置を示しています。  
  
 ![中心点が異なる 2 倍のスケール](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")  
2 つの ScaleTransform 操作では、ScaleX と ScaleY の値は同じですが、中心点が異なっています。  
  
 完全なサンプルについては、「[2-D 変換のサンプル](http://go.microsoft.com/fwlink/?LinkID=158252)」をご覧ください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.ScaleTransform>  
 [変換の概要](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [方法トピック](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
