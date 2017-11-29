---
title: "制限事項の Windows フォームの Timer コンポーネント &#39; s 間隔プロパティ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- timers [Windows Forms], event intervals
- Interval property [Windows Forms], limitations
- timers [Windows Forms], Windows-based
- Timer component [Windows Forms], limitations of Interval property
ms.assetid: 7e5fb513-77e7-4046-a8e8-aab94e61ca0f
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 72af16b7dcb7709dd132a3748a454eda57acc168
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="limitations-of-the-windows-forms-timer-component39s-interval-property"></a><span data-ttu-id="672ea-102">制限事項の Windows フォームの Timer コンポーネント &#39; s 間隔プロパティ</span><span class="sxs-lookup"><span data-stu-id="672ea-102">Limitations of the Windows Forms Timer Component&#39;s Interval Property</span></span>
<span data-ttu-id="672ea-103">Windows フォーム<xref:System.Windows.Forms.Timer>コンポーネントには、<xref:System.Windows.Forms.Timer.Interval%2A>と次の 1 つのタイマー イベント間で渡されるミリ秒数を指定するプロパティです。</span><span class="sxs-lookup"><span data-stu-id="672ea-103">The Windows Forms <xref:System.Windows.Forms.Timer> component has an <xref:System.Windows.Forms.Timer.Interval%2A> property that specifies the number of milliseconds that pass between one timer event and the next.</span></span> <span data-ttu-id="672ea-104">タイマーは引き続き受信コンポーネントが無効にしない限り、<xref:System.Windows.Forms.Timer.Tick>ほぼ一定時間の間隔でイベント。</span><span class="sxs-lookup"><span data-stu-id="672ea-104">Unless the component is disabled, a timer continues to receive the <xref:System.Windows.Forms.Timer.Tick> event at roughly equal intervals of time.</span></span>  
  
 <span data-ttu-id="672ea-105">このコンポーネントは、Windows フォームの環境用に設計されています。</span><span class="sxs-lookup"><span data-stu-id="672ea-105">This component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="672ea-106">サーバー環境に適したタイマーが必要な場合は、「[サーバー ベースのタイマーの概要](http://msdn.microsoft.com/en-us/adc0bc0a-a519-4812-bafc-fb9d1a5801fc)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="672ea-106">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](http://msdn.microsoft.com/en-us/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).</span></span>  
  
## <a name="the-interval-property"></a><span data-ttu-id="672ea-107">間隔のプロパティ</span><span class="sxs-lookup"><span data-stu-id="672ea-107">The Interval Property</span></span>  
 <span data-ttu-id="672ea-108"><xref:System.Windows.Forms.Timer.Interval%2A>プロパティがプログラミングしているときに考慮すべきいくつかの制限、<xref:System.Windows.Forms.Timer>コンポーネント。</span><span class="sxs-lookup"><span data-stu-id="672ea-108">The <xref:System.Windows.Forms.Timer.Interval%2A> property has a few limitations to consider when you are programming a <xref:System.Windows.Forms.Timer> component:</span></span>  
  
-   <span data-ttu-id="672ea-109">アプリケーションまたは別のアプリケーションで、システムで重い負荷が早い場合 — 長いループや複雑な計算、またはドライブ、ネットワーク、またはポートへのアクセスなど、アプリケーションとしてのタイマー イベントを頻繁に利用できない、<xref:System.Windows.Forms.Timer.Interval%2A>プロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="672ea-109">If your application or another application is making heavy demands on the system — such as long loops, intensive calculations, or drive, network, or port access — your application may not get timer events as often as the <xref:System.Windows.Forms.Timer.Interval%2A> property specifies.</span></span>  
  
-   <span data-ttu-id="672ea-110">間隔は、正確に時間の経過時間は保証されません。</span><span class="sxs-lookup"><span data-stu-id="672ea-110">The interval is not guaranteed to elapse exactly on time.</span></span> <span data-ttu-id="672ea-111">精度を保証するには、タイマー必要があります、必要に応じて、システム クロックのチェックではなく保持の累積時間を内部的にしようとしています。</span><span class="sxs-lookup"><span data-stu-id="672ea-111">To ensure accuracy, the timer should check the system clock as needed, rather than try to keep track of accumulated time internally.</span></span>  
  
-   <span data-ttu-id="672ea-112">有効桁数、<xref:System.Windows.Forms.Timer.Interval%2A>プロパティは、(ミリ秒単位)。</span><span class="sxs-lookup"><span data-stu-id="672ea-112">The precision of the <xref:System.Windows.Forms.Timer.Interval%2A> property is in milliseconds.</span></span> <span data-ttu-id="672ea-113">一部のコンピューターでは、ミリ秒単位より高い解像度が高解像度カウンターを提供します。</span><span class="sxs-lookup"><span data-stu-id="672ea-113">Some computers provide a high-resolution counter that has a resolution higher than milliseconds.</span></span> <span data-ttu-id="672ea-114">このようなカウンターの可用性は、コンピューターのプロセッサ ハードウェアに依存します。</span><span class="sxs-lookup"><span data-stu-id="672ea-114">The availability of such a counter depends on the processor hardware of your computer.</span></span> <span data-ttu-id="672ea-115">詳細については、172338、「どのように使用 QueryPerformanceCounter に時間コードへ、」http://support.microsoft.com にで、Microsoft サポート技術情報の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="672ea-115">For more information, see article 172338, "How To Use QueryPerformanceCounter to Time Code," in the Microsoft Knowledge Base at http://support.microsoft.com.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="672ea-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="672ea-116">See Also</span></span>  
 <xref:System.Windows.Forms.Timer>  
 [<span data-ttu-id="672ea-117">Timer コンポーネント</span><span class="sxs-lookup"><span data-stu-id="672ea-117">Timer Component</span></span>](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)  
 [<span data-ttu-id="672ea-118">Timer コンポーネントの概要</span><span class="sxs-lookup"><span data-stu-id="672ea-118">Timer Component Overview</span></span>](../../../../docs/framework/winforms/controls/timer-component-overview-windows-forms.md)
