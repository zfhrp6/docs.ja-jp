---
title: '方法 : 背景として使用するイメージの縦横比を保持する'
ms.date: 03/30/2017
helpviewer_keywords:
- aspect ratios of background images [WPF], preserving
- brushes [WPF], preserving aspect ratios of background images
- background images [WPF], preserving aspect ratios
ms.assetid: 28c39478-13d7-4011-80a3-8b9cc3e54478
ms.openlocfilehash: 906033b43ba657acc873f12a00000189db6796ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-preserve-the-aspect-ratio-of-an-image-used-as-a-background"></a>方法 : 背景として使用するイメージの縦横比を保持する
この例を使用する方法を示しています、<xref:System.Windows.Media.TileBrush.Stretch%2A>のプロパティ、<xref:System.Windows.Media.ImageBrush>イメージの縦横比を維持するためにします。  
  
 既定では、使用すると、<xref:System.Windows.Media.ImageBrush>領域を塗りつぶすには、そのコンテンツ全体に引き伸ばす完全に、出力領域。 出力領域とイメージの縦横比が異なる場合は、この引き伸ばしによってイメージがゆがめられます。  
  
 させる、<xref:System.Windows.Media.ImageBrush>設定、そのイメージの縦横比を保持、<xref:System.Windows.Media.TileBrush.Stretch%2A>プロパティを<xref:System.Windows.Media.Stretch.Uniform>または<xref:System.Windows.Media.Stretch.UniformToFill>です。  
  
## <a name="example"></a>例  
 次の例を使用して 2 つ<xref:System.Windows.Media.ImageBrush>2 つの四角形を描画するオブジェクト。 これらの四角形は 300 × 150 ピクセルで、どちらも 300 × 300 ピクセルのイメージを保持しています。 <xref:System.Windows.Media.TileBrush.Stretch%2A>最初のブラシのプロパティに設定されて<xref:System.Windows.Media.Stretch.Uniform>、および<xref:System.Windows.Media.TileBrush.Stretch%2A>2 番目のブラシのプロパティに設定されて<xref:System.Windows.Media.Stretch.UniformToFill>です。  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushStretchModesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/StretchModes.cs#imagebrushstretchmodesexamplewholepage)]  
  
 次の図は、最初のブラシの出力、<xref:System.Windows.Media.TileBrush.Stretch%2A>設定<xref:System.Windows.Media.Stretch.Uniform>です。  
  
 ![ImageBrush with Uniform stretching](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagebrushuniformstretch.jpg "graphicsmm_ImageBrushUniformStretch")  
  
 次の図には、2 番目のブラシの出力、<xref:System.Windows.Media.TileBrush.Stretch%2A>設定<xref:System.Windows.Media.Stretch.UniformToFill>です。  
  
 ![ImageBrush with UniformToFill stretching](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagebrushuniformtofillstretch.jpg "graphicsmm_ImageBrushUniformToFillStretch")  
  
 なお、<xref:System.Windows.Media.TileBrush.Stretch%2A>プロパティが、他の動作は同じです<xref:System.Windows.Media.TileBrush>オブジェクト、つまりの<xref:System.Windows.Media.DrawingBrush>と<xref:System.Windows.Media.VisualBrush>。 詳細については<xref:System.Windows.Media.ImageBrush>と、その他の<xref:System.Windows.Media.TileBrush>、オブジェクトを参照してください[イメージ、図形、およびビジュアルの描画](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)です。  
  
 なおが、<xref:System.Windows.Media.TileBrush.Stretch%2A>を指定するプロパティが表示されます、<xref:System.Windows.Media.TileBrush>コンテンツは、その出力領域に合わせて拡大、実際に指定方法、<xref:System.Windows.Media.TileBrush>コンテンツの基本タイルをいっぱいに拡大します。 詳細については、「<xref:System.Windows.Media.TileBrush>」を参照してください。  
  
 このコード例は提供されている長い例の一部である、<xref:System.Windows.Media.ImageBrush>クラスです。 サンプル全体については、次を参照してください。 [ImageBrush サンプル](http://go.microsoft.com/fwlink/?LinkID=160005)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Media.TileBrush>  
 [イメージ、描画、およびビジュアルによる塗りつぶし](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
