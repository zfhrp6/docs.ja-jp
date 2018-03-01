---
title: "Timer コンポーネントの概要 (Windows フォーム)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Timer
helpviewer_keywords:
- Timer component [Windows Forms], about Timer components
- timers [Windows Forms], about timers
ms.assetid: e672c05b-a8b6-4b26-9e4d-9223aa9e3873
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 90296d2741a96e8788bf7a9b18bf3ea303ad2bae
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="timer-component-overview-windows-forms"></a><span data-ttu-id="a74b3-102">Timer コンポーネントの概要 (Windows フォーム)</span><span class="sxs-lookup"><span data-stu-id="a74b3-102">Timer Component Overview (Windows Forms)</span></span>
<span data-ttu-id="a74b3-103">Windows フォーム <xref:System.Windows.Forms.Timer> は、一定の間隔でイベントを発生させるコンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="a74b3-103">The Windows Forms <xref:System.Windows.Forms.Timer> is a component that raises an event at regular intervals.</span></span> <span data-ttu-id="a74b3-104">このコンポーネントは、Windows フォームの環境用に設計されています。</span><span class="sxs-lookup"><span data-stu-id="a74b3-104">This component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="a74b3-105">サーバー環境に適したタイマーが必要な場合は、「[サーバー ベースのタイマーの概要](http://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a74b3-105">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](http://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).</span></span>  
  
## <a name="key-properties-methods-and-events"></a><span data-ttu-id="a74b3-106">キー プロパティ、メソッド、およびイベント</span><span class="sxs-lookup"><span data-stu-id="a74b3-106">Key Properties, Methods, and Events</span></span>  
 <span data-ttu-id="a74b3-107">間隔の長さがによって定義された、<xref:System.Windows.Forms.Timer.Interval%2A>プロパティ、値を持つ単位はミリ秒です。</span><span class="sxs-lookup"><span data-stu-id="a74b3-107">The length of the intervals is defined by the <xref:System.Windows.Forms.Timer.Interval%2A> property, whose value is in milliseconds.</span></span> <span data-ttu-id="a74b3-108">コンポーネントが有効にすると、<xref:System.Windows.Forms.Timer.Tick>イベントが発生したすべての間隔。</span><span class="sxs-lookup"><span data-stu-id="a74b3-108">When the component is enabled, the <xref:System.Windows.Forms.Timer.Tick> event is raised every interval.</span></span> <span data-ttu-id="a74b3-109">これは、実行するコードを追加することです。</span><span class="sxs-lookup"><span data-stu-id="a74b3-109">This is where you would add code to be executed.</span></span> <span data-ttu-id="a74b3-110">詳細については、次を参照してください。[する方法: Windows フォームの Timer コンポーネントの設定間隔でプロシージャの実行](../../../../docs/framework/winforms/controls/run-procedures-at-set-intervals-with-wf-timer-component.md)です。</span><span class="sxs-lookup"><span data-stu-id="a74b3-110">For more information, see [How to: Run Procedures at Set Intervals with the Windows Forms Timer Component](../../../../docs/framework/winforms/controls/run-procedures-at-set-intervals-with-wf-timer-component.md).</span></span> <span data-ttu-id="a74b3-111">主要なメソッド、<xref:System.Windows.Forms.Timer>コンポーネントは<xref:System.Windows.Forms.Timer.Start%2A>と<xref:System.Windows.Forms.Timer.Stop%2A>タイマーをオンまたはオフにします。</span><span class="sxs-lookup"><span data-stu-id="a74b3-111">The key methods of the <xref:System.Windows.Forms.Timer> component are <xref:System.Windows.Forms.Timer.Start%2A> and <xref:System.Windows.Forms.Timer.Stop%2A>, which turn the timer on and off.</span></span> <span data-ttu-id="a74b3-112">タイマーをオフにすると、ときにリセットされます。一時停止する方法はありません、<xref:System.Windows.Forms.Timer>コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="a74b3-112">When the timer is switched off, it resets; there is no way to pause a <xref:System.Windows.Forms.Timer> component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a74b3-113">参照</span><span class="sxs-lookup"><span data-stu-id="a74b3-113">See Also</span></span>  
 <xref:System.Windows.Forms.Timer>  
 [<span data-ttu-id="a74b3-114">Timer コンポーネント</span><span class="sxs-lookup"><span data-stu-id="a74b3-114">Timer Component</span></span>](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)  
 [<span data-ttu-id="a74b3-115">Windows フォームの Timer コンポーネントの Interval プロパティの制限</span><span class="sxs-lookup"><span data-stu-id="a74b3-115">Limitations of the Windows Forms Timer Component's Interval Property</span></span>](../../../../docs/framework/winforms/controls/limitations-of-the-timer-component-interval-property.md)
