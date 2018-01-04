---
title: "方法 : 子タイムラインを使用してアニメーションを簡素化する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- simplifying animations by child timelines [WPF]
- animation [WPF], simplifying by child timelines
- child timelines [WPF]
ms.assetid: 8335d770-d13d-42bd-8dfa-63f92c0327e2
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0d3b8f1ca1dbf7ba5452acffc62fdf0b655c9c12
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-simplify-animations-by-using-child-timelines"></a><span data-ttu-id="fd50a-102">方法 : 子タイムラインを使用してアニメーションを簡素化する</span><span class="sxs-lookup"><span data-stu-id="fd50a-102">How to: Simplify Animations by Using Child Timelines</span></span>
<span data-ttu-id="fd50a-103">この例は、子を使用して、アニメーションを簡略化する方法を示しています。<xref:System.Windows.Media.Animation.ParallelTimeline>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="fd50a-103">This example shows how to simplify animations by using child <xref:System.Windows.Media.Animation.ParallelTimeline> objects.</span></span> <span data-ttu-id="fd50a-104">A<xref:System.Windows.Media.Animation.Storyboard>の種類は、<xref:System.Windows.Media.Animation.Timeline>が含まれているタイムラインの対象とする情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="fd50a-104">A <xref:System.Windows.Media.Animation.Storyboard> is a type of <xref:System.Windows.Media.Animation.Timeline> that provides targeting information for the timelines it contains.</span></span> <span data-ttu-id="fd50a-105">使用して、<xref:System.Windows.Media.Animation.Storyboard>オブジェクトとプロパティの情報などの情報を対象とするタイムラインを提供します。</span><span class="sxs-lookup"><span data-stu-id="fd50a-105">Use a <xref:System.Windows.Media.Animation.Storyboard> to provide timeline targeting information, including object and property information.</span></span>  
  
 <span data-ttu-id="fd50a-106">アニメーションを開始するには、1 つまたは複数を使用して<xref:System.Windows.Media.Animation.ParallelTimeline>オブジェクトの入れ子になった子要素として、<xref:System.Windows.Media.Animation.Storyboard>です。</span><span class="sxs-lookup"><span data-stu-id="fd50a-106">To begin an animation, use one or more <xref:System.Windows.Media.Animation.ParallelTimeline> objects as nested child elements of a <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="fd50a-107">これら<xref:System.Windows.Media.Animation.ParallelTimeline>オブジェクトが他のアニメーションを含めることができ、そのためよりをカプセル化できる複雑なアニメーションのタイミング シーケンス。</span><span class="sxs-lookup"><span data-stu-id="fd50a-107">These <xref:System.Windows.Media.Animation.ParallelTimeline> objects can contain other animations and therefore, can better encapsulate the timing sequences in complex animations.</span></span> <span data-ttu-id="fd50a-108">アニメーションする場合など、<xref:System.Windows.Controls.TextBlock>と同じいくつかの図形<xref:System.Windows.Media.Animation.Storyboard>のアニメーションを分離することができます、<xref:System.Windows.Controls.TextBlock>とそれぞれ個別に配置すること、図形<xref:System.Windows.Media.Animation.ParallelTimeline>です。</span><span class="sxs-lookup"><span data-stu-id="fd50a-108">For example, if you are animating a <xref:System.Windows.Controls.TextBlock> and several shapes in the same <xref:System.Windows.Media.Animation.Storyboard>, you can separate the animations for the <xref:System.Windows.Controls.TextBlock> and the shapes, putting each into a separate <xref:System.Windows.Media.Animation.ParallelTimeline>.</span></span> <span data-ttu-id="fd50a-109">各<xref:System.Windows.Media.Animation.ParallelTimeline>で独自<xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>とのすべての子要素、<xref:System.Windows.Media.Animation.ParallelTimeline>基準としたこの開始<xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>タイミングより適切にカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="fd50a-109">Because each <xref:System.Windows.Media.Animation.ParallelTimeline> has its own <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> and all child elements of the <xref:System.Windows.Media.Animation.ParallelTimeline> begin relative to this <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>, timing is better encapsulated.</span></span>  
  
 <span data-ttu-id="fd50a-110">次の例では、2 つのテキスト (<xref:System.Windows.Controls.TextBlock>オブジェクト) から同じ<xref:System.Windows.Media.Animation.Storyboard>です。</span><span class="sxs-lookup"><span data-stu-id="fd50a-110">The following example animates two pieces of text (<xref:System.Windows.Controls.TextBlock> objects) from within the same <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="fd50a-111">A<xref:System.Windows.Media.Animation.ParallelTimeline>のいずれかのアニメーションをカプセル化、<xref:System.Windows.Controls.TextBlock>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="fd50a-111">A <xref:System.Windows.Media.Animation.ParallelTimeline> encapsulates the animations of one of the <xref:System.Windows.Controls.TextBlock> objects.</span></span>  
  
 <span data-ttu-id="fd50a-112">**パフォーマンスに関するメモ:**入れ子にすることが<xref:System.Windows.Media.Animation.Storyboard>、互いに内部タイムライン<xref:System.Windows.Media.Animation.ParallelTimeline>s はオーバーヘッドが少なくて済みますが要求されるために入れ子に適してします。</span><span class="sxs-lookup"><span data-stu-id="fd50a-112">**Performance Note:** Although you can nest <xref:System.Windows.Media.Animation.Storyboard> timelines inside each other, <xref:System.Windows.Media.Animation.ParallelTimeline>s are more suitable for nesting because they require less overhead.</span></span> <span data-ttu-id="fd50a-113">(、<xref:System.Windows.Media.Animation.Storyboard>クラスから継承、<xref:System.Windows.Media.Animation.ParallelTimeline>クラスです)。</span><span class="sxs-lookup"><span data-stu-id="fd50a-113">(The <xref:System.Windows.Media.Animation.Storyboard> class inherits from the <xref:System.Windows.Media.Animation.ParallelTimeline> class.)</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd50a-114">例</span><span class="sxs-lookup"><span data-stu-id="fd50a-114">Example</span></span>  
 [!code-xaml[Timelines_snip#ParallelTimelineWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Timelines_snip/CS/ParallelTimelineExample.xaml#paralleltimelinewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="fd50a-115">参照</span><span class="sxs-lookup"><span data-stu-id="fd50a-115">See Also</span></span>  
 [<span data-ttu-id="fd50a-116">アニメーションの概要</span><span class="sxs-lookup"><span data-stu-id="fd50a-116">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="fd50a-117">ストーリーボード アニメーション間で HandoffBehavior を指定する</span><span class="sxs-lookup"><span data-stu-id="fd50a-117">Specify HandoffBehavior Between Storyboard Animations</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-handoffbehavior-between-storyboard-animations.md)
