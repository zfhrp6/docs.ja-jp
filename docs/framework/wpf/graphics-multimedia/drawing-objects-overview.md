---
title: "Drawing オブジェクトの概要 | Microsoft Docs"
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
  - "Drawing オブジェクト"
  - "DrawingGroup オブジェクト"
  - "描画, 描画の概要"
  - "GeometryDrawing オブジェクト"
  - "GlyphRunDrawing オブジェクト"
  - "ImageDrawing オブジェクト"
ms.assetid: 9b5ce5c0-e204-4320-a7a8-0b2210d62f88
caps.latest.revision: 25
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 24
---
# Drawing オブジェクトの概要
ここでは、<xref:System.Windows.Media.Drawing> オブジェクトについて、およびこのオブジェクトを使用して図形、ビットマップ、テキスト、およびメディアを効率的に描画する方法について説明します。  クリップ アートを作成したり、<xref:System.Windows.Media.DrawingBrush> で塗りつぶしたり、<xref:System.Windows.Media.Visual> オブジェクトを使用したりする場合に、<xref:System.Windows.Media.Drawing> オブジェクトを使用します。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="whatisadrawingsection"></a>   
## 描画オブジェクトとは  
 <xref:System.Windows.Media.Drawing> オブジェクトは、図形、ビットマップ、ビデオ、またはテキスト行などの表示されるコンテンツを記述します。  異なる種類の描画は、異なる種類のコンテンツを記述します。  描画オブジェクトのさまざまな種類を次の一覧に示します。  
  
-   <xref:System.Windows.Media.GeometryDrawing> – 図形を描画します。  
  
-   <xref:System.Windows.Media.ImageDrawing> – イメージを描画します。  
  
-   <xref:System.Windows.Media.GlyphRunDrawing> – テキストを描画します。  
  
-   <xref:System.Windows.Media.VideoDrawing> – オーディオまたはビデオ ファイルを再生します。  
  
-   <xref:System.Windows.Media.DrawingGroup> – その他の描画を描画します。  他の描画を 1 つの複合描画に結合するには、描画グループを使用します。  
  
 <xref:System.Windows.Media.Drawing> は汎用的なオブジェクトです。<xref:System.Windows.Media.Drawing> オブジェクトにはさまざまな使用方法があります。  
  
-   <xref:System.Windows.Media.DrawingImage> および <xref:System.Windows.Controls.Image> コントロールを使用することにより、イメージとして表示できます。  
  
-   <xref:System.Windows.Media.DrawingBrush> を使用して、<xref:System.Windows.Controls.Page> の <xref:System.Windows.Controls.Page.Background%2A> などのオブジェクトを塗りつぶすことができます。  
  
-   <xref:System.Windows.Media.DrawingVisual> の外観を記述するために使用できます。  
  
-   <xref:System.Windows.Media.Visual> のコンテンツを列挙するために使用できます。  
  
 WPF に用意されている他の種類のオブジェクトでも、図形、ビットマップ、テキスト、およびメディアを描画できます。  たとえば、<xref:System.Windows.Shapes.Shape> オブジェクトを使用して図形を描画することもできます。また、<xref:System.Windows.Controls.MediaElement> コントロールによってアプリケーションにビデオを追加する方法もあります。  それでは、どのような場合に <xref:System.Windows.Media.Drawing> オブジェクトを使用したらよいのでしょうか。  それは、パフォーマンス上の利点を得るためにフレームワーク レベルの機能を犠牲にしてもかまわない場合や、<xref:System.Windows.Freezable> 機能が必要な場合です。  <xref:System.Windows.Media.Drawing> オブジェクトは、[レイアウト](../../../../docs/framework/wpf/advanced/layout.md)、入力、およびフォーカスをサポートしないため、背景やクリップ アートを表したり、<xref:System.Windows.Media.Visual> オブジェクトで低レベルの描画を行うのに適したパフォーマンスを実現できます。  
  
 <xref:System.Windows.Media.Drawing> オブジェクトは <xref:System.Windows.Freezable> 型のオブジェクトであるため、[リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)としての宣言、複数のオブジェクトでの共有、読み取り専用に設定することによるパフォーマンスの向上、複製、スレッド セーフの設定など、特殊な機能を備えています。  <xref:System.Windows.Freezable> オブジェクトのさまざまな機能の詳細については、「[Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)」を参照してください。  
  
<a name="drawinggeometriessection"></a>   
## 図形を描画する  
 図形を描画するには、<xref:System.Windows.Media.GeometryDrawing> を使用します。  ジオメトリ描画の <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> プロパティは描画する図形を記述し、<xref:System.Windows.Media.GeometryDrawing.Brush%2A> プロパティは図形の内部の塗りつぶし方法を記述し、<xref:System.Windows.Media.GeometryDrawing.Pen%2A> プロパティは図形のアウトラインの描き方を記述します。  
  
 次の例では、<xref:System.Windows.Media.GeometryDrawing> を使用して図形を描画します。  図形は、1 つの <xref:System.Windows.Media.GeometryGroup> と 2 つの <xref:System.Windows.Media.EllipseGeometry> オブジェクトによって示されます。  図形の内部は <xref:System.Windows.Media.LinearGradientBrush> で塗りつぶし、図形のアウトラインは <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen> で描画します。  
  
 この例では次の <xref:System.Windows.Media.GeometryDrawing> を作成します。  
  
 ![2 つの楕円の GeometryDrawing](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.png "graphicsmm\_geodraw")  
GeometryDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexampleinline)]
 [!code-xml[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexampleinline)]  
  
 コード例全体については、「[GeometryDrawing を作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-geometrydrawing.md)」を参照してください。  
  
 <xref:System.Windows.Media.PathGeometry> など、その他の <xref:System.Windows.Media.Geometry> クラスを使用すると、曲線や円弧を作成することによってさらに複雑な図形を作成できます。  <xref:System.Windows.Media.Geometry> オブジェクトの詳細については、「[ジオメトリの概要](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)」を参照してください。  
  
 <xref:System.Windows.Media.Drawing> オブジェクトを使用しない図形を描画するための他の方法については、「[WPF での図形と基本描画の概要](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)」を参照してください。  
  
<a name="drawingimagessection"></a>   
## イメージを描画する  
 イメージを描画するには、<xref:System.Windows.Media.ImageDrawing> を使用できます。  <xref:System.Windows.Media.ImageDrawing> オブジェクトの <xref:System.Windows.Media.ImageDrawing.ImageSource%2A> プロパティは描画するイメージを記述し、<xref:System.Windows.Media.ImageDrawing.Rect%2A> プロパティはイメージが描画される領域を定義します。  
  
 次の例では、\(75,75\) にある 100 x 100 [ピクセル](GTMT)の四角形の中に、イメージを描画します。  この例で作成した <xref:System.Windows.Media.ImageDrawing> を次の図に示します。  <xref:System.Windows.Media.ImageDrawing> の境界を表すために灰色の境界線を追加しています。  
  
 ![&#40;75,75&#41; に描画される 100×100 の ImageDrawing](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple-imagedrawing-offset.png "graphicsmm\_simple\_imagedrawing\_offset")  
100 x 100 の ImageDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawing100by100inline)]
 [!code-xml[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawing100by100inline)]  
  
 イメージの詳細については、「[イメージングの概要](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)」を参照してください。  
  
<a name="playmedia"></a>   
## メディアを再生する \(コードのみ\)  
  
> [!NOTE]
>  <xref:System.Windows.Media.VideoDrawing> を [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] で宣言することはできますが、コードを使用した場合のみそのメディアを読み込んで再生することができます。  [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] でビデオを再生するには、<xref:System.Windows.Controls.MediaElement> を使用します。  
  
 オーディオ ファイルまたはビデオ ファイルを再生するには、<xref:System.Windows.Media.VideoDrawing> と <xref:System.Windows.Media.MediaPlayer> を使用します。  メディアを読み込んで再生するには、2 つの方法があります。  1 つ目の方法は、<xref:System.Windows.Media.MediaPlayer> および <xref:System.Windows.Media.VideoDrawing> を単独で使用するもので、2 つ目の方法は、独自の <xref:System.Windows.Media.MediaTimeline> を作成して <xref:System.Windows.Media.MediaPlayer> および <xref:System.Windows.Media.VideoDrawing> と共に使用するものです。  
  
> [!NOTE]
>  アプリケーションでメディアを配布する場合は、メディア ファイルをイメージと同じようにプロジェクト リソースとして使用することはできません。  代わりにプロジェクト ファイルでメディアの種類を `Content` に設定し、`CopyToOutputDirectory` を `PreserveNewest` または `Always` に設定する必要があります。  
  
 独自の <xref:System.Windows.Media.MediaTimeline> を作成せずにメディアを再生するには、次の手順を実行します。  
  
1.  <xref:System.Windows.Media.MediaPlayer> オブジェクトを作成します。  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline1)]  
  
2.  メディア ファイルを読み込むには、<xref:System.Windows.Media.MediaPlayer.Open%2A> メソッドを使用します。  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline2)]  
  
3.  <xref:System.Windows.Media.VideoDrawing> を作成します。  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline3)]  
  
4.  <xref:System.Windows.Media.VideoDrawing> の <xref:System.Windows.Media.VideoDrawing.Rect%2A> プロパティを設定して、メディアを描画するサイズと場所を指定します。  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline4)]  
  
5.  作成した <xref:System.Windows.Media.MediaPlayer> で、<xref:System.Windows.Media.VideoDrawing> の <xref:System.Windows.Media.VideoDrawing.Player%2A> プロパティを設定します。  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline5)]  
  
6.  <xref:System.Windows.Media.MediaPlayer> の <xref:System.Windows.Media.MediaPlayer.Play%2A> メソッドを使用して、メディアの再生を開始します。  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline6)]  
  
 <xref:System.Windows.Media.VideoDrawing> および <xref:System.Windows.Media.MediaPlayer> を使用してビデオ ファイルを 1 回再生する例を次に示します。  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 メディアのタイミングをさらに細かく制御するには、<xref:System.Windows.Media.MediaPlayer> オブジェクトおよび <xref:System.Windows.Media.VideoDrawing> オブジェクトと共に <xref:System.Windows.Media.MediaTimeline> を使用します。  <xref:System.Windows.Media.MediaTimeline> を使用すると、ビデオを繰り返すかどうかを指定できます。  <xref:System.Windows.Media.VideoDrawing> と共に <xref:System.Windows.Media.MediaTimeline> を使用するには、次の手順を実行します。  
  
1.  <xref:System.Windows.Media.MediaTimeline> を宣言し、そのタイミング動作を設定します。  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline1)]  
  
2.  <xref:System.Windows.Media.MediaTimeline> から <xref:System.Windows.Media.MediaClock> を作成します。  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline2)]  
  
3.  <xref:System.Windows.Media.MediaPlayer> を作成し、<xref:System.Windows.Media.MediaClock> を使用してその <xref:System.Windows.Media.MediaPlayer.Clock%2A> プロパティを設定します。  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline3)]  
  
4.  <xref:System.Windows.Media.VideoDrawing> を作成し、<xref:System.Windows.Media.MediaPlayer> を <xref:System.Windows.Media.VideoDrawing> の <xref:System.Windows.Media.VideoDrawing.Player%2A> プロパティに割り当てます。  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline4)]  
  
 <xref:System.Windows.Media.MediaTimeline> を <xref:System.Windows.Media.MediaPlayer> および <xref:System.Windows.Media.VideoDrawing> と共に使用してビデオを繰り返し再生する例を次に示します。  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 <xref:System.Windows.Media.MediaTimeline> を使用するときは、<xref:System.Windows.Media.MediaPlayer> の対話型メソッドを使用するのではなく、<xref:System.Windows.Media.MediaClock> の <xref:System.Windows.Media.Animation.Clock.Controller%2A> プロパティから返される対話型の <xref:System.Windows.Media.Animation.ClockController> を使用してメディアの再生を制御することに注意してください。  
  
<a name="drawtext"></a>   
## テキストを描画する  
 テキストを描画するには、<xref:System.Windows.Media.GlyphRunDrawing> と <xref:System.Windows.Media.GlyphRun> を使用します。  次の例では、<xref:System.Windows.Media.GlyphRunDrawing> を使用して "Hello World" というテキストを描画しています。  
  
 [!code-csharp[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GlyphRunDrawingExample.cs#glyphrundrawingexampleinline)]
 [!code-xml[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GlyphRunExample.xaml#glyphrundrawingexampleinline)]  
  
 <xref:System.Windows.Media.GlyphRun> は、固定形式のドキュメントの表示および印刷シナリオでの使用を意図した、低レベルのオブジェクトです。  画面にテキストを描画するには、<xref:System.Windows.Controls.Label> または <xref:System.Windows.Controls.TextBlock> を使用する方が簡単です。  <xref:System.Windows.Media.GlyphRun> の詳細については、「[GlyphRun オブジェクトと Glyphs 要素の概要](../../../../docs/framework/wpf/advanced/introduction-to-the-glyphrun-object-and-glyphs-element.md)」の概要を参照してください。  
  
<a name="compositedrawingssection"></a>   
## 複合描画  
 <xref:System.Windows.Media.DrawingGroup> を使用すると、複数の描画を 1 つの複合描画に結合できます。  <xref:System.Windows.Media.DrawingGroup> を使用すると、複数の図形、イメージ、およびテキストを、1 つの <xref:System.Windows.Media.Drawing> オブジェクトに結合できます。  
  
 <xref:System.Windows.Media.DrawingGroup> を使用して、2 つの <xref:System.Windows.Media.GeometryDrawing> オブジェクトと 1 つの <xref:System.Windows.Media.ImageDrawing> オブジェクトを結合する例を次に示します。  この例を実行すると、次の出力が生成されます。  
  
 ![複数の描画を含む DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple.png "graphicsmm\_simple")  
複合描画  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 また、<xref:System.Windows.Media.DrawingGroup> を使用すると、不透明マスク、変換、ビットマップ効果などの操作もコンテンツに適用できます。  <xref:System.Windows.Media.DrawingGroup> 操作は、<xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>、<xref:System.Windows.Media.DrawingGroup.Opacity%2A>、<xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>、<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>、<xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>、そして <xref:System.Windows.Media.DrawingGroup.Transform%2A> の順に が適用されます。  
  
 <xref:System.Windows.Media.DrawingGroup> 操作が適用される順序を次の図に示します。  
  
 ![操作の DrawingGroup 順序](../../../../docs/framework/wpf/graphics-multimedia/media/graphcismm-drawinggroup-order.png "graphcismm\_drawinggroup\_order")  
DrawingGroup 操作の順序  
  
 <xref:System.Windows.Media.DrawingGroup> オブジェクトのコンテンツの操作に使用できるプロパティを次の表に示します。  
  
|プロパティ|Description|図|  
|-----------|-----------------|-------|  
|<xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>|<xref:System.Windows.Media.DrawingGroup> コンテンツの選択した部分の不透明度を変更します。  例については、「[How to: Control the Opacity of a Drawing](http://msdn.microsoft.com/ja-jp/68580652-7d32-4d27-93cc-a5148cf4d5ee)」を参照してください。||  
|<xref:System.Windows.Media.DrawingGroup.Opacity%2A>|<xref:System.Windows.Media.DrawingGroup> コンテンツの不透明度を一様に変更します。  <xref:System.Windows.Media.Drawing> を透明または部分的に透明にするには、このプロパティを使用します。  例については、「[How to: Apply an Opacity Mask to a Drawing](http://msdn.microsoft.com/ja-jp/d77b420b-9be2-479c-a45e-82f4da30eb9f)」を参照してください。||  
|<xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>|<xref:System.Windows.Media.Effects.BitmapEffect> を <xref:System.Windows.Media.DrawingGroup> コンテンツに適用します。  例については、「[How to: Apply a BitmapEffect to a Drawing](http://msdn.microsoft.com/ja-jp/c5b1de83-8d09-47fb-96db-5f174471f4b5)」を参照してください。||  
|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|<xref:System.Windows.Media.DrawingGroup> コンテンツを、<xref:System.Windows.Media.Geometry> で記述する領域に対してクリップします。  例については、「[How to: Clip a Drawing](http://msdn.microsoft.com/ja-jp/1f7d8a2c-c3c2-42cb-a542-e6796f9fb058)」を参照してください。||  
|<xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>|[デバイス非依存ピクセル](GTMT)を、指定したガイドラインに沿ったデバイス ピクセルにスナップします。  このプロパティは、DPI の低いディスプレイ上で、精緻なグラフィックスをはっきりとレンダリングするために役立ちます。  例については、「[描画に GuidelineSet を適用する](../../../../docs/framework/wpf/graphics-multimedia/how-to-apply-a-guidelineset-to-a-drawing.md)」を参照してください。||  
|<xref:System.Windows.Media.DrawingGroup.Transform%2A>|<xref:System.Windows.Media.DrawingGroup> コンテンツを変換します。  例については、「[How to: Apply a Transform to a Drawing](http://msdn.microsoft.com/ja-jp/0d525f2b-682d-4d67-9660-cf46929fbabd)」を参照してください。||  
  
<a name="usingimagedrawing"></a>   
## 描画をイメージとして表示する  
 <xref:System.Windows.Controls.Image> コントロールを使用して <xref:System.Windows.Media.Drawing> を表示するには、<xref:System.Windows.Media.DrawingImage> を <xref:System.Windows.Controls.Image> コントロールの <xref:System.Windows.Controls.Image.Source%2A> として使用し、<xref:System.Windows.Media.DrawingImage> オブジェクトの <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=fullName> プロパティを表示する描画に設定します。  
  
 <xref:System.Windows.Media.DrawingImage> および <xref:System.Windows.Controls.Image> コントロールを使用して、<xref:System.Windows.Media.GeometryDrawing> を表示する例を次に示します。  この例を実行すると、次の出力が生成されます。  
  
 ![2 つの楕円の GeometryDrawing](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.png "graphicsmm\_geodraw")  
DrawingImage  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
<a name="renderingwithdrawingbrushsection"></a>   
## 描画を使用してオブジェクトを塗りつぶす  
 <xref:System.Windows.Media.DrawingBrush> は、描画オブジェクトで領域を塗りつぶすブラシです。  これを使用すると、ほとんどすべてのグラフィカル オブジェクトを描画で塗りつぶすことができます。  <xref:System.Windows.Media.DrawingBrush> の <xref:System.Windows.Media.Drawing> プロパティは、その <xref:System.Windows.Media.DrawingBrush.Drawing%2A> を記述します。  <xref:System.Windows.Media.DrawingBrush> で <xref:System.Windows.Media.Drawing> をレンダリングするには、ブラシの <xref:System.Windows.Media.Drawing> プロパティを使用してブラシに追加してから、ブラシを使用してコントロールやパネルなどのグラフィカル オブジェクトを塗りつぶします。  
  
 <xref:System.Windows.Media.DrawingBrush> を使用して、<xref:System.Windows.Shapes.Rectangle> の <xref:System.Windows.Shapes.Shape.Fill%2A> を <xref:System.Windows.Media.GeometryDrawing> から作成したパターンで塗りつぶす例を次に示します。  この例を実行すると、次の出力が生成されます。  
  
 ![並べて表示される DrawingBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrush-geometrydrawing.png "graphicsmm\_drawingbrush\_geometrydrawing")  
DrawingBrush と共に使用された GeometryDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-xml[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 <xref:System.Windows.Media.DrawingBrush> クラスには、コンテンツを伸縮したり並べて表示するさまざまなオプションが用意されています。  <xref:System.Windows.Media.DrawingBrush> の詳細については、「[イメージ、描画、およびビジュアルによる塗りつぶし](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)」の概要を参照してください。  
  
<a name="renderingwithvisualsection"></a>   
## ビジュアルを使用した描画のレンダリング  
 <xref:System.Windows.Media.DrawingVisual> は、描画をレンダリングするよう設計されたビジュアル オブジェクトです。  ビジュアル層で直接作業する方法は、高度にカスタマイズされたグラフィカル環境を構築する開発者向けのオプションであり、この概要では説明しません。  詳細については、「[DrawingVisual オブジェクトの使用](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)」の概要を参照してください。  
  
<a name="drawingcontextobjects"></a>   
## DrawingContext オブジェクト  
 <xref:System.Windows.Media.DrawingContext> クラスを使用すると、<xref:System.Windows.Media.Visual> または <xref:System.Windows.Media.Drawing> にビジュアル コンテンツを読み込むことができます。  <xref:System.Windows.Media.DrawingContext> ではグラフィカル コンテンツが効率的に記述されるため、比較的低レベルのグラフィックス オブジェクトの多くで使用されます。  
  
 <xref:System.Windows.Media.DrawingContext> 描画メソッドは <xref:System.Drawing.Graphics?displayProperty=fullName> 型の描画メソッドに似ていますが、機能はまったく異なります。  <xref:System.Windows.Media.DrawingContext> は保持モードのグラフィックス システムで使用され、<xref:System.Drawing.Graphics?displayProperty=fullName> 型は即時モードのグラフィックス システムで使用されます。  <xref:System.Windows.Media.DrawingContext> オブジェクトの描画コマンドを使用すると、リアルタイムで画面に描画するのではなく、実際にはグラフィック システムで今後使用する一連の描画命令が格納されます \(正確なストレージ機構は、<xref:System.Windows.Media.DrawingContext> を提供するオブジェクトの型によって異なります\)。  [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] グラフィックス システムの動作原理の詳細については、「[WPF グラフィックス レンダリングの概要](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)」を参照してください。  
  
 <xref:System.Windows.Media.DrawingContext> を直接インスタンス化することはできませんが、<xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=fullName> や <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=fullName> などの一部のメソッドから描画コンテキストを取得できます。  
  
<a name="enumeratevisualcontents"></a>   
## ビジュアルのコンテンツを列挙する  
 <xref:System.Windows.Media.Drawing> オブジェクトは、他の用途に加えて、<xref:System.Windows.Media.Visual> のコンテンツを列挙するためのオブジェクト モデルも提供します。  
  
 <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> メソッドを使用して、<xref:System.Windows.Media.Visual> の <xref:System.Windows.Media.DrawingGroup> 値を取得し列挙する例を次に示します。  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## 参照  
 <xref:System.Windows.Media.Drawing>   
 <xref:System.Windows.Media.DrawingGroup>   
 [2D グラフィックスとイメージング](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)   
 [イメージ、描画、およびビジュアルによる塗りつぶし](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)   
 [ジオメトリの概要](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)   
 [WPF での図形と基本描画の概要](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)   
 [WPF グラフィックス レンダリングの概要](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)   
 [Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/graphics-multimedia/drawings-how-to-topics.md)