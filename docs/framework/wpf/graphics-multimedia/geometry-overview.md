---
title: "ジオメトリの概要 | Microsoft Docs"
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
  - "クラス, ジオメトリ"
  - "CombinedGeometry クラス"
  - "EllipseGeometry クラス"
  - "ジオメトリ クラス"
  - "グラフィックス, ジオメトリ クラス"
  - "LineGeometry クラス"
  - "PathGeometry クラス"
  - "RectangleGeometry クラス"
ms.assetid: 9fba8934-98b7-4af6-82f6-f4ef887f963a
caps.latest.revision: 23
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 22
---
# ジオメトリの概要
ここでは、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] の <xref:System.Windows.Media.Geometry> クラスを使用して図形を記述する方法を説明します。  また、<xref:System.Windows.Media.Geometry> オブジェクトと <xref:System.Windows.Shapes.Shape> 要素の違いも示します。  
  
   
  
<a name="wcpsdk_graphics_geometry_introduction"></a>   
## ジオメトリとは  
 <xref:System.Windows.Media.Geometry> クラス、および <xref:System.Windows.Media.EllipseGeometry>、<xref:System.Windows.Media.PathGeometry>、<xref:System.Windows.Media.CombinedGeometry> などの派生クラスを使用すると、2\-D 図形のジオメトリを記述できます。  これらの幾何学的な記述には、画面を塗りつぶす図形を定義したり、ヒット テストやクリップ領域を定義するなど、多くの用途があります。  ジオメトリを使用して、アニメーション パスを定義することもできます。  
  
 <xref:System.Windows.Media.Geometry> オブジェクトは、四角形や円などの単純なものにすることも、2 つ以上のジオメトリ オブジェクトから作成された複合的なものにすることもできます。  <xref:System.Windows.Media.PathGeometry> クラスや <xref:System.Windows.Media.StreamGeometry> クラスなど、円弧や曲線を記述できるクラスを使用すると、さらに複雑なジオメトリを作成することができます。  
  
 <xref:System.Windows.Media.Geometry> は <xref:System.Windows.Freezable> オブジェクトの一種であるため、<xref:System.Windows.Media.Geometry> オブジェクトにはいくつかの特殊な機能があります。具体的には、[リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)としての宣言、複数オブジェクトでの共有、読み取り専用に設定することによるパフォーマンスの向上、複製、スレッド セーフの設定などです。  <xref:System.Windows.Freezable> オブジェクトのさまざまな機能の詳細については、「[Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)」を参照してください。  
  
<a name="wcpsdk_graphics_geometry_geometryandshapes"></a>   
## ジオメトリと図形  
 <xref:System.Windows.Media.Geometry> クラスと <xref:System.Windows.Shapes.Shape> クラスは、両方とも 2\-D 図形を記述するという点で似ていますが \(<xref:System.Windows.Media.EllipseGeometry> と <xref:System.Windows.Shapes.Ellipse> を比較した場合など\)、重要な違いがあります。  
  
 その 1 つは、<xref:System.Windows.Media.Geometry> クラスが <xref:System.Windows.Freezable> クラスを継承するのに対し、<xref:System.Windows.Shapes.Shape> クラスは <xref:System.Windows.FrameworkElement> を継承するという点です。  これらは要素であるため、<xref:System.Windows.Shapes.Shape> オブジェクトは自身をレンダリングしたり、レイアウト システムに参加することができますが、<xref:System.Windows.Media.Geometry> オブジェクトはそのような動作を実行できません。  
  
 <xref:System.Windows.Shapes.Shape> オブジェクトは、<xref:System.Windows.Media.Geometry> オブジェクトよりも簡単に使用できますが、<xref:System.Windows.Media.Geometry> オブジェクトは、より幅広い用途で使用できます。  <xref:System.Windows.Shapes.Shape> オブジェクトは、2\-D グラフィックスのレンダリングに使用されますが、<xref:System.Windows.Media.Geometry> オブジェクトは、2\-D グラフィックスの幾何学領域を定義したり、クリップ用の領域を定義したり、ヒット テスト用の領域を定義するなどに使用されます。  
  
### パス図形  
 <xref:System.Windows.Shapes.Shape> の 1 つである <xref:System.Windows.Shapes.Path> クラスは、実際には <xref:System.Windows.Media.Geometry> を使用してそのコンテンツを記述します。  <xref:System.Windows.Media.Geometry> で <xref:System.Windows.Shapes.Path> の <xref:System.Windows.Shapes.Path.Data%2A> プロパティを設定し、その <xref:System.Windows.Shapes.Shape.Fill%2A> プロパティと <xref:System.Windows.Shapes.Shape.Stroke%2A> プロパティを設定することにより、<xref:System.Windows.Media.Geometry> をレンダリングできます。  
  
<a name="commonproperties"></a>   
## ジオメトリを使用する一般的なプロパティ  
 前のセクションでは、ジオメトリ オブジェクトを他のオブジェクトと共にさまざまな目的で \(図形の描画、アニメーション、クリッピングなど\) 使用できることを説明しました。  <xref:System.Windows.Media.Geometry> オブジェクトを使用するプロパティを持ついくつかのクラスを次の表に示します。  
  
|種類|プロパティ|  
|--------|-----------|  
|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.PathGeometry%2A>|  
|<xref:System.Windows.Media.DrawingGroup>|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|  
|<xref:System.Windows.Media.GeometryDrawing>|<xref:System.Windows.Media.GeometryDrawing.Geometry%2A>|  
|<xref:System.Windows.Shapes.Path>|<xref:System.Windows.Shapes.Path.Data%2A>|  
|<xref:System.Windows.UIElement>|<xref:System.Windows.UIElement.Clip%2A>|  
  
<a name="wcpsdk_graphics_geometry_geometrytypes"></a>   
## 単純なジオメトリの種類  
 すべてのジオメトリの基本クラスは、抽象クラス <xref:System.Windows.Media.Geometry> です。  <xref:System.Windows.Media.Geometry> クラスの派生クラスは大きく 3 つのカテゴリに分類されます。単純なジオメトリ、パス ジオメトリ、および複合ジオメトリです。  
  
 単純なジオメトリ クラスには、<xref:System.Windows.Media.LineGeometry>、<xref:System.Windows.Media.RectangleGeometry>、および <xref:System.Windows.Media.EllipseGeometry> があり、線、四角形、円などの基本的な幾何学図形を作成するために使用されます。  
  
-   <xref:System.Windows.Media.LineGeometry> は、行の始点と終点を指定して定義します。  
  
-   <xref:System.Windows.Media.RectangleGeometry> は、その相対位置、および高さと幅を指定する <xref:System.Windows.Rect> 構造体を使用して定義されます。  <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> プロパティと <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> プロパティを設定して、丸みのある四角形を作成できます。  
  
-   <xref:System.Windows.Media.EllipseGeometry> は、中心点、x 半径、および y 半径で定義されます。  レンダリングおよびクリッピング用の単純なジオメトリの作成方法を次の例に示します。  
  
 <xref:System.Windows.Media.PathGeometry> を使用するか、ジオメトリ オブジェクトを結合する方法でも、これらと同じ図形や、さらに複雑な図形を作成することができます。ただし、これらのクラスを使用すると、このような基本的な幾何学図形を簡単に生成できます。  
  
 <xref:System.Windows.Media.LineGeometry> オブジェクトを作成してレンダリングする方法の例を次に示します。  前に述べたように、<xref:System.Windows.Media.Geometry> オブジェクトは自身を描画できないため、この例では <xref:System.Windows.Shapes.Path> 図形を使用して線をレンダリングします。  線には領域がないため、<xref:System.Windows.Shapes.Path> の <xref:System.Windows.Shapes.Shape.Fill%2A> プロパティを設定しても無効です。代わりに、<xref:System.Windows.Shapes.Shape.Stroke%2A> プロパティと <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> プロパティだけを指定します。  この例からの出力を次の図に示します。  
  
 ![LineGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-line.png "graphicsmm\_line")  
\(10,20\) から \(100,130\) まで描画された LineGeometry  
  
 [!code-xml[GeometryOverviewSamples_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmlinegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmlinegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmlinegeometryexample)]  
  
 次の例は、<xref:System.Windows.Media.EllipseGeometry> を作成してレンダリングする方法を示しています。  この例では、<xref:System.Windows.Media.EllipseGeometry> の <xref:System.Windows.Media.EllipseGeometry.Center%2A> を点 `50,50` に設定し、x 半径と y 半径を両方とも `50` に設定して、直径が 100 の円を作成します。  楕円の内部は、値 \(この例では <xref:System.Windows.Media.Brushes.Gold%2A>\) を Path 要素の Fill プロパティに割り当てることによって塗りつぶします。  この例からの出力を次の図に示します。  
  
 ![EllipseGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-ellipse.png "graphicsmm\_ellipse")  
\(50,50\) に描画された EllipseGeometry  
  
 [!code-xml[GeometryOverviewSamples_snip#GraphicsMMEllipseGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmellipsegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmellipsegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmellipsegeometryexample)]  
  
 <xref:System.Windows.Media.RectangleGeometry> オブジェクトを作成してレンダリングする方法の例を次に示します。  四角形の位置およびサイズは、<xref:System.Windows.Rect> 構造体によって定義されます。  位置は `50,50`、高さと幅は両方とも `25` で、正方形が作成されます。  この例からの出力を次の図に示します。  
  
 ![RectangleGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rectangle.png "graphicsmm\_rectangle")  
50,50 に描画された RectangleGeometry  
  
 [!code-xml[GeometryOverviewSamples_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmrectanglegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmrectanglegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmrectanglegeometryexample)]  
  
 <xref:System.Windows.Media.EllipseGeometry> をイメージのクリップ領域として使用する方法を次の例に示します。  <xref:System.Windows.Controls.Image> オブジェクトは、<xref:System.Windows.FrameworkElement.Width%2A> を 200、<xref:System.Windows.FrameworkElement.Height%2A> を 150 として定義されます。  <xref:System.Windows.Media.EllipseGeometry.RadiusX%2A> 値が 100、<xref:System.Windows.Media.EllipseGeometry.RadiusY%2A> 値が 75、および <xref:System.Windows.Media.EllipseGeometry.Center%2A> 値が 100,75 に指定された <xref:System.Windows.Media.EllipseGeometry> が、イメージの <xref:System.Windows.UIElement.Clip%2A> プロパティに設定されます。  イメージの楕円の領域内の部分だけが表示されます。  この例からの出力を次の図に示します。  
  
 ![クリッピングを使用する &#40;または使用しない&#41; イメージ](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-clipexample.png "graphicsmm\_clipexample")  
イメージ コントロールのクリップに使用される EllipseGeometry  
  
 [!code-xml[GeometryOverviewSamples_snip#GraphicsMMImageClipGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmimageclipgeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmimageclipgeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmimageclipgeometryexample)]  
  
<a name="wcpsdk_graphics_geometry_pathgeometry"></a>   
## パス ジオメトリ  
 <xref:System.Windows.Media.PathGeometry> クラスとその軽量等価クラスの <xref:System.Windows.Media.StreamGeometry> を使用すると、円弧、曲線、および線で構成される複数の複雑な図形を記述できます。  
  
 <xref:System.Windows.Media.PathGeometry> の中核は、<xref:System.Windows.Media.PathFigure> オブジェクトのコレクションです。各図形が <xref:System.Windows.Media.PathGeometry> の個々の図形を記述しているため、この名前が付いています。  各 <xref:System.Windows.Media.PathFigure> 自体は 1 つ以上の <xref:System.Windows.Media.PathSegment> オブジェクトで構成されており、これらの各オブジェクトは図形のセグメントを記述します。  
  
 次のように、多くの種類のセグメントがあります。  
  
|セグメントの種類|Description|例|  
|--------------|-----------------|-------|  
|<xref:System.Windows.Media.ArcSegment>|2 つの点の間の楕円の円弧を作成します。|[楕円の円弧を作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md).|  
|<xref:System.Windows.Media.BezierSegment>|2 つの点の間の 3 次ベジエ曲線を作成します。|[3 次ベジエ曲線を作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md).|  
|<xref:System.Windows.Media.LineSegment>|2 つの点の間の直線を作成します。|[PathGeometry で LineSegment を作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-linesegment-in-a-pathgeometry.md)|  
|<xref:System.Windows.Media.PolyBezierSegment>|一連の 3 次ベジエ曲線を作成します。|<xref:System.Windows.Media.PolyBezierSegment> の種類のページを参照してください。|  
|<xref:System.Windows.Media.PolyLineSegment>|一連の直線を作成します。|<xref:System.Windows.Media.PolyLineSegment> の種類のページを参照してください。|  
|<xref:System.Windows.Media.PolyQuadraticBezierSegment>|一連の 2 次ベジエ曲線を作成します。|<xref:System.Windows.Media.PolyQuadraticBezierSegment> のページを参照してください。|  
|<xref:System.Windows.Media.QuadraticBezierSegment>|2 次ベジエ曲線を作成します。|[2 次ベジエ曲線を作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md).|  
  
 <xref:System.Windows.Media.PathFigure> 内のセグメントは 1 つの幾何学図形に結合されて、各セグメントの終点が次のセグメントの始点になります。  <xref:System.Windows.Media.PathFigure> の <xref:System.Windows.Media.PathFigure.StartPoint%2A> プロパティは、最初のセグメントが描画される始点を指定します。  後続の各セグメントは、前のセグメントの終点から開始します。  たとえば、`10,50` から `10,150` までの縦線を定義するには、<xref:System.Windows.Media.PathFigure.StartPoint%2A> プロパティを `10,50` に設定し、<xref:System.Windows.Media.LineSegment.Point%2A> プロパティを `10,150` に設定した <xref:System.Windows.Media.LineSegment> を作成します。  
  
 <xref:System.Windows.Media.LineSegment> を使用して、単一の <xref:System.Windows.Media.PathFigure> で構成される単純な <xref:System.Windows.Media.PathGeometry> を作成し、<xref:System.Windows.Shapes.Path> 要素を使用してそれを表示する例を次に示します。  <xref:System.Windows.Media.PathFigure> オブジェクトの <xref:System.Windows.Media.PathFigure.StartPoint%2A> は `10,20` に設定され、<xref:System.Windows.Media.LineSegment> の終点は `100,130` で定義されます。  この例で作成した <xref:System.Windows.Media.PathGeometry> を次の図に示します。  
  
 ![LineGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-line.png "graphicsmm\_line")  
単一の LineSegment を含む PathGeometry  
  
 [!code-xml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryLineExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrylineexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrylineexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrylineexample)]  
  
 この例と、前の <xref:System.Windows.Media.LineGeometry> 例を比較してみてください。  <xref:System.Windows.Media.PathGeometry> に使用されている構文は、単純な <xref:System.Windows.Media.LineGeometry> に使用されている構文よりもかなり詳細です。この例では <xref:System.Windows.Media.LineGeometry> クラスを使用する方が合理的ですが、<xref:System.Windows.Media.PathGeometry> の詳細な構文を使用すると、非常に複雑な幾何学領域を作成できます。  
  
 より複雑なジオメトリを作成するには、<xref:System.Windows.Media.PathSegment> オブジェクトを組み合わせて使用します。  
  
 次の例では、<xref:System.Windows.Media.BezierSegment>、<xref:System.Windows.Media.LineSegment>、および <xref:System.Windows.Media.ArcSegment> を使用して図形を作成します。  この例では、最初に、始点 \(前のセグメントの終点\)、終点 \(<xref:System.Windows.Media.BezierSegment.Point3%2A>\)、および 2 つの制御点 \(<xref:System.Windows.Media.BezierSegment.Point1%2A> および <xref:System.Windows.Media.BezierSegment.Point2%2A>\) の 4 つの点を定義して 3 次ベジェ曲線を作成します。  3 次ベジエ曲線の 2 つの制御点は磁石のような働きをします。本来は直線になる部分を制御点の方へ引き寄せ、曲線を生成します。  1 つ目の制御点である <xref:System.Windows.Media.BezierSegment.Point1%2A> は、曲線の開始部分に影響します。2 つ目の制御点である <xref:System.Windows.Media.BezierSegment.Point2%2A> は、曲線の終了部分に影響します。  
  
 次に、<xref:System.Windows.Media.LineSegment> を追加します。これは、その前にある <xref:System.Windows.Media.BezierSegment> の終点からその <xref:System.Windows.Media.LineSegment> プロパティで指定された点までの間に描画されます。  
  
 次に、<xref:System.Windows.Media.ArcSegment> を追加します。これは、その前の <xref:System.Windows.Media.LineSegment> の終点からその <xref:System.Windows.Media.ArcSegment.Point%2A> プロパティで指定された点までの間に描画されます。  また、円弧の x 半径と y 半径 \(<xref:System.Windows.Media.ArcSegment.Size%2A>\)、回転角度 \(<xref:System.Windows.Media.ArcSegment.RotationAngle%2A>\)、結果の円弧の角度の大きさを示すフラグ \(<xref:System.Windows.Media.ArcSegment.IsLargeArc%2A>\)、および円弧が描画される方向を示す値 \(<xref:System.Windows.Media.ArcSegment.SweepDirection%2A>\) も指定します。  この例で作成した図形を次の図に示します。  
  
 ![PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-path2.png "graphicsmm\_path2")  
PathGeometry  
  
 [!code-xml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexexample)]  
  
 さらに複雑なジオメトリを作成するには、<xref:System.Windows.Media.PathGeometry> 内で複数の <xref:System.Windows.Media.PathFigure> オブジェクトを使用します。  
  
 2 つの <xref:System.Windows.Media.PathFigure> オブジェクトを使用して <xref:System.Windows.Media.PathGeometry> を作成する例を次に示します。各オブジェクトには、複数の <xref:System.Windows.Media.PathSegment> オブジェクトが含まれます。  上記の例の <xref:System.Windows.Media.PathFigure> と、<xref:System.Windows.Media.PolyLineSegment> および <xref:System.Windows.Media.QuadraticBezierSegment> による <xref:System.Windows.Media.PathFigure> が使用されています。  <xref:System.Windows.Media.PolyLineSegment> は点の配列を使用して定義され、<xref:System.Windows.Media.QuadraticBezierSegment> は制御点と終点を使用して定義されます。  この例で作成した図形を次の図に示します。  
  
 ![PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-path.png "graphicsmm\_path")  
複数の図形を使用する PathGeometry  
  
 [!code-xml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexMultiExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexmultiexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexmultiexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexmultiexample)]  
  
### StreamGeometry  
 <xref:System.Windows.Media.PathGeometry> クラスと同様に、<xref:System.Windows.Media.StreamGeometry> は、曲線、円弧、および線を含む複雑な幾何学図形を定義することができます。  <xref:System.Windows.Media.PathGeometry> とは異なり、<xref:System.Windows.Media.StreamGeometry> のコンテンツは、データ バインディング、アニメーション、変更をサポートしません。  複雑なジオメトリを作成する必要があるが、データ バインディング、アニメーション、または変更をサポートするためのオーバーヘッドが望ましくない場合は、<xref:System.Windows.Media.StreamGeometry> を使用します。  <xref:System.Windows.Media.StreamGeometry> クラスは効率的であるため、装飾の表現に適しています。  
  
 例については、「[StreamGeometry を使用して図形を作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-using-a-streamgeometry.md)」を参照してください。  
  
### パス マークアップ構文  
 <xref:System.Windows.Media.PathGeometry> と <xref:System.Windows.Media.StreamGeometry> は、特殊な一連の移動および描画コマンドを使用して [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 属性構文をサポートします。  詳細については、「[パス マークアップ構文](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)」を参照してください。  
  
<a name="wcpsdk_graphics_geometry_introduction2"></a>   
## 複合ジオメトリ  
 複合ジオメトリ オブジェクトは、<xref:System.Windows.Media.GeometryGroup> または <xref:System.Windows.Media.CombinedGeometry> を使用するか、<xref:System.Windows.Media.Geometry> の静的メソッドである <xref:System.Windows.Media.Geometry.Combine%2A> を呼び出すことによって作成できます。  
  
-   <xref:System.Windows.Media.CombinedGeometry> オブジェクトおよび <xref:System.Windows.Media.Geometry.Combine%2A> メソッドはブール演算を実行して、2 つのジオメトリで定義されている領域を結合します。  領域を持たない <xref:System.Windows.Media.Geometry> オブジェクトは破棄されます。  結合できるのは、2 つの <xref:System.Windows.Media.Geometry> オブジェクトだけです。ただし、この 2 つのジオメトリに複合ジオメトリを使用することもできます。  
  
-   <xref:System.Windows.Media.GeometryGroup> クラスは、そのクラスに含まれる <xref:System.Windows.Media.Geometry> オブジェクトについて、その領域を結合することなく混合を作成します。  <xref:System.Windows.Media.Geometry> オブジェクトはいくつでも <xref:System.Windows.Media.GeometryGroup> に追加できます。  例については、「[複合図形を作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)」を参照してください。  
  
 結合操作を実行しないため、<xref:System.Windows.Media.GeometryGroup> オブジェクトを使用した方が、<xref:System.Windows.Media.CombinedGeometry> オブジェクトまたは <xref:System.Windows.Media.Geometry.Combine%2A> メソッドを使用するよりもパフォーマンスが向上します。  
  
<a name="combindgeometriessection"></a>   
## 結合したジオメトリ  
 前のセクションでは、<xref:System.Windows.Media.CombinedGeometry> オブジェクトと <xref:System.Windows.Media.Geometry.Combine%2A> メソッドが、それらに含まれるジオメトリで定義された領域を結合することを説明しました。  <xref:System.Windows.Media.GeometryCombineMode> 列挙体は、ジオメトリを結合する方法を指定します。  <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> プロパティに指定できる値は、<xref:System.Windows.Media.GeometryCombineMode>、<xref:System.Windows.Media.GeometryCombineMode>、<xref:System.Windows.Media.GeometryCombineMode>、および <xref:System.Windows.Media.GeometryCombineMode> です。  
  
 次の例では、<xref:System.Windows.Media.CombinedGeometry> が和集合の結合モードで定義されています。  <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> および <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> は同じ半径の円として定義されていますが、中心は 50 ずれています。  
  
 [!code-xml[GeometrySample#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 ![結合組み合わせモードの結果](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-union.png "mil\_task\_combined\_geometry\_union")  
  
 次の例では、<xref:System.Windows.Media.CombinedGeometry> が <xref:System.Windows.Media.GeometryCombineMode> の結合モードで定義されています。  <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> および <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> は同じ半径の円として定義されていますが、中心は 50 ずれています。  
  
 [!code-xml[GeometrySample#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 ![Xor 組み合わせモードの結果](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-xor.png "mil\_task\_combined\_geometry\_xor")  
  
 その他の例については、「[複合図形を作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)」と「[結合したジオメトリを作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-combined-geometry.md)」を参照してください。  
  
<a name="freezable_features"></a>   
## Freezable の機能  
 <xref:System.Windows.Media.Geometry> クラスは <xref:System.Windows.Freezable> クラスを継承しているため、いくつかの特殊な機能を備えています。つまり、<xref:System.Windows.Media.Geometry> オブジェクトを[XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)として宣言したり、複数のオブジェクト間で共有したり、読み取り専用にしてパフォーマンスを高めたり、複製したり、スレッド セーフにしたりできます。  <xref:System.Windows.Freezable> オブジェクトのさまざまな機能の詳細については、「[Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)」を参照してください。  
  
<a name="othergeometryfeatures"></a>   
## その他のジオメトリ機能  
 <xref:System.Windows.Media.Geometry> クラスは、次のような便利なユーティリティ メソッドも提供します。  
  
-   <xref:System.Windows.Media.Geometry.GetArea%2A> \- <xref:System.Windows.Media.Geometry> の領域を取得します。  
  
-   <xref:System.Windows.Media.Geometry.FillContains%2A> \- ジオメトリに別の <xref:System.Windows.Media.Geometry> が含まれているかどうかを判断します。  
  
-   <xref:System.Windows.Media.Geometry.StrokeContains%2A> \- 指定した点が <xref:System.Windows.Media.Geometry> のストロークに含まれているかどうかを判断します。  
  
 メソッドの完全な一覧については、<xref:System.Windows.Media.Geometry> クラスを参照してください。  
  
## 参照  
 <xref:System.Windows.Media.Geometry>   
 <xref:System.Windows.Media.PathGeometry>   
 <xref:System.Windows.Shapes.Path>   
 <xref:System.Windows.Media.GeometryDrawing>   
 [2D グラフィックスとイメージング](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)   
 [パス マークアップ構文](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)   
 [方法のトピック](../../../../docs/framework/wpf/graphics-multimedia/geometries-how-to-topics.md)   
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [WPF での図形と基本描画の概要](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)   
 [Drawing オブジェクトの概要](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)