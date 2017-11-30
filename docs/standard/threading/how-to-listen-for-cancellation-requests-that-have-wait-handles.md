---
title: "方法: 待機ハンドルがあるキャンセル要求を待機する"
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
helpviewer_keywords: cancellation, waiting with wait handles
ms.assetid: 6e2aa49b-fc84-4bcf-962b-17db98b7edcb
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e1eaa84d924fde63e94c36fab50a809c7c03f075
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-listen-for-cancellation-requests-that-have-wait-handles"></a><span data-ttu-id="e2043-102">方法: 待機ハンドルがあるキャンセル要求を待機する</span><span class="sxs-lookup"><span data-stu-id="e2043-102">How to: Listen for Cancellation Requests That Have Wait Handles</span></span>
<span data-ttu-id="e2043-103">メソッドは、ブロックされた場合は、シグナル状態になるイベントの待機中、キャンセル トークンの値をチェックおよび適切なタイミングで反応できません。</span><span class="sxs-lookup"><span data-stu-id="e2043-103">If a method is blocked while it is waiting for an event to be signaled, it cannot check the value of the cancellation token and respond in a timely manner.</span></span> <span data-ttu-id="e2043-104">最初の例などのイベントを使用しているときに、この問題を解決する方法を示しています。<xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>統合キャンセル フレームワークをネイティブにサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="e2043-104">The first example shows how to solve this problem when you are working with events such as <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> that do not natively support the unified cancellation framework.</span></span> <span data-ttu-id="e2043-105">2 番目の例を使用するより効率的な方法を示しています。 <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>、一元化されたキャンセルをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="e2043-105">The second example shows a more streamlined approach that uses <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>, which does support unified cancellation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e2043-106">[マイ コードのみ] が有効になっている場合、Visual Studio では、例外をスローする行で処理が中断され、"ユーザー コードで処理されない例外" に関するエラー メッセージが表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="e2043-106">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="e2043-107">このエラーは問題にはなりません。</span><span class="sxs-lookup"><span data-stu-id="e2043-107">This error is benign.</span></span> <span data-ttu-id="e2043-108">F5 キーを押して、処理が中断された箇所から続行し、以下の例に示す例外処理動作を確認できます。</span><span class="sxs-lookup"><span data-stu-id="e2043-108">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="e2043-109">Visual Studio の最初のエラーの処理は中断を防ぐために下にある [マイ コードのみ] チェック ボックスをオフにだけ**ツール、オプション、デバッグ、一般的な**します。</span><span class="sxs-lookup"><span data-stu-id="e2043-109">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2043-110">例</span><span class="sxs-lookup"><span data-stu-id="e2043-110">Example</span></span>  
 <span data-ttu-id="e2043-111">次の例では、<xref:System.Threading.ManualResetEvent>統合キャンセルをサポートしていない待機ハンドルのブロックを解除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e2043-111">The following example uses a <xref:System.Threading.ManualResetEvent> to demonstrate how to unblock wait handles that do not support unified cancellation.</span></span>  
  
 [!code-csharp[Cancellation#9](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#9)]
 [!code-vb[Cancellation#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="e2043-112">例</span><span class="sxs-lookup"><span data-stu-id="e2043-112">Example</span></span>  
 <span data-ttu-id="e2043-113">次の例では、<xref:System.Threading.ManualResetEventSlim>をサポートしているプリミティブがキャンセルを unified 調整のブロックを解除する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e2043-113">The following example uses a <xref:System.Threading.ManualResetEventSlim> to demonstrate how to unblock coordination primitives that do support unified cancellation.</span></span> <span data-ttu-id="e2043-114">同じアプローチをなどその他の軽量な調整プリミティブと共に使用できる<xref:System.Threading.Semaphore>`Slim`と<xref:System.Threading.CountdownEvent>です。</span><span class="sxs-lookup"><span data-stu-id="e2043-114">The same approach can be used with other lightweight coordination primitives, such as <xref:System.Threading.Semaphore>`Slim` and <xref:System.Threading.CountdownEvent>.</span></span>  
  
 [!code-csharp[Cancellation#10](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#10)]
 [!code-vb[Cancellation#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="e2043-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="e2043-115">See Also</span></span>  
 [<span data-ttu-id="e2043-116">マネージ スレッドのキャンセル</span><span class="sxs-lookup"><span data-stu-id="e2043-116">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
