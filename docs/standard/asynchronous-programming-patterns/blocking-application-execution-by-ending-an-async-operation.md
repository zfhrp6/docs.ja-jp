---
title: "非同期操作の終了によるアプリケーション実行のブロック"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- blocks, asynchronous operations
- AsyncWaitHandle property
- asynchronous programming, blocking applications
- blocking application execution
ms.assetid: cc5e2834-a65b-4df8-b750-7bdb79997fee
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
dev_langs:
- csharp
- vb
ms.openlocfilehash: ccca6e1e4f6b5cdf098018b59426fb2262e2b346
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="blocking-application-execution-by-ending-an-async-operation"></a>非同期操作の終了によるアプリケーション実行のブロック
非同期操作の結果の待機中に他の作業を続行できませんできるアプリケーションは、操作が完了するまでブロックする必要があります。 非同期操作の完了を待機中に、アプリケーションのメイン スレッドをブロックするのにには、次のオプションのいずれかを使用します。  
  
-   非同期操作を呼び出す**終了** *OperationName*メソッドです。 この方法は、このトピックで示されています。  
  
-   使用して、<xref:System.IAsyncResult.AsyncWaitHandle%2A>のプロパティ、 <xref:System.IAsyncResult> 、非同期操作によって返される**開始** *OperationName*メソッドです。 この方法は、次を参照してください。[ブロックの実行を使用してアプリケーション AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md)です。  
  
 使用するアプリケーション、**終了** *OperationName*非同期操作が完了するまでブロックするメソッドの呼び出しは通常、**開始** *OperationName*メソッド、何も処理を操作の結果なしで実行できますし、**終了** *OperationName*です。  
  
## <a name="example"></a>例  
 次のコード例では、非同期のメソッドの使用方法を示します、<xref:System.Net.Dns>ユーザー指定のコンピューターのドメイン ネーム システム情報を取得するクラス。 注意してください`null`(`Nothing` Visual Basic で) 渡される、 <xref:System.Net.Dns.BeginGetHostByName%2A> `requestCallback`と`stateObject`パラメーターのため、これらの引数は、このアプローチを使用する場合は必要ありません。  
  
 [!code-csharp[AsyncDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlock.cs#1)]
 [!code-vb[AsyncDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlock.vb#1)]  
  
## <a name="see-also"></a>関連項目  
 [イベント ベースの非同期パターン (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [イベントベースの非同期パターンの概要](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
