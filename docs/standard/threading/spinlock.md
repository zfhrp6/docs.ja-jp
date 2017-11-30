---
title: SpinLock
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: synchronization primitives, SpinLock
ms.assetid: f9af93bb-7a0d-4ba5-afe8-74f48b6b6958
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: efe9b3126b3c952ab156f9ca40752ad8d3fddcd1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="spinlock"></a><span data-ttu-id="172f5-102">SpinLock</span><span class="sxs-lookup"><span data-stu-id="172f5-102">SpinLock</span></span>
<span data-ttu-id="172f5-103"><xref:System.Threading.SpinLock>構造体は、低レベルで相互排他的な同期プリミティブにロックの取得を待機している間に回転します。</span><span class="sxs-lookup"><span data-stu-id="172f5-103">The <xref:System.Threading.SpinLock> structure is a low-level, mutual-exclusion synchronization primitive that spins while it waits to acquire a lock.</span></span> <span data-ttu-id="172f5-104">待機時間が短いファイル名と競合が最小限に抑える場合に予想される場合、マルチコア コンピューターでは<xref:System.Threading.SpinLock>他の種類のロックよりも優れてことができます。</span><span class="sxs-lookup"><span data-stu-id="172f5-104">On multicore computers, when wait times are expected to be short and when contention is minimal, <xref:System.Threading.SpinLock> can perform better than other kinds of locks.</span></span> <span data-ttu-id="172f5-105">ただし、ことをお勧めを使用すること<xref:System.Threading.SpinLock>をプロファイリングして、特定する場合にのみ、<xref:System.Threading.Monitor?displayProperty=nameWithType>メソッドまたは<xref:System.Threading.Interlocked>メソッドは、プログラムのパフォーマンスのパフォーマンスの大幅に低下します。</span><span class="sxs-lookup"><span data-stu-id="172f5-105">However, we recommend that you use <xref:System.Threading.SpinLock> only when you determine by profiling that the <xref:System.Threading.Monitor?displayProperty=nameWithType> method or the <xref:System.Threading.Interlocked> methods are significantly slowing the performance of your program.</span></span>  
  
 <span data-ttu-id="172f5-106"><xref:System.Threading.SpinLock>場合でも、それを取得していない、ロック、スレッドのタイム スライスを生成する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="172f5-106"><xref:System.Threading.SpinLock> may yield the time slice of the thread even if it has not yet acquired the lock.</span></span> <span data-ttu-id="172f5-107">これは、スレッドの優先順位の反転を回避し、進捗ガベージ コレクターを有効にします。</span><span class="sxs-lookup"><span data-stu-id="172f5-107">It does this to avoid thread-priority inversion, and to enable the garbage collector to make progress.</span></span> <span data-ttu-id="172f5-108">使用すると、 <xref:System.Threading.SpinLock>、あるスレッド ロックを保持できるありません非常に短時間の期間より長くなることスレッドがブロックされていないロックを保持していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="172f5-108">When you use a <xref:System.Threading.SpinLock>, ensure that no thread can hold the lock for more than a very brief time span, and that no thread can block while it holds the lock.</span></span>  
  
 <span data-ttu-id="172f5-109">スピンロックが値型であるため、明示的に渡す必要があります、参照渡しする場合は、同じロックを参照する 2 つのコピー。</span><span class="sxs-lookup"><span data-stu-id="172f5-109">Because SpinLock is a value type, you must explicitly pass it by reference if you intend the two copies to refer to the same lock.</span></span>  
  
 <span data-ttu-id="172f5-110">この型を使用する方法の詳細については、次を参照してください。<xref:System.Threading.SpinLock?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="172f5-110">For more information about how to use this type, see <xref:System.Threading.SpinLock?displayProperty=nameWithType>.</span></span> <span data-ttu-id="172f5-111">例については、次を参照してください。[する方法: 低水準の同期のために使用するスピンロック](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md)です。</span><span class="sxs-lookup"><span data-stu-id="172f5-111">For an example, see [How to: Use SpinLock for Low-Level Synchronization](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md).</span></span>  
  
 <span data-ttu-id="172f5-112"><xref:System.Threading.SpinLock>サポートしている、*スレッド*-*追跡*特定の時刻に、ロックが保持しているスレッドを追跡しやすく開発フェーズ中に使用できるモードです。</span><span class="sxs-lookup"><span data-stu-id="172f5-112"><xref:System.Threading.SpinLock> supports a *thread*-*tracking* mode that you can use during the development phase to help track the thread that is holding the lock at a specific time.</span></span> <span data-ttu-id="172f5-113">スレッド追跡モードはデバッグは、非常に便利ですが、オフにすることが、プログラムのリリース バージョンでパフォーマンスが低下する可能性がありますのでことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="172f5-113">Thread-tracking mode is very useful for debugging, but we recommend that you turn it off in the release version of your program because it may slow performance.</span></span> <span data-ttu-id="172f5-114">詳細については、次を参照してください。[する方法: SpinLock のスレッドを有効にする追跡モード](../../../docs/standard/threading/how-to-enable-thread-tracking-mode-in-spinlock.md)です。</span><span class="sxs-lookup"><span data-stu-id="172f5-114">For more information, see [How to: Enable Thread-Tracking Mode in SpinLock](../../../docs/standard/threading/how-to-enable-thread-tracking-mode-in-spinlock.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="172f5-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="172f5-115">See Also</span></span>  
 [<span data-ttu-id="172f5-116">スレッド処理オブジェクトと機能</span><span class="sxs-lookup"><span data-stu-id="172f5-116">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
