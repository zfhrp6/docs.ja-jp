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
helpviewer_keywords: PLINQ queries, how to handle exceptions
ms.assetid: 8d56ff9b-a571-4d31-b41f-80c0b51b70a5
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 209e0c1bf89f231d03647ae4351279bfdb172e68
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-handle-exceptions-in-a-plinq-query"></a><span data-ttu-id="8b5fd-102">方法: PLINQ クエリの例外を処理する</span><span class="sxs-lookup"><span data-stu-id="8b5fd-102">How to: Handle Exceptions in a PLINQ Query</span></span>
<span data-ttu-id="8b5fd-103">このトピックの最初の例は、処理する方法を示しています、<xref:System.AggregateException?displayProperty=nameWithType>を実行すると、PLINQ クエリからスローされることができます。</span><span class="sxs-lookup"><span data-stu-id="8b5fd-103">The first example in this topic shows how to handle the <xref:System.AggregateException?displayProperty=nameWithType> that can be thrown from a PLINQ query when it executes.</span></span> <span data-ttu-id="8b5fd-104">2 番目の例では、例外がスローされますにできるだけ近い、デリゲート内で、try-catch ブロックを配置する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8b5fd-104">The second example shows how to put try-catch blocks within delegates, as close as possible to where the exception will be thrown.</span></span> <span data-ttu-id="8b5fd-105">これによりとすぐに、発生する可能性のあるクエリの実行を続行して、キャッチすることができます。</span><span class="sxs-lookup"><span data-stu-id="8b5fd-105">In this way, you can catch them as soon as they occur and possibly continue query execution.</span></span> <span data-ttu-id="8b5fd-106">連結しているスレッドへ例外が上方向へ通知されると、例外が発生した後も、クエリによって一部の項目の処理が続行される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8b5fd-106">When exceptions are allowed to bubble up back to the joining thread, then it is possible that a query may continue to process some items after the exception is raised.</span></span>  
  
 <span data-ttu-id="8b5fd-107">場合によっては PLINQ に戻って、シーケンシャル実行と、例外が発生するときに例外が直接反映されでラップされません、<xref:System.AggregateException>です。</span><span class="sxs-lookup"><span data-stu-id="8b5fd-107">In some cases when PLINQ falls back to sequential execution, and an exception occurs, the exception may be propagated directly, and not wrapped in an <xref:System.AggregateException>.</span></span> <span data-ttu-id="8b5fd-108">また、 <xref:System.Threading.ThreadAbortException>s が直接反映常にします。</span><span class="sxs-lookup"><span data-stu-id="8b5fd-108">Also, <xref:System.Threading.ThreadAbortException>s are always propagated directly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8b5fd-109">「マイ コードのみ」を有効にすると、Visual Studio は例外をスローする行で中断し、「で処理されない例外ユーザー コードです」というエラー メッセージを表示</span><span class="sxs-lookup"><span data-stu-id="8b5fd-109">When "Just My Code" is enabled, Visual Studio will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="8b5fd-110">このエラーは問題にはなりません。</span><span class="sxs-lookup"><span data-stu-id="8b5fd-110">This error is benign.</span></span> <span data-ttu-id="8b5fd-111">F5 キーを押して、処理が中断された箇所から続行し、以下の例に示す例外処理動作を確認できます。</span><span class="sxs-lookup"><span data-stu-id="8b5fd-111">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="8b5fd-112">Visual Studio の最初のエラーの処理は中断を防ぐために下にある [マイ コードのみ] チェック ボックスをオフにだけ**ツール、オプション、デバッグ、一般的な**します。</span><span class="sxs-lookup"><span data-stu-id="8b5fd-112">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
>   
>  <span data-ttu-id="8b5fd-113">この例は、使用方法を示すことを意図したものであるため、同等の順次的な LINQ to Objects クエリほど高速ではない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8b5fd-113">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="8b5fd-114">高速化の詳細については、次を参照してください。 [PLINQ で高速化について](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)です。</span><span class="sxs-lookup"><span data-stu-id="8b5fd-114">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b5fd-115">例</span><span class="sxs-lookup"><span data-stu-id="8b5fd-115">Example</span></span>  
 <span data-ttu-id="8b5fd-116">この例をキャッチするクエリを実行するコードの周り、try-catch ブロックを配置する方法を示しています。 <xref:System.AggregateException?displayProperty=nameWithType>s は、スローされます。</span><span class="sxs-lookup"><span data-stu-id="8b5fd-116">This example shows how to put the try-catch blocks around the code that executes the query to catch any <xref:System.AggregateException?displayProperty=nameWithType>s that are thrown.</span></span>  
  
 [!code-csharp[PLINQ#41](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#41)]
 [!code-vb[PLINQ#41](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#41)]  
  
 <span data-ttu-id="8b5fd-117">この例では、クエリは、例外がスローされた後に続行できません。</span><span class="sxs-lookup"><span data-stu-id="8b5fd-117">In this example, the query cannot continue after the exception is thrown.</span></span> <span data-ttu-id="8b5fd-118">時点では、アプリケーション コードが例外をキャッチ、PLINQ は既に停止クエリすべてのスレッドにします。</span><span class="sxs-lookup"><span data-stu-id="8b5fd-118">By the time your application code catches the exception, PLINQ has already stopped the query on all threads.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b5fd-119">例</span><span class="sxs-lookup"><span data-stu-id="8b5fd-119">Example</span></span>  
 <span data-ttu-id="8b5fd-120">次の例では、デリゲートで例外をキャッチし、クエリの実行を続行できるようにすることで、try-catch ブロックを配置する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8b5fd-120">The following example shows how to put a try-catch block in a delegate to make it possible to catch an exception and continue with the query execution.</span></span>  
  
 [!code-csharp[PLINQ#42](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#42)]
 [!code-vb[PLINQ#42](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#42)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8b5fd-121">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="8b5fd-121">Compiling the Code</span></span>  
  
-   <span data-ttu-id="8b5fd-122">コンパイルして、これらの例を実行、PLINQ データのサンプルにコピーし、Main からメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="8b5fd-122">To compile and run these examples, copy them into the PLINQ Data Sample example and call the method from Main.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="8b5fd-123">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="8b5fd-123">Robust Programming</span></span>  
 <span data-ttu-id="8b5fd-124">プログラムの状態が破損しないように、それを処理する方法を理解していない限り例外をキャッチしません。</span><span class="sxs-lookup"><span data-stu-id="8b5fd-124">Do not catch an exception unless you know how to handle it so that you do not corrupt the state of your program.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b5fd-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="8b5fd-125">See Also</span></span>  
 <xref:System.Linq.ParallelEnumerable>  
 [<span data-ttu-id="8b5fd-126">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="8b5fd-126">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
