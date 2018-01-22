---
title: "方法 : アニメーションを反復する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RepeatBehavior property of timelines [WPF]
- repeating animating [WPF]
- Timelines RepeatBehavior property [WPF]
- animation [WPF], repeating
ms.assetid: e6f3b068-eeeb-47fd-8d40-8848c31f1e1e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 03ee84463bc6ce76d209d3c9fbb0455fedd9ca1a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-repeat-an-animation"></a><span data-ttu-id="8e79d-102">方法 : アニメーションを反復する</span><span class="sxs-lookup"><span data-stu-id="8e79d-102">How to: Repeat an Animation</span></span>
<span data-ttu-id="8e79d-103">この例を使用する方法を示しています、<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>のプロパティ、<xref:System.Windows.Media.Animation.Timeline>アニメーションの繰り返し動作を制御するためにします。</span><span class="sxs-lookup"><span data-stu-id="8e79d-103">This example shows how to use the <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> in order to control the repeat behavior of an animation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e79d-104">例</span><span class="sxs-lookup"><span data-stu-id="8e79d-104">Example</span></span>  
 <span data-ttu-id="8e79d-105"><xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>のプロパティ、<xref:System.Windows.Media.Animation.Timeline>アニメーションが一定時間の再生を繰り返す回数を制御します。</span><span class="sxs-lookup"><span data-stu-id="8e79d-105">The <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> controls how many times an animation repeats its simple duration.</span></span> <span data-ttu-id="8e79d-106">使用して<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>を指定することができます、<xref:System.Windows.Media.Animation.Timeline>回数だけ繰り返されます (反復カウント) か、指定された期間。</span><span class="sxs-lookup"><span data-stu-id="8e79d-106">By using <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>, you can specify that a <xref:System.Windows.Media.Animation.Timeline> repeats for a certain number of times (an iteration count) or for a specified time period.</span></span> <span data-ttu-id="8e79d-107">いずれの場合は、アニメーションは、要求されたカウントまたは期間を入力するために必要な数だけの先頭、末尾実行を通過します。</span><span class="sxs-lookup"><span data-stu-id="8e79d-107">In either case, the animation goes through as many beginning-to-end runs that it needs in order to fill the requested count or duration.</span></span>  
  
 <span data-ttu-id="8e79d-108">既定では、タイムラインは 1.0 では、これは、1 回だけ再生繰り返さないでの繰り返し回数があります。</span><span class="sxs-lookup"><span data-stu-id="8e79d-108">By default, timelines have a repeat count of 1.0, which means they play one time and do not repeat.</span></span> <span data-ttu-id="8e79d-109">ただし、設定した場合、<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>のプロパティ、<xref:System.Windows.Media.Animation.Timeline>に<xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>タイムラインを無限に繰り返します。</span><span class="sxs-lookup"><span data-stu-id="8e79d-109">However, if you set the <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> to <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, the timeline repeats indefinitely.</span></span>  
  
 <span data-ttu-id="8e79d-110">次の例を使用する方法を示しています、<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>アニメーションの繰り返し動作を制御するプロパティです。</span><span class="sxs-lookup"><span data-stu-id="8e79d-110">The following example shows how to use the <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property to control the repeat behavior of an animation.</span></span> <span data-ttu-id="8e79d-111">例では、アニメーション、<xref:System.Windows.FrameworkElement.Width%2A>さまざまな種類の繰り返し動作を使用して各四角形で 5 つの四角形のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="8e79d-111">The example animates the <xref:System.Windows.FrameworkElement.Width%2A> property of five rectangles with each rectangle using a different type of repeat behavior.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#RepeatBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/RepeatBehaviorExample.xaml#repeatbehaviorwholepage)]  
  
 <span data-ttu-id="8e79d-112">サンプル全体については、次を参照してください。[アニメーション タイミング動作サンプル](http://go.microsoft.com/fwlink/?LinkID=159970)です。</span><span class="sxs-lookup"><span data-stu-id="8e79d-112">For the complete sample, see [Animation Timing Behavior Sample](http://go.microsoft.com/fwlink/?LinkID=159970).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e79d-113">参照</span><span class="sxs-lookup"><span data-stu-id="8e79d-113">See Also</span></span>  
 [<span data-ttu-id="8e79d-114">反復サイクル中にアニメーション値を累積する</span><span class="sxs-lookup"><span data-stu-id="8e79d-114">Accumulate Animation Values During Repeat Cycles</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-accumulate-animation-values-during-repeat-cycles.md)  
 [<span data-ttu-id="8e79d-115">タイムラインを自動的に反転するかどうかを指定する</span><span class="sxs-lookup"><span data-stu-id="8e79d-115">Specify Whether a Timeline Automatically Reverses</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-whether-a-timeline-automatically-reverses.md)  
 [<span data-ttu-id="8e79d-116">方法トピック</span><span class="sxs-lookup"><span data-stu-id="8e79d-116">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)  
 [<span data-ttu-id="8e79d-117">アニメーションおよびタイミング</span><span class="sxs-lookup"><span data-stu-id="8e79d-117">Animation and Timing</span></span>](http://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [<span data-ttu-id="8e79d-118">アニメーションの概要</span><span class="sxs-lookup"><span data-stu-id="8e79d-118">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="8e79d-119">アニメーションのタイミング動作のサンプル</span><span class="sxs-lookup"><span data-stu-id="8e79d-119">Animation Timing Behavior Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=159970)
