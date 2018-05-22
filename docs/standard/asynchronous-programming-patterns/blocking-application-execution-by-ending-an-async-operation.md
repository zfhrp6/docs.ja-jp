---
title: 非同期操作の終了によるアプリケーション実行のブロック
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- blocks, asynchronous operations
- AsyncWaitHandle property
- asynchronous programming, blocking applications
- blocking application execution
ms.assetid: cc5e2834-a65b-4df8-b750-7bdb79997fee
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- vb
ms.openlocfilehash: db46025ca1169f2f93a5b8eabb62a06ccc4bb95e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="blocking-application-execution-by-ending-an-async-operation"></a><span data-ttu-id="c46d1-102">非同期操作の終了によるアプリケーション実行のブロック</span><span class="sxs-lookup"><span data-stu-id="c46d1-102">Blocking Application Execution by Ending an Async Operation</span></span>
<span data-ttu-id="c46d1-103">非同期操作の結果の待機中に、他の作業を継続できないアプリケーションは、操作が完了するまでブロックする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c46d1-103">Applications that cannot continue to do other work while waiting for the results of an asynchronous operation must block until the operation completes.</span></span> <span data-ttu-id="c46d1-104">次のオプションのいずれかを使用して、非同期操作が完了するまでの待機中に、アプリケーションのメイン スレッドをブロックします。</span><span class="sxs-lookup"><span data-stu-id="c46d1-104">Use one of the following options to block your application's main thread while waiting for an asynchronous operation to complete:</span></span>  
  
-   <span data-ttu-id="c46d1-105">非同期操作の **End***OperationName* メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="c46d1-105">Call the asynchronous operations **End***OperationName* method.</span></span> <span data-ttu-id="c46d1-106">このトピックでは、この方法のデモが実行されます。</span><span class="sxs-lookup"><span data-stu-id="c46d1-106">This approach is demonstrated in this topic.</span></span>  
  
-   <span data-ttu-id="c46d1-107">非同期操作の **Begin***OperationName* メソッドによって返される <xref:System.IAsyncResult> の <xref:System.IAsyncResult.AsyncWaitHandle%2A> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="c46d1-107">Use the <xref:System.IAsyncResult.AsyncWaitHandle%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin***OperationName* method.</span></span> <span data-ttu-id="c46d1-108">この方法をデモの例については、「[AsyncWaitHandle の使用によるアプリケーション実行のブロック](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c46d1-108">For an example that demonstrates this approach, see [Blocking Application Execution Using an AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).</span></span>  
  
 <span data-ttu-id="c46d1-109">非同期操作が完了するまでブロックするために **End***OperationName* を使用するアプリケーションは、通常は **Begin***OperationName* メソッドを呼び出し、操作の結果なしで実行できる任意の作業を実行して、**End***OperationName* を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="c46d1-109">Applications that use the **End***OperationName* method to block until an asynchronous operation is complete will typically call the **Begin***OperationName* method, perform any work that can be done without the results of the operation, and then call **End***OperationName*.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c46d1-110">例</span><span class="sxs-lookup"><span data-stu-id="c46d1-110">Example</span></span>  
 <span data-ttu-id="c46d1-111">次のコード例は、ユーザー指定のコンピューターのドメイン ネーム システム情報を取得するために、<xref:System.Net.Dns> クラスの非同期メソッドを使用してデモを実行します。</span><span class="sxs-lookup"><span data-stu-id="c46d1-111">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="c46d1-112">この方法を使用する場合はこれらの引数は必要ないため、`null` (Visual Basic の場合は `Nothing`) は、<xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` と `stateObject` パラメーターに渡されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c46d1-112">Note that `null` (`Nothing` in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` and `stateObject` parameters because these arguments are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlock.cs#1)]
 [!code-vb[AsyncDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlock.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c46d1-113">参照</span><span class="sxs-lookup"><span data-stu-id="c46d1-113">See Also</span></span>  
 [<span data-ttu-id="c46d1-114">イベント ベースの非同期パターン (EAP)</span><span class="sxs-lookup"><span data-stu-id="c46d1-114">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [<span data-ttu-id="c46d1-115">イベントベースの非同期パターンの概要</span><span class="sxs-lookup"><span data-stu-id="c46d1-115">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
