---
title: "From/To/By アニメーションの概要 | Microsoft Docs"
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
  - "アニメーション, From/To/By"
  - "From/To/By アニメーション"
ms.assetid: 516fce0a-e7f8-49b8-b018-53b3d409a8a3
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# From/To/By アニメーションの概要
ここでは、From\/To\/By アニメーションを使用して[依存関係プロパティ](GTMT)をアニメーション化する方法について説明します。  From\/To\/By アニメーションでは、2 つの値の間の遷移が作成されます。  
  
 このトピックは、次のセクションで構成されています。  
  
<a name="autoTopLevelSectionsOUTLINE0"></a>   
<a name="prereq"></a>   
## 必要条件  
 このトピックを理解するには、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のアニメーション機能に精通している必要があります。  アニメーション機能の概要については、「[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)」を参照してください。  
  
<a name="whatisanimation"></a>   
## From\/To\/By アニメーションとは  
 From\/To\/By アニメーションは、開始値と終了値の間の遷移を作成する <xref:System.Windows.Media.Animation.AnimationTimeline> の一種です。  遷移の完了に要する時間は、そのアニメーションの <xref:System.Windows.Media.Animation.Timeline.Duration%2A> によって決まります。  
  
 マークアップとコードで <xref:System.Windows.Media.Animation.Storyboard> を使用することにより、またはコードで <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> メソッドを使用することで、From\/To\/By アニメーションをプロパティに適用できます。  また、From\/To\/By アニメーションを使用して <xref:System.Windows.Media.Animation.AnimationClock> を作成し、1 つ以上のプロパティに適用することもできます。  アニメーションを適用するさまざまな方法の詳細については、「[プロパティ アニメーションの手法の概要](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)」を参照してください。  
  
 From\/To\/By アニメーションで指定できるターゲット値は 2 つまでです。  3 つ以上のターゲット値を持つアニメーションが必要な場合は、キー フレーム アニメーションを使用してください。  キー フレーム アニメーションについては、「[キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)」を参照してください。  
  
<a name="animation_types"></a>   
## From\/To\/By アニメーションの種類  
 アニメーションによってプロパティ値が生成されるため、さまざまなプロパティ型に対応するさまざまな種類のアニメーションが存在します。  <xref:System.Double> を受け取るプロパティ \(要素の <xref:System.Windows.FrameworkElement.Width%2A> プロパティなど\) をアニメーション化するには、<xref:System.Double> 値を生成するアニメーションを使用します。  <xref:System.Windows.Point> を受け取るプロパティをアニメーション化するには、<xref:System.Windows.Point> 値を生成するアニメーションを使用します。他も同様です。  
  
 From\/To\/By アニメーション クラスは <xref:System.Windows.Media.Animation> 名前空間に属し、次の名前付け規則を使用します。  
  
 *\<Type\>* `Animation`  
  
 ここで、*\<Type\>* はクラスによってアニメーション化される値の型です。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、次の From\/To\/By アニメーション クラスが用意されています。  
  
|プロパティの型|対応する From\/To\/By アニメーション クラス|  
|-------------|-----------------------------------|  
|<xref:System.Byte>|<xref:System.Windows.Media.Animation.ByteAnimation>|  
|<xref:System.Windows.Media.Color>|<xref:System.Windows.Media.Animation.ColorAnimation>|  
|<xref:System.Decimal>|<xref:System.Windows.Media.Animation.DecimalAnimation>|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimation>|  
|<xref:System.Int16>|<xref:System.Windows.Media.Animation.Int16Animation>|  
|<xref:System.Int32>|<xref:System.Windows.Media.Animation.Int32Animation>|  
|<xref:System.Int64>|<xref:System.Windows.Media.Animation.Int64Animation>|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimation>|  
|<xref:System.Windows.Media.Media3D.Quaternion>|<xref:System.Windows.Media.Animation.QuaternionAnimation>|  
|<xref:System.Windows.Rect>|<xref:System.Windows.Media.Animation.RectAnimation>|  
|<xref:System.Windows.Media.Media3D.Rotation3D>|<xref:System.Windows.Media.Animation.Rotation3DAnimation>|  
|<xref:System.Single>|<xref:System.Windows.Media.Animation.SingleAnimation>|  
|<xref:System.Windows.Size>|<xref:System.Windows.Media.Animation.SizeAnimation>|  
|<xref:System.Windows.Thickness>|<xref:System.Windows.Media.Animation.ThicknessAnimation>|  
|<xref:System.Windows.Media.Media3D.Vector3D>|<xref:System.Windows.Media.Animation.Vector3DAnimation>|  
|<xref:System.Windows.Vector>|<xref:System.Windows.Media.Animation.VectorAnimation>|  
  
<a name="anim_values"></a>   
## ターゲット値  
 From\/To\/By アニメーションでは、2 つのターゲット値の間の遷移が作成されます。  開始値 \(<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> プロパティを使用して設定\) と終了値 \(<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> プロパティを使用して設定\) を指定するのが一般的です。  ただし、開始値だけ、終点の値だけ、またはオフセット値だけを指定することもできます。  これらの場合、アニメーションは、足りないターゲット値をアニメーション化しているプロパティから取得します。  アニメーションのターゲット値を指定するさまざまな方法を次に示します。  
  
-   **開始値**  
  
     アニメーションの開始値を明示的に指定する場合は、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> プロパティを使用します。  <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> プロパティだけで使用することも、<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> プロパティまたは <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> プロパティと共に使用することもできます。  <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> プロパティだけを指定した場合は、アニメーションはその値から、アニメーション化されているプロパティの基本値まで遷移します。  
  
-   **終了値**  
  
     アニメーションの終了値を指定するには、<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> プロパティを使用します。  <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> プロパティだけを使用すると、アニメーションは開始値を、アニメーション化されているプロパティから、または同じプロパティに適用されている別のアニメーションから取得します。  <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> プロパティと <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> プロパティを一緒に使用することで、アニメーションの開始値と終了値を明示的に指定できます。  
  
-   **オフセット値**  
  
     <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> プロパティを使用すると、アニメーションの明示的な開始値と終了値の代わりに、オフセットを指定できます。  アニメーションの <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> プロパティは、継続時間中にアニメーションが変更する値の大きさを指定します。  <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> プロパティだけで使用することも、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> プロパティと共に使用することもできます。  <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> プロパティだけを指定した場合は、プロパティの基本値または別のアニメーションの出力に、オフセット値が追加されます。  
  
<a name="examples"></a>   
## From\/To\/By 値の使用  
 以下では、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>、<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>、<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> の各プロパティを、一緒に、または個別に使用する方法を説明します。  
  
 このセクションの各例では、From\/To\/By アニメーションの一種である <xref:System.Windows.Media.Animation.DoubleAnimation> を使用し、高さが 10 [デバイス非依存ピクセル](GTMT)で幅が 100 [デバイス非依存ピクセル](GTMT)の <xref:System.Windows.Shapes.Rectangle> の <xref:System.Windows.FrameworkElement.Width%2A> プロパティをアニメーション化します。  
  
 各例では <xref:System.Windows.Media.Animation.DoubleAnimation> を使用しますが、すべての From\/To\/By アニメーションの From、To、By プロパティの動作はまったく同じです。  これらの例では <xref:System.Windows.Media.Animation.Storyboard> を使用しますが、別の方法で From\/To\/By アニメーションを使用することもできます。  詳細については、「[プロパティ アニメーションの手法の概要](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)」を参照してください。  
  
### From\/To  
 <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> 値と <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> 値を設定すると、アニメーションは、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> プロパティで指定されている値から、<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> プロパティで指定されている値まで進行します。  
  
 次の例では、<xref:System.Windows.Media.Animation.DoubleAnimation> の <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> プロパティを 50 に設定し、<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> プロパティを 300 に設定しています。  その結果、<xref:System.Windows.Shapes.Rectangle> の <xref:System.Windows.FrameworkElement.Width%2A> は、50 から 300 までアニメーション化されます。  
  
 [!code-csharp[basicvalues_snip#FromToAnimationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromtoanimationinline)]
 [!code-vb[basicvalues_snip#FromToAnimationInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromtoanimationinline)]  
  
### 目的  
 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> プロパティだけを設定すると、アニメーションは、アニメーション化されているプロパティの基本値から、または同じプロパティに対して先に適用されている構成アニメーションの出力から、<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> プロパティで指定されている値まで進行します。  
  
 "構成アニメーション" とは、同じプロパティに対して以前に適用されていて、現在のアニメーションが <xref:System.Windows.Media.Animation.HandoffBehavior> ハンドオフ動作を使用して適用された時点でまだ有効であった、<xref:System.Windows.Media.Animation.ClockState> アニメーションまたは <xref:System.Windows.Media.Animation.ClockState> アニメーションのことです。  
  
 次の例では、<xref:System.Windows.Media.Animation.DoubleAnimation> の <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> プロパティだけを 300 に設定しています。  開始値は指定されていないので、<xref:System.Windows.Media.Animation.DoubleAnimation> は、<xref:System.Windows.FrameworkElement.Width%2A> プロパティの基本値 \(100\) を開始値として使用します。  <xref:System.Windows.Shapes.Rectangle> の <xref:System.Windows.FrameworkElement.Width%2A> は、100 から、アニメーションのターゲット値である 300 までアニメーション化されます。  
  
 [!code-csharp[basicvalues_snip#ToAnimationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#toanimationinline)]
 [!code-vb[basicvalues_snip#ToAnimationInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#toanimationinline)]  
  
### By  
 アニメーションの <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> プロパティだけを設定すると、アニメーションは、アニメーション化されているプロパティの基本値から、または構成アニメーションの出力から、これらの値に <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> プロパティで指定されている値を加えた合計値まで進行します。  
  
 次の例では、<xref:System.Windows.Media.Animation.DoubleAnimation> の <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> プロパティだけを 300 に設定しています。  開始値は指定されていないので、<xref:System.Windows.Media.Animation.DoubleAnimation> は、<xref:System.Windows.FrameworkElement.Width%2A> プロパティの基本値である 100 を開始値として使用します。  終了値は、アニメーションの <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> の値 300 を開始値 100 に加えた値 400 になります。  その結果、<xref:System.Windows.Shapes.Rectangle> の <xref:System.Windows.FrameworkElement.Width%2A> は、100 から 400 までアニメーション化されます。  
  
 [!code-csharp[basicvalues_snip#ByAnimationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#byanimationinline)]
 [!code-vb[basicvalues_snip#ByAnimationInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#byanimationinline)]  
  
### From\/By  
 アニメーションの <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> プロパティと <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> プロパティを設定すると、アニメーションは、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> プロパティで指定されている値から、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> プロパティと <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> プロパティの合計で指定される値まで進行します。  
  
 次の例では、<xref:System.Windows.Media.Animation.DoubleAnimation> の <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> プロパティを 50 に設定し、<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> プロパティを 300 に設定しています。  終了値は、アニメーションの <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> の値 300 を開始値 50 に加えた値 350 になります。  その結果、<xref:System.Windows.Shapes.Rectangle> の <xref:System.Windows.FrameworkElement.Width%2A> は、50 から 350 までアニメーション化されます。  
  
 [!code-csharp[basicvalues_snip#FromByAnimationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#frombyanimationinline)]
 [!code-vb[basicvalues_snip#FromByAnimationInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#frombyanimationinline)]  
  
### 変換前  
 アニメーションの <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> 値だけを指定すると、アニメーションは、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> プロパティで指定されている値から、アニメーション化されているプロパティの基本値、または構成アニメーションの出力まで進行します。  
  
 次の例では、<xref:System.Windows.Media.Animation.DoubleAnimation> の <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> プロパティだけを 50 に設定しています。  終了値は指定されていないので、<xref:System.Windows.Media.Animation.DoubleAnimation> は、<xref:System.Windows.FrameworkElement.Width%2A> プロパティの基本値 100 を終了値として使用します。  <xref:System.Windows.Shapes.Rectangle> の <xref:System.Windows.FrameworkElement.Width%2A> は、50 から、<xref:System.Windows.FrameworkElement.Width%2A> プロパティの基本値 100 までアニメーション化されます。  
  
 [!code-csharp[basicvalues_snip#FromAnimationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromanimationinline)]
 [!code-vb[basicvalues_snip#FromAnimationInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromanimationinline)]  
  
### To\/By  
 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> プロパティと <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> プロパティの両方を設定した場合は、<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> プロパティは無視されます。  
  
<a name="otheranimationtypes"></a>   
## 他のアニメーションの種類  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] が提供するアニメーションの種類は、From\/To\/By アニメーションだけではありません。キー フレーム アニメーションとパス アニメーションも提供されています。  
  
-   キー フレーム アニメーションは、キー フレームを使用して記述される複数の終了値に沿ってアニメーション化を行います。  詳細については、「[キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)」を参照してください。  
  
-   パス アニメーションは、<xref:System.Windows.Media.PathGeometry> から出力値を生成します。  詳細については、「[パス アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/path-animations-overview.md)」を参照してください。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、独自のカスタム アニメーションの種類を作成することもできます。  詳細については、「[カスタム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/custom-animations-overview.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Media.Animation.Timeline>   
 <xref:System.Windows.Media.Animation.Storyboard>   
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [ストーリーボードの概要](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)   
 [キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [パス アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/path-animations-overview.md)   
 [カスタム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/custom-animations-overview.md)   
 [アニメーションのターゲット値 \(From、To、および By\) のサンプル](http://go.microsoft.com/fwlink/?LinkID=159988)