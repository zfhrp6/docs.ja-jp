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
# <a name="using-an-asynccallback-delegate-to-end-an-asynchronous-operation"></a>AsyncCallback デリゲートの使用による非同期操作の終了
非同期操作の結果の待機中にその他の作業を実行できるアプリケーションは、操作が完了するまで待機をブロックしないでください。 非同期操作の完了を待っている間に命令の実行を続行するのにには、次のオプションのいずれかを使用します。  
  
-   使用して、<xref:System.AsyncCallback>個別のスレッドで非同期操作の結果を処理するデリゲート。 この方法は、このトピックで示されています。  
  
-   使用して、<xref:System.IAsyncResult.IsCompleted%2A>のプロパティ、 <xref:System.IAsyncResult> 、非同期操作によって返される**開始** *OperationName*メソッド操作が完了したかどうかを確認します。 この方法は、次を参照してください。[非同期操作のステータスのポーリング](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md)です。  
  
## <a name="example"></a>例  
 次のコード例では、非同期のメソッドの使用方法を示します、<xref:System.Net.Dns>クラス ユーザーが指定したコンピューターのドメイン ネーム システム (DNS) 情報を取得します。 この例で作成、<xref:System.AsyncCallback>を参照するデリゲート、`ProcessDnsInformation`メソッドです。 このメソッドは、DNS 情報の非同期要求ごとに 1 回呼び出されます。  
  
 渡されるユーザー指定のホストに注意してください、 <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.Object>パラメーター。 示す例を定義してより複雑な状態のオブジェクトを使用して、次を参照してください。 [AsyncCallback デリゲートおよび状態オブジェクトを使用して](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)です。  
  
 [!code-csharp[AsyncDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateNoStateObject.cs#4)]
 [!code-vb[AsyncDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateNoState.vb#4)]  
  
## <a name="see-also"></a>関連項目  
 [イベント ベースの非同期パターン (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [イベントベースの非同期パターンの概要](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [IAsyncResult を使用した非同期メソッドの呼び出し](../../../docs/standard/asynchronous-programming-patterns/calling-asynchronous-methods-using-iasyncresult.md)  
 [AsyncCallback デリゲートおよび状態オブジェクトの使用](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
