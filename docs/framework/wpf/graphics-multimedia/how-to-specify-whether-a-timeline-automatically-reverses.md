---
title: "方法 : タイムラインを自動的に反転するかどうかを指定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- AutoReverse property of timelines [WPF]
- Timelines [WPF], AutoReverse property
ms.assetid: 1648dd90-1bee-409a-ac69-ac729867f557
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2abce54905f0bb06bf983c065e064ce2dfeba932
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-specify-whether-a-timeline-automatically-reverses"></a><span data-ttu-id="eb687-102">方法 : タイムラインを自動的に反転するかどうかを指定する</span><span class="sxs-lookup"><span data-stu-id="eb687-102">How to: Specify Whether a Timeline Automatically Reverses</span></span>
<span data-ttu-id="eb687-103">タイムラインの<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>プロパティは、順方向の反復の完了後に逆方向に再生するかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="eb687-103">A timeline's <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> property determines whether it plays in reverse after it completes a forward iteration.</span></span> <span data-ttu-id="eb687-104">次の例では、同じ期間とターゲットの値ではなく、異なるいくつかのアニメーション<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>設定します。</span><span class="sxs-lookup"><span data-stu-id="eb687-104">The following example shows several animations with identical duration and target values, but with different <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> settings.</span></span> <span data-ttu-id="eb687-105">示すためにどのように<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>プロパティが異なる動作<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>を繰り返す設定、いくつかのアニメーションが設定されています。</span><span class="sxs-lookup"><span data-stu-id="eb687-105">To demonstrate how the <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> property behaves with different <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> settings, some animations are set to repeat.</span></span> <span data-ttu-id="eb687-106">最後のアニメーション表示方法、<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>プロパティの入れ子になったタイムラインで動作します。</span><span class="sxs-lookup"><span data-stu-id="eb687-106">The last animation shows how the <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> property works on nested timelines.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb687-107">例</span><span class="sxs-lookup"><span data-stu-id="eb687-107">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#AutoReverseAndRepeatBehaviorExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AutoReverseExample.xaml#autoreverseandrepeatbehaviorexamplewholepage)]
