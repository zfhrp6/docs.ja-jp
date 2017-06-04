---
title: "WPF のブラシの概要 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ブラシ, ブラシの概要"
ms.assetid: ecea1955-420b-45c6-bf43-c1404c072c41
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# WPF のブラシの概要
スクリーン上に表示されるものはすべてブラシによって描画されているため、目で見ることができます。  たとえば、ブラシはボタンの背景、テキストの前景、および図形を塗りつぶすために使用されます。  ここでは、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] のブラシを使用した塗りつぶしの概念について説明し、例を示します。  ブラシを使用すると、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] オブジェクトに、純色やパターンとイメージの複雑なセットなどを適用できます。  
  
<a name="paintingwithbrush"></a>   
## ブラシによる塗りつぶし  
 <xref:System.Windows.Media.Brush> は、その出力で領域を塗りつぶします。  ブラシによって出力の種類がそれぞれ異なります。  純色で領域を塗りつぶすブラシもあれば、グラデーション、パターン、イメージ、または描画で塗りつぶすブラシもあります。  <xref:System.Windows.Media.Brush> のさまざまな種類の例を次の図に示します。  
  
 ![ブラシの種類](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brushtypes.png "graphicsmm\_brushtypes")  
ブラシの例  
  
 ほとんどのビジュアル オブジェクトでは、その塗りつぶし方法を指定できます。  <xref:System.Windows.Media.Brush> を使用できる一般的なオブジェクトとプロパティの一部を次の表に示します。  
  
|Class|ブラシのプロパティ|  
|-----------|---------------|  
|<xref:System.Windows.Controls.Border>|<xref:System.Windows.Controls.Border.BorderBrush%2A>, <xref:System.Windows.Controls.Border.Background%2A>|  
|<xref:System.Windows.Controls.Control>|<xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>|  
|<xref:System.Windows.Controls.Panel>|<xref:System.Windows.Controls.Panel.Background%2A>|  
|<xref:System.Windows.Media.Pen>|<xref:System.Windows.Media.Pen.Brush%2A>|  
|<xref:System.Windows.Shapes.Shape>|<xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A>|  
|<xref:System.Windows.Controls.TextBlock>|<xref:System.Windows.Controls.TextBlock.Background%2A>|  
  
 以下のセクションでは、さまざまな種類の <xref:System.Windows.Media.Brush> について説明し、それぞれの例を示します。  
  
<a name="paintwithsolidcolorbrush"></a>   
## 純色での塗りつぶし  
 <xref:System.Windows.Media.SolidColorBrush> は、領域を均一の <xref:System.Windows.Media.Color> \(純色\) で塗りつぶします。  <xref:System.Windows.Media.SolidColorBrush> の <xref:System.Windows.Media.SolidColorBrush.Color%2A> を指定するにはさまざまな方法があります。たとえば、アルファ、赤、青、緑の各チャネルを指定したり、<xref:System.Windows.Media.Colors> クラスで提供されている定義済みの色のいずれかを使用したりできます。  
  
 <xref:System.Windows.Media.SolidColorBrush> を使用して、<xref:System.Windows.Shapes.Rectangle> の <xref:System.Windows.Shapes.Shape.Fill%2A> を塗りつぶす例を次に示します。  塗りつぶされた四角形を次の図に示します。  
  
 ![SolidColorBrush を使用して描画された四角形](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-solidcolorbrush.png "graphicsmm\_brush\_ovw\_solidcolorbrush")  
SolidColorBrush を使用して塗りつぶされた四角形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmsolidcolorbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmsolidcolorbrushexampleinline)]
 [!code-xml[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmsolidcolorbrushexampleinline)]  
  
 <xref:System.Windows.Media.SolidColorBrush> クラスの詳細については、「[純色およびグラデーションによる塗りつぶしの概要](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)」を参照してください。  
  
<a name="paintwithlineargradientbrush"></a>   
## 線形グラデーションでの塗りつぶし  
 <xref:System.Windows.Media.LinearGradientBrush> は、線形グラデーションで領域を塗りつぶします。  線形グラデーションは、直線つまりグラデーション軸を境にして 2 つ以上の色をブレンドします。  グラデーション内の色とその位置を指定するには、<xref:System.Windows.Media.GradientStop> オブジェクトを使用します。  
  
 <xref:System.Windows.Media.LinearGradientBrush> を使用して、<xref:System.Windows.Shapes.Rectangle> の <xref:System.Windows.Shapes.Shape.Fill%2A> を塗りつぶす例を次に示します。  塗りつぶされた四角形を次の図に示します。  
  
 ![LinearGradientBrush を使用して描画された四角形](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-lineargradientbrush.png "graphicsmm\_brush\_ovw\_lineargradientbrush")  
LinearGradientBrush を使用して塗りつぶされた四角形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmlineargradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmlineargradientbrushexampleinline)]
 [!code-xml[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmlineargradientbrushexampleinline)]  
  
 <xref:System.Windows.Media.LinearGradientBrush> クラスの詳細については、「[純色およびグラデーションによる塗りつぶしの概要](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)」を参照してください。  
  
<a name="paintwithradialgradientbrush"></a>   
## 放射状グラデーションでの塗りつぶし  
 <xref:System.Windows.Media.RadialGradientBrush> は、放射状グラデーションで領域を塗りつぶします。  放射状グラデーションは、円を境にして 2 つ以上の色をブレンドします。  <xref:System.Windows.Media.LinearGradientBrush> クラスと同様、グラデーション内の色とその位置を指定するには、<xref:System.Windows.Media.GradientStop> オブジェクトを使用します。  
  
 <xref:System.Windows.Media.RadialGradientBrush> を使用して、<xref:System.Windows.Shapes.Rectangle> の <xref:System.Windows.Shapes.Shape.Fill%2A> を塗りつぶす例を次に示します。  塗りつぶされた四角形を次の図に示します。  
  
 ![RadialGradientBrush を使用して描画された四角形](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-radialgradientbrush.png "graphicsmm\_brush\_ovw\_radialgradientbrush")  
RadialGradientBrush を使用して塗りつぶされた四角形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmradialgradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmradialgradientbrushexampleinline)]
 [!code-xml[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmradialgradientbrushexampleinline)]  
  
 <xref:System.Windows.Media.RadialGradientBrush> クラスの詳細については、「[純色およびグラデーションによる塗りつぶしの概要](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)」を参照してください。  
  
<a name="paintwithimage"></a>   
## イメージでの塗りつぶし  
 <xref:System.Windows.Media.ImageBrush> は、<xref:System.Windows.Media.ImageSource> で領域を塗りつぶします。  
  
 <xref:System.Windows.Media.ImageBrush> を使用して、<xref:System.Windows.Shapes.Rectangle> の <xref:System.Windows.Shapes.Shape.Fill%2A> を塗りつぶす例を次に示します。  塗りつぶされた四角形を次の図に示します。  
  
 ![ImageBrush で描画された四角形](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-imagebrush.png "graphicsmm\_brush\_ovw\_imagebrush")  
イメージを使用して塗りつぶされた四角形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmimagebrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmimagebrushexampleinline)]
 [!code-xml[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmimagebrushexampleinline)]  
  
 <xref:System.Windows.Media.ImageBrush> クラスの詳細については、「[イメージ、描画、およびビジュアルによる塗りつぶし](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)」を参照してください。  
  
<a name="paintwithdrawing"></a>   
## 描画での塗りつぶし  
 <xref:System.Windows.Media.DrawingBrush> は、<xref:System.Windows.Media.Drawing> で領域を塗りつぶします。  <xref:System.Windows.Media.Drawing> は、図形、イメージ、テキスト、および、メディアを含むことができます。  
  
 <xref:System.Windows.Media.DrawingBrush> を使用して、<xref:System.Windows.Shapes.Rectangle> の <xref:System.Windows.Shapes.Shape.Fill%2A> を塗りつぶす例を次に示します。  塗りつぶされた四角形を次の図に示します。  
  
 ![DrawingBrush を使用して描画された四角形](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-drawingbrush.png "graphicsmm\_brush\_ovw\_drawingbrush")  
DrawingBrush を使用して塗りつぶされた四角形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmdrawingbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmdrawingbrushexampleinline)]
 [!code-xml[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmdrawingbrushexampleinline)]  
  
 <xref:System.Windows.Media.DrawingBrush> クラスの詳細については、「[イメージ、描画、およびビジュアルによる塗りつぶし](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)」を参照してください。  
  
<a name="paintwithvisual"></a>   
## ビジュアルでの塗りつぶし  
 <xref:System.Windows.Media.VisualBrush> は、<xref:System.Windows.Media.Visual> オブジェクトで領域を塗りつぶします。  Visual オブジェクトの例としては、<xref:System.Windows.Controls.Button>、<xref:System.Windows.Controls.Page>、<xref:System.Windows.Controls.MediaElement> などがあります。  また、<xref:System.Windows.Media.VisualBrush> を使用すると、アプリケーションのある部分の内容を別の領域に投影することもできます。これは、反射効果を作成し、画面の一部を際立たせる場合に非常に役立ちます。  
  
 <xref:System.Windows.Media.VisualBrush> を使用して、<xref:System.Windows.Shapes.Rectangle> の <xref:System.Windows.Shapes.Shape.Fill%2A> を塗りつぶす例を次に示します。  塗りつぶされた四角形を次の図に示します。  
  
 ![VisualBrush を使用して描画された四角形](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-visualbrush.png "graphicsmm\_brush\_ovw\_visualbrush")  
VisualBrush を使用して塗りつぶされた四角形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmvisualbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmvisualbrushexampleinline)]
 [!code-xml[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmvisualbrushexampleinline)]  
  
 <xref:System.Windows.Media.VisualBrush> クラスの詳細については、「[イメージ、描画、およびビジュアルによる塗りつぶし](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)」を参照してください。  
  
<a name="paintwithpredefinedbrushesandsystemcolors"></a>   
## 定義済みブラシおよびシステム ブラシを使用した塗りつぶし  
 便宜上、[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] では、オブジェクトの塗りつぶしに使用できる定義済みブラシとシステム ブラシのセットが提供されています。  
  
-   使用可能な定義済みブラシの一覧については、<xref:System.Windows.Media.Brushes> クラスを参照してください。  定義済みブラシの使用方法の例については、「[純色で領域を塗りつぶす](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-solid-color.md)」を参照してください。  
  
-   使用可能なシステム ブラシの一覧については、<xref:System.Windows.SystemColors> クラスを参照してください。  例については、「[システム ブラシで領域を塗りつぶす](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)」を参照してください。  
  
<a name="commonbrushfeatures"></a>   
## ブラシの共通機能  
 <xref:System.Windows.Media.Brush> オブジェクトが提供する <xref:System.Windows.Media.Brush.Opacity%2A> プロパティを使用すると、ブラシを透明にしたり、部分的に透明にしたりできます。  <xref:System.Windows.Media.Brush.Opacity%2A> の値を 0 にするとブラシは完全に透明になり、<xref:System.Windows.Media.Brush.Opacity%2A> の値を 1 にするとブラシは完全に不透明になります。  <xref:System.Windows.Media.Brush.Opacity%2A> プロパティを使用して、<xref:System.Windows.Media.SolidColorBrush> の不透明度を 25% にする例を次に示します。  
  
 [!code-xml[BrushOverviewExamples_snip#OpacityExample1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/OpacityExample.xaml#opacityexample1xaml)]  
  
 [!code-csharp[BrushOverviewExamples_snip#OpacityExample1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/OpacityExample.cs#opacityexample1csharp)]  
  
 ブラシに部分的に透明な色が含まれる場合は、ブラシの不透明度の値との乗算により、色の不透明度の値が結合されます。  たとえば、ブラシの不透明度の値が 0.5 で、ブラシで使用されている色の不透明度値も 0.5 である場合は、出力される色の不透明度は 0.25 になります。  
  
> [!NOTE]
>  <xref:System.Windows.UIElement.Opacity%2A?displayProperty=fullName> プロパティを使用して要素全体の不透明度を変更するより、ブラシの不透明度の値を変更する方が効率的です。  
  
 <xref:System.Windows.Media.Brush.Transform%2A> プロパティまたは <xref:System.Windows.Media.Brush.RelativeTransform%2A> プロパティを使用すると、ブラシのコンテンツの回転、拡大縮小、傾斜、および平行移動を行うことができます。  詳細については、「[ブラシの変換の概要](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md)」を参照してください。  
  
 これらは <xref:System.Windows.Media.Animation.Animatable> オブジェクトであるため、<xref:System.Windows.Media.Brush> オブジェクトはアニメーション化できます。  詳細については、「[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)」を参照してください。  
  
<a name="freezable_features"></a>   
### Freezable の機能  
 <xref:System.Windows.Freezable> クラスを継承するので、<xref:System.Windows.Media.Brush> クラスはいくつかの特殊な機能を備えています。<xref:System.Windows.Media.Brush> オブジェクトを[リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)として宣言したり、複数のオブジェクトで共有したり、複製したりできます。  さらに、<xref:System.Windows.Media.VisualBrush> を除くすべての種類の <xref:System.Windows.Media.Brush> は、読み取り専用にして、パフォーマンスを向上させ、スレッド セーフにすることができます。  
  
 <xref:System.Windows.Freezable> のさまざまな機能の詳細については、「[Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)」を参照してください。  
  
 <xref:System.Windows.Media.VisualBrush> オブジェクトを固定できない理由の詳細については、<xref:System.Windows.Media.VisualBrush> のページを参照してください。  
  
## 参照  
 <xref:System.Windows.Media.Brush>   
 <xref:System.Windows.Media.Brushes>   
 [純色およびグラデーションによる塗りつぶしの概要](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)   
 [イメージ、描画、およびビジュアルによる塗りつぶし](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)   
 [Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)   
 [ブラシのサンプル](http://go.microsoft.com/fwlink/?LinkID=159973)   
 [ImageBrush のサンプル](http://go.microsoft.com/fwlink/?LinkID=160005)   
 [VisualBrush のサンプル](http://go.microsoft.com/fwlink/?LinkID=160049)   
 [方法のトピック](../../../../docs/framework/wpf/graphics-multimedia/brushes-how-to-topics.md)   
 [パフォーマンスに関するその他の推奨事項](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)