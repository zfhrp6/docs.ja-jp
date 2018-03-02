---
title: "方法: PLINQ クエリの例外を処理する"
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
- PLINQ queries, how to handle exceptions
ms.assetid: 8d56ff9b-a571-4d31-b41f-80c0b51b70a5
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: db3e09bc2b285d014a7d3a6ed6fc4e50f85b537d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-handle-exceptions-in-a-plinq-query"></a><span data-ttu-id="27c1c-102">方法: PLINQ クエリの例外を処理する</span><span class="sxs-lookup"><span data-stu-id="27c1c-102">How to: Handle Exceptions in a PLINQ Query</span></span>
<span data-ttu-id="27c1c-103">このトピックの最初の例では、PLINQ クエリの実行時にスローされる <xref:System.AggregateException?displayProperty=nameWithType> の処理方法を示します。</span><span class="sxs-lookup"><span data-stu-id="27c1c-103">The first example in this topic shows how to handle the <xref:System.AggregateException?displayProperty=nameWithType> that can be thrown from a PLINQ query when it executes.</span></span> <span data-ttu-id="27c1c-104">2 番目の例では、デリゲート内で例外がスローされる場所のできるだけ近くに try-catch ブロックを配置する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="27c1c-104">The second example shows how to put try-catch blocks within delegates, as close as possible to where the exception will be thrown.</span></span> <span data-ttu-id="27c1c-105">こうすると、発生の直後に例外をキャッチしてクエリの実行を続行できる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="27c1c-105">In this way, you can catch them as soon as they occur and possibly continue query execution.</span></span> <span data-ttu-id="27c1c-106">連結しているスレッドへ例外が上方向へ通知されると、例外が発生した後も、クエリによって一部の項目の処理が続行される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="27c1c-106">When exceptions are allowed to bubble up back to the joining thread, then it is possible that a query may continue to process some items after the exception is raised.</span></span>  
  
 <span data-ttu-id="27c1c-107">場合によっては、PLINQ が順次実行に戻り、例外が発生すると、例外が直接反映され、<xref:System.AggregateException> にラップされないことがあります。</span><span class="sxs-lookup"><span data-stu-id="27c1c-107">In some cases when PLINQ falls back to sequential execution, and an exception occurs, the exception may be propagated directly, and not wrapped in an <xref:System.AggregateException>.</span></span> <span data-ttu-id="27c1c-108">また、<xref:System.Threading.ThreadAbortException> は常に直接反映されます。</span><span class="sxs-lookup"><span data-stu-id="27c1c-108">Also, <xref:System.Threading.ThreadAbortException>s are always propagated directly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="27c1c-109">[マイ コードのみ] が有効になっている場合、Visual Studio では、例外をスローする行で処理が中断され、"ユーザー コードで処理されない例外" に関するエラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="27c1c-109">When "Just My Code" is enabled, Visual Studio will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="27c1c-110">このエラーは問題にはなりません。</span><span class="sxs-lookup"><span data-stu-id="27c1c-110">This error is benign.</span></span> <span data-ttu-id="27c1c-111">F5 キーを押して、処理が中断された箇所から続行し、以下の例に示す例外処理動作を確認できます。</span><span class="sxs-lookup"><span data-stu-id="27c1c-111">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="27c1c-112">Visual Studio による処理が最初のエラーで中断しないようにするには、**[ツール] メニューの [オプション]、[デバッグ] 、[全般]** の順にクリックし、[マイ コードのみ] チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="27c1c-112">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
>   
>  <span data-ttu-id="27c1c-113">この例は、使用方法を示すことを意図したものであるため、同等の順次的な LINQ to Objects クエリほど高速ではない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="27c1c-113">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="27c1c-114">高速化の詳細については、「[PLINQ での高速化について](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="27c1c-114">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="27c1c-115">例</span><span class="sxs-lookup"><span data-stu-id="27c1c-115">Example</span></span>  
 <span data-ttu-id="27c1c-116">次の例は、スローされる <xref:System.AggregateException?displayProperty=nameWithType> をキャッチするクエリを実行するコードの近くに try-catch ブロックを配置する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="27c1c-116">This example shows how to put the try-catch blocks around the code that executes the query to catch any <xref:System.AggregateException?displayProperty=nameWithType>s that are thrown.</span></span>  
  
 [!code-csharp[PLINQ#41](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#41)]
 [!code-vb[PLINQ#41](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#41)]  
  
 <span data-ttu-id="27c1c-117">この例では、例外がスローされた後にクエリを続行することはできません。</span><span class="sxs-lookup"><span data-stu-id="27c1c-117">In this example, the query cannot continue after the exception is thrown.</span></span> <span data-ttu-id="27c1c-118">アプリケーション コードが例外をキャッチするまでに、PLINQ はすべてのスレッド上でクエリを停止しています。</span><span class="sxs-lookup"><span data-stu-id="27c1c-118">By the time your application code catches the exception, PLINQ has already stopped the query on all threads.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27c1c-119">例</span><span class="sxs-lookup"><span data-stu-id="27c1c-119">Example</span></span>  
 <span data-ttu-id="27c1c-120">次の例は、例外をキャッチしてクエリの実行を続行できるようにするため、try-catch ブロックをデリゲートに配置する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="27c1c-120">The following example shows how to put a try-catch block in a delegate to make it possible to catch an exception and continue with the query execution.</span></span>  
  
 [!code-csharp[PLINQ#42](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#42)]
 [!code-vb[PLINQ#42](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#42)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="27c1c-121">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="27c1c-121">Compiling the Code</span></span>  
  
-   <span data-ttu-id="27c1c-122">これらの例をコンパイルして実行するには、これらのコードを PLINQ データのサンプルにコピーして、Main からメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="27c1c-122">To compile and run these examples, copy them into the PLINQ Data Sample example and call the method from Main.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="27c1c-123">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="27c1c-123">Robust Programming</span></span>  
 <span data-ttu-id="27c1c-124">プログラムの状態を破損しないようにするため、処理方法がわからない場合は、例外をキャッチしないでください。</span><span class="sxs-lookup"><span data-stu-id="27c1c-124">Do not catch an exception unless you know how to handle it so that you do not corrupt the state of your program.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27c1c-125">参照</span><span class="sxs-lookup"><span data-stu-id="27c1c-125">See Also</span></span>  
 <xref:System.Linq.ParallelEnumerable>  
 [<span data-ttu-id="27c1c-126">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="27c1c-126">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
