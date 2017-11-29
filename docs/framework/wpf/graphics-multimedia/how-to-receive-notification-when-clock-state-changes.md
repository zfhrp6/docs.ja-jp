---
title: "方法: 通知を受け取るときに、クロック &#39; s 状態の変更"
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
- clocks [WPF], notification of state changes
- notifications [WPF], clocks' state changes
ms.assetid: ecb10fc9-d0c2-45c3-b0a1-7b11baa733da
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f59fddb1add29d52ccba6fc8b8ce84938b53a1c2
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-receive-notification-when-a-clock39s-state-changes"></a><span data-ttu-id="307fb-102">方法: 通知を受け取るときに、クロック &#39; s 状態の変更</span><span class="sxs-lookup"><span data-stu-id="307fb-102">How to: Receive Notification When a Clock&#39;s State Changes</span></span>
<span data-ttu-id="307fb-103">クロックの<xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated>イベントが発生したときにその<xref:System.Windows.Media.Animation.Clock.CurrentState%2A>時計が開始または停止するなど、無効になります。</span><span class="sxs-lookup"><span data-stu-id="307fb-103">A clock's <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> event occurs when its <xref:System.Windows.Media.Animation.Clock.CurrentState%2A> becomes invalid, such as when the clock starts or stops.</span></span> <span data-ttu-id="307fb-104">このイベントを使用して直接の登録することができます、 <xref:System.Windows.Media.Animation.Clock>、またはを使用して登録することができます、<xref:System.Windows.Media.Animation.Timeline>です。</span><span class="sxs-lookup"><span data-stu-id="307fb-104">You can register for this event with directly using a <xref:System.Windows.Media.Animation.Clock>, or you can register using a <xref:System.Windows.Media.Animation.Timeline>.</span></span>  
  
 <span data-ttu-id="307fb-105">次の例で、<xref:System.Windows.Media.Animation.Storyboard>と 2 つ<xref:System.Windows.Media.Animation.DoubleAnimation>オブジェクトは 2 つの四角形の幅をアニメーション化するために使用します。</span><span class="sxs-lookup"><span data-stu-id="307fb-105">In the following example, a <xref:System.Windows.Media.Animation.Storyboard> and two <xref:System.Windows.Media.Animation.DoubleAnimation> objects are used to animate the width of two rectangles.</span></span> <span data-ttu-id="307fb-106"><xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated>クロック状態の変更をリッスンするようにイベントを使用します。</span><span class="sxs-lookup"><span data-stu-id="307fb-106">The <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> event is used to listen for clock state changes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="307fb-107">例</span><span class="sxs-lookup"><span data-stu-id="307fb-107">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#_graphicsmm_StateExampleMarkupWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StateExample.xaml#_graphicsmm_stateexamplemarkupwholepage)]  
  
 [!code-csharp[timingbehaviors_snip#_graphicsmm_StateEventHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StateExample.xaml.cs#_graphicsmm_stateeventhandlers)]
 [!code-vb[timingbehaviors_snip#_graphicsmm_StateEventHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/stateexample.xaml.vb#_graphicsmm_stateeventhandlers)]  
  
 <span data-ttu-id="307fb-108">次の図は、さまざまな状態、アニメーションは、親タイムラインを入力してください (*ストーリー ボード*) が進行します。</span><span class="sxs-lookup"><span data-stu-id="307fb-108">The following illustration shows the different states the animations enter as the parent timeline (*Storyboard*) progresses.</span></span>  
  
 <span data-ttu-id="307fb-109">![2 つのアニメーションのあるストーリー ボードの状態をクロック](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-3timelines.png "graphicsmm_3timelines")</span><span class="sxs-lookup"><span data-stu-id="307fb-109">![Clock states for a Storyboard with two animations](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-3timelines.png "graphicsmm_3timelines")</span></span>  
  
 <span data-ttu-id="307fb-110">次の表は、ある時刻を示します*Animation1*の<xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated>イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="307fb-110">The following table shows the times at which *Animation1*'s <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> event fires:</span></span>  
  
||||||||  
|-|-|-|-|-|-|-|  
|<span data-ttu-id="307fb-111">時間 (秒)</span><span class="sxs-lookup"><span data-stu-id="307fb-111">Time (Seconds)</span></span>|<span data-ttu-id="307fb-112">1</span><span class="sxs-lookup"><span data-stu-id="307fb-112">1</span></span>|<span data-ttu-id="307fb-113">10</span><span class="sxs-lookup"><span data-stu-id="307fb-113">10</span></span>|<span data-ttu-id="307fb-114">19</span><span class="sxs-lookup"><span data-stu-id="307fb-114">19</span></span>|<span data-ttu-id="307fb-115">21</span><span class="sxs-lookup"><span data-stu-id="307fb-115">21</span></span>|<span data-ttu-id="307fb-116">30</span><span class="sxs-lookup"><span data-stu-id="307fb-116">30</span></span>|<span data-ttu-id="307fb-117">39</span><span class="sxs-lookup"><span data-stu-id="307fb-117">39</span></span>|  
|<span data-ttu-id="307fb-118">状態</span><span class="sxs-lookup"><span data-stu-id="307fb-118">State</span></span>|<span data-ttu-id="307fb-119">アクティブ</span><span class="sxs-lookup"><span data-stu-id="307fb-119">Active</span></span>|<span data-ttu-id="307fb-120">アクティブ</span><span class="sxs-lookup"><span data-stu-id="307fb-120">Active</span></span>|<span data-ttu-id="307fb-121">停止</span><span class="sxs-lookup"><span data-stu-id="307fb-121">Stopped</span></span>|<span data-ttu-id="307fb-122">アクティブ</span><span class="sxs-lookup"><span data-stu-id="307fb-122">Active</span></span>|<span data-ttu-id="307fb-123">アクティブ</span><span class="sxs-lookup"><span data-stu-id="307fb-123">Active</span></span>|<span data-ttu-id="307fb-124">停止</span><span class="sxs-lookup"><span data-stu-id="307fb-124">Stopped</span></span>|  
  
 <span data-ttu-id="307fb-125">次の表は、ある時刻を示します*Animation2*の<xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated>イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="307fb-125">The following table shows the times at which *Animation2*'s <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> event fires:</span></span>  
  
||||||||||  
|-|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="307fb-126">時間 (秒)</span><span class="sxs-lookup"><span data-stu-id="307fb-126">Time (Seconds)</span></span>|<span data-ttu-id="307fb-127">1</span><span class="sxs-lookup"><span data-stu-id="307fb-127">1</span></span>|<span data-ttu-id="307fb-128">9</span><span class="sxs-lookup"><span data-stu-id="307fb-128">9</span></span>|<span data-ttu-id="307fb-129">11</span><span class="sxs-lookup"><span data-stu-id="307fb-129">11</span></span>|<span data-ttu-id="307fb-130">19</span><span class="sxs-lookup"><span data-stu-id="307fb-130">19</span></span>|<span data-ttu-id="307fb-131">21</span><span class="sxs-lookup"><span data-stu-id="307fb-131">21</span></span>|<span data-ttu-id="307fb-132">29</span><span class="sxs-lookup"><span data-stu-id="307fb-132">29</span></span>|<span data-ttu-id="307fb-133">31</span><span class="sxs-lookup"><span data-stu-id="307fb-133">31</span></span>|<span data-ttu-id="307fb-134">39</span><span class="sxs-lookup"><span data-stu-id="307fb-134">39</span></span>|  
|<span data-ttu-id="307fb-135">状態</span><span class="sxs-lookup"><span data-stu-id="307fb-135">State</span></span>|<span data-ttu-id="307fb-136">アクティブ</span><span class="sxs-lookup"><span data-stu-id="307fb-136">Active</span></span>|<span data-ttu-id="307fb-137">いっぱいになります。</span><span class="sxs-lookup"><span data-stu-id="307fb-137">Filling</span></span>|<span data-ttu-id="307fb-138">アクティブ</span><span class="sxs-lookup"><span data-stu-id="307fb-138">Active</span></span>|<span data-ttu-id="307fb-139">停止</span><span class="sxs-lookup"><span data-stu-id="307fb-139">Stopped</span></span>|<span data-ttu-id="307fb-140">アクティブ</span><span class="sxs-lookup"><span data-stu-id="307fb-140">Active</span></span>|<span data-ttu-id="307fb-141">いっぱいになります。</span><span class="sxs-lookup"><span data-stu-id="307fb-141">Filling</span></span>|<span data-ttu-id="307fb-142">アクティブ</span><span class="sxs-lookup"><span data-stu-id="307fb-142">Active</span></span>|<span data-ttu-id="307fb-143">停止</span><span class="sxs-lookup"><span data-stu-id="307fb-143">Stopped</span></span>|  
  
 <span data-ttu-id="307fb-144">注意して*Animation1*の<xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated>場合でも、その状態のまま 10 秒間にイベントが発生した<xref:System.Windows.Media.Animation.ClockState.Active>です。</span><span class="sxs-lookup"><span data-stu-id="307fb-144">Notice that *Animation1*'s  <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> event fires at 10 seconds, even though its state remains <xref:System.Windows.Media.Animation.ClockState.Active>.</span></span> <span data-ttu-id="307fb-145">変更が、10 秒間にその状態が変更されたためにである<xref:System.Windows.Media.Animation.ClockState.Active>に<xref:System.Windows.Media.Animation.ClockState.Filling>に戻ると<xref:System.Windows.Media.Animation.ClockState.Active>同じティックでします。</span><span class="sxs-lookup"><span data-stu-id="307fb-145">That's because its state changed at 10 seconds, but it changed from <xref:System.Windows.Media.Animation.ClockState.Active> to <xref:System.Windows.Media.Animation.ClockState.Filling> and then back to <xref:System.Windows.Media.Animation.ClockState.Active> in the same tick.</span></span>
