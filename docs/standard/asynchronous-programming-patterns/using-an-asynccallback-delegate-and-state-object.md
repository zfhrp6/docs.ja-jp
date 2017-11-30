---
title: "AsyncCallback デリゲートおよび状態オブジェクトの使用"
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
- asynchronous programming, delegates
- AsyncCallback delegate, samples
- asynchronous programming, state objects
- IAsyncResult interface, samples
ms.assetid: e3e5475d-c5e9-43f0-928e-d18df8ca1f1d
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e8793a78289e9b58407038f41cc9d403ff9f9940
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="using-an-asynccallback-delegate-and-state-object"></a><span data-ttu-id="1cbdd-102">AsyncCallback デリゲートおよび状態オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="1cbdd-102">Using an AsyncCallback Delegate and State Object</span></span>
<span data-ttu-id="1cbdd-103">使用すると、<xref:System.AsyncCallback>個別のスレッドで非同期操作の結果を処理するデリゲート、コールバックの間で情報を渡すと、最終的な結果を取得する状態オブジェクトを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="1cbdd-103">When you use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread, you can use a state object to pass information between the callbacks and to retrieve a final result.</span></span> <span data-ttu-id="1cbdd-104">このトピックでは、例を展開する方法を示します[AsyncCallback デリゲートを使用して、非同期操作を終了する](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)です。</span><span class="sxs-lookup"><span data-stu-id="1cbdd-104">This topic demonstrates that practice by expanding the example in [Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1cbdd-105">例</span><span class="sxs-lookup"><span data-stu-id="1cbdd-105">Example</span></span>  
 <span data-ttu-id="1cbdd-106">次のコード例では、非同期のメソッドの使用方法を示します、<xref:System.Net.Dns>クラス ユーザーが指定したコンピューターのドメイン ネーム システム (DNS) 情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="1cbdd-106">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System (DNS) information for user-specified computers.</span></span> <span data-ttu-id="1cbdd-107">この例は、定義、使用して、`HostRequest`状態情報を格納するクラス。</span><span class="sxs-lookup"><span data-stu-id="1cbdd-107">This example defines and uses the `HostRequest` class to store state information.</span></span> <span data-ttu-id="1cbdd-108">A`HostRequest`オブジェクトは、ユーザーが入力した各コンピューター名の作成を取得します。</span><span class="sxs-lookup"><span data-stu-id="1cbdd-108">A `HostRequest` object gets created for each computer name entered by the user.</span></span> <span data-ttu-id="1cbdd-109">このオブジェクトは、<xref:System.Net.Dns.BeginGetHostByName%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="1cbdd-109">This object is passed to the <xref:System.Net.Dns.BeginGetHostByName%2A> method.</span></span> <span data-ttu-id="1cbdd-110">`ProcessDnsInformation`メソッドは、要求が完了するたびにします。</span><span class="sxs-lookup"><span data-stu-id="1cbdd-110">The `ProcessDnsInformation` method is called each time a request completes.</span></span> <span data-ttu-id="1cbdd-111">`HostRequest`を使用してオブジェクトを取得、<xref:System.IAsyncResult.AsyncState%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="1cbdd-111">The `HostRequest` object is retrieved using the <xref:System.IAsyncResult.AsyncState%2A> property.</span></span> <span data-ttu-id="1cbdd-112">`ProcessDnsInformation`メソッドを使用、`HostRequest`を格納するオブジェクト、<xref:System.Net.IPHostEntry>要求によって返される、または<xref:System.Net.Sockets.SocketException>要求によってスローされます。</span><span class="sxs-lookup"><span data-stu-id="1cbdd-112">The `ProcessDnsInformation` method uses the `HostRequest` object to store the <xref:System.Net.IPHostEntry> returned by the request or a <xref:System.Net.Sockets.SocketException> thrown by the request.</span></span> <span data-ttu-id="1cbdd-113">すべての要求が完了したときに、アプリケーションが反復、`HostRequest`オブジェクトおよび DNS 情報を表示または<xref:System.Net.Sockets.SocketException>エラー メッセージ。</span><span class="sxs-lookup"><span data-stu-id="1cbdd-113">When all requests are complete, the application iterates over the `HostRequest` objects and displays the DNS information or <xref:System.Net.Sockets.SocketException> error message.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateWithStateObject.cs#5)]
 [!code-vb[AsyncDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateWithStateObject.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="1cbdd-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="1cbdd-114">See Also</span></span>  
 [<span data-ttu-id="1cbdd-115">イベント ベースの非同期パターン (EAP)</span><span class="sxs-lookup"><span data-stu-id="1cbdd-115">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [<span data-ttu-id="1cbdd-116">イベントベースの非同期パターンの概要</span><span class="sxs-lookup"><span data-stu-id="1cbdd-116">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [<span data-ttu-id="1cbdd-117">AsyncCallback デリゲートの使用による非同期操作の終了</span><span class="sxs-lookup"><span data-stu-id="1cbdd-117">Using an AsyncCallback Delegate to End an Asynchronous Operation</span></span>](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)
