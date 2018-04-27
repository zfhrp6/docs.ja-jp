---
title: contextSwitchDeadlock MDA
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deadlocks [.NET Framework]
- pumping messages
- STA message pumping
- single-threaded COM components
- MDAs (managed debugging assistants), context switching deadlocks
- managed debugging assistants (MDAs), context switching deadlocks
- ContextSwitchDeadlock MDA
- message pumping
- context switching deadlocks
ms.assetid: 26dfaa15-9ddb-4b0a-b6da-999bba664fa6
caps.latest.revision: 22
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2f3ee9aef3bc824ee25e577a5dbd14aeaa210be3
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="contextswitchdeadlock-mda"></a><span data-ttu-id="d062a-102">contextSwitchDeadlock MDA</span><span class="sxs-lookup"><span data-stu-id="d062a-102">contextSwitchDeadlock MDA</span></span>
<span data-ttu-id="d062a-103">`contextSwitchDeadlock` マネージ デバッグ アシスタント (MDA) は、COM コンテキストの遷移の試行中にデッドロックが検出されるとアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="d062a-103">The `contextSwitchDeadlock` managed debugging assistant (MDA) is activated when a deadlock is detected during an attempted COM context transition.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="d062a-104">症状</span><span class="sxs-lookup"><span data-stu-id="d062a-104">Symptoms</span></span>  
 <span data-ttu-id="d062a-105">最も一般的な症状は、マネージ コードから実行されたアンマネージ COM コンポーネントの呼び出しから戻らないことです。</span><span class="sxs-lookup"><span data-stu-id="d062a-105">The most common symptom is that a call on an unmanaged COM component from managed code does not return.</span></span>  <span data-ttu-id="d062a-106">別の症状として、メモリの使用量が時間と共に増加する場合もあります。</span><span class="sxs-lookup"><span data-stu-id="d062a-106">Another symptom is memory usage increasing over time.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="d062a-107">原因</span><span class="sxs-lookup"><span data-stu-id="d062a-107">Cause</span></span>  
 <span data-ttu-id="d062a-108">最も考えられる原因として、シングルスレッド アパートメント (STA) スレッドがメッセージ ポンプを行っていないことがあります。</span><span class="sxs-lookup"><span data-stu-id="d062a-108">The most probable cause is that a single-threaded apartment (STA) thread is not pumping messages.</span></span> <span data-ttu-id="d062a-109">STA スレッドが、メッセージ ポンプを行わずに待機しているか、または時間のかかる操作を実行していて、メッセージ キューのポンプを許可していません。</span><span class="sxs-lookup"><span data-stu-id="d062a-109">The STA thread is either waiting without pumping messages or is performing lengthy operations and is not allowing the message queue to pump.</span></span>  
  
 <span data-ttu-id="d062a-110">メモリ使用量が時間の経過と共に増加する症状は、ファイナライザー スレッドがアンマネージ COM コンポーネント上の `Release` を呼び出そうとして、そのコンポーネントが戻らない場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="d062a-110">Memory usage increasing over time is caused by the finalizer thread attempting to call `Release` on an unmanaged COM component and that component is not returning.</span></span>  <span data-ttu-id="d062a-111">このため、ファイナライザーは他のオブジェクトを再利用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="d062a-111">This prevents the finalizer from reclaiming other objects.</span></span>  
  
 <span data-ttu-id="d062a-112">既定では、Visual Basic コンソール アプリケーションのメイン スレッドのスレッド処理モデルは STA です。</span><span class="sxs-lookup"><span data-stu-id="d062a-112">By default, the threading model for the main thread of Visual Basic console applications is STA.</span></span> <span data-ttu-id="d062a-113">STA スレッドが共通言語ランタイムまたはサードパーティ コントロールを通じて COM 相互運用性を直接または間接的に使用する場合、この MDA がアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="d062a-113">This MDA is activated if an STA thread uses COM interoperability either directly or indirectly through the common language runtime or a third-party control.</span></span>  <span data-ttu-id="d062a-114">Visual Basic コンソール アプリケーションでこの MDA がアクティブ化されるのを防ぐには、メイン メソッドに <xref:System.MTAThreadAttribute> 属性を適用するか、またはメッセージをポンプするようにアプリケーションを変更します。</span><span class="sxs-lookup"><span data-stu-id="d062a-114">To avoid activating this MDA in a Visual Basic console application, apply the <xref:System.MTAThreadAttribute> attribute to the main method or modify the application to pump messages.</span></span>  
  
 <span data-ttu-id="d062a-115">次のすべての条件が満たされる場合、この MDA が誤ってアクティブ化される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d062a-115">It is possible for this MDA to be falsely activated when all of the following conditions are met:</span></span>  
  
-   <span data-ttu-id="d062a-116">アプリケーションがライブラリを通じて直接または間接的に STA スレッドから COM コンポーネントを作成する。</span><span class="sxs-lookup"><span data-stu-id="d062a-116">An application creates COM components from STA threads either directly or indirectly through libraries.</span></span>  
  
-   <span data-ttu-id="d062a-117">デバッガーでアプリケーションが中断され、ユーザーがアプリケーションを続行したか、またはステップ操作を実行した。</span><span class="sxs-lookup"><span data-stu-id="d062a-117">The application was stopped in the debugger and the user either continued the application or performed a step operation.</span></span>  
  
-   <span data-ttu-id="d062a-118">アンマネージ デバッグが有効になっていない。</span><span class="sxs-lookup"><span data-stu-id="d062a-118">Unmanaged debugging is not enabled.</span></span>  
  
 <span data-ttu-id="d062a-119">MDA が誤ってアクティブ化されたかどうかを判断するには、すべてのブレークポイントを無効にし、アプリケーションを再び実行して、中断なしで実行させます。</span><span class="sxs-lookup"><span data-stu-id="d062a-119">To determine if the MDA is being falsely activated, disable all breakpoints, restart the application, and allow it to run without stopping.</span></span> <span data-ttu-id="d062a-120">MDA がアクティブ化されない場合は、最初のアクティブ化は誤りだった可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d062a-120">If the MDA is not activated, it is likely the initial activation was false.</span></span> <span data-ttu-id="d062a-121">その場合は、MDA を無効にして、デバッグ セッションとの干渉を防ぎます。</span><span class="sxs-lookup"><span data-stu-id="d062a-121">In this case, disable the MDA to avoid interference with the debugging session.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d062a-122">この MDA は、[!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] 以上のバージョンの既定のセットに含まれています。</span><span class="sxs-lookup"><span data-stu-id="d062a-122">This MDA is in the default set for [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] and later versions.</span></span> <span data-ttu-id="d062a-123">Visual Studio では、ホスト プロセスが有効の場合、既定で設定される Mda を無効にできません。</span><span class="sxs-lookup"><span data-stu-id="d062a-123">When the hosting process is enabled in Visual Studio, you cannot disable MDAs that are in the default set.</span></span> <span data-ttu-id="d062a-124">ホスティング プロセスは既定で有効になるため、明示的に無効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d062a-124">The hosting process is enabled by default, so it must be explicitly disabled.</span></span> <span data-ttu-id="d062a-125">MDA を無効にする方法については、「[マネージ デバッグ アシスタントによるエラーの診断](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)」の「MDA の有効化と無効化」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d062a-125">For information about how to disable MDAs, see "Enabling and Disabling MDAs" in [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="d062a-126">解像度</span><span class="sxs-lookup"><span data-stu-id="d062a-126">Resolution</span></span>  
 <span data-ttu-id="d062a-127">STA メッセージ ポンプに関する COM 規則に従います。</span><span class="sxs-lookup"><span data-stu-id="d062a-127">Follow COM rules regarding STA message pumping.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="d062a-128">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="d062a-128">Effect on the Runtime</span></span>  
 <span data-ttu-id="d062a-129">この MDA は CLR に影響しません。</span><span class="sxs-lookup"><span data-stu-id="d062a-129">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="d062a-130">COM コンテキストに関するデータを報告するだけです。</span><span class="sxs-lookup"><span data-stu-id="d062a-130">It only reports data about COM contexts.</span></span>  
  
## <a name="output"></a><span data-ttu-id="d062a-131">出力</span><span class="sxs-lookup"><span data-stu-id="d062a-131">Output</span></span>  
 <span data-ttu-id="d062a-132">現在のコンテキストおよびターゲット コンテキストを説明するメッセージです。</span><span class="sxs-lookup"><span data-stu-id="d062a-132">A message describing the current context and the target context.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="d062a-133">構成</span><span class="sxs-lookup"><span data-stu-id="d062a-133">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <contextSwitchDeadlock />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d062a-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="d062a-134">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="d062a-135">マネージ デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="d062a-135">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="d062a-136">相互運用マーシャリング</span><span class="sxs-lookup"><span data-stu-id="d062a-136">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
