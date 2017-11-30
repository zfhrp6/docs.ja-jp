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
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e1f7f74a8b38c06f6a042d55c0def76ddfc5da77
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="polling-for-the-status-of-an-asynchronous-operation"></a><span data-ttu-id="9142a-102">非同期操作のステータスのポーリング</span><span class="sxs-lookup"><span data-stu-id="9142a-102">Polling for the Status of an Asynchronous Operation</span></span>
<span data-ttu-id="9142a-103">非同期操作の結果の待機中にその他の作業を実行できるアプリケーションは、操作が完了するまで待機をブロックしないでください。</span><span class="sxs-lookup"><span data-stu-id="9142a-103">Applications that can do other work while waiting for the results of an asynchronous operation should not block waiting until the operation completes.</span></span> <span data-ttu-id="9142a-104">非同期操作の完了を待っている間に命令の実行を続行するのにには、次のオプションのいずれかを使用します。</span><span class="sxs-lookup"><span data-stu-id="9142a-104">Use one of the following options to continue executing instructions while waiting for an asynchronous operation to complete:</span></span>  
  
-   <span data-ttu-id="9142a-105">使用して、<xref:System.IAsyncResult.IsCompleted%2A>のプロパティ、 <xref:System.IAsyncResult> 、非同期操作によって返される**開始** *OperationName*メソッド操作が完了したかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="9142a-105">Use the <xref:System.IAsyncResult.IsCompleted%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin** *OperationName* method to determine whether the operation has completed.</span></span> <span data-ttu-id="9142a-106">このアプローチはポーリングと呼ばれ、は、このトピックで説明します。</span><span class="sxs-lookup"><span data-stu-id="9142a-106">This approach is known as polling and is demonstrated in this topic.</span></span>  
  
-   <span data-ttu-id="9142a-107">使用して、<xref:System.AsyncCallback>個別のスレッドで非同期操作の結果を処理するデリゲート。</span><span class="sxs-lookup"><span data-stu-id="9142a-107">Use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread.</span></span> <span data-ttu-id="9142a-108">この方法は、次を参照してください。 [AsyncCallback デリゲートを使用して、非同期操作を終了する](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)です。</span><span class="sxs-lookup"><span data-stu-id="9142a-108">For an example that demonstrates this approach, see [Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9142a-109">例</span><span class="sxs-lookup"><span data-stu-id="9142a-109">Example</span></span>  
 <span data-ttu-id="9142a-110">次のコード例では、非同期のメソッドの使用方法を示します、<xref:System.Net.Dns>ユーザー指定のコンピューターのドメイン ネーム システム情報を取得するクラス。</span><span class="sxs-lookup"><span data-stu-id="9142a-110">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="9142a-111">この例で、非同期操作を開始し、期間に出力します ("です。")、操作が完了するまで、コンソールにします。</span><span class="sxs-lookup"><span data-stu-id="9142a-111">This example starts the asynchronous operation and then prints periods (".") at the console until the operation is complete.</span></span> <span data-ttu-id="9142a-112">注意してください**null** (**何も**Visual Basic で) 渡される、 <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.AsyncCallback>と<xref:System.Object>パラメーターのため、これらの引数は、このアプローチを使用する場合は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="9142a-112">Note that **null** (**Nothing** in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.AsyncCallback> and <xref:System.Object> parameters because these arguments are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_Poll.cs#3)]
 [!code-vb[AsyncDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_Poll.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="9142a-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="9142a-113">See Also</span></span>  
 [<span data-ttu-id="9142a-114">イベント ベースの非同期パターン (EAP)</span><span class="sxs-lookup"><span data-stu-id="9142a-114">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [<span data-ttu-id="9142a-115">イベントベースの非同期パターンの概要</span><span class="sxs-lookup"><span data-stu-id="9142a-115">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
