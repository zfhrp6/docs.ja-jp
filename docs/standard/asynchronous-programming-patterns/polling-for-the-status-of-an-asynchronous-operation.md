---
title: "Polling for the Status of an Asynchronous Operation | Microsoft Docs"
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
  - "asynchronous programming, status polling"
  - "polling asynchronous operation status"
  - "status information [.NET Framework], asynchronous operations"
ms.assetid: b541af31-dacb-4e20-8847-1b1ff7c35363
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# Polling for the Status of an Asynchronous Operation
非同期操作の結果を待っている間に他の作業を行うことができるアプリケーションは、操作が完了するまで待機をブロックしないでください。  非同期操作の完了を待っている間に、命令の実行を継続するには、次のいずれかのオプションを使用します。  
  
-   操作が完了したかどうかを確認するには、非同期操作の **\[開始\]** *OperationName* のメソッドによって返される <xref:System.IAsyncResult> の <xref:System.IAsyncResult.IsCompleted%2A> のプロパティを使用します。  この方法はポーリングと呼ばれます。これについては、このトピックで説明します。  
  
-   <xref:System.AsyncCallback> デリゲートを使用して、個別のスレッド内の非同期操作の結果を処理します。  この方法の実行例については、「[Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)」を参照してください。  
  
## 例  
 <xref:System.Net.Dns> クラスで非同期メソッドを使用して、ユーザー指定のコンピューターのドメイン ネーム システム \(DNS\) 情報を取得するコード例を次に示します。  この例では、非同期操作を開始し、操作が完了するまでコンソールにピリオド \("."\) を出力します。  ここで使用する方法では、<xref:System.Net.Dns.BeginGetHostByName%2A> の <xref:System.AsyncCallback> パラメーターと <xref:System.Object> パラメーターは不要なので、これらのパラメーターには **null** \(Visual Basic では **Nothing**\) が渡されます。  
  
 [!code-csharp[AsyncDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_Poll.cs#3)]
 [!code-vb[AsyncDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_Poll.vb#3)]  
  
## 参照  
 [Event\-based Asynchronous Pattern \(EAP\)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)   
 [Event\-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)