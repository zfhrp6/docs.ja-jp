---
title: "イージング関数"
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
- applying mathematical formulas to animations [WPF]
- applying easing functions to animations [WPF]
- mathematical formulas [WPF], applying to animations
- animations [WPF], realistic movement
- easing functions [WPF]
- customizing easing functions [WPF]
- easing functions [WPF], definition
- easing functions [WPF], customizing
- animations [WPF], applying
ms.assetid: 075b9c2b-82c4-43fa-b3cd-de0b6236eb38
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 570a065d3f28befe8db4887ff908c3bd60a639a1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="easing-functions"></a><span data-ttu-id="3b8b1-102">イージング関数</span><span class="sxs-lookup"><span data-stu-id="3b8b1-102">Easing Functions</span></span>
<span data-ttu-id="3b8b1-103">イージング関数を使うと、独自の数式をアニメーションに適用することができます。</span><span class="sxs-lookup"><span data-stu-id="3b8b1-103">Easing functions allow you to apply custom mathematical formulas to your animations.</span></span> <span data-ttu-id="3b8b1-104">たとえば、オブジェクトをリアルにバウンドさせたり、バネに乗っているように動作させたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="3b8b1-104">For example, you may want an object to realistically bounce or behave as though it were on a spring.</span></span> <span data-ttu-id="3b8b1-105">キー フレーム アニメーションや From/To/By アニメーションを使ってこれらの効果を近似することもできますが、大量の作業が必要であり、アニメーションは数式を使うほど正確ではありません。</span><span class="sxs-lookup"><span data-stu-id="3b8b1-105">You could use Key-Frame or even From/To/By animations to approximate these effects but it would take a significant amount of work and the animation would be less accurate than using a mathematical formula.</span></span>  
  
 <span data-ttu-id="3b8b1-106">継承することで、独自のカスタム イージング関数を作成するだけでなく<xref:System.Windows.Media.Animation.EasingFunctionBase>、ランタイムによって提供されるいくつかのイージング関数のいずれかを使用して、一般的な効果を作成することができます。</span><span class="sxs-lookup"><span data-stu-id="3b8b1-106">Besides creating your own custom easing function by inheriting from <xref:System.Windows.Media.Animation.EasingFunctionBase>, you can use one of several easing functions provided by the runtime to create common effects.</span></span>  
  
-   <span data-ttu-id="3b8b1-107"><xref:System.Windows.Media.Animation.BackEase>: 取り消されますアニメーションの動き若干指定したパスにアニメーション化を開始する前にします。</span><span class="sxs-lookup"><span data-stu-id="3b8b1-107"><xref:System.Windows.Media.Animation.BackEase>: Retracts the motion of an animation slightly before it begins to animate in the path indicated.</span></span>  
  
-   <span data-ttu-id="3b8b1-108"><xref:System.Windows.Media.Animation.BounceEase>: バウンス効果を作成します。</span><span class="sxs-lookup"><span data-stu-id="3b8b1-108"><xref:System.Windows.Media.Animation.BounceEase>: Creates a bouncing effect.</span></span>  
  
-   <span data-ttu-id="3b8b1-109"><xref:System.Windows.Media.Animation.CircleEase>: 加速または減速循環関数を使用するアニメーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="3b8b1-109"><xref:System.Windows.Media.Animation.CircleEase>: Creates an animation that accelerates and/or decelerates using a circular function.</span></span>  
  
-   <span data-ttu-id="3b8b1-110"><xref:System.Windows.Media.Animation.CubicEase>: 加速または減速の公式を使用するアニメーションを作成する*f*(*t*) = *t*<sup>3</sup>です。</span><span class="sxs-lookup"><span data-stu-id="3b8b1-110"><xref:System.Windows.Media.Animation.CubicEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>3</sup>.</span></span>  
  
-   <span data-ttu-id="3b8b1-111"><xref:System.Windows.Media.Animation.ElasticEase>: するまでに前後に動く spring のようなアニメーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="3b8b1-111"><xref:System.Windows.Media.Animation.ElasticEase>: Creates an animation that resembles a spring oscillating back and forth until it comes to rest.</span></span>  
  
-   <span data-ttu-id="3b8b1-112"><xref:System.Windows.Media.Animation.ExponentialEase>: 加速または減速指数の式を使用するアニメーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="3b8b1-112"><xref:System.Windows.Media.Animation.ExponentialEase>: Creates an animation that accelerates and/or decelerates using an exponential formula.</span></span>  
  
-   <span data-ttu-id="3b8b1-113"><xref:System.Windows.Media.Animation.PowerEase>: 加速または減速の公式を使用するアニメーションを作成する*f*(*t*) = *t*<sup>p</sup> p が、に等しい<xref:System.Windows.Media.Animation.PowerEase.Power%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="3b8b1-113"><xref:System.Windows.Media.Animation.PowerEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>p</sup> where p is equal to the <xref:System.Windows.Media.Animation.PowerEase.Power%2A> property.</span></span>  
  
-   <span data-ttu-id="3b8b1-114"><xref:System.Windows.Media.Animation.QuadraticEase>: 加速または減速の公式を使用するアニメーションを作成する*f*(*t*) = *t*<sup>2</sup>です。</span><span class="sxs-lookup"><span data-stu-id="3b8b1-114"><xref:System.Windows.Media.Animation.QuadraticEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>2</sup>.</span></span>  
  
-   <span data-ttu-id="3b8b1-115"><xref:System.Windows.Media.Animation.QuarticEase>: 加速または減速の公式を使用するアニメーションを作成する*f*(*t*) = *t*<sup>4</sup>です。</span><span class="sxs-lookup"><span data-stu-id="3b8b1-115"><xref:System.Windows.Media.Animation.QuarticEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>4</sup>.</span></span>  
  
-   <span data-ttu-id="3b8b1-116"><xref:System.Windows.Media.Animation.QuinticEase>: 加速または減速の公式を使用するアニメーションを作成する*f*(*t*) = *t*<sup>5</sup>です。</span><span class="sxs-lookup"><span data-stu-id="3b8b1-116"><xref:System.Windows.Media.Animation.QuinticEase>: Create an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>5</sup>.</span></span>  
  
-   <span data-ttu-id="3b8b1-117"><xref:System.Windows.Media.Animation.SineEase>: 加速または減速サイン (正弦) 式を使用するアニメーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="3b8b1-117"><xref:System.Windows.Media.Animation.SineEase>: Creates an animation that accelerates and/or decelerates using a sine formula.</span></span>  
  
 <span data-ttu-id="3b8b1-118">これらのイージング関数の動作は、次のサンプルを使って調べることができます。</span><span class="sxs-lookup"><span data-stu-id="3b8b1-118">You can explore the behavior of these easing functions with the following sample.</span></span>  
  
 [<span data-ttu-id="3b8b1-119">このサンプルを実行する</span><span class="sxs-lookup"><span data-stu-id="3b8b1-119">Run this sample</span></span>](http://go.microsoft.com/fwlink/?LinkId=139798&sref=easing_functions_gallery)  
  
 <span data-ttu-id="3b8b1-120">アニメーションにイージング関数を適用するには、使用、`EasingFunction`アニメーションのプロパティをアニメーションに適用するイージング関数を指定します。</span><span class="sxs-lookup"><span data-stu-id="3b8b1-120">To apply an easing function to an animation, use the `EasingFunction` property of the animation specify the easing function to apply to the animation.</span></span> <span data-ttu-id="3b8b1-121">次の例に適用されます、<xref:System.Windows.Media.Animation.BounceEase>イージング関数を<xref:System.Windows.Media.Animation.DoubleAnimation>跳ね返り効果を作成します。</span><span class="sxs-lookup"><span data-stu-id="3b8b1-121">The following example applies a <xref:System.Windows.Media.Animation.BounceEase> easing function to a <xref:System.Windows.Media.Animation.DoubleAnimation> to create a bouncing effect.</span></span>  
  
 [<span data-ttu-id="3b8b1-122">このサンプルを実行する</span><span class="sxs-lookup"><span data-stu-id="3b8b1-122">Run this sample</span></span>](http://go.microsoft.com/fwlink/?LinkId=139798&sref=BounceEase)  
  
 [!code-xaml[BounceEase_snippet#BounceEase](../../../../samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 <span data-ttu-id="3b8b1-123">前の例では、イージング関数を From/To/By アニメーションに適用しました。</span><span class="sxs-lookup"><span data-stu-id="3b8b1-123">In the previous example, the easing function was applied to a From/To/By animation.</span></span> <span data-ttu-id="3b8b1-124">キー フレーム アニメーションにこれらのイージング関数を適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="3b8b1-124">You can also apply these easing functions to Key-Frame animations.</span></span> <span data-ttu-id="3b8b1-125">次の例では、キー フレームとそれらに関連付けられたイージング関数を使って、四角形が上方に縮まり、遅くなり、下方に延び (落下するように)、停止するアニメーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="3b8b1-125">The following example shows how to use key frames with easing functions associated with them to create an animation of a rectangle that contracts upward, slows down, then expands downward (as though falling) and then bounces to a stop.</span></span>  
  
 [<span data-ttu-id="3b8b1-126">このサンプルを実行する</span><span class="sxs-lookup"><span data-stu-id="3b8b1-126">Run this sample</span></span>](http://go.microsoft.com/fwlink/?LinkId=139798&sref=EasingFunctionDoubleKeyFrame)  
  
 [!code-xaml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](../../../../samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 <span data-ttu-id="3b8b1-127">使用することができます、<xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>イージング関数の動作、つまり、変更するプロパティを変更する方法、アニメーションの補間します。</span><span class="sxs-lookup"><span data-stu-id="3b8b1-127">You can use the <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> property to alter how the easing function behaves, that is, change how the animation interpolates.</span></span> <span data-ttu-id="3b8b1-128">3 つの値を与えることができますがある<xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:</span><span class="sxs-lookup"><span data-stu-id="3b8b1-128">There are three possible values you can give for <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:</span></span>  
  
-   <span data-ttu-id="3b8b1-129"><xref:System.Windows.Media.Animation.EasingMode.EaseIn>: 補間には、イージング関数に関連付けられた数式が次に示します。</span><span class="sxs-lookup"><span data-stu-id="3b8b1-129"><xref:System.Windows.Media.Animation.EasingMode.EaseIn>: Interpolation follows the mathematical formula associated with the easing function.</span></span>  
  
-   <span data-ttu-id="3b8b1-130"><xref:System.Windows.Media.Animation.EasingMode.EaseOut>: 補間に依存しているイージング機能に関連付けられている式の出力-100% の補間します。</span><span class="sxs-lookup"><span data-stu-id="3b8b1-130"><xref:System.Windows.Media.Animation.EasingMode.EaseOut>: Interpolation follows 100% interpolation minus the output of the formula associated with the easing function.</span></span>  
  
-   <span data-ttu-id="3b8b1-131"><xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: 補間を使用して<xref:System.Windows.Media.Animation.EasingMode.EaseIn>アニメーションの前半のおよび<xref:System.Windows.Media.Animation.EasingMode.EaseOut>後半を 2 番目のです。</span><span class="sxs-lookup"><span data-stu-id="3b8b1-131"><xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: Interpolation uses <xref:System.Windows.Media.Animation.EasingMode.EaseIn> for the first half of the animation and <xref:System.Windows.Media.Animation.EasingMode.EaseOut> for the second half.</span></span>  
  
 <span data-ttu-id="3b8b1-132">下のグラフのさまざまな値を示す<xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>場所*f*(*x*)、アニメーションの進行状況を表すと*t*時間を表します。</span><span class="sxs-lookup"><span data-stu-id="3b8b1-132">The graphs below demonstrate the different values of <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> where *f*(*x*) represents the animation progress and *t* represents time.</span></span>  
  
 <xref:System.Windows.Media.Animation.BackEase>  
  
 <span data-ttu-id="3b8b1-133">![BackEase EasingMode のグラフ。](../../../../docs/framework/wpf/graphics-multimedia/media/backease-graph.png "BackEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="3b8b1-133">![BackEase EasingMode graphs.](../../../../docs/framework/wpf/graphics-multimedia/media/backease-graph.png "BackEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.BounceEase>  
  
 <span data-ttu-id="3b8b1-134">![BounceEase EasingMode のグラフ。](../../../../docs/framework/wpf/graphics-multimedia/media/bounceease-graph.png "BounceEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="3b8b1-134">![BounceEase EasingMode graphs.](../../../../docs/framework/wpf/graphics-multimedia/media/bounceease-graph.png "BounceEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.CircleEase>  
  
 <span data-ttu-id="3b8b1-135">![CircleEase EasingMode のグラフ。](../../../../docs/framework/wpf/graphics-multimedia/media/circleease-graph.png "CircleEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="3b8b1-135">![CircleEase EasingMode graphs.](../../../../docs/framework/wpf/graphics-multimedia/media/circleease-graph.png "CircleEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.CubicEase>  
  
 <span data-ttu-id="3b8b1-136">![CubicEase EasingMode のグラフ。](../../../../docs/framework/wpf/graphics-multimedia/media/cubicease-graph.png "CubicEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="3b8b1-136">![CubicEase EasingMode graphs.](../../../../docs/framework/wpf/graphics-multimedia/media/cubicease-graph.png "CubicEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.ElasticEase>  
  
 <span data-ttu-id="3b8b1-137">![異なる EasingMode の ElasticEase のグラフ。](../../../../docs/framework/wpf/graphics-multimedia/media/elasticease-graph.png "ElasticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="3b8b1-137">![ElasticEase with graphs of different easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/elasticease-graph.png "ElasticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.ExponentialEase>  
  
 <span data-ttu-id="3b8b1-138">![異なる EasingMode の ExponentialEase のグラフ。](../../../../docs/framework/wpf/graphics-multimedia/media/exponentialease-graph.png "ExponentialEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="3b8b1-138">![ExponentialEase graphs of different easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/exponentialease-graph.png "ExponentialEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.PowerEase>  
  
 <span data-ttu-id="3b8b1-139">![異なる EasingMode の QuarticEase のグラフ。](../../../../docs/framework/wpf/graphics-multimedia/media/quarticease-graph.png "QuarticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="3b8b1-139">![QuarticEase with graphs of different easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/quarticease-graph.png "QuarticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuadraticEase>  
  
 <span data-ttu-id="3b8b1-140">![異なる EasingMode の QuadraticEase のグラフ。](../../../../docs/framework/wpf/graphics-multimedia/media/quadraticease-graph.png "QuadraticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="3b8b1-140">![QuadraticEase with graphs of different easingmodes](../../../../docs/framework/wpf/graphics-multimedia/media/quadraticease-graph.png "QuadraticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuarticEase>  
  
 <span data-ttu-id="3b8b1-141">![異なる EasingMode の QuarticEase のグラフ。](../../../../docs/framework/wpf/graphics-multimedia/media/quarticease-graph.png "QuarticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="3b8b1-141">![QuarticEase with graphs of different easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/quarticease-graph.png "QuarticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuinticEase>  
  
 <span data-ttu-id="3b8b1-142">![異なる EasingMode の QuinticEase のグラフ。](../../../../docs/framework/wpf/graphics-multimedia/media/quinticease-graph.png "QuinticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="3b8b1-142">![QuinticEase with graphs of different easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/quinticease-graph.png "QuinticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.SineEase>  
  
 <span data-ttu-id="3b8b1-143">![異なる EasingMode 値の SineEase](../../../../docs/framework/wpf/graphics-multimedia/media/sineease-graph.png "SineEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="3b8b1-143">![SineEase for different EasingMode values](../../../../docs/framework/wpf/graphics-multimedia/media/sineease-graph.png "SineEase_Graph")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3b8b1-144">使用することができます<xref:System.Windows.Media.Animation.PowerEase>と同じ動作を作成する<xref:System.Windows.Media.Animation.CubicEase>、 <xref:System.Windows.Media.Animation.QuadraticEase>、 <xref:System.Windows.Media.Animation.QuarticEase>、および<xref:System.Windows.Media.Animation.QuinticEase>を使用して、<xref:System.Windows.Media.Animation.PowerEase.Power%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="3b8b1-144">You can use <xref:System.Windows.Media.Animation.PowerEase> to create the same behavior as <xref:System.Windows.Media.Animation.CubicEase>, <xref:System.Windows.Media.Animation.QuadraticEase>, <xref:System.Windows.Media.Animation.QuarticEase>, and <xref:System.Windows.Media.Animation.QuinticEase> by using the <xref:System.Windows.Media.Animation.PowerEase.Power%2A> property.</span></span> <span data-ttu-id="3b8b1-145">たとえば、使用する場合<xref:System.Windows.Media.Animation.PowerEase>の代替として<xref:System.Windows.Media.Animation.CubicEase>を指定、 <xref:System.Windows.Media.Animation.PowerEase.Power%2A> 3 の値。</span><span class="sxs-lookup"><span data-stu-id="3b8b1-145">For example, if you want to use <xref:System.Windows.Media.Animation.PowerEase> to substitute for <xref:System.Windows.Media.Animation.CubicEase>, specify a <xref:System.Windows.Media.Animation.PowerEase.Power%2A> value of 3.</span></span>  
  
 <span data-ttu-id="3b8b1-146">継承することで、独自のカスタム イージング関数を作成するだけでなく、実行時に含まれるイージング関数を使用して、<xref:System.Windows.Media.Animation.EasingFunctionBase>です。</span><span class="sxs-lookup"><span data-stu-id="3b8b1-146">In addition to using the easing functions included in the run-time, you can create your own custom easing functions by inheriting from <xref:System.Windows.Media.Animation.EasingFunctionBase>.</span></span> <span data-ttu-id="3b8b1-147">次の例では、簡単なカスタム イージング関数を作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="3b8b1-147">The following example demonstrates how to create a simple custom easing function.</span></span> <span data-ttu-id="3b8b1-148">イージング関数をオーバーライドすることで動作する方法を独自の数値演算ロジックを追加することができます、<xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="3b8b1-148">You can add your own mathematical logic for how the easing function behaves by overriding the <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> method.</span></span>  
  
 [<span data-ttu-id="3b8b1-149">このサンプルを実行する</span><span class="sxs-lookup"><span data-stu-id="3b8b1-149">Run this sample</span></span>](http://go.microsoft.com/fwlink/?LinkId=139798&sref=CustomEasingFunction)  
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xaml[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]
