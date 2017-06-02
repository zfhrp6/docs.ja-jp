---
title: "WPF での図形と基本描画の概要 | Microsoft Docs"
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
  - "基本描画"
  - "図形オブジェクト"
  - "形状, 図形の概要"
  - "ベクター描画, 概要"
  - "ベクター, 描画"
ms.assetid: 66d7a6d6-e3b6-47bc-8dfe-8a1b26f7d901
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# WPF での図形と基本描画の概要
ここでは、<xref:System.Windows.Shapes.Shape> オブジェクトを使用した描画方法の概要を示します。  <xref:System.Windows.Shapes.Shape> は、画面に図形を描画できるようにする <xref:System.Windows.UIElement> の一種です。  <xref:System.Windows.Shapes.Shape> オブジェクトは UI 要素であるため、<xref:System.Windows.Controls.Panel> 要素およびほとんどのコントロール内で使用できます。  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] には、グラフィックス サービスやレンダリング サービスへのアクセスのレイヤーがいくつか用意されています。  最上位レイヤーにある <xref:System.Windows.Shapes.Shape> オブジェクトは使いやすく、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] イベント システムでのレイアウトや参加などのさまざまな役立つ機能を提供します。  
  
   
  
<a name="shapes"></a>   
## 図形オブジェクト  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、すぐに使用できるさまざまな <xref:System.Windows.Shapes.Shape> オブジェクトが用意されています。  すべての図形オブジェクトは <xref:System.Windows.Shapes.Shape> クラスから継承されます。  使用可能な図形オブジェクトには、<xref:System.Windows.Shapes.Ellipse>、<xref:System.Windows.Shapes.Line>、<xref:System.Windows.Shapes.Path>、<xref:System.Windows.Shapes.Polygon>、<xref:System.Windows.Shapes.Polyline>、<xref:System.Windows.Shapes.Rectangle> などがあります。<xref:System.Windows.Shapes.Shape> オブジェクトは、次の共通プロパティを共有します。  
  
-   <xref:System.Windows.Shapes.Shape.Stroke%2A> : 図形のアウトラインをどのように塗りつぶすかを示します。  
  
-   <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> : 図形のアウトラインの太さを示します。  
  
-   <xref:System.Windows.Shapes.Shape.Fill%2A> : 図形の内部をどのように塗りつぶすかを示します。  
  
-   [デバイス非依存ピクセル](GTMT)単位で計測される座標と頂点を指定するデータ プロパティ。  
  
 図形オブジェクトは <xref:System.Windows.UIElement> から派生するため、パネルおよびほとんどのコントロール内で使用できます。  <xref:System.Windows.Controls.Canvas> パネルは子オブジェクトの絶対配置をサポートするため、複雑な描画の作成に特に適しています。  
  
 <xref:System.Windows.Shapes.Line> クラスを使用すると、2 つの点の間の直線を描画できます。  直線の座標およびストローク プロパティを指定するいくつかの方法を次の例に示します。  
  
 [!code-xml[drawingwithshapeelements#LineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 [!code-cpp[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/cpp/VS_Snippets_Wpf/ShapesProcedural/CPP/ShapesProcedural.cpp#shapesproceduralline)]
 [!code-csharp[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ShapesProcedural/Csharp/ShapesProcedural.cs#shapesproceduralline)]
 [!code-vb[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ShapesProcedural/VisualBasic/ShapesProceduralVB.vb#shapesproceduralline)]  
  
 レンダリングされた <xref:System.Windows.Shapes.Line> を次の図に示します。  
  
 ![線の図](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-line2.png "shape\_ovw\_line2")  
  
 <xref:System.Windows.Shapes.Line> クラスは <xref:System.Windows.Shapes.Shape.Fill%2A> プロパティを提供しますが、<xref:System.Windows.Shapes.Line> には領域がないため、そのプロパティを設定しても無効です。  
  
 もう 1 つの一般的な図形は <xref:System.Windows.Shapes.Ellipse> です。  <xref:System.Windows.Shapes.Ellipse> は、図形の <xref:System.Windows.FrameworkElement.Width%2A> および <xref:System.Windows.FrameworkElement.Height%2A> プロパティを定義して作成します。  円を描画するには、<xref:System.Windows.FrameworkElement.Width%2A> および <xref:System.Windows.FrameworkElement.Height%2A> の値が等しい <xref:System.Windows.Shapes.Ellipse> を指定します。  
  
 [!code-xml[ShapeOverviews#ShapesOVW1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ShapeOverviews/CS/Window1.xaml#shapesovw1)]  
  
 [!code-csharp[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/CSharp/SetBackgroundColorOfShapeExample.cs#setbackgroundcolorofshapecodeexamplewholepage)]
 [!code-vb[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/visualbasic/setbackgroundcolorofshapeexample.vb#setbackgroundcolorofshapecodeexamplewholepage)]  
  
 レンダリングされた <xref:System.Windows.Shapes.Ellipse> の例を次の図に示します。  
  
 ![楕円の図](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-ellipse2.png "shape\_ovw\_ellipse2")  
  
<a name="paths"></a>   
## パスとジオメトリの使用  
 <xref:System.Windows.Shapes.Path> クラスを使用すると、曲線および複雑な図形を描画できます。  これらの曲線および図形は、<xref:System.Windows.Media.Geometry> オブジェクトを使用して表現されます。  <xref:System.Windows.Shapes.Path> を使用するには、<xref:System.Windows.Media.Geometry> を作成し、それを使用して <xref:System.Windows.Shapes.Path> オブジェクトの <xref:System.Windows.Shapes.Path.Data%2A> プロパティを設定します。  
  
 さまざまな <xref:System.Windows.Media.Geometry> オブジェクトが用意されています。  <xref:System.Windows.Media.LineGeometry>、<xref:System.Windows.Media.RectangleGeometry>、および <xref:System.Windows.Media.EllipseGeometry> クラスは、比較的単純な図形を表現します。  より複雑な図形または曲線を作成するには、<xref:System.Windows.Media.PathGeometry> を使用します。  
  
<a name="pathgeometry"></a>   
### PathGeometry と PathSegment  
 <xref:System.Windows.Media.PathGeometry> オブジェクトは 1 つ以上の <xref:System.Windows.Media.PathFigure> オブジェクトで構成され、各 <xref:System.Windows.Media.PathFigure> は異なる "形状" または図形を表します。  各 <xref:System.Windows.Media.PathFigure> 自体は 1 つ以上の <xref:System.Windows.Media.PathSegment> オブジェクトで構成されており、このオブジェクトは形状または図形の接続されている部分を表します。  セグメントの種類には、<xref:System.Windows.Media.LineSegment>、<xref:System.Windows.Media.BezierSegment>、<xref:System.Windows.Media.ArcSegment> などがあります。  
  
 次の例では、<xref:System.Windows.Shapes.Path> を使用して 2 次ベジエ曲線を描画します。  
  
 [!code-xml[geometrysample#34](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 レンダリングされた図形を次の図に示します。  
  
 ![パスの図](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path2.png "shape\_ovw\_path2")  
  
 <xref:System.Windows.Media.PathGeometry> およびその他の <xref:System.Windows.Media.Geometry> クラスの詳細については、「[ジオメトリの概要](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)」を参照してください。  
  
<a name="pathdatastring"></a>   
### 省略された XAML 構文  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] では、省略された特殊な構文を使用して <xref:System.Windows.Shapes.Path> を記述することもできます。  次の例では、省略された構文を使用して複雑な図形を描画します。  
  
```xaml  
<Path Stroke="DarkGoldenRod" StrokeThickness="3"   
Data="M 100,200 C 100,25 400,350 400,175 H 280" />  
```  
  
 レンダリングされた <xref:System.Windows.Shapes.Path> を次の図に示します。  
  
 ![パスの図](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path.png "shape\_ovw\_path")  
  
 <xref:System.Windows.Shapes.Path.Data%2A> 属性文字列は、M で示される "moveto" コマンドで始まります。このコマンドは、<xref:System.Windows.Controls.Canvas> の座標系のパスの始点を設定します。  <xref:System.Windows.Shapes.Path> データ パラメーターでは、大文字と小文字が区別されます。  大文字の M は、現在の新しい点の絶対位置を示します。  小文字の m は、相対座標を示します。  最初のセグメントは、2 つの制御点 \(100,25\) と \(400,350\) を使用して描画される、始点が \(100,200\) で終点が \(400,175\) の 3 次[ベジエ曲線](GTMT)です。  このセグメントは、<xref:System.Windows.Shapes.Path.Data%2A> 属性文字列の C コマンドで示されます。  ここでも、大文字の C は絶対パスを示し、小文字の c は相対パスを示します。  
  
 2 番目のセグメントは、絶対水平 "lineto" コマンド H で始まります。このコマンドは、前のサブパスの終点 \(400,175\) から新しい終点 \(280,175\) まで描画される直線を指定します。  水平 "lineto" コマンドであるため、指定される値は x 座標です。  
  
 パスの構文全体については、<xref:System.Windows.Shapes.Path.Data%2A> のリファレンスと「[PathGeometry を使用して図形を作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)」を参照してください。  
  
<a name="fillpaint"></a>   
## 図形の塗りつぶし  
 <xref:System.Windows.Media.Brush> オブジェクトは、図形の <xref:System.Windows.Shapes.Shape.Stroke%2A> および <xref:System.Windows.Shapes.Shape.Fill%2A> を塗りつぶす場合に使用します。  次の例では、<xref:System.Windows.Shapes.Ellipse> のストロークおよび塗りつぶしを指定します。  ブラシ プロパティの有効な入力は、キーワードまたは 16 進数のカラー値のいずれかです。  使用可能なカラー キーワードの詳細については、<xref:System.Windows.Media> 名前空間の <xref:System.Windows.Media.Colors> クラスのプロパティを参照してください。  
  
```  
  
<Canvas Background="LightGray">   
   <Ellipse  
      Canvas.Top="50"  
      Canvas.Left="50"  
      Fill="#FFFFFF00"  
      Height="75"  
      Width="75"  
      StrokeThickness="5"  
      Stroke="#FF0000FF"/>  
</Canvas>  
  
```  
  
 レンダリングされた <xref:System.Windows.Shapes.Ellipse> を次の図に示します。  
  
 ![楕円](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-ellipsefill.png "shape\_ovw\_ellipsefill")  
  
 このほか、プロパティ要素構文を使用して <xref:System.Windows.Media.SolidColorBrush> オブジェクトを明示的に作成し、純色で図形を塗りつぶすこともできます。  
  
```  
  
<!-- This polygon shape uses pre-defined color values for its Stroke and  
     Fill properties.   
     The SolidColorBrush's Opacity property affects the fill color in   
     this case by making it slightly transparent (opacity of 0.4) so   
     that it blends with any underlying color. -->  
  
<Polygon  
    Points="300,200 400,125 400,275 300,200"  
    Stroke="Purple"   
    StrokeThickness="2">  
    <Polygon.Fill>  
       <SolidColorBrush Color="Blue" Opacity="0.4"/>  
    </Polygon.Fill>  
</Polygon>  
```  
  
 レンダリングされた図形を次の図に示します。  
  
 ![SolidColorBrush の図](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-solidcolorbrush.png "shape\_ovw\_solidcolorbrush")  
  
 図形のストロークまたは塗りつぶしをグラデーション、イメージ、パターンなどで塗りつぶすこともできます。  詳細については、「[純色およびグラデーションによる塗りつぶしの概要](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)」を参照してください。  
  
<a name="stretchableshapessection"></a>   
## 伸縮可能な図形  
 <xref:System.Windows.Shapes.Line>、<xref:System.Windows.Shapes.Path>、<xref:System.Windows.Shapes.Polygon>、<xref:System.Windows.Shapes.Polyline>、および <xref:System.Windows.Shapes.Rectangle> クラスには、すべて <xref:System.Windows.Shapes.Shape.Stretch%2A> プロパティがあります。  このプロパティは、<xref:System.Windows.Shapes.Shape> オブジェクトのコンテンツ \(描画される図形\) をどのように引き伸ばして <xref:System.Windows.Shapes.Shape> オブジェクトのレイアウト空間を塗りつぶすかを決定します。  <xref:System.Windows.Shapes.Shape> オブジェクトのレイアウト空間は、明示的な <xref:System.Windows.FrameworkElement.Width%2A> および <xref:System.Windows.FrameworkElement.Height%2A> 設定または <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> および <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> 設定のために、レイアウト システムによって <xref:System.Windows.Shapes.Shape> に割り当てられるスペースです。  Windows Presentation Foundation のレイアウトの詳細については、「[レイアウト](../../../../docs/framework/wpf/advanced/layout.md)」を参照してください。  
  
 Stretch プロパティには、次のいずれかの値を指定します。  
  
-   <xref:System.Windows.Media.Stretch> : <xref:System.Windows.Shapes.Shape> オブジェクトのコンテンツは引き伸ばされません。  
  
-   <xref:System.Windows.Media.Stretch> : <xref:System.Windows.Shapes.Shape> オブジェクトのコンテンツは、レイアウト空間を塗りつぶすように引き伸ばされます。  縦横比は維持されません。  
  
-   <xref:System.Windows.Media.Stretch> : <xref:System.Windows.Shapes.Shape> オブジェクトのコンテンツは、元の縦横比を維持しながら、レイアウト空間を塗りつぶすように可能な限り引き伸ばされます。  
  
-   <xref:System.Windows.Media.Stretch> : <xref:System.Windows.Shapes.Shape> オブジェクトのコンテンツは、元の縦横比を維持しながら、レイアウト空間を完全に塗りつぶすように引き伸ばされます。  
  
 <xref:System.Windows.Shapes.Shape> オブジェクトのコンテンツを引き伸ばすとき、<xref:System.Windows.Shapes.Shape> オブジェクトのアウトラインは、引き伸ばされた後に塗りつぶされます。  
  
 次の例では、<xref:System.Windows.Shapes.Polygon> を使用して、頂点が \(0,0\)、\(0,1\)、および \(1,1\) の非常に小さい三角形を描画します。  <xref:System.Windows.Shapes.Polygon> オブジェクトの <xref:System.Windows.FrameworkElement.Width%2A> および <xref:System.Windows.FrameworkElement.Height%2A> は 100 に設定され、その Stretch プロパティは Fill に設定されます。  その結果、<xref:System.Windows.Shapes.Polygon> オブジェクトのコンテンツ \(三角形\) は、より大きい空間を塗りつぶすように引き伸ばされます。  
  
```  
...  
<Polygon  
  Points="0,0 0,1 1,1"  
  Fill="Blue"  
  Width="100"  
  Height="100"  
  Stretch="Fill"  
  Stroke="Black"  
  StrokeThickness="2" />  
...  
```  
  
```  
...  
PointCollection myPointCollection = new PointCollection();  
myPointCollection.Add(new Point(0,0));  
myPointCollection.Add(new Point(0,1));  
myPointCollection.Add(new Point(1,1));  
  
Polygon myPolygon = new Polygon();  
myPolygon.Points = myPointCollection;  
myPolygon.Fill = Brushes.Blue;  
myPolygon.Width = 100;  
myPolygon.Height = 100;  
myPolygon.Stretch = Stretch.Fill;  
myPolygon.Stroke = Brushes.Black;  
myPolygon.StrokeThickness = 2;  
...  
```  
  
<a name="transforms"></a>   
## 図形の変換  
 <xref:System.Windows.Media.Transform> クラスは、2 次元の平面で図形を変換する手段を提供します。  変換には、回転 \(<xref:System.Windows.Media.RotateTransform>\)、スケーリング \(<xref:System.Windows.Media.ScaleTransform>\)、傾斜 \(<xref:System.Windows.Media.SkewTransform>\)、および平行移動 \(<xref:System.Windows.Media.TranslateTransform>\) などのさまざまな種類があります。  
  
 図形に適用される一般的な変換は回転です。  図形を回転するには、<xref:System.Windows.Media.RotateTransform> を作成し、その <xref:System.Windows.Media.RotateTransform.Angle%2A> を指定します。  <xref:System.Windows.Media.RotateTransform.Angle%2A> が 45 の場合は要素が時計回りに 45 度回転し、90 では要素が時計回りに 90 度回転します。  要素の回転の中心点を設定するには、<xref:System.Windows.Media.RotateTransform.CenterX%2A> と <xref:System.Windows.Media.RotateTransform.CenterY%2A> のプロパティを設定します。  これらのプロパティ値は、変換する要素の座標空間で表します。  <xref:System.Windows.Media.RotateTransform.CenterX%2A> および <xref:System.Windows.Media.RotateTransform.CenterY%2A> の既定値は 0 です。  最後に、要素に <xref:System.Windows.Media.RotateTransform> を適用します。  変換がレイアウトに影響しないようにする場合は、図形の <xref:System.Windows.UIElement.RenderTransform%2A> プロパティを設定します。  
  
 次の例では、<xref:System.Windows.Media.RotateTransform> を使用して、図形をその左上隅 \(0,0\) を中心に 45 度回転しています。  
  
 [!code-xml[transformssample#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#14)]  
  
 次の例では、別の図形を 45 度回転していますが、この場合は \(25,50\) が回転の中心です。  
  
 [!code-xml[transformssample#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#15)]  
  
 上記 2 つの変換を適用すると、結果は次の図のようになります。  
  
 ![中心点が異なる 45 度の回転](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-rotatetransform45degrees.png "wcpsdk\_graphicsmm\_rotatetransform45degrees")  
  
 前の例では、単一の変換を各図形オブジェクトに適用しました。  1 つの図形 \(またはその他の UI 要素\) に複数の変換を適用するには、<xref:System.Windows.Media.TransformGroup> を使用します。  
  
## 参照  
 [2D グラフィックスとイメージング](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)   
 [純色およびグラデーションによる塗りつぶしの概要](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)   
 [ジオメトリの概要](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)   
 [チュートリアル: WPF の概要](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)   
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)