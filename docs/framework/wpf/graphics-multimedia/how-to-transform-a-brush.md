---
title: '方法 : ブラシを変換する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], rotating contents
- brushes [WPF], Transform property
- rotating contents of brushes [WPF]
ms.assetid: ebada2f9-f01f-4863-9ea2-c2e4e51610f1
ms.openlocfilehash: 5caa00a378101ff4dff7745a18c3ec8905cc168b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561604"
---
# <a name="how-to-transform-a-brush"></a>方法 : ブラシを変換する
この例は、変換する方法を示しています。 <xref:System.Windows.Media.Brush> 、2 つの変換のプロパティを使用して、オブジェクト:<xref:System.Windows.Media.Brush.RelativeTransform%2A>と<xref:System.Windows.Media.Brush.Transform%2A>です。  
  
 次の例を使用して、<xref:System.Windows.Media.RotateTransform>の内容を回転する、<xref:System.Windows.Media.ImageBrush>で 45 度。  
  
 次の図は、<xref:System.Windows.Media.ImageBrush>せず、<xref:System.Windows.Media.RotateTransform>で、<xref:System.Windows.Media.RotateTransform>に適用される、<xref:System.Windows.Media.Brush.RelativeTransform%2A>プロパティを使用して、<xref:System.Windows.Media.RotateTransform>に適用される、<xref:System.Windows.Media.Brush.Transform%2A>プロパティです。  
  
 ![ブラシの RelativeTransform と Transform の設定](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")  
  
## <a name="example"></a>例  
 最初の例に適用されます、<xref:System.Windows.Media.RotateTransform>を<xref:System.Windows.Media.Brush.RelativeTransform%2A>のプロパティ、<xref:System.Windows.Media.ImageBrush>です。 <xref:System.Windows.Media.RotateTransform.CenterX%2A>と<xref:System.Windows.Media.RotateTransform.CenterY%2A>のプロパティ、<xref:System.Windows.Media.RotateTransform>オブジェクトは、このコンテンツの中心点の相対座標を 0.5 に設定されています。 その結果、<xref:System.Windows.Media.ImageBrush>コンテンツがその中心を中心として回転します。  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 2 番目の例も適用されます、<xref:System.Windows.Media.RotateTransform>を<xref:System.Windows.Media.ImageBrush>。 ただし、この例では、<xref:System.Windows.Media.Brush.Transform%2A>プロパティの代わりに、<xref:System.Windows.Media.Brush.RelativeTransform%2A>プロパティです。  
  
 ブラシ中心の周りの回転、設定、<xref:System.Windows.Media.RotateTransform.CenterX%2A>と<xref:System.Windows.Media.RotateTransform.CenterY%2A>のプロパティ、<xref:System.Windows.Media.RotateTransform>絶対座標するオブジェクト。 このブラシは、175 x 90 ピクセルの四角形を描画するため、四角形の中心点は (87.5, 45) になります。  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 方法の詳細については<xref:System.Windows.Media.Brush.RelativeTransform%2A>と<xref:System.Windows.Media.Brush.Transform%2A>プロパティが動作しを参照してください、[ブラシの変換の概要](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md)です。  
  
 完全なサンプルについては、「[ブラシのサンプル](http://go.microsoft.com/fwlink/?LinkID=159973)」を参照してください。 ブラシの詳細については、「[純色およびグラデーションによる塗りつぶしの概要](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [ブラシの変換の概要](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md)  
 [純色およびグラデーションによる塗りつぶしの概要](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [変換の概要](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
