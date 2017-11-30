---
title: "AsyncCallback デリゲートおよび状態オブジェクトの使用"
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
- asynchronous programming, delegates
- AsyncCallback delegate, samples
- asynchronous programming, state objects
- IAsyncResult interface, samples
ms.assetid: e3e5475d-c5e9-43f0-928e-d18df8ca1f1d
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e8793a78289e9b58407038f41cc9d403ff9f9940
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="using-an-asynccallback-delegate-and-state-object"></a>AsyncCallback デリゲートおよび状態オブジェクトの使用
使用すると、<xref:System.AsyncCallback>個別のスレッドで非同期操作の結果を処理するデリゲート、コールバックの間で情報を渡すと、最終的な結果を取得する状態オブジェクトを使用することができます。 このトピックでは、例を展開する方法を示します[AsyncCallback デリゲートを使用して、非同期操作を終了する](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)です。  
  
## <a name="example"></a>例  
 次のコード例では、非同期のメソッドの使用方法を示します、<xref:System.Net.Dns>クラス ユーザーが指定したコンピューターのドメイン ネーム システム (DNS) 情報を取得します。 この例は、定義、使用して、`HostRequest`状態情報を格納するクラス。 A`HostRequest`オブジェクトは、ユーザーが入力した各コンピューター名の作成を取得します。 このオブジェクトは、<xref:System.Net.Dns.BeginGetHostByName%2A>メソッドです。 `ProcessDnsInformation`メソッドは、要求が完了するたびにします。 `HostRequest`を使用してオブジェクトを取得、<xref:System.IAsyncResult.AsyncState%2A>プロパティです。 `ProcessDnsInformation`メソッドを使用、`HostRequest`を格納するオブジェクト、<xref:System.Net.IPHostEntry>要求によって返される、または<xref:System.Net.Sockets.SocketException>要求によってスローされます。 すべての要求が完了したときに、アプリケーションが反復、`HostRequest`オブジェクトおよび DNS 情報を表示または<xref:System.Net.Sockets.SocketException>エラー メッセージ。  
  
 [!code-csharp[AsyncDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateWithStateObject.cs#5)]
 [!code-vb[AsyncDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateWithStateObject.vb#5)]  
  
## <a name="see-also"></a>関連項目  
 [イベント ベースの非同期パターン (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [イベントベースの非同期パターンの概要](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [AsyncCallback デリゲートの使用による非同期操作の終了](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)
