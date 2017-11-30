---
title: "方法: キャンセル要求のコールバックを登録する"
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
helpviewer_keywords: cancellation, how to register callbacks
ms.assetid: 8838dd75-18ed-4b8b-b322-cd4531faac64
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 85b15ed610d80958ac9d7e3762ac8ea7b781b8d0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-register-callbacks-for-cancellation-requests"></a><span data-ttu-id="893d1-102">方法: キャンセル要求のコールバックを登録する</span><span class="sxs-lookup"><span data-stu-id="893d1-102">How to: Register Callbacks for Cancellation Requests</span></span>
<span data-ttu-id="893d1-103">次の例は、れるデリゲートを登録する方法を示しています。 ときに呼び出されます、<xref:System.Threading.CancellationToken.IsCancellationRequested%2A>プロパティが呼び出されたため true になる<xref:System.Threading.CancellationTokenSource.Cancel%2A>トークンを作成したオブジェクトにします。</span><span class="sxs-lookup"><span data-stu-id="893d1-103">The following example shows how to register a delegate that will be invoked when a <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property becomes true due to a call to <xref:System.Threading.CancellationTokenSource.Cancel%2A> on the object that created the token.</span></span> <span data-ttu-id="893d1-104">この方法は、統合キャンセル フレームワークをネイティブにはサポートしていない非同期操作を取り消す場合や、非同期操作の終了を待機している可能性のあるメソッドのブロックを解除する場合に使用できます。</span><span class="sxs-lookup"><span data-stu-id="893d1-104">Use this technique for cancelling asynchronous operations that do not natively support the unified cancellation framework, and for unblocking methods that might be waiting for an asynchronous operation to finish.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="893d1-105">[マイ コードのみ] が有効になっている場合、Visual Studio では、例外をスローする行で処理が中断され、"ユーザー コードで処理されない例外" に関するエラー メッセージが表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="893d1-105">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="893d1-106">このエラーは問題にはなりません。</span><span class="sxs-lookup"><span data-stu-id="893d1-106">This error is benign.</span></span> <span data-ttu-id="893d1-107">F5 キーを押して、処理が中断された箇所から続行し、以下の例に示す例外処理動作を確認できます。</span><span class="sxs-lookup"><span data-stu-id="893d1-107">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="893d1-108">Visual Studio の最初のエラーの処理は中断を防ぐために下にある [マイ コードのみ] チェック ボックスをオフにだけ**ツール、オプション、デバッグ、一般的な**します。</span><span class="sxs-lookup"><span data-stu-id="893d1-108">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="893d1-109">例</span><span class="sxs-lookup"><span data-stu-id="893d1-109">Example</span></span>  
 <span data-ttu-id="893d1-110">次の例では、<xref:System.Net.WebClient.CancelAsync%2A> メソッドを、キャンセル トークンを通じてキャンセルが要求されたときに呼び出されるメソッドとして登録します。</span><span class="sxs-lookup"><span data-stu-id="893d1-110">In the following example, the <xref:System.Net.WebClient.CancelAsync%2A> method is registered as the method to be invoked when cancellation is requested through the cancellation token.</span></span>  
  
 [!code-csharp[Conceptual.Cancellation.Callback#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.cancellation.callback/cs/howtoexample1.cs#1)]
 [!code-vb[Conceptual.Cancellation.Callback#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.cancellation.callback/vb/howtoexample1.vb#1)]  
  
 <span data-ttu-id="893d1-111">コールバックを登録するときにキャンセルが既に要求されていても、コールバックは必ず呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="893d1-111">If cancellation has already been requested when the callback is registered, the callback is still guaranteed to be called.</span></span> <span data-ttu-id="893d1-112">このような場合、進行中の非同期操作がないと <xref:System.Net.WebClient.CancelAsync%2A> メソッドは何も実行しないので、このメソッドの呼び出しは常に安全です。</span><span class="sxs-lookup"><span data-stu-id="893d1-112">In this particular case, the <xref:System.Net.WebClient.CancelAsync%2A> method will do nothing if no asynchronous operation is in progress, so it is always safe to call the method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="893d1-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="893d1-113">See Also</span></span>  
 [<span data-ttu-id="893d1-114">マネージ スレッドのキャンセル</span><span class="sxs-lookup"><span data-stu-id="893d1-114">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
