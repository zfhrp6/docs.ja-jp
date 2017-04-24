---
title: "イメージ、描画、およびビジュアルによる塗りつぶし | Microsoft Docs"
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
  - "ブラシ, 描画による塗りつぶし"
  - "ブラシ, イメージによる塗りつぶし"
  - "ブラシ, 塗りつぶし (ビジュアルによる)"
  - "塗りつぶし (ビジュアルによる)"
  - "描画, 描画を使用"
  - "描画, イメージを使用"
ms.assetid: 779aac3f-8d41-49d8-8130-768244aa2240
caps.latest.revision: 28
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 27
---
# イメージ、描画、およびビジュアルによる塗りつぶし
ここでは、<xref:System.Windows.Media.ImageBrush> オブジェクト、<xref:System.Windows.Media.DrawingBrush> オブジェクト、および <xref:System.Windows.Media.VisualBrush> オブジェクトを使用して領域をイメージ、<xref:System.Windows.Media.Drawing>、または <xref:System.Windows.Media.Visual> で塗りつぶす方法について説明します。  
  
   
  
<a name="prereqs"></a>   
## 必要条件  
 このトピックを理解するには、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] で提供されるさまざまな種類のブラシとその基本的な機能に精通している必要があります。  詳細については、「[WPF のブラシの概要](../../../../docs/framework/wpf/graphics-multimedia/wpf-brushes-overview.md)」を参照してください。  
  
<a name="image"></a>   
## イメージで領域を塗りつぶす  
 <xref:System.Windows.Media.ImageBrush> は、<xref:System.Windows.Media.ImageSource> で領域を塗りつぶします。  <xref:System.Windows.Media.ImageBrush> で使用される最も一般的な種類の <xref:System.Windows.Media.ImageSource> は <xref:System.Windows.Media.Imaging.BitmapImage> で、これは 1 個のビットマップ グラフィックを表します。  <xref:System.Windows.Media.DrawingImage> を使用しても、<xref:System.Windows.Media.Drawing> オブジェクトによる塗りつぶしは可能ですが、代わりに <xref:System.Windows.Media.DrawingBrush> を使用する方が簡単です。  <xref:System.Windows.Media.ImageSource> オブジェクトの詳細については、「[イメージングの概要](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)」を参照してください。  
  
 <xref:System.Windows.Media.ImageBrush> で塗りつぶすには、<xref:System.Windows.Media.Imaging.BitmapImage> を作成し、このオブジェクトを使用してビットマップ コンテンツを読み込みます。  次に、<xref:System.Windows.Media.Imaging.BitmapImage> を使用して、<xref:System.Windows.Media.ImageBrush> の <xref:System.Windows.Media.ImageBrush.ImageSource%2A> プロパティを設定します。  最後に、塗りつぶす対象のオブジェクトに <xref:System.Windows.Media.ImageBrush> を適用します。  [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] では、<xref:System.Windows.Media.ImageBrush> の <xref:System.Windows.Media.ImageBrush.ImageSource%2A> プロパティに、読み込むイメージのパスを設定するだけでもかまいません。  
  
 すべての <xref:System.Windows.Media.Brush> オブジェクトと同様に、<xref:System.Windows.Media.ImageBrush> は、図形、パネル、コントロール、およびテキストなどのオブジェクトの塗りつぶしに使用できます。  <xref:System.Windows.Media.ImageBrush> で適用できるいくつかの効果を次の図に示します。  
  
 ![ImageBrush の出力例](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-imagebrushexamples.png "wcpsdk\_mmgraphics\_imagebrushexamples")  
ImageBrush によって塗りつぶされたオブジェクト  
  
 <xref:System.Windows.Media.ImageBrush> の既定の設定では、対象の領域を完全に塗りつぶすようにイメージが引き伸ばされるので、塗りつぶす領域の縦横比がイメージの縦横比と異なる場合にイメージがゆがむことがあります。  この動作を変更するには、<xref:System.Windows.Media.TileBrush.Stretch%2A> プロパティを既定値の <xref:System.Windows.Media.Stretch> から <xref:System.Windows.Media.Stretch>、<xref:System.Windows.Media.Stretch>、または <xref:System.Windows.Media.Stretch> に変更します。  <xref:System.Windows.Media.ImageBrush> は <xref:System.Windows.Media.TileBrush> の型の 1 つであるので、イメージ ブラシで出力領域を塗りつぶす方法を正確に指定でき、パターンを作成することもできます。  高度な <xref:System.Windows.Media.TileBrush> 機能の詳細については、「[TileBrush の概要](../../../../docs/framework/wpf/graphics-multimedia/tilebrush-overview.md)」を参照してください。  
  
<a name="fillingpanelwithimage"></a>   
## 例 : ビットマップ イメージでオブジェクトを塗りつぶす  
 <xref:System.Windows.Media.ImageBrush> を使用して <xref:System.Windows.Controls.Canvas> の <xref:System.Windows.Controls.Panel.Background%2A> を塗りつぶす例を次に示します。  
  
 [!code-xml[BrushOverviewExamples_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/ImageBrushExample.xaml#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/ImageBrushExample.cs#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/imagebrushexample.vb#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
<a name="drawingbrushintro"></a>   
## 描画を使用して領域を塗りつぶす  
 <xref:System.Windows.Media.DrawingBrush> を使用すると、図形、テキスト、イメージ、およびビデオで領域を塗りつぶすことができます。  描画ブラシ内の図形自体も、単色、グラデーション、イメージ、または別の <xref:System.Windows.Media.DrawingBrush> で塗りつぶすことができます。  <xref:System.Windows.Media.DrawingBrush> のいくつかの使用例を次の図に示します。  
  
 ![DrawingBrush の出力例](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-drawingbrushexamples.png "wcpsdk\_mmgraphics\_drawingbrushexamples")  
DrawingBrush によって塗りつぶされたオブジェクト  
  
 <xref:System.Windows.Media.DrawingBrush> は、<xref:System.Windows.Media.Drawing> オブジェクトで領域を塗りつぶします。  <xref:System.Windows.Media.Drawing> オブジェクトは、図形、ビットマップ、ビデオ、またはテキスト行などの表示されるコンテンツを記述します。  異なる種類の描画は、異なる種類のコンテンツを記述します。  描画オブジェクトのさまざまな種類を次の一覧に示します。  
  
-   <xref:System.Windows.Media.GeometryDrawing> – 図形を描画します。  
  
-   <xref:System.Windows.Media.ImageDrawing> – イメージを描画します。  
  
-   <xref:System.Windows.Media.GlyphRunDrawing> – テキストを描画します。  
  
-   <xref:System.Windows.Media.VideoDrawing> – オーディオまたはビデオ ファイルを再生します。  
  
-   <xref:System.Windows.Media.DrawingGroup> – その他の描画を描画します。  他の描画を 1 つの複合描画に結合するには、描画グループを使用します。  
  
 <xref:System.Windows.Media.Drawing> オブジェクトの詳細については、「[Drawing オブジェクトの概要](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)」を参照してください。  
  
 <xref:System.Windows.Media.ImageBrush> と同様に、<xref:System.Windows.Media.DrawingBrush> は <xref:System.Windows.Media.DrawingBrush.Drawing%2A> を引き伸ばして出力領域を塗りつぶします。  この動作をオーバーライドするには、<xref:System.Windows.Media.TileBrush.Stretch%2A> プロパティを、既定の設定である <xref:System.Windows.Media.Stretch> から別の設定に変更します。  詳細については、<xref:System.Windows.Media.TileBrush.Stretch%2A> プロパティのトピックを参照してください。  
  
<a name="fillingareawithdrawingbrushexample"></a>   
## 例 : 描画を使用してオブジェクトを塗りつぶす  
 3 つの楕円の描画を使用してオブジェクトを塗りつぶす方法を次の例に示します。  楕円の記述には、<xref:System.Windows.Media.GeometryDrawing> を使用しています。  
  
 [!code-xml[BrushOverviewExamples_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/DrawingBrushExample.xaml#graphicsmmdrawingbrushasbuttonbackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/DrawingBrushExample.cs#graphicsmmdrawingbrushasbuttonbackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/drawingbrushexample.vb#graphicsmmdrawingbrushasbuttonbackgroundexample1)]  
  
<a name="visualbrushsection"></a>   
## ビジュアルで領域を塗りつぶす  
 すべてのブラシの中で最も用途が広く、多くの機能を持つ <xref:System.Windows.Media.VisualBrush> は、<xref:System.Windows.Media.Visual> で領域を塗りつぶします。  <xref:System.Windows.Media.Visual> は低レベルのグラフィックス型で、多数の有用なグラフィカル コンポーネントの先祖として使用されます。  たとえば、<xref:System.Windows.Window> クラス、<xref:System.Windows.FrameworkElement> クラス、および <xref:System.Windows.Controls.Control> クラスはすべて、<xref:System.Windows.Media.Visual> オブジェクトの一種です。  <xref:System.Windows.Media.VisualBrush> による領域の塗りつぶしには、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] のほぼすべてのグラフィカル オブジェクトが使用可能です。  
  
> [!NOTE]
>  <xref:System.Windows.Media.VisualBrush> は、一種の <xref:System.Windows.Freezable> オブジェクトですが、その <xref:System.Windows.Media.VisualBrush.Visual%2A> プロパティが `null` 以外の値に設定されている場合は、フリーズする \(読み取り専用にする\) ことはできません。  
  
 <xref:System.Windows.Media.VisualBrush> の <xref:System.Windows.Media.VisualBrush.Visual%2A> コンテンツを指定するには、2 とおりの方法があります。  
  
-   新しい <xref:System.Windows.Media.Visual> を作成し、このビジュアルを使用して <xref:System.Windows.Media.VisualBrush> の <xref:System.Windows.Media.VisualBrush.Visual%2A> プロパティを設定します。  例については、後の「[例 : ビジュアルを使用してオブジェクトを塗りつぶす](#examplevisualbrush1)」を参照してください。  
  
-   既存の <xref:System.Windows.Media.Visual> を使用して、ターゲットの <xref:System.Windows.Media.Visual> の複製イメージを作成します。  次に、<xref:System.Windows.Media.VisualBrush> を使用して反射や拡大などの効果を作成します。  例については、「[例 : 反射を作成する](#examplevisualbrush2)」を参照してください。  
  
 <xref:System.Windows.Media.VisualBrush> の <xref:System.Windows.Media.VisualBrush.Visual%2A> を新たに定義したときに、その <xref:System.Windows.Media.Visual> が <xref:System.Windows.UIElement> \(パネルやコントロールなど\) ならば、<xref:System.Windows.Media.VisualBrush.AutoLayoutContent%2A> プロパティが `true` に設定されている場合に <xref:System.Windows.UIElement> およびその子要素に基づいてレイアウト システムが実行されます。  ただし、ルートの <xref:System.Windows.UIElement> は実質的にシステムのその他の部分から切り離され、スタイルや外部レイアウトがこの境界を通過することはできません。  したがって、ルートの <xref:System.Windows.UIElement> のサイズは明示的に指定してください。その唯一の親が <xref:System.Windows.Media.VisualBrush> であるために、描画される領域に合わせて自身のサイズが自動的に設定されることはないからです。  [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] でのレイアウトの詳細については、「[レイアウト](../../../../docs/framework/wpf/advanced/layout.md)」を参照してください。  
  
 <xref:System.Windows.Media.ImageBrush> や <xref:System.Windows.Media.DrawingBrush> と同様に、<xref:System.Windows.Media.VisualBrush> で出力領域を塗りつぶすときはコンテンツが引き伸ばされます。  この動作をオーバーライドするには、<xref:System.Windows.Media.TileBrush.Stretch%2A> プロパティを、既定の設定である <xref:System.Windows.Media.Stretch> から別の設定に変更します。  詳細については、<xref:System.Windows.Media.TileBrush.Stretch%2A> プロパティのトピックを参照してください。  
  
<a name="examplevisualbrush1"></a>   
## 例 : ビジュアルを使用してオブジェクトを塗りつぶす  
 次の例では、いくつかのコントロールと 1 つのパネルを使用して四角形を塗りつぶします。  
  
 [!code-xml[BrushOverviewExamples_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/VisualBrushExample.xaml#graphicsmmvisualbrushasrectanglebackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/VisualBrushExample.cs#graphicsmmvisualbrushasrectanglebackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/visualbrushexample.vb#graphicsmmvisualbrushasrectanglebackgroundexample1)]  
  
<a name="examplevisualbrush2"></a>   
## 例 : 鏡像を作成する  
 前の例では、背景として使用するために <xref:System.Windows.Media.Visual> を新規作成する方法を示しました。  <xref:System.Windows.Media.VisualBrush> を使用して既存のビジュアルを表示することもできます。この機能を使用すると、反射や拡大などのユニークな視覚効果を作成できます。  次の例では、<xref:System.Windows.Media.VisualBrush> を使用して、複数の要素が含まれる <xref:System.Windows.Controls.Border> の鏡像を作成します。  この例が生成する出力を次の図に示します。  
  
 ![反映された Visual オブジェクト](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-visualbrush-reflection-small.png "graphicsmm\_visualbrush\_reflection\_small")  
ビジュアル オブジェクトの鏡像  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 この他の、画面の一部分を拡大する方法や鏡像を作成する方法の例については、[VisualBrush のサンプル](http://go.microsoft.com/fwlink/?LinkID=160049)を参照してください。  
  
<a name="tilebrush"></a>   
## TileBrush の機能  
 <xref:System.Windows.Media.ImageBrush>、<xref:System.Windows.Media.DrawingBrush>、および <xref:System.Windows.Media.VisualBrush> は、<xref:System.Windows.Media.TileBrush> オブジェクトの一種です。  <xref:System.Windows.Media.TileBrush> オブジェクトを使用すると、イメージ、描画、またはビジュアルで領域を塗りつぶす方法を細かく制御できます。  たとえば、引き伸ばした単一のイメージで領域をただ塗りつぶすのではなく、パターンを作成する一連のイメージ タイルで領域を塗りつぶすことができます。  
  
 <xref:System.Windows.Media.TileBrush> には、コンテンツ、タイル、および出力領域の 3 つの主要コンポーネントがあります。  
  
 ![TileBrush コンポーネント](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-defaultcontentprojection2.png "wcpsdk\_mmgraphics\_defaultcontentprojection2")  
1 つのタイルを使用する TileBrush のコンポーネント  
  
 ![並べて表示された TileBrush のコンポーネント](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tiledprojection.png "graphicsmm\_tiledprojection")  
複数のタイルを使用する TileBrush のコンポーネント  
  
 <xref:System.Windows.Media.TileBrush> オブジェクトの、並べて表示する機能の詳細については、「[TileBrush の概要](../../../../docs/framework/wpf/graphics-multimedia/tilebrush-overview.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Media.ImageBrush>   
 <xref:System.Windows.Media.DrawingBrush>   
 <xref:System.Windows.Media.VisualBrush>   
 <xref:System.Windows.Media.TileBrush>   
 [TileBrush の概要](../../../../docs/framework/wpf/graphics-multimedia/tilebrush-overview.md)   
 [WPF のブラシの概要](../../../../docs/framework/wpf/graphics-multimedia/wpf-brushes-overview.md)   
 [イメージングの概要](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)   
 [Drawing オブジェクトの概要](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)   
 [不透明マスクの概要](../../../../docs/framework/wpf/graphics-multimedia/opacity-masks-overview.md)   
 [WPF グラフィックス レンダリングの概要](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)   
 [ImageBrush のサンプル](http://go.microsoft.com/fwlink/?LinkID=160005)   
 [VisualBrush のサンプル](http://go.microsoft.com/fwlink/?LinkID=160049)