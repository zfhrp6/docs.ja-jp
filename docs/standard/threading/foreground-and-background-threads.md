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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 83022bd27379e1ee34197af4897a5c809f495f48
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="foreground-and-background-threads"></a><span data-ttu-id="8c22c-102">フォアグラウンド スレッドとバックグラウンド スレッド</span><span class="sxs-lookup"><span data-stu-id="8c22c-102">Foreground and Background Threads</span></span>
<span data-ttu-id="8c22c-103">マネージ スレッドは、バックグラウンド スレッドまたはフォアグラウンド スレッドのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="8c22c-103">A managed thread is either a background thread or a foreground thread.</span></span> <span data-ttu-id="8c22c-104">バックグラウンド スレッドは、1 つの例外を除き、フォアグラウンド スレッドと同じです。その例外とは、バックグラウンド スレッドではマネージ実行環境を実行させておくことができないことです。</span><span class="sxs-lookup"><span data-stu-id="8c22c-104">Background threads are identical to foreground threads with one exception: a background thread does not keep the managed execution environment running.</span></span> <span data-ttu-id="8c22c-105">すべてのフォアグラウンド スレッドが (.exe ファイルがマネージ アセンブリである) マネージ プロセスで停止されると、システムはすべてのバックグラウンド スレッドを停止し、シャットダウンします。</span><span class="sxs-lookup"><span data-stu-id="8c22c-105">Once all foreground threads have been stopped in a managed process (where the .exe file is a managed assembly), the system stops all background threads and shuts down.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8c22c-106">プロセスがシャットダウンしているため、ランタイムがバックグラウンド スレッドを停止した場合、スレッドでは例外がスローされません。</span><span class="sxs-lookup"><span data-stu-id="8c22c-106">When the runtime stops a background thread because the process is shutting down, no exception is thrown in the thread.</span></span> <span data-ttu-id="8c22c-107">ただし、<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> メソッドがアプリケーション ドメインをアンロードしたために、スレッドが停止された場合、フォアグラウンド スレッドとバックグラウンド スレッドの両方で <xref:System.Threading.ThreadAbortException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="8c22c-107">However, when threads are stopped because the <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> method unloads the application domain, a <xref:System.Threading.ThreadAbortException> is thrown in both foreground and background threads.</span></span>  
  
 <span data-ttu-id="8c22c-108">スレッドがバックグラウンド スレッドであるか、フォアグラウンド スレッドであるかを判断する場合や、その状態を変更する場合は、<xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="8c22c-108">Use the <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> property to determine whether a thread is a background or a foreground thread, or to change its status.</span></span> <span data-ttu-id="8c22c-109">スレッドは、<xref:System.Threading.Thread.IsBackground%2A> プロパティを `true` に設定することで、いつでもバックグラウンド スレッドに変更できます。</span><span class="sxs-lookup"><span data-stu-id="8c22c-109">A thread can be changed to a background thread at any time by setting its <xref:System.Threading.Thread.IsBackground%2A> property to `true`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8c22c-110">スレッドのフォアグラウンドまたはバックグラウンドの状態が、スレッドのハンドルされない例外の結果に影響することはありません。</span><span class="sxs-lookup"><span data-stu-id="8c22c-110">The foreground or background status of a thread does not affect the outcome of an unhandled exception in the thread.</span></span> <span data-ttu-id="8c22c-111">.NET framework Version 2.0 では、フォアグラウンドまたはバックグラウンド スレッドのハンドルされない例外により、アプリケーションが終了します。</span><span class="sxs-lookup"><span data-stu-id="8c22c-111">In the .NET Framework version 2.0, an unhandled exception in either foreground or background threads results in termination of the application.</span></span> <span data-ttu-id="8c22c-112">「[マネージ スレッドの例外](../../../docs/standard/threading/exceptions-in-managed-threads.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c22c-112">See [Exceptions in Managed Threads](../../../docs/standard/threading/exceptions-in-managed-threads.md).</span></span>  
  
 <span data-ttu-id="8c22c-113">マネージ スレッド プールに属するスレッド (つまり、<xref:System.Threading.Thread.IsThreadPoolThread%2A> プロパティが `true` のスレッド) はバックグラウンド スレッドです。</span><span class="sxs-lookup"><span data-stu-id="8c22c-113">Threads that belong to the managed thread pool (that is, threads whose <xref:System.Threading.Thread.IsThreadPoolThread%2A> property is `true`) are background threads.</span></span> <span data-ttu-id="8c22c-114">アンマネージ コードからマネージ実行環境に入るすべてのスレッドは、バックグラウンド スレッドとしてマークされます。</span><span class="sxs-lookup"><span data-stu-id="8c22c-114">All threads that enter the managed execution environment from unmanaged code are marked as background threads.</span></span> <span data-ttu-id="8c22c-115">新しい <xref:System.Threading.Thread> オブジェクトを作成して開始することで生成されるすべてのスレッドは、既定でフォアグラウンド スレッドとなります。</span><span class="sxs-lookup"><span data-stu-id="8c22c-115">All threads generated by creating and starting a new <xref:System.Threading.Thread> object are by default foreground threads.</span></span>  
  
 <span data-ttu-id="8c22c-116">スレッドを使用して、ソケット接続などのアクティビティを監視する場合は、その <xref:System.Threading.Thread.IsBackground%2A> プロパティを `true` に設定して、スレッドがプロセスの終了を回避しないようにします。</span><span class="sxs-lookup"><span data-stu-id="8c22c-116">If you use a thread to monitor an activity, such as a socket connection, set its <xref:System.Threading.Thread.IsBackground%2A> property to `true` so that the thread does not prevent your process from terminating.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c22c-117">参照</span><span class="sxs-lookup"><span data-stu-id="8c22c-117">See Also</span></span>  
 <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadAbortException>
