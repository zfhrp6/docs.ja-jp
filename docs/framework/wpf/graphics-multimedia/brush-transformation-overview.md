---
title: "ブラシの変換の概要 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ブラシ, 変換プロパティ"
  - "プロパティ, 変換"
  - "変換プロパティ (ブラシの)"
ms.assetid: 8b9bfc09-12fd-4cd5-b445-99949f27bc39
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# ブラシの変換の概要
Brush クラスは、<xref:System.Windows.Media.Brush.RelativeTransform%2A> と <xref:System.Windows.Media.Brush.Transform%2A> の 2 つの変換プロパティを提供します。  これらのプロパティを使用すると、ブラシのコンテンツの回転、拡大縮小、傾斜、および平行移動を行うことができます。  ここでは、2 つのプロパティの違いについて説明し、それらの使用例を示します。  
  
<a name="autoTopLevelSectionsOUTLINE0"></a>   
<a name="prerequisites"></a>   
## 必要条件  
 このトピックを理解するには、変換するブラシの機能を理解する必要があります。  <xref:System.Windows.Media.LinearGradientBrush> と <xref:System.Windows.Media.RadialGradientBrush> については、「[純色およびグラデーションによる塗りつぶしの概要](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)」を参照してください。  <xref:System.Windows.Media.ImageBrush>、<xref:System.Windows.Media.DrawingBrush>、または <xref:System.Windows.Media.VisualBrush> については、「[イメージ、描画、およびビジュアルによる塗りつぶし](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)」を参照してください。  また、「[変換の概要](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)」で説明されている 2D 変換にも精通している必要があります。  
  
<a name="transformversusrelativetransform"></a>   
## Transform プロパティと RelativeTransform プロパティの違い  
 ブラシの <xref:System.Windows.Media.Brush.Transform%2A> プロパティに変換を適用する場合、ブラシのコンテンツをその中心を軸に変換するときは、塗りつぶされる領域のサイズを認識しておく必要があります。  塗りつぶされる領域は、幅が 200 [デバイス非依存ピクセル](GTMT)で、高さが 150 であると仮定します。  <xref:System.Windows.Media.RotateTransform> を使用して、ブラシの中心を軸に出力を 45 度回転した場合は、<xref:System.Windows.Media.RotateTransform> で <xref:System.Windows.Media.RotateTransform.CenterX%2A> に 100、<xref:System.Windows.Media.RotateTransform.CenterY%2A> に 75 を指定したことになります。  
  
 ブラシの <xref:System.Windows.Media.Brush.RelativeTransform%2A> プロパティに変換を適用する場合は、この変換がブラシに適用されてから、塗りつぶされる領域に出力がマップされます。  ブラシのコンテンツが処理および変換される順序を次に示します。  
  
1.  ブラシのコンテンツを処理します。  これは、<xref:System.Windows.Media.GradientBrush> では、グラデーション領域を決定することを意味します。  <xref:System.Windows.Media.TileBrush> では、<xref:System.Windows.Media.TileBrush.Viewbox%2A> が <xref:System.Windows.Media.TileBrush.Viewport%2A> にマップされます。  これがブラシの出力になります。  
  
2.  ブラシの出力を 1 × 1 の変換四角形に投影します。  
  
3.  ブラシの <xref:System.Windows.Media.Brush.RelativeTransform%2A> がある場合は、それを適用します。  
  
4.  塗りつぶす領域に、変換された出力を投影します。  
  
5.  ブラシの <xref:System.Windows.Media.Transform> がある場合は、それを適用します。  
  
 ブラシの出力が 1 × 1 の四角形にマップされている間に <xref:System.Windows.Media.Brush.RelativeTransform%2A> が適用されるため、変換の中心とオフセット値は相対的に表されます。  たとえば、<xref:System.Windows.Media.RotateTransform> を使用して、ブラシの中心を軸に出力を 45 度回転した場合は、<xref:System.Windows.Media.RotateTransform> で <xref:System.Windows.Media.RotateTransform.CenterX%2A> に 0.5、<xref:System.Windows.Media.RotateTransform.CenterY%2A> に 0.5 を指定したことになります。  
  
 次の図は、<xref:System.Windows.Media.Brush.RelativeTransform%2A> プロパティと <xref:System.Windows.Media.Brush.Transform%2A> プロパティを使用して 45 度回転された複数のブラシの出力を示しています。  
  
 ![RelativeTransform プロパティと Transform プロパティ](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brushrelativetransform-transform-small.png "graphicsmm\_brushrelativetransform\_transform\_small")  
  
<a name="relativetransformandtilebrush"></a>   
## TileBrush での RelativeTransform の使用  
 タイル ブラシは他のブラシより複雑であるため、これに <xref:System.Windows.Media.Brush.RelativeTransform%2A> を適用すると予期しない結果が生じる可能性があります。  たとえば、次のイメージを使用するとします。  
  
 ![ソース イメージ](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-1-original-image.png "graphicsmm\_reltransform\_1\_original\_image")  
  
 次の例では、<xref:System.Windows.Media.ImageBrush> を使用して、四角形領域を上のイメージで塗りつぶします。  <xref:System.Windows.Media.RotateTransform> を <xref:System.Windows.Media.ImageBrush> オブジェクトの <xref:System.Windows.Media.Brush.RelativeTransform%2A> プロパティに適用し、<xref:System.Windows.Media.TileBrush.Stretch%2A> プロパティを <xref:System.Windows.Media.Stretch> に設定します。この設定によって、イメージが引き伸ばされて四角形を完全に塗りつぶす際に、イメージの縦横比が保持されます。  
  
 [!code-xml[BrushOverviewExamples_snip#GraphicsMMRelativeTransformExample2Inline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/RelativeTransformIllustration.xaml#graphicsmmrelativetransformexample2inline)]  
  
 この例を実行すると、次の出力が生成されます。  
  
 ![変換された出力](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-6-output.png "graphicsmm\_reltransform\_6\_output")  
  
 ブラシの <xref:System.Windows.Media.TileBrush.Stretch%2A> が <xref:System.Windows.Media.Stretch> に設定された場合でも、イメージがゆがめられます。  これは、ブラシの <xref:System.Windows.Media.TileBrush.Viewbox%2A> が <xref:System.Windows.Media.TileBrush.Viewport%2A> にマップされた後に相対変換が適用されるためです。  プロセスの手順を次に示します。  
  
1.  ブラシの <xref:System.Windows.Media.TileBrush.Stretch%2A> を設定して、ブラシのコンテンツ \(<xref:System.Windows.Media.TileBrush.Viewbox%2A>\) を基本タイル \(<xref:System.Windows.Media.TileBrush.Viewport%2A>\) に投影します。  
  
     ![ビューポートに合わせて Viewbox を拡大](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-2-viewbox-to-viewport.png "graphicsmm\_reltransform\_2\_viewbox\_to\_viewport")  
  
2.  基本タイルを 1 × 1 の変換四角形に投影します。  
  
     ![ビューポートを変換四角形に割り当て](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-3-output-to-transform.png "graphicsmm\_reltransform\_3\_output\_to\_transform")  
  
3.  <xref:System.Windows.Media.RotateTransform> を適用します。  
  
     ![相対変換の適用](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-4-transform-rotate.png "graphicsmm\_reltransform\_4\_transform\_rotate")  
  
4.  塗りつぶす領域に、変換された基本タイルを投影します。  
  
     ![変換されたブラシを出力領域に反映](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-5-transform-to-output.png "graphicsmm\_reltransform\_5\_transform\_to\_output")  
  
<a name="rotateexample"></a>   
## 例 : ImageBrush を 45 度回転する  
 次の例では、<xref:System.Windows.Media.RotateTransform> を <xref:System.Windows.Media.ImageBrush> の <xref:System.Windows.Media.Brush.RelativeTransform%2A> プロパティに適用しています。  <xref:System.Windows.Media.RotateTransform> オブジェクトの <xref:System.Windows.Media.RotateTransform.CenterX%2A> プロパティおよび <xref:System.Windows.Media.RotateTransform.CenterY%2A> プロパティは、コンテンツの中心点の相対座標である 0.5 に設定されています。  その結果、ブラシの内容はその中心を軸にして回転します。  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 次の例でも <xref:System.Windows.Media.RotateTransform> を <xref:System.Windows.Media.ImageBrush> に適用していますが、<xref:System.Windows.Media.Brush.RelativeTransform%2A> プロパティの代わりに <xref:System.Windows.Media.Brush.Transform%2A> プロパティを使用しています。  ブラシをその中心を軸に回転するには、<xref:System.Windows.Media.RotateTransform> オブジェクトの <xref:System.Windows.Media.RotateTransform.CenterX%2A> および <xref:System.Windows.Media.RotateTransform.CenterY%2A> を絶対座標に設定する必要があります。  ブラシで描画される四角形は 175 × 90 ピクセルであるため、その中心点は \(87.5, 45\) になります。  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xml[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 次の図は、変換していないブラシ、<xref:System.Windows.Media.Brush.RelativeTransform%2A> プロパティに変換を適用したブラシ、および <xref:System.Windows.Media.Brush.Transform%2A> プロパティに変換を適用したブラシを示しています。  
  
 ![ブラシ RelativeTransform と変換の設定](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk\_graphicsmm\_transformandrelativetransform")  
  
 この例は、より大きなサンプルの一部です。  サンプル全体については、[ブラシのサンプル](http://go.microsoft.com/fwlink/?LinkID=159973)を参照してください。  ブラシの詳細については、「[WPF のブラシの概要](../../../../docs/framework/wpf/graphics-multimedia/wpf-brushes-overview.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Media.Brush.Transform%2A>   
 <xref:System.Windows.Media.Brush.RelativeTransform%2A>   
 <xref:System.Windows.Media.Transform>   
 <xref:System.Windows.Media.Brush>   
 [純色およびグラデーションによる塗りつぶしの概要](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)   
 [イメージ、描画、およびビジュアルによる塗りつぶし](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)   
 [変換の概要](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)