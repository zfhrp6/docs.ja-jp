---
title: "タイマー"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [.NET Framework], timers
- timers, about timers
ms.assetid: 7091500d-be18-499b-a942-95366ce185e5
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 80b4cee03e934d3aec98ca323aac43f934c56455
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="timers"></a><span data-ttu-id="ce89f-102">タイマー</span><span class="sxs-lookup"><span data-stu-id="ce89f-102">Timers</span></span>
<span data-ttu-id="ce89f-103">タイマーとは、指定時刻に指定のデリゲートを呼び出す軽量オブジェクトのことです。</span><span class="sxs-lookup"><span data-stu-id="ce89f-103">Timers are lightweight objects that enable you to specify a delegate to be called at a specified time.</span></span> <span data-ttu-id="ce89f-104">スレッド プール内の 1 つのスレッドが、待機操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="ce89f-104">A thread in the thread pool performs the wait operation.</span></span>  
  
 <span data-ttu-id="ce89f-105"><xref:System.Threading.Timer?displayProperty=nameWithType> クラスの使用法は単純です。</span><span class="sxs-lookup"><span data-stu-id="ce89f-105">Using the <xref:System.Threading.Timer?displayProperty=nameWithType> class is straightforward.</span></span> <span data-ttu-id="ce89f-106">**Timer** を作成するには、コールバック メソッドへの <xref:System.Threading.TimerCallback> デリゲート、コールバックに渡される状態を表すオブジェクト、最初に発生する時間、コールバック呼び出しの間隔を表す時間を渡します。</span><span class="sxs-lookup"><span data-stu-id="ce89f-106">You create a **Timer**, passing a <xref:System.Threading.TimerCallback> delegate to the callback method, an object representing state that will be passed to the callback, an initial raise time, and a time representing the period between callback invocations.</span></span> <span data-ttu-id="ce89f-107">保留中のタイマーを取り消すには、**Timer.Dispose** 関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="ce89f-107">To cancel a pending timer, call the **Timer.Dispose** function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ce89f-108">他にも 2 つのタイマー クラスがあります。</span><span class="sxs-lookup"><span data-stu-id="ce89f-108">There are two other timer classes.</span></span> <span data-ttu-id="ce89f-109"><xref:System.Windows.Forms.Timer?displayProperty=nameWithType> クラスは、ビジュアルなデザイナーを操作するコントロールで、ユーザー インターフェイスのコンテキストで使用するように設計されています。このクラスは、ユーザー インターフェイス スレッドでイベントを発生させます。</span><span class="sxs-lookup"><span data-stu-id="ce89f-109">The <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> class is a control that works with visual designers and is meant to be used in user interface contexts; it raises events on the user interface thread.</span></span> <span data-ttu-id="ce89f-110"><xref:System.Timers.Timer?displayProperty=nameWithType> クラスは <xref:System.ComponentModel.Component> から派生するため、ビジュアルなデザイナーで使用できます。このクラスもイベントを発生させますが、イベントは <xref:System.Threading.ThreadPool> スレッドで発生します。</span><span class="sxs-lookup"><span data-stu-id="ce89f-110">The <xref:System.Timers.Timer?displayProperty=nameWithType> class derives from <xref:System.ComponentModel.Component>, so it can be used with visual designers; it also raises events, but it raises them on a <xref:System.Threading.ThreadPool> thread.</span></span> <span data-ttu-id="ce89f-111"><xref:System.Threading.Timer?displayProperty=nameWithType> クラスは <xref:System.Threading.ThreadPool> スレッドでコールバックを行い、イベント モデルは使用しません。</span><span class="sxs-lookup"><span data-stu-id="ce89f-111">The <xref:System.Threading.Timer?displayProperty=nameWithType> class makes callbacks on a <xref:System.Threading.ThreadPool> thread and does not use the event model at all.</span></span> <span data-ttu-id="ce89f-112">またこのクラスは、状態オブジェクトをコールバック メソッドに提供します。他のタイマーは状態オブジェクトを提供しません。</span><span class="sxs-lookup"><span data-stu-id="ce89f-112">It also provides a state object to the callback method, which the other timers do not.</span></span> <span data-ttu-id="ce89f-113">このクラスは、非常に軽量です。</span><span class="sxs-lookup"><span data-stu-id="ce89f-113">It is extremely lightweight.</span></span>  
  
 <span data-ttu-id="ce89f-114">次のコード例は、1 秒 (1000 ミリ秒) 後に起動し、**Enter** キーを押すまで 1 秒ごとに時を刻むタイマーを開始します。</span><span class="sxs-lookup"><span data-stu-id="ce89f-114">The following code example starts a timer that starts after one second (1000 milliseconds) and ticks every second until you press the **Enter** key.</span></span> <span data-ttu-id="ce89f-115">実行中にタイマーがガベージ コレクションの対象とならないように、このタイマーへの参照を含む変数はクラス レベルのフィールドとします。</span><span class="sxs-lookup"><span data-stu-id="ce89f-115">The variable containing the reference to the timer is a class-level field, to ensure that the timer is not subject to garbage collection while it is still running.</span></span> <span data-ttu-id="ce89f-116">積極的なガベージ コレクションの詳細については、「<xref:System.GC.KeepAlive%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ce89f-116">For more information on aggressive garbage collection, see <xref:System.GC.KeepAlive%2A>.</span></span>  
  
 [!code-cpp[System.Threading.Timer#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.Timer/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.Timer#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.Timer/CS/source2.cs#2)]
 [!code-vb[System.Threading.Timer#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.Timer/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="ce89f-117">参照</span><span class="sxs-lookup"><span data-stu-id="ce89f-117">See Also</span></span>  
 <xref:System.Threading.Timer>  
 [<span data-ttu-id="ce89f-118">スレッド処理オブジェクトと機能</span><span class="sxs-lookup"><span data-stu-id="ce89f-118">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
