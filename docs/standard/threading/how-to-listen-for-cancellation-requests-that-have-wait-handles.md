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
helpviewer_keywords:
- cancellation, waiting with wait handles
ms.assetid: 6e2aa49b-fc84-4bcf-962b-17db98b7edcb
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a0998703ef5b27b4de725a2c2adcfc3d9a2135b9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-listen-for-cancellation-requests-that-have-wait-handles"></a><span data-ttu-id="6f20b-102">方法: 待機ハンドルがあるキャンセル要求を待機する</span><span class="sxs-lookup"><span data-stu-id="6f20b-102">How to: Listen for Cancellation Requests That Have Wait Handles</span></span>
<span data-ttu-id="6f20b-103">イベントがシグナル状態になるのを待機している間にメソッドがブロックされた場合、取り消しトークンの値を確認して、適切なタイミングで応答することはできません。</span><span class="sxs-lookup"><span data-stu-id="6f20b-103">If a method is blocked while it is waiting for an event to be signaled, it cannot check the value of the cancellation token and respond in a timely manner.</span></span> <span data-ttu-id="6f20b-104">最初の例は、統合取り消しフレームワークをネイティブにサポートしない <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> などのイベントの処理時にこの問題を解決する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="6f20b-104">The first example shows how to solve this problem when you are working with events such as <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> that do not natively support the unified cancellation framework.</span></span> <span data-ttu-id="6f20b-105">2 番目の例は、統合取り消しをサポートする、<xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> を使用するより効率的な方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="6f20b-105">The second example shows a more streamlined approach that uses <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>, which does support unified cancellation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6f20b-106">[マイ コードのみ] が有効になっている場合、Visual Studio では、例外をスローする行で処理が中断され、"ユーザー コードで処理されない例外" に関するエラー メッセージが表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="6f20b-106">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="6f20b-107">このエラーは問題にはなりません。</span><span class="sxs-lookup"><span data-stu-id="6f20b-107">This error is benign.</span></span> <span data-ttu-id="6f20b-108">F5 キーを押して、処理が中断された箇所から続行し、以下の例に示す例外処理動作を確認できます。</span><span class="sxs-lookup"><span data-stu-id="6f20b-108">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="6f20b-109">Visual Studio による処理が最初のエラーで中断しないようにするには、**[ツール] メニューの [オプション]、[デバッグ] 、[全般]** の順にクリックし、[マイ コードのみ] チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="6f20b-109">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f20b-110">例</span><span class="sxs-lookup"><span data-stu-id="6f20b-110">Example</span></span>  
 <span data-ttu-id="6f20b-111">次の例では <xref:System.Threading.ManualResetEvent> を使用して、統合取り消しをサポートしない待機ハンドルのブロックを解除する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="6f20b-111">The following example uses a <xref:System.Threading.ManualResetEvent> to demonstrate how to unblock wait handles that do not support unified cancellation.</span></span>  
  
 [!code-csharp[Cancellation#9](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#9)]
 [!code-vb[Cancellation#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="6f20b-112">例</span><span class="sxs-lookup"><span data-stu-id="6f20b-112">Example</span></span>  
 <span data-ttu-id="6f20b-113">次の例では <xref:System.Threading.ManualResetEventSlim> を使用して、統合取り消しをサポートするコーディネーション プリミティブのブロックを解除する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="6f20b-113">The following example uses a <xref:System.Threading.ManualResetEventSlim> to demonstrate how to unblock coordination primitives that do support unified cancellation.</span></span> <span data-ttu-id="6f20b-114"><xref:System.Threading.Semaphore>`Slim` や <xref:System.Threading.CountdownEvent> などの他の軽量なコーディネーション プリミティブでも同じ方法を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="6f20b-114">The same approach can be used with other lightweight coordination primitives, such as <xref:System.Threading.Semaphore>`Slim` and <xref:System.Threading.CountdownEvent>.</span></span>  
  
 [!code-csharp[Cancellation#10](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#10)]
 [!code-vb[Cancellation#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="6f20b-115">参照</span><span class="sxs-lookup"><span data-stu-id="6f20b-115">See Also</span></span>  
 [<span data-ttu-id="6f20b-116">マネージ スレッドのキャンセル</span><span class="sxs-lookup"><span data-stu-id="6f20b-116">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
