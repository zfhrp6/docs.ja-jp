---
title: "パス アニメーションの概要 | Microsoft Docs"
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
  - "パスのアニメーション"
  - "パス アニメーション"
ms.assetid: 979c732c-df74-47a6-be96-8e07b3707d53
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# パス アニメーションの概要
<a name="introduction"></a>このトピックでは、出力値を生成するジオメトリック パスを使用するため、パスのアニメーションを紹介します。 パス アニメーションは、移動および複雑なパスに沿ってオブジェクトを回転するのに便利です。  
  
<a name="autoTopLevelSectionsOUTLINE0"></a>   
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックを理解するのには理解しておく[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アニメーション機能します。 アニメーション機能の概要については、次を参照してください。、[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)します。  
  
 使用するため、 <xref:System.Windows.Media.PathGeometry>パスのアニメーションを定義するオブジェクトする必要がありますも理解しておく<xref:System.Windows.Media.PathGeometry>さまざまなタイプの<xref:System.Windows.Media.PathSegment>オブジェクトです。 詳細については、次を参照してください。、[ジオメトリの概要](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)します。  
  
<a name="what_is_a_path_animation"></a>   
## <a name="what-is-a-path-animation"></a>パス アニメーションとは何ですか。  
 パス アニメーションの種類は、 <xref:System.Windows.Media.Animation.AnimationTimeline>を使用する、 <xref:System.Windows.Media.PathGeometry>として入力します。 プロパティ、To、From を設定する代わりに (な From/に/By の場合とアニメーション) または (キー フレーム アニメーションのと)、キー フレームを使用して、ジオメトリック パスを定義し、設定を使用する、`PathGeometry`パス アニメーションのプロパティです。 パス アニメーション進行状況に応じて、パスから x、y、および角度情報を読み取り、その情報を使用して、その出力を生成することです。  
  
 パス アニメーションは、複雑なパスに沿ってオブジェクトをアニメーション化するのに便利です。 使用するパスに沿ってオブジェクトを移動する方法の&1; つ、 <xref:System.Windows.Media.MatrixTransform>と<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>複雑なパスに沿ってオブジェクトを変換します。 次の例では、この手法をでを使用して、 <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>アニメーション化するオブジェクト、<xref:System.Windows.Media.MatrixTransform.Matrix%2A>のプロパティ、 <xref:System.Windows.Media.MatrixTransform>します。 <xref:System.Windows.Media.MatrixTransform>ボタンに適用され、曲線のパスに沿って移動する場合は、です。 <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A>にプロパティが設定されている`true`パスの接線に沿った四角形が回転します。  
  
 [!code-xml[PathAnimationGallery_snippet#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathdoesrotatewithtangentexample.xaml#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathDoesRotateWithTangentExample.cs#matrixanimationusingpathdoesrotatewithtangentwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathDoesRotateWithTangentExample.vb#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 使用されているパスの構文の詳細については、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]例を参照してください、[パス マークアップ構文](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)の概要です。 完全なサンプルを参照してください。[パス アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160028)します。  
  
 パス アニメーションをプロパティに適用するにを使用して、<xref:System.Windows.Media.Animation.Storyboard>で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]とコード、またはを使用して、 <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>コード内のメソッドです。 パス アニメーションを使用して作成した、 <xref:System.Windows.Media.Animation.AnimationClock>し、1 つまたは複数のプロパティに適用します。 アニメーションを適用するためのさまざまな方法の詳細については、次を参照してください。[プロパティ アニメーションの手法の概要](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)します。  
  
<a name="animation_types"></a>   
## <a name="path-animation-types"></a>パス アニメーションの種類  
 アニメーションは、プロパティの値を生成するためには、プロパティの種類別のアニメーションの種類があります。 受け取るプロパティをアニメーション化する、<xref:System.Double>(など、 [X](assetId:///P:System.Windows.Media.TranslateTransform.X?qualifyHint=False&autoUpgrade=True)のプロパティを[TranslateTransform](assetId:///T:System.Windows.Media.TranslateTransform?qualifyHint=False&autoUpgrade=True))、生成されるアニメーションを使用して<xref:System.Double>値。 受け取るプロパティをアニメーション化する、<xref:System.Windows.Point>、生成されるアニメーションを使用して<xref:System.Windows.Point>値、およびなどです。  
  
 パス アニメーション クラスは、 <xref:System.Windows.Media.Animation>名前空間および名前付け規則を使用します。  
  
 *<>\>*`AnimationUsingPath`  
  
 ここで* <> \> *クラスをアニメーション化する値の型です。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]次のパスのアニメーション クラスを提供します。  
  
|プロパティの型|対応するパスのアニメーション クラス|例|  
|-------------------|----------------------------------------|-------------|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|[(ダブル アニメーション) のパスに沿ってオブジェクトをアニメーション化します。](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-double-animation.md)|  
|<xref:System.Windows.Media.Matrix>|<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>|[(行列アニメーション) のパスに沿ってオブジェクトをアニメーション化します。](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md)|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimationUsingPath>|[(ポイント アニメーション) のパスに沿ってオブジェクトをアニメーション化します。](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-point-animation.md)|  
  
 A <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>生成<xref:System.Windows.Media.Matrix>値からその<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.PathGeometry%2A>します。 使用すると、 <xref:System.Windows.Media.MatrixTransform>、 <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>パスに沿ってオブジェクトを移動することができます。 設定した場合、 <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A>のプロパティ、 <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>に`true`パスの曲線に沿ってオブジェクトが回転されます。  
  
 A <xref:System.Windows.Media.Animation.PointAnimationUsingPath>生成<xref:System.Windows.Point>値から、x 座標と y 座標の<xref:System.Windows.Media.Animation.PointAnimationUsingPath.PathGeometry%2A>します。 使用して、 <xref:System.Windows.Media.Animation.PointAnimationUsingPath>を受け取るプロパティをアニメーション化する<xref:System.Windows.Point>値、パスに沿ってオブジェクトを移動することができます。 A <xref:System.Windows.Media.Animation.PointAnimationUsingPath>オブジェクトを回転させることはできません。  
  
 A <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>生成<xref:System.Double>値からその<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.PathGeometry%2A>します。 設定して、<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.Source%2A>プロパティを指定できるかどうか、 <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>は x 座標、y 座標、またはパスの角度の出力として使用します。 使用することができます、 <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>をオブジェクトを回転させるか、x 軸または y 軸に沿って移動します。  
  
<a name="pathanimationinput"></a>   
## <a name="path-animation-input"></a>パス アニメーションの入力  
 各パスのアニメーション クラスでは、 <xref:System.Windows.Media.PathGeometry>を入力を指定するプロパティです。 パス アニメーションを使用して、 <xref:System.Windows.Media.PathGeometry>の出力値を生成します。 <xref:System.Windows.Media.PathGeometry>クラスでは、円弧、曲線、および行で構成される複数の複雑な図形を記述することができます。  
  
 中心に、 <xref:System.Windows.Media.PathGeometry>のコレクションは、 <xref:System.Windows.Media.PathFigure>オブジェクト。 これらのオブジェクトはという名前は、各図形内の個別の図形の説明、 <xref:System.Windows.Media.PathGeometry>します。 各<xref:System.Windows.Media.PathFigure>は、1 つ以上の<xref:System.Windows.Media.PathSegment>オブジェクトの図のセグメントをそれぞれ記述します。  
  
 さまざまな種類のセグメントがあります。  
  
|セグメントの種類|説明|  
|------------------|-----------------|  
|<xref:System.Windows.Media.ArcSegment>|2 つの地点の楕円の円弧を作成します。|  
|<xref:System.Windows.Media.BezierSegment>|2 つの地点の&3; 次ベジエ曲線を作成します。|  
|<xref:System.Windows.Media.LineSegment>|2 つのポイントの間に行を作成します。|  
|<xref:System.Windows.Media.PolyBezierSegment>|一連の&3; 次ベジエ曲線を作成します。|  
|<xref:System.Windows.Media.PolyLineSegment>|一連の線を作成します。|  
|<xref:System.Windows.Media.PolyQuadraticBezierSegment>|一連の二次ベジエ曲線を作成します。|  
|<xref:System.Windows.Media.QuadraticBezierSegment>|2 次ベジエ曲線を作成します。|  
  
 内のセグメント、 <xref:System.Windows.Media.PathFigure>セグメントの終了点を次のセグメントの開始点として使用する単一幾何図形に結合されます。 <xref:System.Windows.Media.PathFigure.StartPoint%2A>のプロパティ、 <xref:System.Windows.Media.PathFigure>最初のセグメントの描画元となるポイントを指定します。 後続の各セグメントは、前のセグメントの終了位置から開始されます。 垂直線など`10,50`に`10,150`を設定して定義されていることができます、 <xref:System.Windows.Media.PathFigure.StartPoint%2A>プロパティを`10,50`を作成して、 <xref:System.Windows.Media.LineSegment>で、<xref:System.Windows.Media.LineSegment.Point%2A>のプロパティの設定`10,150`します。  
  
 詳細については<xref:System.Windows.Media.PathGeometry>オブジェクトを参照してください、[ジオメトリの概要](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)します。  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を設定する特別な省略構文を使用することもできます。、<xref:System.Windows.Media.PathGeometry.Figures%2A>のプロパティ、 <xref:System.Windows.Media.PathGeometry>します。 詳細については、次を参照してください。[パス マークアップ構文](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)の概要です。  
  
 使用されているパスの構文の詳細については、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]例を参照してください、[パス マークアップ構文](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)の概要です。  
  
## <a name="see-also"></a>関連項目  
 [パス アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160028)   
 [パス マークアップ構文](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)   
 [パス アニメーションに関する「方法」トピック](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)   
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [プロパティ アニメーションの手法の概要](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)