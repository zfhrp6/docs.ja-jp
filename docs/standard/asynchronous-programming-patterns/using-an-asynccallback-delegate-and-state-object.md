---
title: "Using an AsyncCallback Delegate and State Object | Microsoft Docs"
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
  - "asynchronous programming, delegates"
  - "AsyncCallback delegate, samples"
  - "asynchronous programming, state objects"
  - "IAsyncResult interface, samples"
ms.assetid: e3e5475d-c5e9-43f0-928e-d18df8ca1f1d
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# Using an AsyncCallback Delegate and State Object
別のスレッドで非同期操作の結果を処理するために <xref:System.AsyncCallback> デリゲートを使用するときには、状態オブジェクトを使用すると、コールバック間での情報の受け渡しおよび最終結果の取得ができます。  このトピックでは、「[Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)」の例を拡張するその実例を示します。  
  
## 例  
 <xref:System.Net.Dns> クラスで非同期メソッドを使用して、ユーザー指定のコンピューターのドメイン ネーム システム \(DNS\) 情報を取得するコード例を次に示します。  この例では、`HostRequest` クラスを定義および使用して、状態情報を格納します。  `HostRequest` オブジェクトは、ユーザーによって入力されたコンピューター名ごとに作成されます。  このオブジェクトは、<xref:System.Net.Dns.BeginGetHostByName%2A> メソッドに渡されます。  `ProcessDnsInformation` メソッドは、要求が完了するたびに呼び出されます。  `HostRequest` オブジェクトは、<xref:System.IAsyncResult.AsyncState%2A> プロパティを使用して取得されます。  `ProcessDnsInformation` メソッドは `HostRequest` オブジェクトを使用して、要求によって返された <xref:System.Net.IPHostEntry> または要求によってスローされた <xref:System.Net.Sockets.SocketException> を格納します。  すべての要求が完了すると、アプリケーションは `HostRequest` オブジェクトを反復処理し、DNS 情報または <xref:System.Net.Sockets.SocketException> エラー メッセージを表示します。  
  
 [!code-csharp[AsyncDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateWithStateObject.cs#5)]
 [!code-vb[AsyncDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateWithStateObject.vb#5)]  
  
## 参照  
 [Event\-based Asynchronous Pattern \(EAP\)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)   
 [Event\-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)   
 [Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)