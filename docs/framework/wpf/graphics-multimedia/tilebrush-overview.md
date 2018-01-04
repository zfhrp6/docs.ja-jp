---
title: "TileBrush の概要"
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
helpviewer_keywords:
- TileBrush [WPF]
- brushes [WPF], TileBrush
ms.assetid: aa4a7b7e-d09d-44c2-8d61-310c50e08d68
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a7d5e9fa36ddeda0c724eeb0bb46a64d0ba36c99
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="tilebrush-overview"></a>TileBrush の概要
<xref:System.Windows.Media.TileBrush>オブジェクトを使用する、イメージで領域を描画する方法を細かく制御が大幅に向上<xref:System.Windows.Media.Drawing>、または<xref:System.Windows.Media.Visual>です。 このトピックを使用する方法について説明<xref:System.Windows.Media.TileBrush>の機能をより細かく方法、 <xref:System.Windows.Media.ImageBrush>、 <xref:System.Windows.Media.DrawingBrush>、または<xref:System.Windows.Media.VisualBrush>領域を塗りつぶします。  
  
  
<a name="prerequisite"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックの内容を理解するのにはの基本的な機能を使用する方法を理解しておいて、 <xref:System.Windows.Media.ImageBrush>、 <xref:System.Windows.Media.DrawingBrush>、または<xref:System.Windows.Media.VisualBrush>クラスです。 これらの型の概要については、次を参照してください。、[イメージ、図形、およびビジュアルの描画](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)です。  
  
<a name="tilebrush"></a>   
## <a name="painting-an-area-with-tiles"></a>タイルで領域を塗りつぶす  
 <xref:System.Windows.Media.ImageBrush>、 <xref:System.Windows.Media.DrawingBrush>、は<xref:System.Windows.Media.VisualBrush>種類<xref:System.Windows.Media.TileBrush>オブジェクト。 タイル ブラシを使用すると、イメージ、描画、またはビジュアルで領域を塗りつぶす方法を細かく制御できます。 たとえば、単一のイメージを引き伸ばして領域を塗りつぶすだけではなく、一連のイメージ タイルでパターンを作って領域を塗りつぶすことができます。  
  
 タイル ブラシによる領域の塗りつぶしには、コンテンツ、基本タイル、および出力領域の 3 つのコンポーネントが含まれます。  
  
 ![TileBrush コンポーネント](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-defaultcontentprojection2.png "wcpsdk_mmgraphics_defaultcontentprojection2")  
1 つのタイルが TileBrush のコンポーネント  
  
 ![並べて表示された TileBrush のコンポーネント](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tiledprojection.png "graphicsmm_tiledprojection")  
Tile の TileMode を使用する TileBrush のコンポーネント  
  
 出力領域のように、描画する領域が、<xref:System.Windows.Shapes.Shape.Fill%2A>の<xref:System.Windows.Shapes.Ellipse>または<xref:System.Windows.Controls.Control.Background%2A>の<xref:System.Windows.Controls.Button>です。 次のセクションでは、の他の 2 つのコンポーネントを記述する、<xref:System.Windows.Media.TileBrush>です。  
  
<a name="brushcontent"></a>   
## <a name="brush-content"></a>ブラシのコンテンツ  
 3 つの種類がある<xref:System.Windows.Media.TileBrush>様々 な種類のコンテンツを描画各とします。  
  
-   ブラシがの場合、 <xref:System.Windows.Media.ImageBrush>、このコンテンツは、イメージ、<xref:System.Windows.Media.ImageBrush.ImageSource%2A>プロパティの内容を指定する、<xref:System.Windows.Media.ImageBrush>です。  
  
-   ブラシがの場合、 <xref:System.Windows.Media.DrawingBrush>、このコンテンツは、描画します。 <xref:System.Windows.Media.DrawingBrush.Drawing%2A>プロパティの内容を指定する、<xref:System.Windows.Media.DrawingBrush>です。  
  
-   ブラシがの場合、 <xref:System.Windows.Media.VisualBrush>、このコンテンツは、ビジュアル。 <xref:System.Windows.Media.VisualBrush.Visual%2A>プロパティの内容を指定する、<xref:System.Windows.Media.VisualBrush>です。  
  
 位置および寸法を指定することができます<xref:System.Windows.Media.TileBrush>コンテンツを使用して、<xref:System.Windows.Media.TileBrush.Viewbox%2A>プロパティのままにするが一般的ですが、<xref:System.Windows.Media.TileBrush.Viewbox%2A>その既定値に設定します。 既定では、<xref:System.Windows.Media.TileBrush.Viewbox%2A>ブラシの内容を完全に格納するように構成します。 構成の詳細については、<xref:System.Windows.Controls.Viewbox>を参照してください、<xref:System.Windows.Controls.Viewbox>プロパティ ページ。  
  
<a name="thebasetile"></a>   
## <a name="the-base-tile"></a>基本タイル  
 A<xref:System.Windows.Media.TileBrush>基本タイルの内容を射影します。 <xref:System.Windows.Media.TileBrush.Stretch%2A>プロパティ コントロール方法<xref:System.Windows.Media.TileBrush>コンテンツが基本タイルに合わせて引き伸ばされます。 <xref:System.Windows.Media.TileBrush.Stretch%2A>プロパティによって定義された、次の値では、<xref:System.Windows.Media.Stretch>列挙します。  
  
-   <xref:System.Windows.Media.Stretch.None>: ブラシのコンテンツは、タイルに合わせて引き伸ばされますされません。  
  
-   <xref:System.Windows.Media.Stretch.Fill>: ブラシのコンテンツは、タイルに合わせてスケーリングされます。 コンテンツの高さと幅は別々にスケーリングされるため、コンテンツの元の縦横比が維持されない場合があります。 つまり、出力タイルを完全に塗りつぶすために、ブラシのコンテンツがいびつになることがあります。  
  
-   <xref:System.Windows.Media.Stretch.Uniform>: ブラシのコンテンツは、に、タイル内で完全に収まるようにスケーリングされます。 コンテンツの縦横比は維持されます。  
  
-   <xref:System.Windows.Media.Stretch.UniformToFill>: ブラシのコンテンツは、コンテンツの元の縦横比を維持しながら、出力領域が完全にいっぱいされるようにスケーリングされます。  
  
 次の図は、さまざまな示します<xref:System.Windows.Media.TileBrush.Stretch%2A>設定します。  
  
 ![TileBrush のさまざまな Stretch 設定](../../../../docs/framework/wpf/graphics-multimedia/media/img-mmgraphics-stretchenum.jpg "img_mmgraphics_stretchenum")  
  
 次の例の内容、<xref:System.Windows.Media.ImageBrush>設定されているため、出力領域に合わせて伸縮しません。  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMNoStretchExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/StretchExample.xaml#graphicsmmnostretchexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMNoStretchExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/StretchExample.cs#graphicsmmnostretchexample)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMNoStretchExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/stretchexample.vb#graphicsmmnostretchexample)]  
  
 既定では、 <xref:System.Windows.Media.TileBrush> 1 つのタイル (基本タイル) を生成し、出力領域がいっぱいにするには、そのタイルを拡大します。 基本タイルの位置とサイズを変更するには設定して、<xref:System.Windows.Media.TileBrush.Viewport%2A>と<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>プロパティです。  
  
<a name="basetilesize"></a>   
### <a name="base-tile-size"></a>基本タイルのサイズ  
 <xref:System.Windows.Media.TileBrush.Viewport%2A>プロパティは、基本のタイルの位置とサイズを決定し、<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>プロパティを決定するかどうか、<xref:System.Windows.Media.TileBrush.Viewport%2A>絶対または相対座標を使用して指定します。 座標が相対的な場合、座標は出力領域のサイズに対して相対的になります。 点 (0,0) は出力領域の左上隅を表し、(1,1) は出力領域の右下隅を表します。 指定する、<xref:System.Windows.Media.TileBrush.Viewport%2A>プロパティが絶対座標を使用して、設定、<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>プロパティを<xref:System.Windows.Media.BrushMappingMode.Absolute>です。  
  
 次の図に、出力の間の違い、<xref:System.Windows.Media.TileBrush>絶対と相対で<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>です。 どの図も、並べて表示するパターンを示しています。次のセクションでは、パターンの指定方法について説明します。  
  
 ![ビューポートの絶対単位と総体単位](../../../../docs/framework/wpf/graphics-multimedia/media/absolute-and-relative-viewports.png "absolute_and_relative_viewports")  
  
 次の例では、イメージを使用して幅と高さが 50% のタイルを作成しています。 基本タイルは、出力領域の (0,0) の位置にあります。  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMRelativeViewportUnitsExample1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileSizeExample.xaml#graphicsmmrelativeviewportunitsexample1)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMRelativeViewportUnitsExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TileSizeExample.cs#graphicsmmrelativeviewportunitsexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMRelativeViewportUnitsExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilesizeexample.vb#graphicsmmrelativeviewportunitsexample1)]  
  
 次の例では、のタイル、 <xref:System.Windows.Media.ImageBrush> 25 で 25 デバイス非依存のピクセルにします。 <xref:System.Windows.Media.TileBrush.ViewportUnits%2A>絶対では、<xref:System.Windows.Media.ImageBrush>タイルは 25 で 25 (ピクセル単位) 描画される領域のサイズに関係なく、常にします。  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMAbsoluteViewportUnitsExample1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileSizeExample.xaml#graphicsmmabsoluteviewportunitsexample1)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMAbsoluteViewportUnitsExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TileSizeExample.cs#graphicsmmabsoluteviewportunitsexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMAbsoluteViewportUnitsExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilesizeexample.vb#graphicsmmabsoluteviewportunitsexample1)]  
  
<a name="tilingbehavior"></a>   
### <a name="tiling-behavior"></a>並べて表示する動作  
 A<xref:System.Windows.Media.TileBrush>基本タイルが完全にいっぱいにならない、出力領域とし、他のタイル モード時に、並べて表示するパターンを生成する<xref:System.Windows.Media.TileMode.None>を指定します。 タイル ブラシのタイルが完全にいっぱいにならない、出力領域とその<xref:System.Windows.Media.TileBrush.TileMode%2A>プロパティ基本タイルが出力領域を塗りつぶすに複製する必要があり場合は、基本のタイル複製するかどうかを指定します。 <xref:System.Windows.Media.TileBrush.TileMode%2A>プロパティによって定義された、次の値では、<xref:System.Windows.Media.TileMode>列挙します。  
  
-   <xref:System.Windows.Media.TileMode.None>: 基本タイルのみが描画されます。  
  
-   <xref:System.Windows.Media.TileMode.Tile>: 基本タイルが描画され、残りの領域が繰り返しで塗りつぶされます基本タイルを 1 つのタイルの右エッジは、次の左の端に同様に上下の。  
  
-   <xref:System.Windows.Media.TileMode.FlipX>: 同じ<xref:System.Windows.Media.TileMode.Tile>、が、タイルの代替列が水平方向に反転します。  
  
-   <xref:System.Windows.Media.TileMode.FlipY>: 同じ<xref:System.Windows.Media.TileMode.Tile>、が、タイルの代替の行が垂直方向に反転します。  
  
-   <xref:System.Windows.Media.TileMode.FlipXY>: を組み合わせた<xref:System.Windows.Media.TileMode.FlipX>と<xref:System.Windows.Media.TileMode.FlipY>です。  
  
 並べて表示するさまざまなモードを次のイメージに示します。  
  
 ![TileBrush のさまざまな TileMode 設定](../../../../docs/framework/wpf/graphics-multimedia/media/img-mmgraphics-tilemodes.gif "img_mmgraphics_tilemodes")  
  
 次の例では、幅と高さが 100 ピクセルの四角形がイメージを使用して塗りつぶされます。 ブラシを設定して<xref:System.Windows.Media.TileBrush.Viewport%2A>が設定されている 0,0,0.25,0.25、するブラシの基本タイルが出力領域の 1/4 を作成します。 ブラシの<xref:System.Windows.Media.TileBrush.TileMode%2A>に設定されている<xref:System.Windows.Media.TileMode.FlipXY>です。 そのため、四角形はタイルの行で塗りつぶされます。  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMFlipXYExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TilingExample.xaml#graphicsmmflipxyexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMFlipXYExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TilingExample.cs#graphicsmmflipxyexample)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMFlipXYExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilingexample.vb#graphicsmmflipxyexample)]  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Media.ImageBrush>  
 <xref:System.Windows.Media.DrawingBrush>  
 <xref:System.Windows.Media.VisualBrush>  
 <xref:System.Windows.Media.TileBrush>  
 [イメージ、描画、およびビジュアルによる塗りつぶし](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [方法トピック](../../../../docs/framework/wpf/graphics-multimedia/brushes-how-to-topics.md)  
 [Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [ImageBrush のサンプル](http://go.microsoft.com/fwlink/?LinkID=160005)  
 [VisualBrush のサンプル](http://go.microsoft.com/fwlink/?LinkID=160049)
