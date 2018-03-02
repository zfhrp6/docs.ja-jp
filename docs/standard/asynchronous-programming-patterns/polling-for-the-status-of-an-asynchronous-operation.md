---
title: "非同期操作のステータスのポーリング"
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
- asynchronous programming, status polling
- polling asynchronous operation status
- status information [.NET Framework], asynchronous operations
ms.assetid: b541af31-dacb-4e20-8847-1b1ff7c35363
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 51e2ada4b493e8b1cbe0744c00fc2c25f9a266fb
ms.sourcegitcommit: 957c696f25e39f923a827fc3ad5e8ab72768838c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/13/2018
---
# <a name="polling-for-the-status-of-an-asynchronous-operation"></a><span data-ttu-id="ad782-102">非同期操作のステータスのポーリング</span><span class="sxs-lookup"><span data-stu-id="ad782-102">Polling for the Status of an Asynchronous Operation</span></span>
<span data-ttu-id="ad782-103">非同期操作の結果の待機中に、他の作業を実行できるアプリケーションは、操作が完了するまで待機をブロックする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="ad782-103">Applications that can do other work while waiting for the results of an asynchronous operation should not block waiting until the operation completes.</span></span> <span data-ttu-id="ad782-104">次のオプションのいずれかを使用して、非同期操作が完了するまでの待機中に、手順の実行を継続します。</span><span class="sxs-lookup"><span data-stu-id="ad782-104">Use one of the following options to continue executing instructions while waiting for an asynchronous operation to complete:</span></span>  
  
-   <span data-ttu-id="ad782-105">非同期操作の **Begin***OperationName* メソッドによって返される <xref:System.IAsyncResult> の <xref:System.IAsyncResult.IsCompleted%2A> プロパティを使用して、その操作が完了したかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="ad782-105">Use the <xref:System.IAsyncResult.IsCompleted%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin***OperationName* method to determine whether the operation has completed.</span></span> <span data-ttu-id="ad782-106">この方法はポーリングと呼ばれ、このトピックでデモが実行されます。</span><span class="sxs-lookup"><span data-stu-id="ad782-106">This approach is known as polling and is demonstrated in this topic.</span></span>  
  
-   <span data-ttu-id="ad782-107"><xref:System.AsyncCallback> デリゲートを使用し、個別のスレッドで非同期操作の結果を処理します。</span><span class="sxs-lookup"><span data-stu-id="ad782-107">Use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread.</span></span> <span data-ttu-id="ad782-108">この方法のデモを実行する例については、「[AsyncCallback デリゲートの使用による非同期操作の終了](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ad782-108">For an example that demonstrates this approach, see [Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad782-109">例</span><span class="sxs-lookup"><span data-stu-id="ad782-109">Example</span></span>  
 <span data-ttu-id="ad782-110">次のコード例は、ユーザー指定のコンピューターのドメイン ネーム システム情報を取得するために、<xref:System.Net.Dns> クラスの非同期メソッドを使用してデモを実行します。</span><span class="sxs-lookup"><span data-stu-id="ad782-110">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="ad782-111">この例では、非同期操作が開始され、操作が完了するまでコンソールにピリオド (".") が出力されます。</span><span class="sxs-lookup"><span data-stu-id="ad782-111">This example starts the asynchronous operation and then prints periods (".") at the console until the operation is complete.</span></span> <span data-ttu-id="ad782-112">この方法を使用する場合はこれらの引数は必要ないため、**null** (Visual Basic の場合は **Nothing**) は、<xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.AsyncCallback> と <xref:System.Object> パラメーターに渡されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ad782-112">Note that **null** (**Nothing** in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.AsyncCallback> and <xref:System.Object> parameters because these arguments are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_Poll.cs#3)]
 [!code-vb[AsyncDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_Poll.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="ad782-113">参照</span><span class="sxs-lookup"><span data-stu-id="ad782-113">See Also</span></span>  
 [<span data-ttu-id="ad782-114">イベント ベースの非同期パターン (EAP)</span><span class="sxs-lookup"><span data-stu-id="ad782-114">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [<span data-ttu-id="ad782-115">イベントベースの非同期パターンの概要</span><span class="sxs-lookup"><span data-stu-id="ad782-115">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
