---
title: 'パフォーマンスの最適化 : 2D グラフィックスとイメージング'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], performance
- drawing [WPF], optimizing performance
- imaging [WPF], optimizing performance
- shapes [WPF], optimizing performance
- 2-D graphics [WPF]
- images [WPF], optimizing performance
ms.assetid: e335601e-28c8-4d64-ba27-778fffd55f72
ms.openlocfilehash: 4e6b72dae863e89d70ec70c2cb99a5874581e9ea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549102"
---
# <a name="optimizing-performance-2d-graphics-and-imaging"></a>パフォーマンスの最適化 : 2D グラフィックスとイメージング
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、アプリケーションの要件に合わせて最適化できる広範な 2D グラフィックス機能とイメージング機能が用意されています。 このトピックでは、この領域でのパフォーマンスの最適化に関する情報を提供します。  
  
  
<a name="Drawing_and_Shapes"></a>   
## <a name="drawing-and-shapes"></a>描画と図形  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 両方を提供<xref:System.Windows.Media.Drawing>と<xref:System.Windows.Shapes.Shape>グラフィックの描画コンテンツを表すオブジェクト。 ただし、<xref:System.Windows.Media.Drawing>オブジェクトよりシンプルなコンストラクト<xref:System.Windows.Shapes.Shape>オブジェクトし、パフォーマンス特性を指定します。  
  
 A<xref:System.Windows.Shapes.Shape>グラフィカル図形を画面に描画することができます。 派生しているため、<xref:System.Windows.FrameworkElement>クラス、<xref:System.Windows.Shapes.Shape>パネルとほとんどのコントロール内のオブジェクトで使用できます。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、グラフィックス サービスやレンダリング サービスへのアクセスのレイヤーがいくつか用意されています。 最上位のレイヤーで<xref:System.Windows.Shapes.Shape>オブジェクトが簡単に使用し、レイアウトやイベント処理など、多くの便利な機能を提供します。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、すぐに使用できるさまざまな図形オブジェクトが用意されています。 すべての図形オブジェクトの継承、<xref:System.Windows.Shapes.Shape>クラスです。 使用可能な図形オブジェクトには、 <xref:System.Windows.Shapes.Ellipse>、 <xref:System.Windows.Shapes.Line>、 <xref:System.Windows.Shapes.Path>、 <xref:System.Windows.Shapes.Polygon>、 <xref:System.Windows.Shapes.Polyline>、および<xref:System.Windows.Shapes.Rectangle>です。  
  
 <xref:System.Windows.Media.Drawing> オブジェクト、その一方からは派生しません、<xref:System.Windows.FrameworkElement>クラスおよび表示の図形、画像、およびテキストの軽量の実装を提供します。  
  
 次の 4 種類がある<xref:System.Windows.Media.Drawing>オブジェクト。  
  
-   <xref:System.Windows.Media.GeometryDrawing> 図形を描画します。  
  
-   <xref:System.Windows.Media.ImageDrawing> イメージを描画します。  
  
-   <xref:System.Windows.Media.GlyphRunDrawing> テキストを描画します。  
  
-   <xref:System.Windows.Media.DrawingGroup> その他の図を描画します。 他の描画を 1 つの複合描画に結合するには、描画グループを使用します。  
  
 <xref:System.Windows.Media.GeometryDrawing> Geometry コンテンツを表示するためにオブジェクトを使用します。 <xref:System.Windows.Media.Geometry>クラスと具象クラスなど、そこから派生する<xref:System.Windows.Media.CombinedGeometry>、 <xref:System.Windows.Media.EllipseGeometry>、および<xref:System.Windows.Media.PathGeometry>2D グラフィックのレンダリングする手段として、ヒット テストとクリッピングのサポートを提供します。 ジオメトリ オブジェクトを使用すると、たとえば、コントロールの領域を定義したり、イメージに適用するクリップ領域を定義したりすることができます。 ジオメトリ オブジェクトは、四角形や円などの単純な領域にすることも、2 つ以上のジオメトリ オブジェクトから作成された複合的な領域にすることもできます。 複雑な幾何学的領域を結合して作成できる<xref:System.Windows.Media.PathSegment>-など、オブジェクトの派生<xref:System.Windows.Media.ArcSegment>、 <xref:System.Windows.Media.BezierSegment>、および<xref:System.Windows.Media.QuadraticBezierSegment>です。  
  
 画面で、<xref:System.Windows.Media.Geometry>クラスおよび<xref:System.Windows.Shapes.Shape>クラスは非常に似ています。 2 D グラフィックスの表示の使用はどちらもありどちらも同様の具象クラスをたとえば、これらのファイルから派生する<xref:System.Windows.Media.EllipseGeometry>と<xref:System.Windows.Shapes.Ellipse>です。 ただし、この 2 つのクラスのセットの間には重要な違いがいくつかあります。 1 つの<xref:System.Windows.Media.Geometry>クラスでは、機能の一部がない、<xref:System.Windows.Shapes.Shape>自身で描画する機能などのクラスです。 ジオメトリ オブジェクトを描画するには、DrawingContext、Drawing、Path (Path が Shape であることは注目に値します) などの別のクラスを使用して描画操作を実行する必要があります。 塗りつぶし、ストローク、ストロークの太さなどの描画プロパティは、ジオメトリ オブジェクトを描画するクラスにあります。一方、図形オブジェクトにはこれらのプロパティが含まれています。 この違いは、ジオメトリ オブジェクトが円などの領域を定義するのに対し、図形オブジェクトは領域を定義するとともに、その領域の塗りつぶしやアウトラインも定義し、レイアウト システムに参加する、と考えることができます。  
  
 <xref:System.Windows.Shapes.Shape>オブジェクトから取得、<xref:System.Windows.FrameworkElement>それらを使用して、クラスは、アプリケーションで非常に多くのメモリ消費量を追加できます。 本当に必要としない場合、 <xref:System.Windows.FrameworkElement> 、グラフィカルなコンテンツのための機能は、軽量の使用を検討<xref:System.Windows.Media.Drawing>オブジェクト。  
  
 詳細については<xref:System.Windows.Media.Drawing>、オブジェクトを参照してください[描画オブジェクトの概要](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)です。  
  
<a name="StreamGeometry_Objects"></a>   
## <a name="streamgeometry-objects"></a>StreamGeometry オブジェクト  
 <xref:System.Windows.Media.StreamGeometry>オブジェクトは、軽量な代替<xref:System.Windows.Media.PathGeometry>幾何学図形を作成するためです。 使用して、<xref:System.Windows.Media.StreamGeometry>複合ジオメトリを記述する必要がある場合。 <xref:System.Windows.Media.StreamGeometry> 多くの処理用に最適化された<xref:System.Windows.Media.PathGeometry>オブジェクトし、多くの個々 の使用と比べてパフォーマンスが向上<xref:System.Windows.Media.PathGeometry>オブジェクト。  
  
 次の例では、属性の構文を使用して、作成、三角形<xref:System.Windows.Media.StreamGeometry>で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]です。  
  
 [!code-xaml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 詳細については<xref:System.Windows.Media.StreamGeometry>、オブジェクトを参照してください[の作成を使用して、図形、StreamGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-using-a-streamgeometry.md)です。  
  
<a name="DrawingVisual_Objects"></a>   
## <a name="drawingvisual-objects"></a>DrawingVisual オブジェクト  
 <xref:System.Windows.Media.DrawingVisual>オブジェクトは、軽量な図形、画像、またはテキストを表示するために使用されるクラスを描画します。 このクラスが軽量と見なされる理由は、レイアウトやイベントの処理を行わないことで、パフォーマンスが向上するからです。 そのため、背景やクリップ アートの描画に適しています。 詳しくは、「[DrawingVisual オブジェクトの使用](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)」を参照してください。  
  
<a name="Images"></a>   
## <a name="images"></a>イメージ  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のイメージング機能は、以前のバージョンの [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] のイメージング機能から大幅に強化されています。 イメージング機能 (ビットマップの表示や一般的なコントロール上でのイメージの使用など) は、以前は主に Microsoft Windows Graphics Device Interface (GDI) または Microsoft Windows GDI+ のアプリケーション プログラミング インターフェイス (API) によって処理されていました。 これらの API では、基本的なイメージング機能は提供されていましたが、コーデック拡張機能のサポートや高品質なイメージのサポートなどの機能が不足していました。 WPF Imaging API は、GDI および GDI+ の欠点を克服し、アプリケーション内でイメージを表示および使用するための新しい API のセットを提供するために再設計されています。  
  
 イメージを使用する際には、パフォーマンスを向上させるために以下の推奨事項をご検討ください。  
  
-   アプリケーションでサムネイル イメージを表示する必要がある場合は、縮小版のイメージを作成することをご検討ください。 既定では、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は読み込んだイメージを本来のサイズにデコードします。 サムネイル バージョンのイメージのみが必要な場合は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] がイメージを本来のサイズにデコードしてからサムネイル サイズに縮小するという無駄が生じます。 この不要なオーバーヘッドを回避するには、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] に対してイメージをサムネイル サイズにデコードするように要求するか、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] にサムネイル サイズのイメージを読み込むように要求します。  
  
-   イメージは常に、既定のサイズではなく必要なサイズにデコードするようにしてください。 前述のように、既定の実際のサイズではなく必要なサイズにイメージをデコードするように [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] に要求します。 これにより、アプリケーションの作業セットを縮小できるだけでなく、実行速度も向上します。  
  
-   可能であれば、複数のイメージを 1 つに結合します (複数のイメージから成るフィルム ストリップなど)。  
  
-   詳しくは、「 [イメージングの概要](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)」をご覧ください。  
  
### <a name="bitmapscalingmode"></a>BitmapScalingMode  
 ビットマップのスケーリングをアニメーション化する場合、既定の高品質イメージの再サンプリング アルゴリズムは、フレーム レートを低下させるほどシステム リソースを消費する場合があり、実際にはアニメーションの動きが滑らかでなくなることがあります。 設定して、<xref:System.Windows.Media.RenderOptions.BitmapScalingMode%2A>のプロパティ、<xref:System.Windows.Media.RenderOptions>オブジェクトを<xref:System.Windows.Media.BitmapScalingMode.LowQuality>ビットマップを拡張するときに滑らかなアニメーションを作成することができます。 <xref:System.Windows.Media.BitmapScalingMode.LowQuality> モードの通知、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]品質用に最適化されたアルゴリズムからに切り替える速度が最適化されたアルゴリズムのイメージを処理するときにレンダリング エンジンです。  
  
 次の例は、設定する方法を示します、<xref:System.Windows.Media.BitmapScalingMode>イメージ オブジェクト。  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet2)]
 [!code-vb[RenderOptions#RenderOptionsSnippet2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet2)]  
  
### <a name="cachinghint"></a>CachingHint  
 既定では、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]の表示内容をキャッシュしません<xref:System.Windows.Media.TileBrush>などのオブジェクト<xref:System.Windows.Media.DrawingBrush>と<xref:System.Windows.Media.VisualBrush>です。 静的なシナリオで、内容もの使用、<xref:System.Windows.Media.TileBrush>でシーンの変更は、これは、ビデオ メモリを節約するための意味します。 言えませんはるか理ときに、<xref:System.Windows.Media.TileBrush>静的なコンテンツで静的でない方法でを使用して — 静的な場合など、<xref:System.Windows.Media.DrawingBrush>または<xref:System.Windows.Media.VisualBrush>回転の 3D オブジェクトの表面にマップされます。 既定の動作[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]のコンテンツ全体が再表示するためには、<xref:System.Windows.Media.DrawingBrush>または<xref:System.Windows.Media.VisualBrush>フレームごとにいなくても、コンテンツが変化しません。  
  
 設定して、<xref:System.Windows.Media.RenderOptions.CachingHint%2A>のプロパティ、<xref:System.Windows.Media.RenderOptions>オブジェクトを<xref:System.Windows.Media.CachingHint.Cache>ブラシを並べて表示されたオブジェクトのキャッシュされたバージョンを使用してパフォーマンスを向上させることができます。  
  
 <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMinimum%2A>と<xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A>プロパティの値は、タイミングを決定する相対的なサイズ値、<xref:System.Windows.Media.TileBrush>スケールの変更のためには、オブジェクトを再生成する必要があります。 設定などにより、 <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A> 2.0 では、キャッシュするプロパティ、<xref:System.Windows.Media.TileBrush>だけのサイズは、現在のキャッシュのサイズの 2 倍を超えています。 再生成する必要があります。  
  
 次の例のキャッシュのヒント オプションを使用する方法を示しています、<xref:System.Windows.Media.DrawingBrush>です。  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet3)]
 [!code-vb[RenderOptions#RenderOptionsSnippet3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet3)]  
  
## <a name="see-also"></a>関連項目  
 [WPF アプリケーションのパフォーマンスの最適化](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [アプリケーション パフォーマンスの計画](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
 [ハードウェアの活用](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
 [レイアウトとデザイン](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [オブジェクトの動作](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
 [アプリケーション リソース](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [[テキスト]](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [データ バインディング](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [パフォーマンスに関するその他の推奨事項](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)  
 [アニメーションのヒントとテクニック](../../../../docs/framework/wpf/graphics-multimedia/animation-tips-and-tricks.md)
