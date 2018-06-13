---
title: '方法 : タイムラインの速度を変更せずにクロックの速度を変更する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- speed of Clock [WPF], changing
- clocks [WPF], changing speed of
ms.assetid: 72f36dd0-f085-445d-8589-19a83fe74f5e
ms.openlocfilehash: 126d260fbd59c1c35d8f56be6aa7dabe7688fa32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556615"
---
# <a name="how-to-change-the-speed-of-a-clock-without-changing-the-speed-of-its-timeline"></a><span data-ttu-id="8ed5c-102">方法 : タイムラインの速度を変更せずにクロックの速度を変更する</span><span class="sxs-lookup"><span data-stu-id="8ed5c-102">How to: Change the Speed of a Clock Without Changing the Speed of Its Timeline</span></span>
<span data-ttu-id="8ed5c-103">A<xref:System.Windows.Media.Animation.ClockController>オブジェクトの<xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A>プロパティでは、速度を変更することができます、<xref:System.Windows.Media.Animation.Clock>を変更せず、<xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A>の時計の<xref:System.Windows.Media.Animation.Timeline>します。</span><span class="sxs-lookup"><span data-stu-id="8ed5c-103">A <xref:System.Windows.Media.Animation.ClockController> object's <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> property enables you to change the speed of a <xref:System.Windows.Media.Animation.Clock> without altering the <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> of the clock's <xref:System.Windows.Media.Animation.Timeline>.</span></span> <span data-ttu-id="8ed5c-104">次の例で、<xref:System.Windows.Media.Animation.ClockController>対話的に変更することは、<xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A>時計のです。</span><span class="sxs-lookup"><span data-stu-id="8ed5c-104">In the following example, a <xref:System.Windows.Media.Animation.ClockController> is used to interactively modify the <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> of a clock.</span></span> <span data-ttu-id="8ed5c-105"><xref:System.Windows.Media.Animation.Clock.CurrentGlobalSpeedInvalidated>イベントと、クロックの<xref:System.Windows.Media.Animation.Clock.CurrentGlobalSpeed%2A>プロパティは、クロックの現在のグローバル速度を表示に使用されるたびに、対話による<xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A>が変更されました。</span><span class="sxs-lookup"><span data-stu-id="8ed5c-105">The <xref:System.Windows.Media.Animation.Clock.CurrentGlobalSpeedInvalidated> event and the clock's <xref:System.Windows.Media.Animation.Clock.CurrentGlobalSpeed%2A> property are used to display the clock's current global speed each time its interactive <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> is changed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ed5c-106">例</span><span class="sxs-lookup"><span data-stu-id="8ed5c-106">Example</span></span>  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerSpeedRatioExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerSpeedRatioExample.cs#graphicsmmclockcontrollerspeedratioexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerSpeedRatioExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerspeedratioexample.vb#graphicsmmclockcontrollerspeedratioexample)]
