---
title: "AsyncWaitHandle の使用によるアプリケーション実行のブロック"
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
- blocks, asynchronous operations
- ending asynchronous operations
- asynchronous programming, ending operations
- asynchronous programming, blocking applications
- stopping asynchronous operations
- blocking application execution
ms.assetid: 3e32daf2-8161-4e8f-addd-9fd9ff101b03
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2660b3cbf7e8ee43a22edbfb66a4262684983b87
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="blocking-application-execution-using-an-asyncwaithandle"></a>AsyncWaitHandle の使用によるアプリケーション実行のブロック
非同期操作の結果の待機中に他の作業を続行できませんできるアプリケーションは、操作が完了するまでブロックする必要があります。 非同期操作の完了を待機中に、アプリケーションのメイン スレッドをブロックするのにには、次のオプションのいずれかを使用します。  
  
-   使用して、<xref:System.IAsyncResult.AsyncWaitHandle%2A>のプロパティ、 <xref:System.IAsyncResult> 、非同期操作によって返される**開始** *OperationName*メソッドです。 この方法は、このトピックで示されています。  
  
-   非同期操作の呼び出し**終了** *OperationName*メソッドです。 この方法は、次を参照してください。 [、非同期操作を終了してアプリケーションの実行をブロックして](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md)です。  
  
 1 つまたは複数を使用するアプリケーション<xref:System.Threading.WaitHandle>非同期操作が完了するまでブロックするオブジェクトを呼び出す通常、**開始** *OperationName*メソッド、何も処理を実行します。操作と、非同期処理されるまでブロックの結果なし次のコマンドを完了します。 1 回の操作でのいずれかを呼び出すことによってアプリケーションをブロックすることができます、<xref:System.Threading.WaitHandle.WaitOne%2A>メソッドを使用して、<xref:System.IAsyncResult.AsyncWaitHandle%2A>です。 一連の非同期操作の完了を待っている間にブロックは、格納、関連付けられている<xref:System.IAsyncResult.AsyncWaitHandle%2A>オブジェクト配列の最初の呼び出しで、<xref:System.Threading.WaitHandle.WaitAll%2A>メソッドです。 いずれかの一連の非同期操作が完了するを待っている間にブロックは、格納、関連付けられている<xref:System.IAsyncResult.AsyncWaitHandle%2A>オブジェクト配列の最初の呼び出しで、<xref:System.Threading.WaitHandle.WaitAny%2A>メソッドです。  
  
## <a name="example"></a>例  
 次のコード例では、ユーザー指定のコンピューターのドメイン ネーム システム情報を取得する DNS クラスで非同期メソッドの使用を示します。 例では、ブロックを使用して、<xref:System.Threading.WaitHandle>非同期操作に関連付けられています。 なお`null`(`Nothing` Visual Basic で) が渡されました、 <xref:System.Net.Dns.BeginGetHostByName%2A> `requestCallback`と`stateObject`パラメーターこのアプローチを使用するときに、必要なこれらがないためです。  
  
 [!code-csharp[AsyncDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlockWait.cs#2)]
 [!code-vb[AsyncDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlockWait.vb#2)]  
  
## <a name="see-also"></a>関連項目  
 [イベント ベースの非同期パターン (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [イベントベースの非同期パターンの概要](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
