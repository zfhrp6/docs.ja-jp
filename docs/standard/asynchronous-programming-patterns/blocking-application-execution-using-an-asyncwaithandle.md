---
title: AsyncWaitHandle の使用によるアプリケーション実行のブロック
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- blocks, asynchronous operations
- ending asynchronous operations
- asynchronous programming, ending operations
- asynchronous programming, blocking applications
- stopping asynchronous operations
- blocking application execution
ms.assetid: 3e32daf2-8161-4e8f-addd-9fd9ff101b03
caps.latest.revision: ''
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 380080c0aa05bc5b94c9ec5fe471f2f255562cd2
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/26/2018
---
# <a name="blocking-application-execution-using-an-asyncwaithandle"></a>AsyncWaitHandle の使用によるアプリケーション実行のブロック
非同期操作の結果の待機中に、他の作業を継続できないアプリケーションは、操作が完了するまでブロックする必要があります。 次のオプションのいずれかを使用して、非同期操作が完了するまでの待機中に、アプリケーションのメイン スレッドをブロックします。  
  
-   非同期操作の **Begin***OperationName* メソッドによって返される <xref:System.IAsyncResult> の <xref:System.IAsyncResult.AsyncWaitHandle%2A> プロパティを使用します。 このトピックでは、この方法のデモが実行されます。  
  
-   非同期操作の **End***OperationName* メソッドを呼び出します。 この方法をデモの例については、「[非同期操作の終了によるアプリケーション実行のブロック](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md)」を参照してください。  
  
 非同期操作が完了するまでブロックする 1 つ以上の <xref:System.Threading.WaitHandle> を使用するアプリケーションは、通常は **Begin***OperationName* メソッドを呼び出し、操作の結果なしで実行できる任意の作業を実行し、非同期操作が完了するまでブロックします。 アプリケーションは、<xref:System.IAsyncResult.AsyncWaitHandle%2A> を使用して <xref:System.Threading.WaitHandle.WaitOne%2A> メソッドのいずれかを呼び出し、単一の操作上でブロックできます。 非同期操作のセットが完了するまで待機しながらブロックするには、関連する <xref:System.IAsyncResult.AsyncWaitHandle%2A> オブジェクトを配列に格納し、<xref:System.Threading.WaitHandle.WaitAll%2A> メソッドのいずれかを呼び出します。 非同期操作のいずれかのセットが完了するまで待機しながらブロックするには、関連する <xref:System.IAsyncResult.AsyncWaitHandle%2A> オブジェクトを配列に格納し、<xref:System.Threading.WaitHandle.WaitAny%2A> メソッドのいずれかを呼び出します。  
  
## <a name="example"></a>例  
 次のコード例は、ユーザー指定のコンピューターのドメイン ネーム システム情報を取得するために、DNS クラスの非同期メソッドを使用してデモを実行します。 例では、非同期操作に関連付けられた <xref:System.Threading.WaitHandle> を使用して、ブロックのデモを実行します。 この方法を使用する場合は必要ないため、`null` (Visual Basic の場合は `Nothing`) は、<xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` と `stateObject` パラメーターに渡されることに注意してください。  
  
 [!code-csharp[AsyncDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlockWait.cs#2)]
 [!code-vb[AsyncDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlockWait.vb#2)]  
  
## <a name="see-also"></a>関連項目  
 [イベント ベースの非同期パターン (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [イベントベースの非同期パターンの概要](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
