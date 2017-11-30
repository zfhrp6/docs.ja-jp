---
title: "フォアグラウンド スレッドとバックグラウンド スレッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], foreground
- threading [.NET Framework], background
- foreground threads
- background threads
ms.assetid: cfe0d632-dd35-47e0-91ad-f742a444005e
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 42ad427fc2c1175c0d9b333aa418aea039f11a35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="foreground-and-background-threads"></a><span data-ttu-id="8ea00-102">フォアグラウンド スレッドとバックグラウンド スレッド</span><span class="sxs-lookup"><span data-stu-id="8ea00-102">Foreground and Background Threads</span></span>
<span data-ttu-id="8ea00-103">マネージ スレッドは、バック グラウンド スレッドまたはフォア グラウンド スレッドのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="8ea00-103">A managed thread is either a background thread or a foreground thread.</span></span> <span data-ttu-id="8ea00-104">バック グラウンド スレッドは同じですがフォア グラウンド スレッドを 1 つの例外: バック グラウンド スレッドが実行されているマネージ実行環境を維持しません。</span><span class="sxs-lookup"><span data-stu-id="8ea00-104">Background threads are identical to foreground threads with one exception: a background thread does not keep the managed execution environment running.</span></span> <span data-ttu-id="8ea00-105">すべてのフォア グラウンド スレッドをマネージ プロセス (.exe ファイルは、マネージ アセンブリ) に停止すると、システムはすべてのバック グラウンド スレッドを停止し、シャット ダウンします。</span><span class="sxs-lookup"><span data-stu-id="8ea00-105">Once all foreground threads have been stopped in a managed process (where the .exe file is a managed assembly), the system stops all background threads and shuts down.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ea00-106">ランタイムでは、プロセスをシャット ダウンしているため、バック グラウンド スレッドが停止したら、スレッドで例外はスローされません。</span><span class="sxs-lookup"><span data-stu-id="8ea00-106">When the runtime stops a background thread because the process is shutting down, no exception is thrown in the thread.</span></span> <span data-ttu-id="8ea00-107">ただし、場合のスレッドは停止ため、<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType>メソッドは、アプリケーション ドメインをアンロード、<xref:System.Threading.ThreadAbortException>がフォア グラウンドとバック グラウンド スレッドでスローされます。</span><span class="sxs-lookup"><span data-stu-id="8ea00-107">However, when threads are stopped because the <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> method unloads the application domain, a <xref:System.Threading.ThreadAbortException> is thrown in both foreground and background threads.</span></span>  
  
 <span data-ttu-id="8ea00-108">使用して、<xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>スレッドがバック グラウンドまたはフォア グラウンド スレッドがかどうかを判断する、またはその状態を変更するプロパティです。</span><span class="sxs-lookup"><span data-stu-id="8ea00-108">Use the <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> property to determine whether a thread is a background or a foreground thread, or to change its status.</span></span> <span data-ttu-id="8ea00-109">スレッドはバック グラウンド スレッドにいつでも設定してその<xref:System.Threading.Thread.IsBackground%2A>プロパティを`true`です。</span><span class="sxs-lookup"><span data-stu-id="8ea00-109">A thread can be changed to a background thread at any time by setting its <xref:System.Threading.Thread.IsBackground%2A> property to `true`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8ea00-110">スレッドの前景色または背景の状態は、スレッドで未処理の例外の結果には影響しません。</span><span class="sxs-lookup"><span data-stu-id="8ea00-110">The foreground or background status of a thread does not affect the outcome of an unhandled exception in the thread.</span></span> <span data-ttu-id="8ea00-111">.NET framework version 2.0 では、フォア グラウンドまたはバック グラウンド スレッドで未処理の例外は、アプリケーションの終了になります。</span><span class="sxs-lookup"><span data-stu-id="8ea00-111">In the .NET Framework version 2.0, an unhandled exception in either foreground or background threads results in termination of the application.</span></span> <span data-ttu-id="8ea00-112">参照してください[マネージ スレッドの例外](../../../docs/standard/threading/exceptions-in-managed-threads.md)です。</span><span class="sxs-lookup"><span data-stu-id="8ea00-112">See [Exceptions in Managed Threads](../../../docs/standard/threading/exceptions-in-managed-threads.md).</span></span>  
  
 <span data-ttu-id="8ea00-113">マネージ スレッド プールに属するスレッドを (つまり、あるスレッド<xref:System.Threading.Thread.IsThreadPoolThread%2A>プロパティは`true`) スレッドがバック グラウンドします。</span><span class="sxs-lookup"><span data-stu-id="8ea00-113">Threads that belong to the managed thread pool (that is, threads whose <xref:System.Threading.Thread.IsThreadPoolThread%2A> property is `true`) are background threads.</span></span> <span data-ttu-id="8ea00-114">アンマネージ コードからマネージ実行環境を入力するすべてのスレッドがバック グラウンド スレッドとしてマークされます。</span><span class="sxs-lookup"><span data-stu-id="8ea00-114">All threads that enter the managed execution environment from unmanaged code are marked as background threads.</span></span> <span data-ttu-id="8ea00-115">すべてのスレッドを作成して、新しい開始によって生成された<xref:System.Threading.Thread>オブジェクトは既定のフォア グラウンド スレッドでします。</span><span class="sxs-lookup"><span data-stu-id="8ea00-115">All threads generated by creating and starting a new <xref:System.Threading.Thread> object are by default foreground threads.</span></span>  
  
 <span data-ttu-id="8ea00-116">スレッドを使用して、ソケット接続などのアクティビティを監視する場合は、設定、<xref:System.Threading.Thread.IsBackground%2A>プロパティを`true`スレッドが終了してから、プロセスをできないようにします。</span><span class="sxs-lookup"><span data-stu-id="8ea00-116">If you use a thread to monitor an activity, such as a socket connection, set its <xref:System.Threading.Thread.IsBackground%2A> property to `true` so that the thread does not prevent your process from terminating.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ea00-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="8ea00-117">See Also</span></span>  
 <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadAbortException>
