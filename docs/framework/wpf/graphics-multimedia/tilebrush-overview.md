---
title: "TileBrush の概要 | Microsoft Docs"
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
  - "ブラシ, TileBrush"
  - "TileBrush"
ms.assetid: aa4a7b7e-d09d-44c2-8d61-310c50e08d68
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# TileBrush の概要
<xref:System.Windows.Media.TileBrush> オブジェクトを使用すると、イメージ、<xref:System.Windows.Media.Drawing>、または <xref:System.Windows.Media.Visual> で領域を塗りつぶす方法を細かく制御できます。  ここでは、<xref:System.Windows.Media.TileBrush> 機能を使用して、<xref:System.Windows.Media.ImageBrush>、<xref:System.Windows.Media.DrawingBrush>、または <xref:System.Windows.Media.VisualBrush> で領域を塗りつぶす方法を詳細に制御する方法について説明します。  
  
   
  
<a name="prerequisite"></a>   
## 必要条件  
 このトピックを理解するには、<xref:System.Windows.Media.ImageBrush>、<xref:System.Windows.Media.DrawingBrush>、または <xref:System.Windows.Media.VisualBrush> の各クラスの基本的な機能の使用方法について理解しておくと役立ちます。  これらの型の概要については、「[イメージ、描画、およびビジュアルによる塗りつぶし](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)」を参照してください。  
  
<a name="tilebrush"></a>   
## タイルで領域を塗りつぶす  
 <xref:System.Windows.Media.ImageBrush>、<xref:System.Windows.Media.DrawingBrush>、および <xref:System.Windows.Media.VisualBrush> は、<xref:System.Windows.Media.TileBrush> オブジェクトの一種です。  タイル ブラシを使用すると、イメージ、描画、またはビジュアルで領域を塗りつぶす方法を細かく制御できます。  たとえば、引き伸ばした単一のイメージで領域をただ塗りつぶすのではなく、パターンを作成する一連のイメージ タイルで領域を塗りつぶすことができます。  
  
 タイル ブラシによる領域の塗りつぶしには、コンテンツ、基本タイル、および出力領域の 3 つのコンポーネントが含まれます。  
  
 ![TileBrush コンポーネント](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-defaultcontentprojection2.png "wcpsdk\_mmgraphics\_defaultcontentprojection2")  
1 つのタイルを使用する TileBrush のコンポーネント  
  
 ![並べて表示された TileBrush のコンポーネント](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tiledprojection.png "graphicsmm\_tiledprojection")  
Tile の TileMode を使用する TileBrush のコンポーネント  
  
 出力領域とは、<xref:System.Windows.Shapes.Ellipse> の <xref:System.Windows.Shapes.Shape.Fill%2A> や <xref:System.Windows.Controls.Button> の <xref:System.Windows.Controls.Control.Background%2A> など、塗りつぶされる領域のことです。  次のセクションでは、<xref:System.Windows.Media.TileBrush> の他の 2 つのコンポーネントについて説明します。  
  
<a name="brushcontent"></a>   
## ブラシのコンテンツ  
 <xref:System.Windows.Media.TileBrush> には 3 つの種類があり、それぞれが異なる種類のコンテンツを使用して塗りつぶしを行います。  
  
-   ブラシが <xref:System.Windows.Media.ImageBrush> の場合、このコンテンツはイメージです。<xref:System.Windows.Media.ImageBrush.ImageSource%2A> プロパティは、<xref:System.Windows.Media.ImageBrush> のコンテンツを指定します。  
  
-   ブラシが <xref:System.Windows.Media.DrawingBrush> である場合、このコンテンツは描画です。  <xref:System.Windows.Media.DrawingBrush.Drawing%2A> プロパティは、<xref:System.Windows.Media.DrawingBrush> のコンテンツを指定します。  
  
-   ブラシが <xref:System.Windows.Media.VisualBrush> である場合、このコンテンツはビジュアルです。  <xref:System.Windows.Media.VisualBrush.Visual%2A> プロパティは、<xref:System.Windows.Media.VisualBrush> のコンテンツを指定します。  
  
 <xref:System.Windows.Media.TileBrush.Viewbox%2A> プロパティを使用して、<xref:System.Windows.Media.TileBrush> のコンテンツの位置およびサイズを指定できます。ただし、この <xref:System.Windows.Media.TileBrush.Viewbox%2A> は、通常は既定値のままにしておきます。  既定では、<xref:System.Windows.Media.TileBrush.Viewbox%2A> は、ブラシのコンテンツを完全に含むように構成されます。  <xref:System.Windows.Controls.Viewbox> の構成の詳細については、<xref:System.Windows.Controls.Viewbox> プロパティのページを参照してください。  
  
<a name="thebasetile"></a>   
## 基本タイル  
 <xref:System.Windows.Media.TileBrush> は、そのコンテンツを基本タイルに投影します。  <xref:System.Windows.Media.TileBrush.Stretch%2A> プロパティは、<xref:System.Windows.Media.TileBrush> のコンテンツを引き伸ばして基本タイルを塗りつぶす方法を制御します。  <xref:System.Windows.Media.TileBrush.Stretch%2A> プロパティは、<xref:System.Windows.Media.Stretch> 列挙体によって定義された次の値を受け入れます。  
  
-   <xref:System.Windows.Media.Stretch> : ブラシのコンテンツは、タイルを塗りつぶすために引き伸ばされません。  
  
-   <xref:System.Windows.Media.Stretch> : ブラシのコンテンツは、タイルに合わせてスケーリングされます。  コンテンツの高さと幅は別々にスケーリングされるため、コンテンツの元の縦横比が維持されない場合があります。  つまり、出力タイルを完全に塗りつぶすために、ブラシのコンテンツがいびつになることがあります。  
  
-   <xref:System.Windows.Media.Stretch> : ブラシのコンテンツは、タイル内に完全に収まるようにスケーリングされます。  コンテンツの縦横比は維持されます。  
  
-   <xref:System.Windows.Media.Stretch> : ブラシのコンテンツは、コンテンツの元の縦横比を維持しながら、出力領域を完全に塗りつぶすようにスケーリングされます。  
  
 さまざまな <xref:System.Windows.Media.TileBrush.Stretch%2A> 設定を次のイメージに示します。  
  
 ![別の TileBrush Stretch 設定](../../../../docs/framework/wpf/graphics-multimedia/media/img-mmgraphics-stretchenum.png "img\_mmgraphics\_stretchenum")  
  
 次の例では、<xref:System.Windows.Media.ImageBrush> のコンテンツは、引き伸ばして出力領域を塗りつぶすことは行わない設定になっています。  
  
 [!code-xml[BrushOverviewExamples_snip#GraphicsMMNoStretchExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/StretchExample.xaml#graphicsmmnostretchexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMNoStretchExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/StretchExample.cs#graphicsmmnostretchexample)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMNoStretchExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/stretchexample.vb#graphicsmmnostretchexample)]  
  
 既定では、<xref:System.Windows.Media.TileBrush> は 1 つのタイル \(基本タイル\) を生成し、そのタイルを出力領域と完全に一致するように引き伸ばします。  基本タイルのサイズと位置は、<xref:System.Windows.Media.TileBrush.Viewport%2A> および <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> プロパティを設定して変更できます。  
  
<a name="basetilesize"></a>   
### 基本タイルのサイズ  
 <xref:System.Windows.Media.TileBrush.Viewport%2A> プロパティは、基本タイルのサイズと位置を決定し、<xref:System.Windows.Media.TileBrush.ViewportUnits%2A> プロパティは、<xref:System.Windows.Media.TileBrush.Viewport%2A> を指定する際に、絶対座標と相対座標のどちらを使用するかを決定します。  座標が相対的な場合、座標は出力領域のサイズに対して相対的になります。  点 \(0,0\) は出力領域の左上隅を表し、\(1,1\) は出力領域の右下隅を表します。  <xref:System.Windows.Media.TileBrush.Viewport%2A> プロパティで絶対座標を使用するように指定するには、<xref:System.Windows.Media.TileBrush.ViewportUnits%2A> プロパティを <xref:System.Windows.Media.BrushMappingMode> に設定します。  
  
 <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> で相対座標を指定した場合と絶対座標を指定した場合の <xref:System.Windows.Media.TileBrush> の出力の違いを次の図に示します。  どの図も、並べて表示するパターンを示しています。次のセクションでは、パターンの指定方法について説明します。  
  
 ![ビューポートの絶対単位と相対単位](../../../../docs/framework/wpf/graphics-multimedia/media/absolute-and-relative-viewports.png "absolute\_and\_relative\_viewports")  
  
 次の例では、イメージを使用して幅と高さが 50% のタイルを作成しています。  基本タイルは、出力領域の \(0,0\) の位置にあります。  
  
 [!code-xml[BrushOverviewExamples_snip#GraphicsMMRelativeViewportUnitsExample1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileSizeExample.xaml#graphicsmmrelativeviewportunitsexample1)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMRelativeViewportUnitsExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TileSizeExample.cs#graphicsmmrelativeviewportunitsexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMRelativeViewportUnitsExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilesizeexample.vb#graphicsmmrelativeviewportunitsexample1)]  
  
 次の例では、<xref:System.Windows.Media.ImageBrush> のタイルを 25 x 25 [デバイス非依存ピクセル](GTMT)に設定します。  <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> は絶対値であるため、<xref:System.Windows.Media.ImageBrush> のタイルは、塗りつぶす領域のサイズに関係なく常に 25 × 25 ピクセルになります。  
  
 [!code-xml[BrushOverviewExamples_snip#GraphicsMMAbsoluteViewportUnitsExample1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileSizeExample.xaml#graphicsmmabsoluteviewportunitsexample1)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMAbsoluteViewportUnitsExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TileSizeExample.cs#graphicsmmabsoluteviewportunitsexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMAbsoluteViewportUnitsExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilesizeexample.vb#graphicsmmabsoluteviewportunitsexample1)]  
  
<a name="tilingbehavior"></a>   
### 並べて表示する動作  
 <xref:System.Windows.Media.TileBrush> は、基本タイルが出力領域を完全に塗りつぶさず、並べて表示するモードが <xref:System.Windows.Media.TileMode> 以外に指定されている場合に、並べて表示するパターンを生成します。  タイル ブラシのタイルが出力領域を完全に塗りつぶさない場合、<xref:System.Windows.Media.TileBrush.TileMode%2A> プロパティは出力領域を塗りつぶすために基本タイルを繰り返す必要があるかどうかを指定します。繰り返す必要がある場合は、繰り返し方法も指定します。  <xref:System.Windows.Media.TileBrush.TileMode%2A> プロパティは、<xref:System.Windows.Media.TileMode> 列挙体によって定義された次の値を受け入れます。  
  
-   <xref:System.Windows.Media.TileMode> : 基本タイルのみが描画されます。  
  
-   <xref:System.Windows.Media.TileMode> : 基本タイルが描画され、残りの領域は基本タイルの繰り返しによって塗りつぶされます。つまり、1 つのタイルの右端が次のタイルの左端に隣接し、同様に上端と下端も隣接します。  
  
-   <xref:System.Windows.Media.TileMode> : タイルが 1 列おきに左右に反転することを除き、<xref:System.Windows.Media.TileMode> と同じです。  
  
-   <xref:System.Windows.Media.TileMode> : タイルが 1 行おきに上下に反転することを除き、<xref:System.Windows.Media.TileMode> と同じです。  
  
-   <xref:System.Windows.Media.TileMode> : <xref:System.Windows.Media.TileMode> と <xref:System.Windows.Media.TileMode> の組み合わせです。  
  
 並べて表示するさまざまなモードを次のイメージに示します。  
  
 ![別の TileBrush TileMode 設定](../../../../docs/framework/wpf/graphics-multimedia/media/img-mmgraphics-tilemodes.png "img\_mmgraphics\_tilemodes")  
  
 次の例では、イメージを使用して幅と高さが 100 ピクセルの四角形が塗りつぶされます。  ブラシの <xref:System.Windows.Media.TileBrush.Viewport%2A> を 0,0,0.25,0.25 に設定することにより、ブラシの基本タイルは出力領域の 1\/4 のサイズになります。  ブラシの <xref:System.Windows.Media.TileBrush.TileMode%2A> は <xref:System.Windows.Media.TileMode> に設定されます。  そのため、四角形はタイルの行で塗りつぶされます。  
  
 [!code-xml[BrushOverviewExamples_snip#GraphicsMMFlipXYExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TilingExample.xaml#graphicsmmflipxyexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMFlipXYExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TilingExample.cs#graphicsmmflipxyexample)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMFlipXYExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilingexample.vb#graphicsmmflipxyexample)]  
  
## 参照  
 <xref:System.Windows.Media.ImageBrush>   
 <xref:System.Windows.Media.DrawingBrush>   
 <xref:System.Windows.Media.VisualBrush>   
 <xref:System.Windows.Media.TileBrush>   
 [イメージ、描画、およびビジュアルによる塗りつぶし](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)   
 [方法のトピック](../../../../docs/framework/wpf/graphics-multimedia/brushes-how-to-topics.md)   
 [Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)   
 [ImageBrush のサンプル](http://go.microsoft.com/fwlink/?LinkID=160005)   
 [VisualBrush のサンプル](http://go.microsoft.com/fwlink/?LinkID=160049)