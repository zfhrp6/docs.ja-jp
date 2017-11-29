---
title: "方法 : \"From\"、\"To\"、および \"By\" を使用してアニメーションを制御する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], From/to/by
- basic animation [WPF]
- animation [WPF], basic animation
- From/to/by animation
ms.assetid: 59afba57-6fc1-44c8-987e-8a5f4142adad
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: aab775ab1c2f55d79da0773f81c006015c349f8b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-control-an-animation-using-from-to-and-by"></a><span data-ttu-id="46f01-102">方法 : "From"、"To"、および "By" を使用してアニメーションを制御する</span><span class="sxs-lookup"><span data-stu-id="46f01-102">How to: Control an Animation using From, To, and By</span></span>
<span data-ttu-id="46f01-103">「から/に/される」または「基本的なアニメーション」が 2 つのターゲット値の間の遷移を作成 (を参照してください[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)アニメーションのさまざまな種類の概要について)。</span><span class="sxs-lookup"><span data-stu-id="46f01-103">A "From/To/By" or "basic animation" creates a transition between two target values (see [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) for an introduction to different types of animations).</span></span> <span data-ttu-id="46f01-104">基本的なアニメーションのターゲット値を設定するを使用してその<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>、 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>、および<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="46f01-104">To set the target values of a basic animation, use its <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, and <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> properties.</span></span>  <span data-ttu-id="46f01-105">次の表方法、 <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>、 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>、および<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>プロパティは一緒に使用される可能性がありますまたは単独で、アニメーションのターゲットを決定する値します。</span><span class="sxs-lookup"><span data-stu-id="46f01-105">The following table summarizes how the <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, and <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> properties may be used together or separately to determine an animation's target values.</span></span>  
  
|<span data-ttu-id="46f01-106">指定するプロパティ</span><span class="sxs-lookup"><span data-stu-id="46f01-106">Properties specified</span></span>|<span data-ttu-id="46f01-107">結果として生じる動作</span><span class="sxs-lookup"><span data-stu-id="46f01-107">Resulting behavior</span></span>|  
|--------------------------|------------------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>|<span data-ttu-id="46f01-108">指定された値、アニメーション、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>プロパティをアニメーション化されているプロパティのベース値または前のアニメーションの前のアニメーションの構成方法に応じて、値を出力します。</span><span class="sxs-lookup"><span data-stu-id="46f01-108">The animation progresses from the value specified by the <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> property to the base value of the property being animated or to a previous animation's output value, depending on how the previous animation is configured.</span></span>|  
|<span data-ttu-id="46f01-109"><xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> および <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A></span><span class="sxs-lookup"><span data-stu-id="46f01-109"><xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> and <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A></span></span>|<span data-ttu-id="46f01-110">指定された値、アニメーション、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>プロパティで指定された値を<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="46f01-110">The animation progresses from the value specified by the <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> property to the value specified by the <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> property.</span></span>|  
|<span data-ttu-id="46f01-111"><xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> および <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A></span><span class="sxs-lookup"><span data-stu-id="46f01-111"><xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> and <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A></span></span>|<span data-ttu-id="46f01-112">指定された値、アニメーション、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>プロパティの合計で指定された値を<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>と<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="46f01-112">The animation progresses from the value specified by the <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> property to the value specified by the sum of the <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> and <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> properties.</span></span>|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|<span data-ttu-id="46f01-113">アニメーションがアニメーション化されたプロパティの基本値から移行するか、前のアニメーションの出力値を指定する値を<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="46f01-113">The animation progresses from the animated property's base value or a previous animation's output value to the value specified by the <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> property.</span></span>|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|<span data-ttu-id="46f01-114">出力で指定された値とその値を合計する値をアニメーション化されているプロパティのベース値からアニメーション、または前のアニメーション、<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="46f01-114">The animation progresses from the base value of the property being animated or a previous animation's output value to the sum of that value and the value specified by the <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> property.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="46f01-115">両方を設定しないでください、<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>プロパティおよび<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>同じアニメーションのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="46f01-115">Do not set both the <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> property and the <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> property on the same animation.</span></span>  
  
 <span data-ttu-id="46f01-116">他の補間方式を使用したり、3 つ以上のターゲット値の間でアニメーション化したりするには、キー フレーム アニメーションを使用します。</span><span class="sxs-lookup"><span data-stu-id="46f01-116">To use other interpolation methods or animate between more than two target values, use a key frame animation.</span></span> <span data-ttu-id="46f01-117">参照してください[キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="46f01-117">See [Key-Frame Animations Overview](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md) for more information.</span></span>  
  
 <span data-ttu-id="46f01-118">1 つのプロパティを複数のアニメーションを適用する方法については、次を参照してください。[キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="46f01-118">For information about applying multiple animations to a single property, see [Key-Frame Animations Overview](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).</span></span>  
  
 <span data-ttu-id="46f01-119">次の例は、さまざまな設定の効果を示しています。 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>、 <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>、および<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>アニメーションのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="46f01-119">The example below shows the different effects of setting <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>, and <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> properties on animations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46f01-120">例</span><span class="sxs-lookup"><span data-stu-id="46f01-120">Example</span></span>  
 [!code-xaml[BasicAnimations_snippet#AnimationTargetValuesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snippet/CS/AnimationTargetValuesExample.xaml#animationtargetvalueswholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="46f01-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="46f01-121">See Also</span></span>  
 [<span data-ttu-id="46f01-122">アニメーションの概要</span><span class="sxs-lookup"><span data-stu-id="46f01-122">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="46f01-123">キー フレーム アニメーションの概要</span><span class="sxs-lookup"><span data-stu-id="46f01-123">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="46f01-124">アニメーションのターゲット値 (From、To、および By) のサンプル</span><span class="sxs-lookup"><span data-stu-id="46f01-124">From, To, and By Animation Target Values Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=159988)
