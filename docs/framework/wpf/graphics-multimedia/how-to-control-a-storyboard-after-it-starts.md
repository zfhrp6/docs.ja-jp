---
title: "方法 : ストーリーボードを開始後に制御する"
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
helpviewer_keywords: Storyboards [WPF], controlling after start
ms.assetid: 040f13f0-69f9-4ab5-be2b-079f4f80c7c0
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b28cdf3b653925a5856c0bc9def5aebb9fdc6c14
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-control-a-storyboard-after-it-starts"></a><span data-ttu-id="54e90-102">方法 : ストーリーボードを開始後に制御する</span><span class="sxs-lookup"><span data-stu-id="54e90-102">How to: Control a Storyboard After It Starts</span></span>
<span data-ttu-id="54e90-103">この例では、コントロールにコードを使用して、<xref:System.Windows.Media.Animation.Storyboard>開始後にします。</span><span class="sxs-lookup"><span data-stu-id="54e90-103">This example shows how to use code to control a <xref:System.Windows.Media.Animation.Storyboard> after it has started.</span></span> <span data-ttu-id="54e90-104">ストーリー ボードを制御[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を使用して<xref:System.Windows.Trigger>と<xref:System.Windows.TriggerAction>オブジェクトです。 例については、次を参照してください。[起動を制御、ストーリー ボードの後に、イベント トリガーを使用して](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)です。</span><span class="sxs-lookup"><span data-stu-id="54e90-104">To control a storyboard in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use <xref:System.Windows.Trigger> and <xref:System.Windows.TriggerAction> objects; for an example, see [Use Event Triggers to Control a Storyboard After It Starts](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span></span>  
  
 <span data-ttu-id="54e90-105">使用するストーリー ボードを開始するには、その<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>ストーリー ボードのアニメーションをアニメーション化し、ストーリーのプロパティを配信するメソッド。</span><span class="sxs-lookup"><span data-stu-id="54e90-105">To start a storyboard, you use its <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method, which distributes the storyboard's animations to the properties they animate and starts the storyboard.</span></span>  
  
 <span data-ttu-id="54e90-106">ストーリー ボードを制御するためには、使用する、<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>メソッドを指定して**true** 2 番目のパラメーターとして。</span><span class="sxs-lookup"><span data-stu-id="54e90-106">To make a storyboard controllable, you use the <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method and specify **true** as the second parameter.</span></span> <span data-ttu-id="54e90-107">一時停止、再開、シーク、停止、速度が上がり、または、ストーリー ボードの速度が低下または塗りつぶし期間に進めることにし、ストーリー ボードの対話型のメソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="54e90-107">You can then use the storyboard's interactive methods to pause, resume, seek, stop, speed up, or slow down the storyboard, or advance it to its fill period.</span></span> <span data-ttu-id="54e90-108">ストーリー ボードの対話型のメソッドの一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="54e90-108">The following is a list of the storyboard's interactive methods:</span></span>  
  
-   <span data-ttu-id="54e90-109"><xref:System.Windows.Media.Animation.Storyboard.Pause%2A>: ストーリー ボードを一時停止します。</span><span class="sxs-lookup"><span data-stu-id="54e90-109"><xref:System.Windows.Media.Animation.Storyboard.Pause%2A>: Pauses the storyboard.</span></span>  
  
-   <span data-ttu-id="54e90-110"><xref:System.Windows.Media.Animation.Storyboard.Resume%2A>: 一時停止しているストーリー ボードを再開します。</span><span class="sxs-lookup"><span data-stu-id="54e90-110"><xref:System.Windows.Media.Animation.Storyboard.Resume%2A>: Resumes a paused storyboard.</span></span>  
  
-   <span data-ttu-id="54e90-111"><xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A>: ストーリー ボードの対話速度を設定します。</span><span class="sxs-lookup"><span data-stu-id="54e90-111"><xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A>: Sets the storyboard's interactive speed.</span></span>  
  
-   <span data-ttu-id="54e90-112"><xref:System.Windows.Media.Animation.Storyboard.Seek%2A>: ストーリー ボードの指定した位置をシークします。</span><span class="sxs-lookup"><span data-stu-id="54e90-112"><xref:System.Windows.Media.Animation.Storyboard.Seek%2A>: Seeks the storyboard the specified location.</span></span>  
  
-   <span data-ttu-id="54e90-113"><xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A>: 指定した場所にストーリー ボードを目指しています。</span><span class="sxs-lookup"><span data-stu-id="54e90-113"><xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A>: Seeks the storyboard to the specified location.</span></span> <span data-ttu-id="54e90-114">異なり、<xref:System.Windows.Media.Animation.Storyboard.Seek%2A>メソッド、この操作は次のタイマー刻みの前に処理します。</span><span class="sxs-lookup"><span data-stu-id="54e90-114">Unlike the <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> method, this operation is processed before the next tick.</span></span>  
  
-   <span data-ttu-id="54e90-115"><xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>: 1 つがある場合は、その保留期間をストーリー ボードを進めます。</span><span class="sxs-lookup"><span data-stu-id="54e90-115"><xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>: Advances the storyboard to its fill period, if it has one.</span></span>  
  
-   <span data-ttu-id="54e90-116"><xref:System.Windows.Media.Animation.Storyboard.Stop%2A>: ストーリー ボードを停止します。</span><span class="sxs-lookup"><span data-stu-id="54e90-116"><xref:System.Windows.Media.Animation.Storyboard.Stop%2A>: Stops the storyboard.</span></span>  
  
 <span data-ttu-id="54e90-117">次の例では、いくつかのストーリー ボード メソッドは、ストーリー ボードを対話的に制御に使用されます。</span><span class="sxs-lookup"><span data-stu-id="54e90-117">In the following example, several storyboard methods are used to interactively control a storyboard.</span></span>  
  
 <span data-ttu-id="54e90-118">**注:**でトリガーを使用したストーリー ボードを制御する例を参照する[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を参照してください[イベント トリガーを使用して、ストーリー ボードの後に開始を制御する](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)です。</span><span class="sxs-lookup"><span data-stu-id="54e90-118">**Note:** To see an example of controlling a storyboard using triggers with [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], see [Use Event Triggers to Control a Storyboard After It Starts](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="54e90-119">例</span><span class="sxs-lookup"><span data-stu-id="54e90-119">Example</span></span>  
 [!code-csharp[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ControlStoryboardExample.cs#controlstoryboardexampleusingwholepage)]
 [!code-vb[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/controlstoryboardexample.vb#controlstoryboardexampleusingwholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="54e90-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="54e90-120">See Also</span></span>  
 [<span data-ttu-id="54e90-121">開始後のストーリーボードをイベント トリガーを使用して制御する</span><span class="sxs-lookup"><span data-stu-id="54e90-121">Use Event Triggers to Control a Storyboard After It Starts</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)
