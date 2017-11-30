---
title: "方法: SpinLock のスレッド追跡モードを有効にする"
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
helpviewer_keywords: SpinLock, how to enable thread-tracking
ms.assetid: 62ee2e68-0bdd-4869-afc9-f0a57a11ae01
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ca5f1b6eace7a24a6bbb7fd541858246828fa757
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-enable-thread-tracking-mode-in-spinlock"></a><span data-ttu-id="2a066-102">方法: SpinLock のスレッド追跡モードを有効にする</span><span class="sxs-lookup"><span data-stu-id="2a066-102">How to: Enable Thread-Tracking Mode in SpinLock</span></span>
<span data-ttu-id="2a066-103"><xref:System.Threading.SpinLock?displayProperty=nameWithType>非常に短い待機時間が含まれる場合に使用できる低レベルの相互排他ロックです。</span><span class="sxs-lookup"><span data-stu-id="2a066-103"><xref:System.Threading.SpinLock?displayProperty=nameWithType> is a low-level mutual exclusion lock that you can use for scenarios that have very short wait times.</span></span> <span data-ttu-id="2a066-104"><xref:System.Threading.SpinLock>再入可能ではありません。</span><span class="sxs-lookup"><span data-stu-id="2a066-104"><xref:System.Threading.SpinLock> is not re-entrant.</span></span> <span data-ttu-id="2a066-105">スレッドがロックに入った後、再入する前に正しくロックを終了にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2a066-105">After a thread enters the lock, it must exit the lock correctly before it can enter again.</span></span> <span data-ttu-id="2a066-106">通常、ロックを再入力しようとすると、デッドロックが発生し、デッドロックをデバッグが非常に困難になることができます。</span><span class="sxs-lookup"><span data-stu-id="2a066-106">Typically, any attempt to re-enter the lock would cause deadlock, and deadlocks can be very difficult to debug.</span></span> <span data-ttu-id="2a066-107">開発を支援するため<xref:System.Threading.SpinLock?displayProperty=nameWithType>スレッドが既に保持しているロックを再入力しようとしたときにスローされる例外を発生させるスレッド追跡モードをサポートします。</span><span class="sxs-lookup"><span data-stu-id="2a066-107">As an aid to development, <xref:System.Threading.SpinLock?displayProperty=nameWithType> supports a thread-tracking mode that causes an exception to be thrown when a thread attempts to re-enter a lock that it already holds.</span></span> <span data-ttu-id="2a066-108">これは、操作により、あるロックが適切に終了しなかったポイントを簡単に特定できます。</span><span class="sxs-lookup"><span data-stu-id="2a066-108">This lets you more easily locate the point at which the lock was not exited correctly.</span></span> <span data-ttu-id="2a066-109">使用してスレッド追跡モードをオンすることができます、<xref:System.Threading.SpinLock>をブール値を受け取るコンス トラクターは入力パラメーター、およびの引数を渡すこと`true`です。</span><span class="sxs-lookup"><span data-stu-id="2a066-109">You can turn on thread-tracking mode by using the <xref:System.Threading.SpinLock> constructor that takes a Boolean input parameter, and passing in an argument of `true`.</span></span> <span data-ttu-id="2a066-110">開発およびテスト フェーズを完了すると後、は、パフォーマンス向上のためのスレッド追跡モードをオフにします。</span><span class="sxs-lookup"><span data-stu-id="2a066-110">After you complete the development and testing phases, turn off thread-tracking mode for better performance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a066-111">例</span><span class="sxs-lookup"><span data-stu-id="2a066-111">Example</span></span>  
 <span data-ttu-id="2a066-112">次の例では、スレッド追跡モードを示します。</span><span class="sxs-lookup"><span data-stu-id="2a066-112">The following example demonstrates thread-tracking mode.</span></span> <span data-ttu-id="2a066-113">ロックを適切に終了する行については、結果は、次のいずれかの原因となるコーディング エラーをシミュレートするためにコメント アウトします。</span><span class="sxs-lookup"><span data-stu-id="2a066-113">The lines that correctly exit the lock are commented out to simulate a coding error that causes one of the following results:</span></span>  
  
-   <span data-ttu-id="2a066-114">場合、例外がスローされます、<xref:System.Threading.SpinLock>の引数を使用して作成された`true`(`True` Visual Basic で)。</span><span class="sxs-lookup"><span data-stu-id="2a066-114">An exception is thrown if the <xref:System.Threading.SpinLock> was created by using an argument of `true` (`True` in Visual Basic).</span></span>  
  
-   <span data-ttu-id="2a066-115">デッドロックに陥る、<xref:System.Threading.SpinLock>の引数を使用して作成された`false`(`False` Visual Basic で)。</span><span class="sxs-lookup"><span data-stu-id="2a066-115">Deadlock if the <xref:System.Threading.SpinLock> was created by using an argument of `false` (`False` in Visual Basic).</span></span>  
  
 [!code-csharp[CDS_SpinLock#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#01)]
 [!code-vb[CDS_SpinLock#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_threadtracking.vb#01)]  
  
## <a name="see-also"></a><span data-ttu-id="2a066-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="2a066-116">See Also</span></span>  
 [<span data-ttu-id="2a066-117">SpinLock</span><span class="sxs-lookup"><span data-stu-id="2a066-117">SpinLock</span></span>](../../../docs/standard/threading/spinlock.md)
