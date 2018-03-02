---
title: "AsyncCallback デリゲートの使用による非同期操作の終了"
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
- ending asynchronous operations
- asynchronous programming, ending operations
- AsyncCallback delegate
- stopping asynchronous operations
ms.assetid: 9d97206c-8917-406c-8961-7d0909d84eeb
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d71e78ecd5bf365d0a1f3efb8c8e15d4a1de6dc7
ms.sourcegitcommit: 957c696f25e39f923a827fc3ad5e8ab72768838c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/13/2018
---
# <a name="using-an-asynccallback-delegate-to-end-an-asynchronous-operation"></a><span data-ttu-id="ee0fe-102">AsyncCallback デリゲートの使用による非同期操作の終了</span><span class="sxs-lookup"><span data-stu-id="ee0fe-102">Using an AsyncCallback Delegate to End an Asynchronous Operation</span></span>
<span data-ttu-id="ee0fe-103">非同期操作の結果の待機中に、他の作業を実行できるアプリケーションは、操作が完了するまで待機をブロックする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="ee0fe-103">Applications that can do other work while waiting for the results of an asynchronous operation should not block waiting until the operation completes.</span></span> <span data-ttu-id="ee0fe-104">次のオプションのいずれかを使用して、非同期操作が完了するまでの待機中に、手順の実行を継続します。</span><span class="sxs-lookup"><span data-stu-id="ee0fe-104">Use one of the following options to continue executing instructions while waiting for an asynchronous operation to complete:</span></span>  
  
-   <span data-ttu-id="ee0fe-105"><xref:System.AsyncCallback> デリゲートを使用し、個別のスレッドで非同期操作の結果を処理します。</span><span class="sxs-lookup"><span data-stu-id="ee0fe-105">Use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread.</span></span> <span data-ttu-id="ee0fe-106">このトピックでは、この方法のデモが実行されます。</span><span class="sxs-lookup"><span data-stu-id="ee0fe-106">This approach is demonstrated in this topic.</span></span>  
  
-   <span data-ttu-id="ee0fe-107">非同期操作の **Begin***OperationName* メソッドによって返される <xref:System.IAsyncResult> の <xref:System.IAsyncResult.IsCompleted%2A> プロパティを使用して、その操作が完了したかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="ee0fe-107">Use the <xref:System.IAsyncResult.IsCompleted%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin***OperationName* method to determine whether the operation has completed.</span></span> <span data-ttu-id="ee0fe-108">この方法のデモを実行する例については、「[非同期操作のステータスのポーリング](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ee0fe-108">For an example that demonstrates this approach, see [Polling for the Status of an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee0fe-109">例</span><span class="sxs-lookup"><span data-stu-id="ee0fe-109">Example</span></span>  
 <span data-ttu-id="ee0fe-110">次のコード例は、ユーザー指定のコンピューターのドメイン ネーム システム (DNS) 情報を取得するために、<xref:System.Net.Dns> クラスの非同期メソッドを使用してデモを実行します。</span><span class="sxs-lookup"><span data-stu-id="ee0fe-110">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System (DNS) information for user-specified computers.</span></span> <span data-ttu-id="ee0fe-111">この例では、`ProcessDnsInformation` メソッドを参照する <xref:System.AsyncCallback> デリゲートを作成します。</span><span class="sxs-lookup"><span data-stu-id="ee0fe-111">This example creates an <xref:System.AsyncCallback> delegate that references the `ProcessDnsInformation` method.</span></span> <span data-ttu-id="ee0fe-112">このメソッドは、DNS 情報に対する非同期要求ごとに 1 回呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="ee0fe-112">This method is called once for each asynchronous request for DNS information.</span></span>  
  
 <span data-ttu-id="ee0fe-113">ユーザー指定のホストは、<xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.Object> パラメーターに渡されます。</span><span class="sxs-lookup"><span data-stu-id="ee0fe-113">Note that the user-specified host is passed to the <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.Object> parameter.</span></span> <span data-ttu-id="ee0fe-114">複雑な状態オブジェクトの定義と使用に関するデモを実行する例については、「[AsyncCallback デリゲートおよび状態オブジェクトの使用](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ee0fe-114">For an example that demonstrates defining and using a more complex state object, see [Using an AsyncCallback Delegate and State Object](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md).</span></span>  
  
 [!code-csharp[AsyncDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateNoStateObject.cs#4)]
 [!code-vb[AsyncDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateNoState.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="ee0fe-115">参照</span><span class="sxs-lookup"><span data-stu-id="ee0fe-115">See Also</span></span>  
 [<span data-ttu-id="ee0fe-116">イベント ベースの非同期パターン (EAP)</span><span class="sxs-lookup"><span data-stu-id="ee0fe-116">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [<span data-ttu-id="ee0fe-117">イベントベースの非同期パターンの概要</span><span class="sxs-lookup"><span data-stu-id="ee0fe-117">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [<span data-ttu-id="ee0fe-118">IAsyncResult を使用した非同期メソッドの呼び出し</span><span class="sxs-lookup"><span data-stu-id="ee0fe-118">Calling Asynchronous Methods Using IAsyncResult</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-asynchronous-methods-using-iasyncresult.md)  
 [<span data-ttu-id="ee0fe-119">AsyncCallback デリゲートおよび状態オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="ee0fe-119">Using an AsyncCallback Delegate and State Object</span></span>](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
