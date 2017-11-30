---
title: "IAsyncResult を使用した非同期メソッドの呼び出し"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ending asynchronous operations
- waiting for asynchronous operations
- asynchronous method calling
- calling asynchronous methods
- asynchronous programming, calling asynchronous methods
- IAsyncResult interface, calling asynchronous methods
- stopping asynchronous operations
ms.assetid: 07fba116-045b-473c-a0b7-acdbeb49861f
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 81c05aeae00e79f614ef1514e54765b21e7e2dde
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="calling-asynchronous-methods-using-iasyncresult"></a><span data-ttu-id="c58da-102">IAsyncResult を使用した非同期メソッドの呼び出し</span><span class="sxs-lookup"><span data-stu-id="c58da-102">Calling Asynchronous Methods Using IAsyncResult</span></span>
<span data-ttu-id="c58da-103">.NET Framework およびサード パーティ製のクラス ライブラリ内の型は、アプリケーションをアプリケーションのメイン スレッド以外のスレッドで非同期操作を実行中に実行を継続できるようにするメソッドを提供できます。</span><span class="sxs-lookup"><span data-stu-id="c58da-103">Types in the .NET Framework and third-party class libraries can provide methods that allow an application to continue executing while performing asynchronous operations in threads other than the main application thread.</span></span> <span data-ttu-id="c58da-104">次のセクションでは、記述しを使用して非同期メソッドを呼び出すことができます、さまざまな方法を示すコード例を提供、<xref:System.IAsyncResult>デザイン パターンです。</span><span class="sxs-lookup"><span data-stu-id="c58da-104">The following sections describe and provide code examples that demonstrate the different ways you can call asynchronous methods that use the <xref:System.IAsyncResult> design pattern.</span></span>  
  
-   <span data-ttu-id="c58da-105">[非同期操作を終了してアプリケーションの実行をブロックして](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md)です。</span><span class="sxs-lookup"><span data-stu-id="c58da-105">[Blocking Application Execution by Ending an Async Operation](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).</span></span>  
  
-   <span data-ttu-id="c58da-106">[AsyncWaitHandle の使用、アプリケーションの実行をブロックして](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md)です。</span><span class="sxs-lookup"><span data-stu-id="c58da-106">[Blocking Application Execution Using an AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).</span></span>  
  
-   <span data-ttu-id="c58da-107">[非同期操作のステータスのポーリング](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md)です。</span><span class="sxs-lookup"><span data-stu-id="c58da-107">[Polling for the Status of an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).</span></span>  
  
-   <span data-ttu-id="c58da-108">[AsyncCallback デリゲートを使用して、非同期操作を終了する](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)です。</span><span class="sxs-lookup"><span data-stu-id="c58da-108">[Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c58da-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="c58da-109">See Also</span></span>  
 [<span data-ttu-id="c58da-110">イベント ベースの非同期パターン (EAP)</span><span class="sxs-lookup"><span data-stu-id="c58da-110">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [<span data-ttu-id="c58da-111">イベントベースの非同期パターンの概要</span><span class="sxs-lookup"><span data-stu-id="c58da-111">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
