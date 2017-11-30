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
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bbe170588776daa97fec4c736d4b1bdd871de518
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="using-an-asynccallback-delegate-to-end-an-asynchronous-operation"></a><span data-ttu-id="24f6f-102">AsyncCallback デリゲートの使用による非同期操作の終了</span><span class="sxs-lookup"><span data-stu-id="24f6f-102">Using an AsyncCallback Delegate to End an Asynchronous Operation</span></span>
<span data-ttu-id="24f6f-103">非同期操作の結果の待機中にその他の作業を実行できるアプリケーションは、操作が完了するまで待機をブロックしないでください。</span><span class="sxs-lookup"><span data-stu-id="24f6f-103">Applications that can do other work while waiting for the results of an asynchronous operation should not block waiting until the operation completes.</span></span> <span data-ttu-id="24f6f-104">非同期操作の完了を待っている間に命令の実行を続行するのにには、次のオプションのいずれかを使用します。</span><span class="sxs-lookup"><span data-stu-id="24f6f-104">Use one of the following options to continue executing instructions while waiting for an asynchronous operation to complete:</span></span>  
  
-   <span data-ttu-id="24f6f-105">使用して、<xref:System.AsyncCallback>個別のスレッドで非同期操作の結果を処理するデリゲート。</span><span class="sxs-lookup"><span data-stu-id="24f6f-105">Use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread.</span></span> <span data-ttu-id="24f6f-106">この方法は、このトピックで示されています。</span><span class="sxs-lookup"><span data-stu-id="24f6f-106">This approach is demonstrated in this topic.</span></span>  
  
-   <span data-ttu-id="24f6f-107">使用して、<xref:System.IAsyncResult.IsCompleted%2A>のプロパティ、 <xref:System.IAsyncResult> 、非同期操作によって返される**開始** *OperationName*メソッド操作が完了したかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="24f6f-107">Use the <xref:System.IAsyncResult.IsCompleted%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin** *OperationName* method to determine whether the operation has completed.</span></span> <span data-ttu-id="24f6f-108">この方法は、次を参照してください。[非同期操作のステータスのポーリング](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md)です。</span><span class="sxs-lookup"><span data-stu-id="24f6f-108">For an example that demonstrates this approach, see [Polling for the Status of an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="24f6f-109">例</span><span class="sxs-lookup"><span data-stu-id="24f6f-109">Example</span></span>  
 <span data-ttu-id="24f6f-110">次のコード例では、非同期のメソッドの使用方法を示します、<xref:System.Net.Dns>クラス ユーザーが指定したコンピューターのドメイン ネーム システム (DNS) 情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="24f6f-110">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System (DNS) information for user-specified computers.</span></span> <span data-ttu-id="24f6f-111">この例で作成、<xref:System.AsyncCallback>を参照するデリゲート、`ProcessDnsInformation`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="24f6f-111">This example creates an <xref:System.AsyncCallback> delegate that references the `ProcessDnsInformation` method.</span></span> <span data-ttu-id="24f6f-112">このメソッドは、DNS 情報の非同期要求ごとに 1 回呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="24f6f-112">This method is called once for each asynchronous request for DNS information.</span></span>  
  
 <span data-ttu-id="24f6f-113">渡されるユーザー指定のホストに注意してください、 <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.Object>パラメーター。</span><span class="sxs-lookup"><span data-stu-id="24f6f-113">Note that the user-specified host is passed to the <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.Object> parameter.</span></span> <span data-ttu-id="24f6f-114">示す例を定義してより複雑な状態のオブジェクトを使用して、次を参照してください。 [AsyncCallback デリゲートおよび状態オブジェクトを使用して](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)です。</span><span class="sxs-lookup"><span data-stu-id="24f6f-114">For an example that demonstrates defining and using a more complex state object, see [Using an AsyncCallback Delegate and State Object](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md).</span></span>  
  
 [!code-csharp[AsyncDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateNoStateObject.cs#4)]
 [!code-vb[AsyncDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateNoState.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="24f6f-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="24f6f-115">See Also</span></span>  
 [<span data-ttu-id="24f6f-116">イベント ベースの非同期パターン (EAP)</span><span class="sxs-lookup"><span data-stu-id="24f6f-116">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [<span data-ttu-id="24f6f-117">イベントベースの非同期パターンの概要</span><span class="sxs-lookup"><span data-stu-id="24f6f-117">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [<span data-ttu-id="24f6f-118">IAsyncResult を使用した非同期メソッドの呼び出し</span><span class="sxs-lookup"><span data-stu-id="24f6f-118">Calling Asynchronous Methods Using IAsyncResult</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-asynchronous-methods-using-iasyncresult.md)  
 [<span data-ttu-id="24f6f-119">AsyncCallback デリゲートおよび状態オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="24f6f-119">Using an AsyncCallback Delegate and State Object</span></span>](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
