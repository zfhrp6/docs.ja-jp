---
title: "カスタム メッセージ フォーマッタ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c07435f3-5214-4791-8961-2c2b61306d71
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 413adbc25e2f92ae2e989290685db6dfeaf58368
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="custom-message-formatters"></a>カスタム メッセージ フォーマッタ
メッセージの内容は、XML 形式で表されることが多く、この形式は通常、アプリケーションにとって処理しやすい形式ではありません。 アプリケーションでは、オブジェクトのプロパティを取得および設定することによってオブジェクトを操作します。 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]使用して、*データ コントラクト*に変換する、<xref:System.ServiceModel.Channels.Message>オブジェクトに、オブジェクトをアプリケーションで簡単に処理します。 このプロセスは、シリアル化および逆シリアル化と呼ばれます。 これと同じ用語が、トランスポート層によって行われるメッセージ ワイヤ形式へのシリアル化とその形式からの逆シリアル化を説明するときに使用されますが、これは関連のないプロセスです。  
  
 データ コントラクトによって実現できないメッセージとオブジェクト間の特殊な変換を実装する必要がある場合、カスタム メッセージ フォーマッタを使用できます。 これを使用するには、クライアントまたはサービス上で特定のコントラクト操作の実行動作を変更または拡張します。  
  
## <a name="custom-message-formatters-on-the-client"></a>クライアントのカスタム メッセージ フォーマッタ  
 <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> インターフェイスは、メッセージからオブジェクトへの変換およびオブジェクトからクライアント アプリケーション用のメッセージへの変換を制御するためのメソッドを定義します。  
  
 このインターフェイスを実装する必要があります。 まず、メッセージを逆シリアル化するための <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%2A> メソッドをオーバーライドします。 このメソッドは、受信メッセージを受信した後でそのメッセージがクライアント操作にディスパッチされる前に呼び出されます。  
  
 次に、オブジェクトをシリアル化するための <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%2A> メソッドをオーバーライドします。 このメソッドは、送信メッセージを送信する前に呼び出されます。  
  
 カスタム フォーマッタをサービス アプリケーションに挿入するには、操作の動作を使用して、<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> オブジェクトを <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A> プロパティに割り当てます。 動作方法については、次を参照してください。[を構成すると、ランタイムのビヘイビアーの使用を拡張する](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)です。  
  
## <a name="custom-message-formatters-on-the-service"></a>サービスのカスタム メッセージ フォーマッタ  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> インターフェイスは、<xref:System.ServiceModel.Channels.Message> オブジェクトを操作用のパラメーターに変換し、これらのパラメーターをサービス アプリケーション用の <xref:System.ServiceModel.Channels.Message> オブジェクトに変換するためのメソッドを定義します。  
  
 このインターフェイスを実装する必要があります。 まず、メッセージを逆シリアル化するための <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%2A> メソッドをオーバーライドします。 このメソッドは、受信メッセージを受信した後でそのメッセージがクライアント操作にディスパッチされる前に呼び出されます。  
  
 次に、オブジェクトをシリアル化するための <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%2A> メソッドをオーバーライドします。 このメソッドは、送信メッセージを送信する前に呼び出されます。  
  
 カスタム フォーマッタをサービス アプリケーションに挿入するには、操作の動作を使用して、<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> オブジェクトを <xref:System.ServiceModel.Dispatcher.DispatchOperation.Formatter%2A> プロパティに割り当てます。 動作方法については、次を参照してください。[を構成すると、ランタイムのビヘイビアーの使用を拡張する](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>  
 [構成して、ランタイムのビヘイビアーの使用を拡張します。](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
