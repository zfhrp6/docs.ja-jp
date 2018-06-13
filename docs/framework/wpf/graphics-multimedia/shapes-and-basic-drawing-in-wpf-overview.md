---
title: WPF での図形と基本描画の概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- shapes [WPF], about shapes
- basic drawing [WPF]
- vector drawing [WPF], overview
- vectors [WPF], drawing
- Shape objects [WPF]
ms.assetid: 66d7a6d6-e3b6-47bc-8dfe-8a1b26f7d901
ms.openlocfilehash: adbf982da25ff445d277b7c1b5911217d9825c02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566312"
---
# <a name="shapes-and-basic-drawing-in-wpf-overview"></a>WPF での図形と基本描画の概要
このトピックでを使用して描画する方法の概要<xref:System.Windows.Shapes.Shape>オブジェクト。 A<xref:System.Windows.Shapes.Shape>の種類は、<xref:System.Windows.UIElement>形を画面に描画することができます。 UI 要素であるため<xref:System.Windows.Shapes.Shape>内のオブジェクトで使用できます<xref:System.Windows.Controls.Panel>要素およびほとんどのコントロールです。  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] には、グラフィックス サービスやレンダリング サービスへのアクセスのレイヤーがいくつか用意されています。 最上位のレイヤーで<xref:System.Windows.Shapes.Shape>オブジェクトが簡単に使用し、レイアウトやへの参加など、多くの便利な機能を提供、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]イベント システムです。  
  
  
<a name="shapes"></a>   
## <a name="shape-objects"></a>図形オブジェクト  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] すぐに使用できるいくつか提供<xref:System.Windows.Shapes.Shape>オブジェクト。  すべての図形オブジェクトの継承、<xref:System.Windows.Shapes.Shape>クラスです。 使用可能な図形オブジェクトには、 <xref:System.Windows.Shapes.Ellipse>、 <xref:System.Windows.Shapes.Line>、 <xref:System.Windows.Shapes.Path>、 <xref:System.Windows.Shapes.Polygon>、 <xref:System.Windows.Shapes.Polyline>、および<xref:System.Windows.Shapes.Rectangle>です。 <xref:System.Windows.Shapes.Shape> オブジェクトは、次の一般的なプロパティを共有します。  
  
-   <xref:System.Windows.Shapes.Shape.Stroke%2A>: 図形の輪郭を描画する方法について説明します。  
  
-   <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: 図形の輪郭の幅を示します。  
  
-   <xref:System.Windows.Shapes.Shape.Fill%2A>: 図形の内部を描画する方法について説明します。  
  
-   デバイス非依存ピクセル単位で計測される座標と頂点を指定するデータ プロパティ。  
  
 派生させ、ため<xref:System.Windows.UIElement>パネルとほとんどのコントロールの内部の図形オブジェクトを使用できます。 <xref:System.Windows.Controls.Canvas>パネルは、その子オブジェクトの絶対位置指定をサポートするために、複雑な図面を作成するのに特に適しています。  
  
 <xref:System.Windows.Shapes.Line>クラスでは、2 点を結ぶ線を描画することができます。 直線の座標およびストローク プロパティを指定するいくつかの方法を次の例に示します。  
  
 [!code-xaml[drawingwithshapeelements#LineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 [!code-cpp[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/cpp/VS_Snippets_Wpf/ShapesProcedural/CPP/ShapesProcedural.cpp#shapesproceduralline)]
 [!code-csharp[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ShapesProcedural/Csharp/ShapesProcedural.cs#shapesproceduralline)]
 [!code-vb[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ShapesProcedural/VisualBasic/ShapesProceduralVB.vb#shapesproceduralline)]  
  
 次の図は、レンダリングされた<xref:System.Windows.Shapes.Line>です。  
  
 ![線の図](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-line2.gif "shape_ovw_line2")  
  
 ただし、<xref:System.Windows.Shapes.Line>クラスを提供、<xref:System.Windows.Shapes.Shape.Fill%2A>プロパティを設定しても何も起こりませんため、<xref:System.Windows.Shapes.Line>領域がありません。  
  
 別の一般的な図形は、<xref:System.Windows.Shapes.Ellipse>です。  作成、<xref:System.Windows.Shapes.Ellipse>図形を定義することによって<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>プロパティです。 円を描画するには、指定、<xref:System.Windows.Shapes.Ellipse>が<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>値が等しい。  
  
 [!code-xaml[ShapeOverviews#ShapesOVW1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ShapeOverviews/CS/Window1.xaml#shapesovw1)]  
  
 [!code-csharp[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/CSharp/SetBackgroundColorOfShapeExample.cs#setbackgroundcolorofshapecodeexamplewholepage)]
 [!code-vb[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/visualbasic/setbackgroundcolorofshapeexample.vb#setbackgroundcolorofshapecodeexamplewholepage)]  
  
 次の図は、レンダリングの例を示します<xref:System.Windows.Shapes.Ellipse>です。  
  
 ![楕円の図](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")  
  
<a name="paths"></a>   
## <a name="using-paths-and-geometries"></a>パスとジオメトリの使用  
 <xref:System.Windows.Shapes.Path>クラスでは、曲線と複雑な図形を描画することができます。 これらの曲線および図形を使用して記述<xref:System.Windows.Media.Geometry>オブジェクト。 使用する、 <xref:System.Windows.Shapes.Path>、作成する、<xref:System.Windows.Media.Geometry>設定を使用して、<xref:System.Windows.Shapes.Path>オブジェクトの<xref:System.Windows.Shapes.Path.Data%2A>プロパティです。  
  
 さまざまな<xref:System.Windows.Media.Geometry>からを選択するオブジェクト。 <xref:System.Windows.Media.LineGeometry>、 <xref:System.Windows.Media.RectangleGeometry>、および<xref:System.Windows.Media.EllipseGeometry>クラスは、比較的単純な図形を記述します。 複雑な図形を作成または曲線を作成、使用して、<xref:System.Windows.Media.PathGeometry>です。  
  
<a name="pathgeometry"></a>   
### <a name="pathgeometry-and-pathsegments"></a>PathGeometry と PathSegment  
 <xref:System.Windows.Media.PathGeometry> オブジェクトは、1 つまたは複数の構成要素は<xref:System.Windows.Media.PathFigure>オブジェクトです。 各<xref:System.Windows.Media.PathFigure>異なる"図"または図形を表します。 各<xref:System.Windows.Media.PathFigure>はそれ自体から成る 1 つ以上の<xref:System.Windows.Media.PathSegment>それぞれ図や図形の接続の部分を表すオブジェクトします。 セグメントの種類、次のとおりです: <xref:System.Windows.Media.LineSegment>、 <xref:System.Windows.Media.BezierSegment>、および<xref:System.Windows.Media.ArcSegment>です。  
  
 次の例で、 <xref:System.Windows.Shapes.Path> 2 次ベジエ曲線の描画に使用します。  
  
 [!code-xaml[geometrysample#34](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 レンダリングされた図形を次の図に示します。  
  
 ![パスの図](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path2.gif "shape_ovw_path2")  
  
 詳細については<xref:System.Windows.Media.PathGeometry>と、その他の<xref:System.Windows.Media.Geometry>クラスを参照してください、[ジオメトリの概要](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)です。  
  
<a name="pathdatastring"></a>   
### <a name="xaml-abbreviated-syntax"></a>省略された XAML 構文  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]、記述する、特殊な省略構文を使用することも、<xref:System.Windows.Shapes.Path>です。 次の例では、省略された構文を使用して複雑な図形を描画します。  
  
```xaml  
      <Path Stroke="DarkGoldenRod" StrokeThickness="3"   
Data="M 100,200 C 100,25 400,350 400,175 H 280" />  
```  
  
 次の図は、レンダリングされた<xref:System.Windows.Shapes.Path>です。  
  
 ![パスの図](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path.PNG "shape_ovw_path")  
  
 <xref:System.Windows.Shapes.Path.Data%2A>属性文字列の先頭の座標システムで、パスの開始ポイントを確立する、M によって示される、"moveto"コマンドが、<xref:System.Windows.Controls.Canvas>です。 <xref:System.Windows.Shapes.Path> データのパラメーターは大文字小文字を区別します。 大文字の M では、新しい現在のポイントの絶対位置を示します。 小文字の m は、相対座標を示します。 最初のセグメントは、2 つの制御点 (100,25) と (400,350) を使用して描画される、始点が (100,200) で終点が (400,175) の 3 次ベジエ曲線です。 このセグメントは、C コマンドで、<xref:System.Windows.Shapes.Path.Data%2A>属性の文字列。 ここでも、大文字の C は絶対パスを示し、小文字の c は相対パスを示します。  
  
 2 番目のセグメントは、絶対水平 "lineto" コマンド H で始まります。このコマンドは、前のサブパスの終点 (400,175) から新しい終点 (280,175) まで描画される直線を指定します。 指定された値は、水平"lineto"コマンドになっているため、 *x*-を調整します。  
  
 完全なパスの構文については、次を参照してください。、<xref:System.Windows.Shapes.Path.Data%2A>参照と[PathGeometry を使用して図形を作成](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)です。  
  
<a name="fillpaint"></a>   
## <a name="painting-shapes"></a>図形の塗りつぶし  
 <xref:System.Windows.Media.Brush> オブジェクトは、図形の描画に使用<xref:System.Windows.Shapes.Shape.Stroke%2A>と<xref:System.Windows.Shapes.Shape.Fill%2A>です。 次の例、線、およびの塗りつぶし、<xref:System.Windows.Shapes.Ellipse>が指定されています。 ブラシ プロパティの有効な入力は、キーワードまたは 16 進数のカラー値のいずれかです。 使用可能な色のキーワードの詳細については、のプロパティを参照してください、<xref:System.Windows.Media.Colors>クラス内で、<xref:System.Windows.Media>名前空間。  
  
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
  
 次の図は、レンダリングされた<xref:System.Windows.Shapes.Ellipse>です。  
  
 ![楕円](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")  
  
 プロパティ要素構文を使用して明示的に作成する代わりに、<xref:System.Windows.Media.SolidColorBrush>を純色で図形を描画するオブジェクト。  
  
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
  
 ![SolidColorBrush の図](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")  
  
 図形のストロークまたは塗りつぶしをグラデーション、イメージ、パターンなどで塗りつぶすこともできます。 詳細については、次を参照してください。、[純色、グラデーションの概要でペイント](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)です。  
  
<a name="stretchableshapessection"></a>   
## <a name="stretchable-shapes"></a>伸縮可能な図形  
 <xref:System.Windows.Shapes.Line>、 <xref:System.Windows.Shapes.Path>、 <xref:System.Windows.Shapes.Polygon>、 <xref:System.Windows.Shapes.Polyline>、および<xref:System.Windows.Shapes.Rectangle>クラスがすべて、<xref:System.Windows.Shapes.Shape.Stretch%2A>プロパティです。 このプロパティを決定する方法、<xref:System.Windows.Shapes.Shape>オブジェクトの内容 (描画される図形) に合わせて引き伸ばされます、<xref:System.Windows.Shapes.Shape>オブジェクトのレイアウト領域。 A<xref:System.Windows.Shapes.Shape>オブジェクトのレイアウト領域は、領域の量、<xref:System.Windows.Shapes.Shape>が割り当てられる、レイアウト システムでは、いずれかの明示的な<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>設定のため、またはその<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>と<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>設定します。 Windows Presentation Foundation でのレイアウトの詳細については、次を参照してください。[レイアウト](../../../../docs/framework/wpf/advanced/layout.md)の概要です。  
  
 プロパティには、次のいずれかの値を指定します。  
  
-   <xref:System.Windows.Media.Stretch.None><xref:System.Windows.Shapes.Shape>オブジェクトの内容が拡大されていません。  
  
-   <xref:System.Windows.Media.Stretch.Fill><xref:System.Windows.Shapes.Shape>オブジェクトの内容がそのレイアウト領域に合わせて引き伸ばされます。  縦横比は維持されません。  
  
-   <xref:System.Windows.Media.Stretch.Uniform><xref:System.Windows.Shapes.Shape>オブジェクトの内容が元の縦横比を維持しながら、レイアウト領域に可能な限りは拡大します。  
  
-   <xref:System.Windows.Media.Stretch.UniformToFill><xref:System.Windows.Shapes.Shape>オブジェクトの内容が元の縦横比を維持しながら完全にそのレイアウト領域に合わせて引き伸ばされます。  
  
 なお、ときに、<xref:System.Windows.Shapes.Shape>オブジェクトの内容は拡大、<xref:System.Windows.Shapes.Shape>拡大した後はオブジェクトの輪郭を描画します。  
  
 次の例で、 <xref:System.Windows.Shapes.Polygon> (1, 1) に (0, 0) から (0, 1) には非常に小さな三角形の描画に使用します。 <xref:System.Windows.Shapes.Polygon>オブジェクトの<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>100 に設定され、拡張プロパティは Fill に設定します。 その結果、<xref:System.Windows.Shapes.Polygon>オブジェクトの内容 (三角形) が、領域に合わせて引き伸ばされます。  
  
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
## <a name="transforming-shapes"></a>図形の変換  
 <xref:System.Windows.Media.Transform>クラスは、2 次元平面内の図形を変換するための手段を提供します。  変換のさまざまな種類は、回転 (<xref:System.Windows.Media.RotateTransform>)、小数点以下桁数 (<xref:System.Windows.Media.ScaleTransform>)、傾斜 (<xref:System.Windows.Media.SkewTransform>)、および翻訳 (<xref:System.Windows.Media.TranslateTransform>)。  
  
 図形に適用される一般的な変換は回転です。  回転するには、図形を作成、<xref:System.Windows.Media.RotateTransform>を指定し、<xref:System.Windows.Media.RotateTransform.Angle%2A>です。 <xref:System.Windows.Media.RotateTransform.Angle%2A> 45 の要素を 45 度回転角度が 90 の要素を 90 度回転; 時計回り時計回りします。 設定、<xref:System.Windows.Media.RotateTransform.CenterX%2A>と<xref:System.Windows.Media.RotateTransform.CenterY%2A>プロパティを要素を回転するポイントを制御する場合。 これらのプロパティ値は、変換する要素の座標空間で表します。 <xref:System.Windows.Media.RotateTransform.CenterX%2A> および<xref:System.Windows.Media.RotateTransform.CenterY%2A>ゼロの既定値があります。 最後に、適用、<xref:System.Windows.Media.RotateTransform>要素にします。 レイアウトに影響する変換しない場合は、設定、図形の<xref:System.Windows.UIElement.RenderTransform%2A>プロパティです。  
  
 次の例で、<xref:System.Windows.Media.RotateTransform>図形の左上隅 (0, 0) に関する図形 45 度回転するために使用します。  
  
 [!code-xaml[transformssample#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#14)]  
  
 次の例では、別の図形を 45 度回転していますが、この場合は (25,50) が回転の中心です。  
  
 [!code-xaml[transformssample#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#15)]  
  
 上記 2 つの変換を適用すると、結果は次の図のようになります。  
  
 ![中心点が異なる 45 度の回転](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")  
  
 前の例では、単一の変換を各図形オブジェクトに適用しました。 適用するには複数の変換図形 (またはその他の UI 要素) を使用して、<xref:System.Windows.Media.TransformGroup>です。  
  
## <a name="see-also"></a>関連項目  
 [2D グラフィックスとイメージング](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [純色およびグラデーションによる塗りつぶしの概要](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [ジオメトリの概要](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [チュートリアル: 初めての WPF デスクトップ アプリケーション](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
