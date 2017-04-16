---
title: "Using an AsyncCallback Delegate to End an Asynchronous Operation | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ending asynchronous operations"
  - "asynchronous programming, ending operations"
  - "AsyncCallback delegate"
  - "stopping asynchronous operations"
ms.assetid: 9d97206c-8917-406c-8961-7d0909d84eeb
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# Using an AsyncCallback Delegate to End an Asynchronous Operation
非同期操作の結果を待っている間に他の作業を行うことができるアプリケーションは、操作が完了するまで待機をブロックしないでください。  非同期操作の完了を待っている間に、命令の実行を継続するには、次のいずれかのオプションを使用します。  
  
-   <xref:System.AsyncCallback> デリゲートを使用して、個別のスレッド内の非同期操作の結果を処理します。  この方法については、このトピックで説明します。  
  
-   操作が完了したかどうかを確認するには、非同期操作の **\[開始\]** *OperationName* のメソッドによって返される <xref:System.IAsyncResult> の <xref:System.IAsyncResult.IsCompleted%2A> のプロパティを使用します。  この方法の実行例については、「[Polling for the Status of an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md)」を参照してください。  
  
## 例  
 <xref:System.Net.Dns> クラスで非同期メソッドを使用して、ユーザー指定のコンピューターのドメイン ネーム システム \(DNS\) 情報を取得するコード例を次に示します。  この例では、`ProcessDnsInformation` メソッドを参照する <xref:System.AsyncCallback> デリゲートを作成します。  このメソッドは、DNS 情報の非同期要求を行うたびに一度だけ呼び出されます。  
  
 ユーザー指定のホストが <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.Object> パラメーターに渡される点に注意してください。  さらに複雑な状態オブジェクトの定義および使い方の例については、「[Using an AsyncCallback Delegate and State Object](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)」を参照してください。  
  
 [!code-csharp[AsyncDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateNoStateObject.cs#4)]
 [!code-vb[AsyncDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateNoState.vb#4)]  
  
## 参照  
 [Event\-based Asynchronous Pattern \(EAP\)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)   
 [Event\-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)   
 [Calling Asynchronous Methods Using IAsyncResult](../../../docs/standard/asynchronous-programming-patterns/calling-asynchronous-methods-using-iasyncresult.md)   
 [Using an AsyncCallback Delegate and State Object](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)