---
title: "方法 : ストーリーボードを使用せずにプロパティをアニメーション化する"
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
- cpp
helpviewer_keywords:
- non-Storyboard animation
- local animation [WPF]
- animation [WPF], non-Storyboard (local)
ms.assetid: d411db70-4df7-487d-82bc-95a7c1b2e7f8
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4a1292dae3a6fc7e86387ecbe3bf2b1da6912cc0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-a-property-without-using-a-storyboard"></a><span data-ttu-id="415a5-102">方法 : ストーリーボードを使用せずにプロパティをアニメーション化する</span><span class="sxs-lookup"><span data-stu-id="415a5-102">How to: Animate a Property Without Using a Storyboard</span></span>
<span data-ttu-id="415a5-103">この例を使用せず、プロパティにアニメーションを適用する方法を示しています、<xref:System.Windows.Media.Animation.Storyboard>です。</span><span class="sxs-lookup"><span data-stu-id="415a5-103">This example shows one way to apply an animation to a property without using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="415a5-104">この機能は、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] では使用できません。</span><span class="sxs-lookup"><span data-stu-id="415a5-104">This functionality is not available in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="415a5-105">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] でプロパティをアニメーション化する方法については、「[ストーリーボードを使ってプロパティをアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="415a5-105">For information about animating a property in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], see [Animate a Property by Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md).</span></span>  
  
 <span data-ttu-id="415a5-106">適用するには、ローカルのアニメーション プロパティを使用して、<xref:System.Windows.UIElement.BeginAnimation%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="415a5-106">To apply a local animation to a property, use the <xref:System.Windows.UIElement.BeginAnimation%2A> method.</span></span> <span data-ttu-id="415a5-107">このメソッドは、2 つのパラメーター: <xref:System.Windows.DependencyProperty> 、アニメーション化するプロパティとそのプロパティに適用するアニメーションを指定します。</span><span class="sxs-lookup"><span data-stu-id="415a5-107">This method takes two parameters: a <xref:System.Windows.DependencyProperty> that specifies the property to animate, and the animation to apply to that property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="415a5-108">例</span><span class="sxs-lookup"><span data-stu-id="415a5-108">Example</span></span>  
 <span data-ttu-id="415a5-109">次の例の幅と背景色をアニメーション化する方法を示しています、<xref:System.Windows.Controls.Button>です。</span><span class="sxs-lookup"><span data-stu-id="415a5-109">The following example shows how to animate the width and background color of a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-cpp[animateproperty#11](../../../../samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
 <span data-ttu-id="415a5-110">アニメーションのクラスのさまざまな、<xref:System.Windows.Media.Animation>さまざまな種類のプロパティをアニメーション化する名前空間が存在します。</span><span class="sxs-lookup"><span data-stu-id="415a5-110">A variety of animation classes in the <xref:System.Windows.Media.Animation> namespace exist for animating different types of properties.</span></span> <span data-ttu-id="415a5-111">プロパティのアニメーション化の詳細については、「[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="415a5-111">For more information about animating properties, see [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span></span> <span data-ttu-id="415a5-112">依存関係プロパティ (これらの例に示されているプロパティの種類) とその機能の詳細については、「[依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="415a5-112">For more information about dependency properties (the type of properties that are shown in these examples) and their features, see [Dependency Properties Overview](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).</span></span>  
  
 <span data-ttu-id="415a5-113">使用せずにアニメーション化するには、その他の方法がある<xref:System.Windows.Media.Animation.Storyboard>オブジェクトです。 詳細については、次を参照してください。[プロパティ アニメーションの技術概要](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="415a5-113">There are other ways to animate without using <xref:System.Windows.Media.Animation.Storyboard> objects; for more information, see [Property Animation Techniques Overview](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="415a5-114">参照</span><span class="sxs-lookup"><span data-stu-id="415a5-114">See Also</span></span>  
 <xref:System.Windows.Media.Animation.AnimationTimeline>  
 <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>  
 <xref:System.Windows.Media.Animation>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 [<span data-ttu-id="415a5-115">プロパティ アニメーションの手法の概要</span><span class="sxs-lookup"><span data-stu-id="415a5-115">Property Animation Techniques Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)  
 [<span data-ttu-id="415a5-116">アニメーションの概要</span><span class="sxs-lookup"><span data-stu-id="415a5-116">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
