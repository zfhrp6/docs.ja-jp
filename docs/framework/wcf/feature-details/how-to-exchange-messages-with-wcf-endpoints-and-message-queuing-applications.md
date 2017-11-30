---
title: "方法 : WCF エンドポイントとメッセージ キュー アプリケーションを使用してメッセージを交換する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 62210fd8-a372-4d55-ab9b-c99827d1885e
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d09b8e662b2876fa5d5c5246ea7e7a4998cde9ea
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications"></a>方法 : WCF エンドポイントとメッセージ キュー アプリケーションを使用してメッセージを交換する
既存の MSMQ アプリケーションを [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] アプリケーションと統合できます。それには、メッセージ キュー (MSMQ) 統合バインディングを使用して MSMQ メッセージを [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] メッセージとの間で相互に変換できます。 これにより、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントから MSMQ の受信側アプリケーションを呼び出したり、MSMQ の送信元アプリケーションから [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスを呼び出したりできます。  
  
 ここでは、<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> を使用して、(1) System.Messaging を使用して記述された MSMQ アプリケーション サービスと [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントの間および (2) MSMQ アプリケーション クライアントと [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスの間で、キュー通信を行う方法について説明します。  
  
 MSMQ 受信側のアプリケーションを呼び出す方法を説明する完全なサンプルについては、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]クライアントを参照してください、[メッセージ キューへの Windows Communication Foundation](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)サンプルです。  
  
 呼び出す方法を示す完全なサンプルについては、 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] MSMQ クライアントからサービスを参照してください、[メッセージ キューが Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)サンプルです。  
  
### <a name="to-create-a-wcf-service-that-receives-messages-from-a-msmq-client"></a>MSMQ クライアントからのメッセージを受信する WCF サービスを作成するには  
  
1.  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスのサービス コントラクトを定義するインターフェイスを、次のコード例に示すように定義します。このサービスは、MSMQ の送信元アプリケーションからキューに置かれたメッセージを受信します。  
  
     [!code-csharp[S_MsmqToWcf#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#1)]
     [!code-vb[S_MsmqToWcf#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#1)]  
  
2.  次のコード例に示すように、定義したインターフェイスを実装し、<xref:System.ServiceModel.ServiceBehaviorAttribute> 属性をクラスに適用します。  
  
     [!code-csharp[S_MsmqToWcf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#2)]
     [!code-vb[S_MsmqToWcf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#2)]  
  
3.  <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> を指定する構成ファイルを作成します。  
  
  
  
4.  構成されたバインディングを使用する <xref:System.ServiceModel.ServiceHost> オブジェクトをインスタンス化します。  
  
  
  
### <a name="to-create-a-wcf-client-that-sends-messages-to-a-msmq-receiver-application"></a>MSMQ の受信側アプリケーションにメッセージを送信する WCF クライアントを作成するには  
  
1.  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントのサービス コントラクトを定義するインターフェイスを、次のコード例に示すように定義します。このクライアントは、キューに置かれたメッセージを MSMQ の受信側に送信します。  
  
     [!code-csharp[S_WcfToMsmq#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/proxy.cs#6)]
     [!code-vb[S_WcfToMsmq#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/proxy.vb#6)]  
  
2.  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントが MSMQ の受信側を呼び出すために使用するクライアント クラスを定義します。  
  
     [!code-csharp[S_WcfToMsmq#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#2)]
     [!code-vb[S_WcfToMsmq#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#2)]  
  
3.  MsmqIntegrationBinding バインディングの使用を指定する構成を作成します。  
  
     [!code-csharp[S_WcfToMsmq#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#3)]
     [!code-vb[S_WcfToMsmq#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#3)]  
  
4.  クライアント クラスのインスタンスを作成し、メッセージ受信サービスによって定義されたメソッドを呼び出します。  
  
     [!code-csharp[S_WcfToMsmq#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/client.cs#4)]  
  
## <a name="see-also"></a>関連項目  
 [キューの概要](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 [方法: Exchange の WCF エンドポイントとメッセージのキュー](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 [メッセージ キューへの Windows Communication Foundation](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)  
 [メッセージ キュー (MSMQ) をインストールします。](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)  
 [Windows Communication foundation キュー メッセージ](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)  
 [メッセージ キューを介したメッセージ セキュリティ](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
