---
title: "Blocking Application Execution by Ending an Async Operation | Microsoft Docs"
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
  - "blocks, asynchronous operations"
  - "AsyncWaitHandle property"
  - "asynchronous programming, blocking applications"
  - "blocking application execution"
ms.assetid: cc5e2834-a65b-4df8-b750-7bdb79997fee
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# Blocking Application Execution by Ending an Async Operation
非同期操作の結果を待っている間に他の作業を行うことができないアプリケーションは、操作が完了するまでブロックする必要があります。  非同期操作の完了を待っている間に、アプリケーションのメイン スレッドをブロックするには、次のいずれかのオプションを使用します。  
  
-   非同期操作の **\[終了\]** *OperationName* のメソッドを呼び出します。  この方法については、このトピックで説明します。  
  
-   非同期操作の **\[開始\]** *OperationName* のメソッドによって返される <xref:System.IAsyncResult> の <xref:System.IAsyncResult.AsyncWaitHandle%2A> のプロパティを使用します。  この方法の実行例については、「[Blocking Application Execution Using an AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md)」を参照してください。  
  
 非同期操作が完了するまでブロックするに **\[終了\]** *OperationName* のメソッドを使用するアプリケーションは、通常 **\[開始\]** *OperationName* のメソッドを呼び出した後、操作の結果がなくても行うことができます。次に、**\[終了\]** *OperationName*を作業を呼び出します。  
  
## 例  
 <xref:System.Net.Dns> クラスで非同期メソッドを使用して、ユーザー指定のコンピューターのドメイン ネーム システム \(DNS\) 情報を取得するコード例を次に示します。  ここで使用する方法では、<xref:System.Net.Dns.BeginGetHostByName%2A> の `requestCallback` パラメーターと `stateObject` パラメーターは不要なので、これらには `null` \(Visual Basic では `Nothing`\) が渡されます。  
  
 [!code-csharp[AsyncDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlock.cs#1)]
 [!code-vb[AsyncDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlock.vb#1)]  
  
## 参照  
 [Event\-based Asynchronous Pattern \(EAP\)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)   
 [Event\-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)