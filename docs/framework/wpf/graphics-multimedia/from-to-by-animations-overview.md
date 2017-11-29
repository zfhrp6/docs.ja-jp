---
title: "別のアニメーションの概要"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], From/to/by
- From/to/by animation
ms.assetid: 516fce0a-e7f8-49b8-b018-53b3d409a8a3
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f5eba773a290f1100fcea411919c5c16558e01ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="fromtoby-animations-overview"></a>From/To/By アニメーションの概要
このトピックでは、From/To/By アニメーションを使って依存関係プロパティをアニメーション化する方法を説明します。 From/To/By アニメーションでは、2 つの値の間の遷移が作成されます。  
  
<a name="prereq"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックの内容を理解しておく必要があります慣れて[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アニメーション機能します。 アニメーションの機能の概要については、次を参照してください。、[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)です。  
  
<a name="whatisanimation"></a>   
## <a name="what-is-a-fromtoby-animation"></a>From/To/By アニメーションとは  
 From/に/でアニメーションの種類は、<xref:System.Windows.Media.Animation.AnimationTimeline>開始値と終了値の間の遷移を作成します。 移行が完了にかかる時間はによって決まります、<xref:System.Windows.Media.Animation.Timeline.Duration%2A>したアニメーションのです。  
  
 適用するには From/に/アニメーションのプロパティを使用して、<xref:System.Windows.Media.Animation.Storyboard>マークアップおよびコード、またはを使用して、<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>コード内のメソッドです。 作成する From/To/By アニメーションを使用することも、<xref:System.Windows.Media.Animation.AnimationClock>し、1 つまたは複数のプロパティに適用します。 アニメーションを適用するためのさまざまなメソッドの詳細については、「[プロパティ アニメーションの手法の概要](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)」を参照してください。  
  
 From/To/By アニメーションは、2 つのターゲット値以外の値を持つことはできません。 3 つ以上のターゲット値を持つアニメーションを必要とする場合は、キー フレーム アニメーションを使います。 キー フレーム アニメーションに記載されている、[キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)です。  
  
<a name="animation_types"></a>   
## <a name="fromtoby-animation-types"></a>From/To/By アニメーションの種類  
 アニメーションはプロパティ値を生成するため、プロパティの型ごとに異なるアニメーションの種類があります。 受け取るプロパティをアニメーション化する、 <xref:System.Double>、ように、 <xref:System.Windows.FrameworkElement.Width%2A> 、要素のプロパティを生成するアニメーションを使用して<xref:System.Double>値。 受け取るプロパティをアニメーション化する、 <xref:System.Windows.Point>、生成されるアニメーションを使用して<xref:System.Windows.Point>値、およびなどです。  
  
 アニメーションによって/クラスが属している、<xref:System.Windows.Media.Animation>名前空間および次の命名規則を使用します。  
  
 *\<Type>* `Animation`  
  
 ここで、*\<Type>*は、クラスがアニメーション化する値の型です。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、次の From/To/By アニメーション クラスが用意されています。  
  
|プロパティの型|対応する From/To/By アニメーションのクラス|  
|-------------------|------------------------------------------------|  
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
## <a name="target-values"></a>ターゲット値  
 From/To/By アニメーションでは、2 つのターゲット値の間の遷移が作成されます。 開始値を指定するが一般的 (を使用して設定、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>プロパティ) と終了値 (を使用して設定、<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>プロパティ)。 ただし、開始値、終了値、またはオフセット値のみを指定することもできます。 これらの場合、アニメーションは不足しているターゲット値をアニメーション化するプロパティから取得します。 次の一覧では、アニメーションのターゲット値を指定する方法について説明します。  
  
-   **開始値**  
  
     使用して、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>プロパティをアニメーションの開始値を明示的に指定する場合。 使用することができます、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>プロパティ自体は、または、<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>または<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>プロパティです。 のみを指定する場合、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>プロパティ、アニメーションのプロパティのベース値に、その値をアニメーション遷移します。  
  
-   **終了値**  
  
     アニメーションの終了値を指定するには、次のように使用します。 その<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>プロパティです。 使用する場合、<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>プロパティ自体によって、アニメーションはその開始値はアニメーション化するプロパティと同じプロパティに適用される別のアニメーションの出力からします。 使用することができます、<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>と共に、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>開始、アニメーションの値と終了を明示的に指定するプロパティです。  
  
-   **オフセット値**  
  
     <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>プロパティでは、明示的な開始時刻またはアニメーションの終了値ではなくオフセットを指定することができます。 <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>アニメーションのプロパティは、どの程度のアニメーションで、その期間にわたって値を変更します。 を指定します。 使用することができます、<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>プロパティまたは単独で、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>プロパティです。 のみを指定する場合、<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>プロパティのベース値に、または別のアニメーションの出力に、プロパティ、アニメーションがオフセット値を追加します。  
  
<a name="examples"></a>   
## <a name="using-fromtoby-values"></a>From/To/By 値の使用  
 次のセクションを使用する方法について説明、 <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>、 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>、および<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>プロパティとは別にまたは同時にします。  
  
 例では、このセクションの各使用、 <xref:System.Windows.Media.Animation.DoubleAnimation>、これは、/、アニメーションのアニメーション化する型、<xref:System.Windows.FrameworkElement.Width%2A>のプロパティ、 <xref:System.Windows.Shapes.Rectangle> 10 デバイス非依存ピクセル高と 100 デバイス非依存のピクセル幅の広いされています。  
  
 それぞれの例を使用しますが、 <xref:System.Windows.Media.Animation.DoubleAnimation>、およびすべて From/に/でのプロパティでアニメーションの動作は同じです。 これらの例を使用しますが、 <xref:System.Windows.Media.Animation.Storyboard>、他の方法で、またはアニメーションを使用することができます。 詳細については、次を参照してください。[プロパティ アニメーションの技術概要](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)です。  
  
### <a name="fromto"></a>From/To  
 設定すると、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>と<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>値を同時に、アニメーション、によって指定される値、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>で指定された値に、プロパティ、<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>プロパティです。  
  
 次の例のセット、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>のプロパティ、<xref:System.Windows.Media.Animation.DoubleAnimation>に 50 およびその<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>300 プロパティです。 その結果、<xref:System.Windows.FrameworkElement.Width%2A>の<xref:System.Windows.Shapes.Rectangle>50 から 300 にアニメーションを実行します。  
  
 [!code-csharp[basicvalues_snip#FromToAnimationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromtoanimationinline)]
 [!code-vb[basicvalues_snip#FromToAnimationInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromtoanimationinline)]  
  
### <a name="to"></a>終了  
 設定した場合だけ、<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>プロパティ、アニメーション、アニメーションのプロパティのベース値から、またはで指定された値に、同じプロパティに適用されていた作成中のアニメーションの出力から、 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>プロパティ。  
  
 (「構成アニメーション」を指す、<xref:System.Windows.Media.Animation.ClockState.Active>または<xref:System.Windows.Media.Animation.ClockState.Filling>アニメーションを使用して現在のアニメーションが適用されたときに、有効なままで、同じプロパティに適用されていた、<xref:System.Windows.Media.Animation.HandoffBehavior.Compose>ハンドオフ動作します)。  
  
 次の例の設定だけ、<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>のプロパティ、 <xref:System.Windows.Media.Animation.DoubleAnimation> 300 にします。 開始値が指定されなかったため、<xref:System.Windows.Media.Animation.DoubleAnimation>のベース値 (100) を使用して、<xref:System.Windows.FrameworkElement.Width%2A>プロパティとしてその開始値。 <xref:System.Windows.FrameworkElement.Width%2A>の<xref:System.Windows.Shapes.Rectangle>100 人から 300 のアニメーションの対象の値をアニメーション化します。  
  
 [!code-csharp[basicvalues_snip#ToAnimationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#toanimationinline)]
 [!code-vb[basicvalues_snip#ToAnimationInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#toanimationinline)]  
  
### <a name="by"></a>By  
 設定した場合だけ、<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>アニメーションのプロパティ、アニメーションをアニメーション化するプロパティのベース値から、またはその値とで指定されている値の合計に作成したアニメーションの出力から、 <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>プロパティ。  
  
 次の例の設定だけ、<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>のプロパティ、 <xref:System.Windows.Media.Animation.DoubleAnimation> 300 にします。 この例で、開始値が指定されていないため、<xref:System.Windows.Media.Animation.DoubleAnimation>のベース値を使用して、<xref:System.Windows.FrameworkElement.Width%2A>プロパティ、100、開始値として。 終了値を追加することで決定されます、<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>アニメーション、その開始値 100: 400 の値。 その結果、<xref:System.Windows.FrameworkElement.Width%2A>の<xref:System.Windows.Shapes.Rectangle>100 人から 400 にアニメーションを実行します。  
  
 [!code-csharp[basicvalues_snip#ByAnimationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#byanimationinline)]
 [!code-vb[basicvalues_snip#ByAnimationInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#byanimationinline)]  
  
### <a name="fromby"></a>From/By  
 設定すると、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>と<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>アニメーションのプロパティをアニメーションで指定された値、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>の値の合計で指定されている値を<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>と<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>プロパティです。  
  
 次の例のセット、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>のプロパティ、<xref:System.Windows.Media.Animation.DoubleAnimation>に 50 およびその<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>300 プロパティです。 終了値を追加することで決定されます、<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>アニメーション、その開始値 50: 350 の値。 その結果、<xref:System.Windows.FrameworkElement.Width%2A>の<xref:System.Windows.Shapes.Rectangle>350 を 50 からアニメーション化します。  
  
 [!code-csharp[basicvalues_snip#FromByAnimationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#frombyanimationinline)]
 [!code-vb[basicvalues_snip#FromByAnimationInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#frombyanimationinline)]  
  
### <a name="from"></a>変換前  
 指定した場合だけ、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>アニメーションの値、アニメーションで指定された値、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>プロパティ、または作成中のアニメーションの出力にはアニメーション化するプロパティのベース値にします。  
  
 次の例の設定だけ、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>のプロパティ、 <xref:System.Windows.Media.Animation.DoubleAnimation> 50 にします。 終了値が指定されなかったため、<xref:System.Windows.Media.Animation.DoubleAnimation>のベース値を使用して、<xref:System.Windows.FrameworkElement.Width%2A>プロパティを 100、としてその終了値。 <xref:System.Windows.FrameworkElement.Width%2A>の<xref:System.Windows.Shapes.Rectangle>は 50 からのベース値にアニメーション、<xref:System.Windows.FrameworkElement.Width%2A>プロパティ、100 です。  
  
 [!code-csharp[basicvalues_snip#FromAnimationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromanimationinline)]
 [!code-vb[basicvalues_snip#FromAnimationInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromanimationinline)]  
  
### <a name="toby"></a>To/By  
 両方を設定する場合、<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>と<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>、アニメーションのプロパティを<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>プロパティは無視されます。  
  
<a name="otheranimationtypes"></a>   
## <a name="other-animation-types"></a>他のアニメーションの種類  
 によって/アニメーションがアニメーションの唯一の種類ではないを[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]提供: キー フレーム アニメーション、およびパス アニメーションも用意されています。  
  
-   キー フレーム アニメーションは、キー フレームを使って記述されている任意の数の目標値に沿ってアニメーション化します。 詳細については、次を参照してください。、[キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)です。  
  
-   パスのアニメーションからの出力値を生成する、<xref:System.Windows.Media.PathGeometry>です。 詳細については、次を参照してください。、[パス アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/path-animations-overview.md)です。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、独自のカスタム アニメーションの種類を作成することもできます。 詳細については、次を参照してください。、[カスタム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/custom-animations-overview.md)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Media.Animation.Timeline>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [ストーリーボードの概要](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [パス アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/path-animations-overview.md)  
 [カスタム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/custom-animations-overview.md)  
 [アニメーションのターゲット値 (From、To、および By) のサンプル](http://go.microsoft.com/fwlink/?LinkID=159988)
