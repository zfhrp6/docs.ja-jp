---
title: "方法 : アクティブな期間の末尾に到達したタイムラインの FillBehavior を指定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FillBehavior property for inactive timelines [WPF]
- Timelines [WPF], FillBehavior property
ms.assetid: db805f59-d513-4dac-af15-47005dae3199
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4b890d121cf06dc377a3bbc1dc569d9dac7c011b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-specify-the-fillbehavior-for-a-timeline-that-has-reached-the-end-of-its-active-period"></a><span data-ttu-id="2e8b8-102">方法 : アクティブな期間の末尾に到達したタイムラインの FillBehavior を指定する</span><span class="sxs-lookup"><span data-stu-id="2e8b8-102">How to: Specify the FillBehavior for a Timeline that has Reached the End of Its Active Period</span></span>
<span data-ttu-id="2e8b8-103">この例を指定する方法を示しています、 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> 、非アクティブの<xref:System.Windows.Media.Animation.Timeline>アニメーション化されたプロパティのです。</span><span class="sxs-lookup"><span data-stu-id="2e8b8-103">This example shows how to specify the <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> for the inactive <xref:System.Windows.Media.Animation.Timeline> of an animated property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e8b8-104">例</span><span class="sxs-lookup"><span data-stu-id="2e8b8-104">Example</span></span>  
 <span data-ttu-id="2e8b8-105"><xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>のプロパティ、<xref:System.Windows.Media.Animation.Timeline>されていないときにアニメーション化されたプロパティの値に動作が決定されます、アニメーション化は、ときに、<xref:System.Windows.Media.Animation.Timeline>がその親がアクティブでない<xref:System.Windows.Media.Animation.Timeline>アクティブまたは保留期間。</span><span class="sxs-lookup"><span data-stu-id="2e8b8-105">The <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> determines what happens to the value of an animated property when it is not being animated, that is, when the <xref:System.Windows.Media.Animation.Timeline> is inactive but its parent <xref:System.Windows.Media.Animation.Timeline> is inside its active or hold period.</span></span> <span data-ttu-id="2e8b8-106">たとえばはアニメーション化されたプロパティのまま、最後に、アニメーションを終了またはその後の値がアニメーションの開始前に、の値に戻すか。</span><span class="sxs-lookup"><span data-stu-id="2e8b8-106">For example, does an animated property remain at its end value after the animation ends or does it revert back to the value it had before the animation started?</span></span>  
  
 <span data-ttu-id="2e8b8-107">次の例では、<xref:System.Windows.Media.Animation.DoubleAnimation>アニメーション化する、 <xref:System.Windows.FrameworkElement.Width%2A> 2 つの四角形。</span><span class="sxs-lookup"><span data-stu-id="2e8b8-107">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the <xref:System.Windows.FrameworkElement.Width%2A> of two rectangles.</span></span> <span data-ttu-id="2e8b8-108">各四角形を使用して、異なる<xref:System.Windows.Media.Animation.Timeline>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="2e8b8-108">Each rectangle uses a different <xref:System.Windows.Media.Animation.Timeline> object.</span></span>  
  
 <span data-ttu-id="2e8b8-109">1 つ<xref:System.Windows.Media.Animation.Timeline>が、<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>に設定されている<xref:System.Windows.Media.Animation.FillBehavior.Stop>、そのアニメーション化されていないに戻すに四角形の幅を停止するときの値、<xref:System.Windows.Media.Animation.Timeline>を終了します。</span><span class="sxs-lookup"><span data-stu-id="2e8b8-109">One <xref:System.Windows.Media.Animation.Timeline> has a <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> that is set to <xref:System.Windows.Media.Animation.FillBehavior.Stop>, which causes the width of the rectangle to revert back to its non-animated value when the <xref:System.Windows.Media.Animation.Timeline> ends.</span></span> <span data-ttu-id="2e8b8-110">他の<xref:System.Windows.Media.Animation.Timeline>が、<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>の<xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>、それが原因で、幅の末尾にしたままにするときの値、<xref:System.Windows.Media.Animation.Timeline>を終了します。</span><span class="sxs-lookup"><span data-stu-id="2e8b8-110">The other <xref:System.Windows.Media.Animation.Timeline> has a <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> of <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, which causes the width to remain at its end value when the <xref:System.Windows.Media.Animation.Timeline> ends.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#FillBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/FillBehaviorExample.xaml#fillbehaviorwholepage)]  
  
 <span data-ttu-id="2e8b8-111">サンプル全体については、次を参照してください。[アニメーション サンプル ギャラリー](http://go.microsoft.com/fwlink/?LinkID=159969)です。</span><span class="sxs-lookup"><span data-stu-id="2e8b8-111">For the complete sample, see [Animation Example Gallery](http://go.microsoft.com/fwlink/?LinkID=159969).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e8b8-112">参照</span><span class="sxs-lookup"><span data-stu-id="2e8b8-112">See Also</span></span>  
 <xref:System.Windows.Media.Animation.DoubleAnimation>  
 <xref:System.Windows.FrameworkElement.Width%2A>  
 <xref:System.Windows.Media.Animation.Timeline>  
 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>  
 <xref:System.Windows.Media.Animation.FillBehavior.Stop>  
 <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>  
 [<span data-ttu-id="2e8b8-113">アニメーションの概要</span><span class="sxs-lookup"><span data-stu-id="2e8b8-113">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="2e8b8-114">アニメーションおよびタイミング</span><span class="sxs-lookup"><span data-stu-id="2e8b8-114">Animation and Timing</span></span>](http://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [<span data-ttu-id="2e8b8-115">方法トピック</span><span class="sxs-lookup"><span data-stu-id="2e8b8-115">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
