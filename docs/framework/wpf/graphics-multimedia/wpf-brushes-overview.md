---
title: "WPF のブラシの概要"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: brushes [WPF], about brushes
ms.assetid: ecea1955-420b-45c6-bf43-c1404c072c41
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ec7e566e6f56c215bbaeafdfb5c5e97cc0add0bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="wpf-brushes-overview"></a>WPF のブラシの概要
画面に表示できるものは、ブラシによって描画されているために表示されます。 たとえば、ブラシを使用して、ボタン、テキストの前景色、図形の塗りつぶしの背景について説明します。 このトピックでの描画の概念を説明する[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]ブラシし、例について説明します。 ブラシを使用すると、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] オブジェクトを単色で塗りつぶすことも、パターンとイメージの複雑な組み合わせで塗りつぶすこともできます。  
  
<a name="paintingwithbrush"></a>   
## <a name="painting-with-a-brush"></a>ブラシで描画  
 A<xref:System.Windows.Media.Brush>その出力を使用して領域を「描画」です。 さまざまなブラシでは、さまざまな種類の出力があります。 ブラシは、純色、グラデーション、パターン、画像、または描画と他のユーザーで領域を塗りつぶすです。 次の図は、別のそれぞれの例を示します<xref:System.Windows.Media.Brush>型です。  
  
 ![ブラシの種類](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brushtypes.jpg "graphicsmm_brushtypes")  
ブラシの例  
  
 ほとんどのビジュアル オブジェクトを使用すると、描画された方法を指定できます。 次の表は、いくつかの一般的なオブジェクトおよびプロパティを使用することができます、<xref:System.Windows.Media.Brush>です。  
  
|クラス|ブラシのプロパティ|  
|-----------|----------------------|  
|<xref:System.Windows.Controls.Border>|<xref:System.Windows.Controls.Border.BorderBrush%2A>, <xref:System.Windows.Controls.Border.Background%2A>|  
|<xref:System.Windows.Controls.Control>|<xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>|  
|<xref:System.Windows.Controls.Panel>|<xref:System.Windows.Controls.Panel.Background%2A>|  
|<xref:System.Windows.Media.Pen>|<xref:System.Windows.Media.Pen.Brush%2A>|  
|<xref:System.Windows.Shapes.Shape>|<xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A>|  
|<xref:System.Windows.Controls.TextBlock>|<xref:System.Windows.Controls.TextBlock.Background%2A>|  
  
 次のセクションでは、説明、異なる<xref:System.Windows.Media.Brush>型し、それぞれの例を提供します。  
  
<a name="paintwithsolidcolorbrush"></a>   
## <a name="paint-with-a-solid-color"></a>純色で描画  
 A <xref:System.Windows.Media.SolidColorBrush> 、純色で領域を塗りつぶします<xref:System.Windows.Media.Color>です。 さまざまなを指定する方法がある、<xref:System.Windows.Media.SolidColorBrush.Color%2A>の<xref:System.Windows.Media.SolidColorBrush>: たとえば、そのアルファ、赤、青、および緑チャネルを指定したり、によって提供される定義済みの色のいずれかを使用、<xref:System.Windows.Media.Colors>クラスです。  
  
 次の例では、<xref:System.Windows.Media.SolidColorBrush>を描画する、<xref:System.Windows.Shapes.Shape.Fill%2A>の<xref:System.Windows.Shapes.Rectangle>です。 塗りつぶされた四角形を次の図に示します。  
  
 ![SolidColorBrush を使用して描画された四角形](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-solidcolorbrush.png "graphicsmm_brush_ovw_solidcolorbrush")  
SolidColorBrush を使用して描画された四角形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmsolidcolorbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmsolidcolorbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmsolidcolorbrushexampleinline)]  
  
 詳細については、<xref:System.Windows.Media.SolidColorBrush>クラスを参照してください[純色、グラデーションの概要でペイント](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)です。  
  
<a name="paintwithlineargradientbrush"></a>   
## <a name="paint-with-a-linear-gradient"></a>線形グラデーションの描画  
 A<xref:System.Windows.Media.LinearGradientBrush>線形グラデーションで領域を塗りつぶします。 線形グラデーションは、次の 2 つまたは複数の色をグラデーション軸のライン全体でブレンドします。 使用する<xref:System.Windows.Media.GradientStop>グラデーションとその位置に、色を指定するオブジェクト。  
  
 次の例では、<xref:System.Windows.Media.LinearGradientBrush>を描画する、<xref:System.Windows.Shapes.Shape.Fill%2A>の<xref:System.Windows.Shapes.Rectangle>です。 塗りつぶされた四角形を次の図に示します。  
  
 ![LinearGradientBrush を使用して描画された四角形](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-lineargradientbrush.jpg "graphicsmm_brush_ovw_lineargradientbrush")  
LinearGradientBrush を使用して描画された四角形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmlineargradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmlineargradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmlineargradientbrushexampleinline)]  
  
 詳細については、<xref:System.Windows.Media.LinearGradientBrush>クラスを参照してください[純色、グラデーションの概要でペイント](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)です。  
  
<a name="paintwithradialgradientbrush"></a>   
## <a name="paint-with-a-radial-gradient"></a>放射状グラデーションの描画  
 A<xref:System.Windows.Media.RadialGradientBrush>放射状グラデーションで領域を塗りつぶします。 放射状グラデーションは、円の間で 2 つまたは複数の色を合成します。 同様、<xref:System.Windows.Media.LinearGradientBrush>クラスを使用する<xref:System.Windows.Media.GradientStop>グラデーションとその位置に、色を指定するオブジェクト。  
  
 次の例では、<xref:System.Windows.Media.RadialGradientBrush>を描画する、<xref:System.Windows.Shapes.Shape.Fill%2A>の<xref:System.Windows.Shapes.Rectangle>です。 塗りつぶされた四角形を次の図に示します。  
  
 ![RadialGradientBrush を使用して描画された四角形](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-radialgradientbrush.jpg "graphicsmm_brush_ovw_radialgradientbrush")  
RadialGradientBrush を使用して描画された四角形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmradialgradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmradialgradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmradialgradientbrushexampleinline)]  
  
 詳細については、<xref:System.Windows.Media.RadialGradientBrush>クラスを参照してください[純色、グラデーションの概要でペイント](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)です。  
  
<a name="paintwithimage"></a>   
## <a name="paint-with-an-image"></a>イメージの描画  
 <xref:System.Windows.Media.ImageBrush>領域を塗りつぶします、<xref:System.Windows.Media.ImageSource>です。  
  
 次の例では、<xref:System.Windows.Media.ImageBrush>を描画する、<xref:System.Windows.Shapes.Shape.Fill%2A>の<xref:System.Windows.Shapes.Rectangle>です。 塗りつぶされた四角形を次の図に示します。  
  
 ![ImageBrush で描画された四角形](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-imagebrush.jpg "graphicsmm_brush_ovw_imagebrush")  
イメージを使用して描画された四角形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmimagebrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmimagebrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmimagebrushexampleinline)]  
  
 詳細については、<xref:System.Windows.Media.ImageBrush>クラスを参照してください[イメージ、図形、およびビジュアルの描画](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)です。  
  
<a name="paintwithdrawing"></a>   
## <a name="paint-with-a-drawing"></a>描画を使用して描画  
 A<xref:System.Windows.Media.DrawingBrush>領域を塗りつぶします、<xref:System.Windows.Media.Drawing>です。 A<xref:System.Windows.Media.Drawing>図形、画像、テキスト、およびメディアに含めることができます。  
  
 次の例では、<xref:System.Windows.Media.DrawingBrush>を描画する、<xref:System.Windows.Shapes.Shape.Fill%2A>の<xref:System.Windows.Shapes.Rectangle>です。 塗りつぶされた四角形を次の図に示します。  
  
 ![DrawingBrush を使用して描画された四角形](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-drawingbrush.jpg "graphicsmm_brush_ovw_drawingbrush")  
DrawingBrush を使用して描画された四角形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmdrawingbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmdrawingbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmdrawingbrushexampleinline)]  
  
 詳細については、<xref:System.Windows.Media.DrawingBrush>クラスを参照してください[イメージ、図形、およびビジュアルの描画](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)です。  
  
<a name="paintwithvisual"></a>   
## <a name="paint-with-a-visual"></a>ビジュアルを使用して描画  
 A<xref:System.Windows.Media.VisualBrush>領域を塗りつぶします、<xref:System.Windows.Media.Visual>オブジェクト。 ビジュアル オブジェクトの例として、 <xref:System.Windows.Controls.Button>、 <xref:System.Windows.Controls.Page>、および<xref:System.Windows.Controls.MediaElement>です。 A<xref:System.Windows.Media.VisualBrush>別の領域に、アプリケーションの 1 つの部分からコンテンツをプロジェクトすることもできますが反射効果を作成し、画面の一部を際立たせるを非常に役立ちます。  
  
 次の例では、<xref:System.Windows.Media.VisualBrush>を描画する、<xref:System.Windows.Shapes.Shape.Fill%2A>の<xref:System.Windows.Shapes.Rectangle>です。 塗りつぶされた四角形を次の図に示します。  
  
 ![VisualBrush を使用して描画された四角形](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-visualbrush.jpg "graphicsmm_brush_ovw_visualbrush")  
VisualBrush を使用して描画された四角形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmvisualbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmvisualbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmvisualbrushexampleinline)]  
  
 詳細については、<xref:System.Windows.Media.VisualBrush>クラスを参照してください[イメージ、図形、およびビジュアルの描画](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)です。  
  
<a name="paintwithpredefinedbrushesandsystemcolors"></a>   
## <a name="paint-using-predefined-and-system-brushes"></a>定義済みおよびシステム ブラシを使用して描く  
 便宜上、[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]のセットがあらかじめ定義されており、オブジェクトの描画に使用できるシステムのブラシを提供します。  
  
-   使用可能な定義済みのブラシの一覧は、次を参照してください。、<xref:System.Windows.Media.Brushes>クラスです。 定義済みのブラシを使用する方法を示す例は、次を参照してください。[を純色で領域を塗りつぶす](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-solid-color.md)です。  
  
-   使用可能なシステム ブラシの一覧は、次を参照してください。、<xref:System.Windows.SystemColors>クラスです。 例については、次を参照してください。[システム ブラシを使用して領域を塗りつぶす](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)です。  
  
<a name="commonbrushfeatures"></a>   
## <a name="common-brush-features"></a>ブラシの共通機能  
 <xref:System.Windows.Media.Brush>オブジェクトは、提供、<xref:System.Windows.Media.Brush.Opacity%2A>ブラシを透明または半透明な使用できるプロパティです。 <xref:System.Windows.Media.Brush.Opacity%2A> 0 の値により、ブラシの中に完全に透明、 <xref:System.Windows.Media.Brush.Opacity%2A> 1 の値を指定すると、ブラシは完全に不透明です。 次の例では、<xref:System.Windows.Media.Brush.Opacity%2A>プロパティを<xref:System.Windows.Media.SolidColorBrush>25% 不透明です。  
  
 [!code-xaml[BrushOverviewExamples_snip#OpacityExample1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/OpacityExample.xaml#opacityexample1xaml)]  
  
 [!code-csharp[BrushOverviewExamples_snip#OpacityExample1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/OpacityExample.cs#opacityexample1csharp)]  
  
 ブラシに部分的に透明な色が含まれている場合、色の不透明度の値がブラシの不透明度の値で乗算を結合します。 たとえば、ブラシが 0.5 の不透明度の値、ブラシで使用される色も 0.5 の不透明度の値を持っている場合は、出力色によって 0.25 の不透明度値があります。  
  
> [!NOTE]
>  使用して、要素全体の不透明度を変更するよりも、ブラシの不透明度の値を変更する方が効率的であるその<xref:System.Windows.UIElement.Opacity%2A?displayProperty=nameWithType>プロパティです。  
  
 回転、拡大縮小、傾斜、およびを使用して、ブラシのコンテンツを翻訳、<xref:System.Windows.Media.Brush.Transform%2A>または<xref:System.Windows.Media.Brush.RelativeTransform%2A>プロパティです。 詳細については、次を参照してください。[ブラシの変換の概要](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md)です。  
  
 いるため、<xref:System.Windows.Media.Animation.Animatable>オブジェクト、<xref:System.Windows.Media.Brush>オブジェクトをアニメーション化します。 詳しくは、「 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)」をご覧ください。  
  
<a name="freezable_features"></a>   
### <a name="freezable-features"></a>Freezable 機能  
 継承しているため、<xref:System.Windows.Freezable>クラス、<xref:System.Windows.Media.Brush>クラスには、いくつかの特別な機能が用意されています:<xref:System.Windows.Media.Brush>としてオブジェクトを宣言することができます[リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)、複数のオブジェクト間で共有およびクローンを作成します。 さらに、すべて、<xref:System.Windows.Media.Brush>型除く<xref:System.Windows.Media.VisualBrush>パフォーマンスを向上させるためには読み取り専用に、スレッド セーフに行われたことができます。  
  
 によって提供されるさまざまな機能の詳細については<xref:System.Windows.Freezable>、オブジェクトを参照してください[Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)です。  
  
 理由の詳細については<xref:System.Windows.Media.VisualBrush>オブジェクトにすることはできません固定されるを参照してください、<xref:System.Windows.Media.VisualBrush>の種類 ページ。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Media.Brush>  
 <xref:System.Windows.Media.Brushes>  
 [純色およびグラデーションによる塗りつぶしの概要](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [イメージ、描画、およびビジュアルによる塗りつぶし](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [ブラシのサンプル](http://go.microsoft.com/fwlink/?LinkID=159973)  
 [ImageBrush のサンプル](http://go.microsoft.com/fwlink/?LinkID=160005)  
 [VisualBrush のサンプル](http://go.microsoft.com/fwlink/?LinkID=160049)  
 [方法トピック](../../../../docs/framework/wpf/graphics-multimedia/brushes-how-to-topics.md)  
 [パフォーマンスに関するその他の推奨事項](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)
