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
# <a name="polling-for-the-status-of-an-asynchronous-operation"></a>非同期操作のステータスのポーリング
非同期操作の結果の待機中にその他の作業を実行できるアプリケーションは、操作が完了するまで待機をブロックしないでください。 非同期操作の完了を待っている間に命令の実行を続行するのにには、次のオプションのいずれかを使用します。  
  
-   使用して、<xref:System.IAsyncResult.IsCompleted%2A>のプロパティ、 <xref:System.IAsyncResult> 、非同期操作によって返される**開始** *OperationName*メソッド操作が完了したかどうかを確認します。 このアプローチはポーリングと呼ばれ、は、このトピックで説明します。  
  
-   使用して、<xref:System.AsyncCallback>個別のスレッドで非同期操作の結果を処理するデリゲート。 この方法は、次を参照してください。 [AsyncCallback デリゲートを使用して、非同期操作を終了する](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)です。  
  
## <a name="example"></a>例  
 次のコード例では、非同期のメソッドの使用方法を示します、<xref:System.Net.Dns>ユーザー指定のコンピューターのドメイン ネーム システム情報を取得するクラス。 この例で、非同期操作を開始し、期間に出力します ("です。")、操作が完了するまで、コンソールにします。 注意してください**null** (**何も**Visual Basic で) 渡される、 <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.AsyncCallback>と<xref:System.Object>パラメーターのため、これらの引数は、このアプローチを使用する場合は必要ありません。  
  
 [!code-csharp[AsyncDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_Poll.cs#3)]
 [!code-vb[AsyncDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_Poll.vb#3)]  
  
## <a name="see-also"></a>関連項目  
 [イベント ベースの非同期パターン (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [イベントベースの非同期パターンの概要](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
