---
title: "方法 : AnimationClock を使用してプロパティをアニメーション化する"
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
- animation [WPF], properties [WPF], with AnimationClocks
- AnimationClocks [WPF]
ms.assetid: e6542021-714c-4675-9567-04f1c7380834
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 47df7aaad45000bc8c761a9bb9022d37e0f0828c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-a-property-by-using-an-animationclock"></a><span data-ttu-id="14425-102">方法 : AnimationClock を使用してプロパティをアニメーション化する</span><span class="sxs-lookup"><span data-stu-id="14425-102">How to: Animate a Property by Using an AnimationClock</span></span>
<span data-ttu-id="14425-103">この例を使用する方法を示しています。<xref:System.Windows.Media.Animation.Clock>プロパティをアニメーション化するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="14425-103">This example shows how to use <xref:System.Windows.Media.Animation.Clock> objects to animate a property.</span></span>  
  
 <span data-ttu-id="14425-104">依存関係プロパティをアニメーション化するには次の 3 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="14425-104">There are three ways to animate a dependency property:</span></span>  
  
-   <span data-ttu-id="14425-105">作成、<xref:System.Windows.Media.Animation.AnimationTimeline>を使用してそのプロパティに関連付けると、<xref:System.Windows.Media.Animation.Storyboard>です。</span><span class="sxs-lookup"><span data-stu-id="14425-105">Create an <xref:System.Windows.Media.Animation.AnimationTimeline> and associate it with that property by using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
-   <span data-ttu-id="14425-106">オブジェクトの<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>メソッドを 1 つを適用する<xref:System.Windows.Media.Animation.AnimationTimeline>対象のプロパティにします。</span><span class="sxs-lookup"><span data-stu-id="14425-106">Use the object's <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method to apply a single <xref:System.Windows.Media.Animation.AnimationTimeline> to a target property.</span></span>  
  
-   <span data-ttu-id="14425-107">作成、<xref:System.Windows.Media.Animation.AnimationClock>から、<xref:System.Windows.Media.Animation.AnimationTimeline>し、プロパティに適用します。</span><span class="sxs-lookup"><span data-stu-id="14425-107">Create an <xref:System.Windows.Media.Animation.AnimationClock> from an <xref:System.Windows.Media.Animation.AnimationTimeline> and apply it to a property.</span></span>  
  
 <span data-ttu-id="14425-108"><xref:System.Windows.Media.Animation.Storyboard>オブジェクトおよび<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>メソッドに直接作成および時計を配布することがなくプロパティをアニメーション化することが有効にする (例については、次を参照してください[ストーリー ボードを使用してプロパティをアニメーション化](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)と[プロパティなしをアニメーション化します。ストーリー ボードを使って](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)) です。クロックが作成され、自動的に配布します。</span><span class="sxs-lookup"><span data-stu-id="14425-108"><xref:System.Windows.Media.Animation.Storyboard> objects and the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method enable you to animate properties without directly creating and distributing clocks (for examples, see [Animate a Property by Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md) and [Animate a Property Without Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)); clocks are created and distributed for you automatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14425-109">例</span><span class="sxs-lookup"><span data-stu-id="14425-109">Example</span></span>  
 <span data-ttu-id="14425-110">次の例を作成する方法を示しています、<xref:System.Windows.Media.Animation.AnimationClock>し、同様の 2 つのプロパティに適用します。</span><span class="sxs-lookup"><span data-stu-id="14425-110">The following example shows how to create an <xref:System.Windows.Media.Animation.AnimationClock> and apply it to two similar properties.</span></span>  
  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/AnimationClockExample.cs#graphicsmmcreateanimationclockwholeclass)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/animationclockexample.vb#graphicsmmcreateanimationclockwholeclass)]  
  
 <span data-ttu-id="14425-111">対話的に制御する方法を示す例については、<xref:System.Windows.Media.Animation.Clock>が起動したらを参照してください。[クロックを対話的に制御する](../../../../docs/framework/wpf/graphics-multimedia/how-to-interactively-control-a-clock.md)です。</span><span class="sxs-lookup"><span data-stu-id="14425-111">For an example showing how to interactively control a <xref:System.Windows.Media.Animation.Clock> after it starts, see [Interactively Control a Clock](../../../../docs/framework/wpf/graphics-multimedia/how-to-interactively-control-a-clock.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14425-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="14425-112">See Also</span></span>  
 [<span data-ttu-id="14425-113">ストーリーボードを使ってプロパティをアニメーション化する</span><span class="sxs-lookup"><span data-stu-id="14425-113">Animate a Property by Using a Storyboard</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)  
 [<span data-ttu-id="14425-114">ストーリーボードを使用せずにプロパティをアニメーション化する</span><span class="sxs-lookup"><span data-stu-id="14425-114">Animate a Property Without Using a Storyboard</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)  
 [<span data-ttu-id="14425-115">プロパティ アニメーションの手法の概要</span><span class="sxs-lookup"><span data-stu-id="14425-115">Property Animation Techniques Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)
