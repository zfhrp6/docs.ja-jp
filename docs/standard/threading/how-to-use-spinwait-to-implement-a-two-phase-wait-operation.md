---
title: "方法: SpinWait を使用して 2 フェーズ待機操作を実装する"
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
helpviewer_keywords: SpinWait, how to synchronize two-phase wait
ms.assetid: b2ac4e4a-051a-4f65-b4b9-f8e103aff195
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2717ba2d63e4ecf40638c369b66f2c696e396a5e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-spinwait-to-implement-a-two-phase-wait-operation"></a><span data-ttu-id="1c122-102">方法: SpinWait を使用して 2 フェーズ待機操作を実装する</span><span class="sxs-lookup"><span data-stu-id="1c122-102">How to: Use SpinWait to Implement a Two-Phase Wait Operation</span></span>
<span data-ttu-id="1c122-103">次の例を使用する方法を示しています、 <xref:System.Threading.SpinWait?displayProperty=nameWithType> 2 フェーズ待機操作を実装するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="1c122-103">The following example shows how to use a <xref:System.Threading.SpinWait?displayProperty=nameWithType> object to implement a two-phase wait operation.</span></span> <span data-ttu-id="1c122-104">最初のフェーズでは、同期オブジェクトでは、`Latch`ロックが使用可能になるかどうかを確認中に、いくつかのサイクルを回転します。</span><span class="sxs-lookup"><span data-stu-id="1c122-104">In the first phase, the synchronization object, a `Latch`, spins for a few cycles while it checks whether the lock has become available.</span></span> <span data-ttu-id="1c122-105">ロックが使用可能になる場合、2 番目のフェーズでは、`Wait`メソッドを返しますを使用せず、<xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>実行待ち状態です。 それ以外の場合、`Wait`は待機を実行します。</span><span class="sxs-lookup"><span data-stu-id="1c122-105">In the second phase, if the lock becomes available, then the `Wait` method returns without using the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> to perform its wait; otherwise, `Wait` performs the wait.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c122-106">例</span><span class="sxs-lookup"><span data-stu-id="1c122-106">Example</span></span>  
 <span data-ttu-id="1c122-107">この例は、プリミティブ ラッチ同期の非常に基本的な実装を示します。</span><span class="sxs-lookup"><span data-stu-id="1c122-107">This example shows a very basic implementation of a Latch synchronization primitive.</span></span> <span data-ttu-id="1c122-108">非常に短い待機時間が予想される場合は、このデータ構造体を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="1c122-108">You can use this data structure when wait times are expected to be very short.</span></span> <span data-ttu-id="1c122-109">この例はデモ目的でのみです。</span><span class="sxs-lookup"><span data-stu-id="1c122-109">This example is for demonstration purposes only.</span></span> <span data-ttu-id="1c122-110">ラッチ型機能をプログラムで必要とする場合は、使用を検討して<xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="1c122-110">If you require latch-type functionality in your program, consider using <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>.</span></span>  
  
 [!code-csharp[CDS_SpinWait#03](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait03.cs#03)]
 [!code-vb[CDS_SpinWait#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/spinwait2.vb#03)]  
  
 <span data-ttu-id="1c122-111">ラッチを使用して、<xref:System.Threading.SpinWait>オブジェクトを次の呼び出しまでだけ回転`SpinOnce`により、<xref:System.Threading.SpinWait>スレッドのタイム スライスを生成します。</span><span class="sxs-lookup"><span data-stu-id="1c122-111">The latch uses the <xref:System.Threading.SpinWait> object to spin in place only until the next call to `SpinOnce` causes the <xref:System.Threading.SpinWait> to yield the time slice of the thread.</span></span> <span data-ttu-id="1c122-112">ラッチと呼び出すことによって、独自のコンテキスト スイッチをその時点では、<xref:System.Threading.WaitHandle.WaitOne%2A>上、<xref:System.Threading.ManualResetEvent>とタイムアウト値の残りの部分で渡すことです。</span><span class="sxs-lookup"><span data-stu-id="1c122-112">At that point, the latch causes its own context switch by calling <xref:System.Threading.WaitHandle.WaitOne%2A> on the <xref:System.Threading.ManualResetEvent> and passing in the remainder of the time-out value.</span></span>  
  
 <span data-ttu-id="1c122-113">ラッチを使用せず、ロックを取得することによってパフォーマンスを向上させることがどのくらいの頻度、ログ出力を示しています、<xref:System.Threading.ManualResetEvent>です。</span><span class="sxs-lookup"><span data-stu-id="1c122-113">The logging output shows how often the Latch was able to increase performance by acquiring the lock without using the <xref:System.Threading.ManualResetEvent>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c122-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="1c122-114">See Also</span></span>  
 [<span data-ttu-id="1c122-115">SpinWait</span><span class="sxs-lookup"><span data-stu-id="1c122-115">SpinWait</span></span>](../../../docs/standard/threading/spinwait.md)  
 [<span data-ttu-id="1c122-116">スレッド処理オブジェクトと機能</span><span class="sxs-lookup"><span data-stu-id="1c122-116">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
