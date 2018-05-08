---
title: パス アニメーションの概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], paths
- path animations [WPF]
ms.assetid: 979c732c-df74-47a6-be96-8e07b3707d53
ms.openlocfilehash: 466e22a5b40ddb4f3674422ac7620832b44be51d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="path-animations-overview"></a>パス アニメーションの概要
<a name="introduction"></a>このトピックでは、ジオメトリック パスを使用して出力値を生成できるパス アニメーションの概要を説明します。 パス アニメーションは、複雑なパスに沿ってオブジェクトを移動および回転させるときに便利です。  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックの内容を理解しておく必要があります慣れて[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アニメーション機能します。 アニメーションの機能の概要については、次を参照してください。、[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)です。  
  
 使用するため、<xref:System.Windows.Media.PathGeometry>パス アニメーションを定義するオブジェクトもよく理解してくださいで<xref:System.Windows.Media.PathGeometry>とさまざまな種類の<xref:System.Windows.Media.PathSegment>オブジェクト。 詳細については、次を参照してください。、[ジオメトリの概要](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)です。  
  
<a name="what_is_a_path_animation"></a>   
## <a name="what-is-a-path-animation"></a>パス アニメーションとは  
 パスのアニメーションの種類は、<xref:System.Windows.Media.Animation.AnimationTimeline>を使用して、<xref:System.Windows.Media.PathGeometry>の入力として。 To、From を設定する代わりに、またはプロパティで (な From/に/By の場合とアニメーション) を使用してキー フレームのキー フレーム アニメーションを使用すると)、または、ジオメトリのパスを定義して、それを使用、`PathGeometry`パス アニメーションのプロパティです。 パス アニメーションが進むとき、パスから x、y、および角度情報を読み取り、その情報を使用して、出力を生成します。  
  
 パス アニメーションは、複雑なパスに沿ってオブジェクトをアニメーション化するのに便利です。 パスに沿ってオブジェクトを使用して移動する方法の 1 つ、<xref:System.Windows.Media.MatrixTransform>と<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>複合パスに沿ってオブジェクトを変換します。 次の例では、この方法を示しますを使用して、<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>アニメーション化するオブジェクト、<xref:System.Windows.Media.MatrixTransform.Matrix%2A>のプロパティ、<xref:System.Windows.Media.MatrixTransform>です。 <xref:System.Windows.Media.MatrixTransform>ボタンに適用され、曲線のパスに沿って移動する場合は、します。 <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A>プロパティに設定されている`true`、四角形がパスの接線に沿って回転します。  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathdoesrotatewithtangentexample.xaml#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathDoesRotateWithTangentExample.cs#matrixanimationusingpathdoesrotatewithtangentwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathDoesRotateWithTangentExample.vb#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 使用されているパスの構文の詳細については、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]例を参照してください、[パス マークアップ構文](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)の概要です。 サンプル全体については、次を参照してください。[パス アニメーション サンプル](http://go.microsoft.com/fwlink/?LinkID=160028)です。  
  
 使用してプロパティにパス アニメーションを適用することができます、<xref:System.Windows.Media.Animation.Storyboard>で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]とコード、またはを使用して、<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>コード内のメソッドです。 作成するパスのアニメーションを使用することもできます、<xref:System.Windows.Media.Animation.AnimationClock>し、1 つまたは複数のプロパティに適用します。 アニメーションを適用するためのさまざまな方法の詳細については、次を参照してください。[プロパティ アニメーションの技術概要](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)です。  
  
<a name="animation_types"></a>   
## <a name="path-animation-types"></a>パス アニメーションの種類  
 アニメーションはプロパティ値を生成するため、プロパティの型ごとに異なるアニメーションの種類があります。 受け取るプロパティをアニメーション化する、 <xref:System.Double> (など、<xref:System.Windows.Media.TranslateTransform.X%2A>のプロパティを<xref:System.Windows.Media.TranslateTransform>)、生成されるアニメーションを使用する<xref:System.Double>値。 受け取るプロパティをアニメーション化する、 <xref:System.Windows.Point>、生成されるアニメーションを使用する<xref:System.Windows.Point>値、およびなどです。  
  
 パス アニメーション クラスが属している、<xref:System.Windows.Media.Animation>名前空間および次の命名規則を使用します。  
  
 *\<Type>* `AnimationUsingPath`  
  
 ここで、*\<Type>* は、クラスがアニメーション化する値の型です。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、次のパス アニメーション クラスが用意されています。  
  
|プロパティの型|対応するパス アニメーション クラス|例|  
|-------------------|----------------------------------------|-------------|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|[パスに沿ってオブジェクトをアニメーション化する (ダブル アニメーション)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-double-animation.md)|  
|<xref:System.Windows.Media.Matrix>|<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>|[パスに沿ってオブジェクトをアニメーション化する (行列アニメーション)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md)|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimationUsingPath>|[パスに沿ってオブジェクトをアニメーション化する (ポイント アニメーション)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-point-animation.md)|  
  
 A<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>生成<xref:System.Windows.Media.Matrix>値からその<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.PathGeometry%2A>です。 使用すると、 <xref:System.Windows.Media.MatrixTransform>、<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>をパスに沿ってオブジェクトを移動できます。 設定した場合、<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A>のプロパティ、<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>に`true`オブジェクトのパスの曲線に沿って回転させます。  
  
 A<xref:System.Windows.Media.Animation.PointAnimationUsingPath>生成<xref:System.Windows.Point>値からの x 座標と y 座標の<xref:System.Windows.Media.Animation.PointAnimationUsingPath.PathGeometry%2A>です。 使用して、<xref:System.Windows.Media.Animation.PointAnimationUsingPath>を受け取るプロパティをアニメーション化する<xref:System.Windows.Point>値をパスに沿ってオブジェクトを移動することができます。 A<xref:System.Windows.Media.Animation.PointAnimationUsingPath>オブジェクトを回転させることはできません。  
  
 A<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>生成<xref:System.Double>値からその<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.PathGeometry%2A>です。 設定して、<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.Source%2A>プロパティを指定できるかどうか、 <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> x 座標、座標の y 座標またはパスの角度の出力として使用します。 使用することができます、<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>オブジェクトの回転を x 軸または y 軸に沿って移動します。  
  
<a name="pathanimationinput"></a>   
## <a name="path-animation-input"></a>パス アニメーションの入力  
 各パス アニメーション クラスでは、<xref:System.Windows.Media.PathGeometry>を入力を指定するプロパティです。 パスのアニメーションで使用される、<xref:System.Windows.Media.PathGeometry>その出力値を生成します。 <xref:System.Windows.Media.PathGeometry>クラスでは、円弧、曲線、および行で構成される複数の複雑な図形を記述することができます。  
  
 中心に、<xref:System.Windows.Media.PathGeometry>のコレクションは、<xref:System.Windows.Media.PathFigure>オブジェクトです。 これらのオブジェクトは、という名前は、各図形には、個別の図形がについて説明します、<xref:System.Windows.Media.PathGeometry>です。 各<xref:System.Windows.Media.PathFigure>は、1 つ以上の<xref:System.Windows.Media.PathSegment>オブジェクト、図のセグメントそれぞれについて説明します。  
  
 多くの種類のセグメントがあります。  
  
|セグメントの種類|説明|  
|------------------|-----------------|  
|<xref:System.Windows.Media.ArcSegment>|2 つの点を結ぶ楕円の円弧を作成します。|  
|<xref:System.Windows.Media.BezierSegment>|2 つの点を結ぶ 3 次ベジエ曲線を作成します。|  
|<xref:System.Windows.Media.LineSegment>|2 つの点を結ぶ直性を作成します。|  
|<xref:System.Windows.Media.PolyBezierSegment>|一続きの 3 次ベジエ曲線を作成します。|  
|<xref:System.Windows.Media.PolyLineSegment>|一続きの直線を作成します。|  
|<xref:System.Windows.Media.PolyQuadraticBezierSegment>|一続きの 2 次ベジエ曲線を作成します。|  
|<xref:System.Windows.Media.QuadraticBezierSegment>|2 次ベジエ曲線を作成します。|  
  
 セグメントに、<xref:System.Windows.Media.PathFigure>に 1 つの幾何学図形を次のセグメントの開始点として、線分の終点を使用して結合されます。 <xref:System.Windows.Media.PathFigure.StartPoint%2A>のプロパティ、<xref:System.Windows.Media.PathFigure>最初のセグメントを描画する元となるポイントを指定します。 後続の各セグメントは、前のセグメントの終点から始まります。 などの垂直線がから`10,50`に`10,150`設定で定義されていることができます、<xref:System.Windows.Media.PathFigure.StartPoint%2A>プロパティを`10,50`を作成して、<xref:System.Windows.Media.LineSegment>で、<xref:System.Windows.Media.LineSegment.Point%2A>プロパティの設定`10,150`です。  
  
 詳細については<xref:System.Windows.Media.PathGeometry>、オブジェクトを参照してください、[ジオメトリの概要](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)です。  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、特殊な省略構文を使用して設定する、<xref:System.Windows.Media.PathGeometry.Figures%2A>のプロパティ、<xref:System.Windows.Media.PathGeometry>です。 詳細については、次を参照してください。[パス マークアップ構文](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)の概要です。  
  
 使用されているパスの構文の詳細については、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]例を参照してください、[パス マークアップ構文](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)の概要です。  
  
## <a name="see-also"></a>関連項目  
 [パス アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160028)  
 [パス マークアップ構文](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)  
 [パス アニメーションに関する「方法」トピック](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [プロパティ アニメーションの手法の概要](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)
