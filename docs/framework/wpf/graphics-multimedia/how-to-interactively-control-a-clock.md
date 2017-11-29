---
title: "方法 : クロックを対話的に制御する"
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
- controlling clocks interactively [WPF]
- clocks [WPF], controlling interactively
ms.assetid: d0b520e0-2f18-4cef-977f-2909e709548a
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: debe65ef1587171dc2f324a19da4b43e7274c438
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-interactively-control-a-clock"></a><span data-ttu-id="5fbd6-102">方法 : クロックを対話的に制御する</span><span class="sxs-lookup"><span data-stu-id="5fbd6-102">How to: Interactively Control a Clock</span></span>
<span data-ttu-id="5fbd6-103">A<xref:System.Windows.Media.Animation.Clock>オブジェクトの<xref:System.Windows.Media.Animation.ClockController>プロパティでは、対話形式で開始、一時停止、再開、シーク、塗りつぶし期間、時計を進めるおよび時計を停止することができます。</span><span class="sxs-lookup"><span data-stu-id="5fbd6-103">A <xref:System.Windows.Media.Animation.Clock> object's <xref:System.Windows.Media.Animation.ClockController> property enables you to interactively start, pause, resume, seek, advance the clock to its fill period, and stop the clock.</span></span> <span data-ttu-id="5fbd6-104">タイミング ツリーのルート クロックのみを対話的に制御できます。</span><span class="sxs-lookup"><span data-stu-id="5fbd6-104">Only the root clock of a timing tree can be interactively controlled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5fbd6-105">クロックを直接操作することを必要としないアニメーションを対話的に制御するには、その他の方法があります: ストーリー ボードを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="5fbd6-105">There are other ways to interactively control animations that don't require you to work directly with clocks: you can also use Storyboards.</span></span> <span data-ttu-id="5fbd6-106">ストーリー ボードは、マークアップとコードの両方でサポートされます。</span><span class="sxs-lookup"><span data-stu-id="5fbd6-106">Storyboards are supported in both markup and code.</span></span> <span data-ttu-id="5fbd6-107">例については、次を参照してください。[ストーリー ボードを使用してプロパティをアニメーション化](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)または[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="5fbd6-107">For an example, see [Animate a Property by Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md) or the [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span></span>  
  
 <span data-ttu-id="5fbd6-108">次の例では、いくつかのボタンはアニメーション クロックを対話的に制御に使用されます。</span><span class="sxs-lookup"><span data-stu-id="5fbd6-108">In the following example, several buttons are used to interactively control an animation clock.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5fbd6-109">例</span><span class="sxs-lookup"><span data-stu-id="5fbd6-109">Example</span></span>  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerExample.cs#graphicsmmclockcontrollerexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerexample.vb#graphicsmmclockcontrollerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="5fbd6-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="5fbd6-110">See Also</span></span>  
 [<span data-ttu-id="5fbd6-111">ストーリーボードを使ってプロパティをアニメーション化する</span><span class="sxs-lookup"><span data-stu-id="5fbd6-111">Animate a Property by Using a Storyboard</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)  
 [<span data-ttu-id="5fbd6-112">アニメーションの概要</span><span class="sxs-lookup"><span data-stu-id="5fbd6-112">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
