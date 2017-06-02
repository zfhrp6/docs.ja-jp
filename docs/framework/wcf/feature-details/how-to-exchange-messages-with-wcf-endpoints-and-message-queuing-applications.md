---
title: "方法 : WCF エンドポイントとメッセージ キュー アプリケーションを使用してメッセージを交換する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 62210fd8-a372-4d55-ab9b-c99827d1885e
caps.latest.revision: 18
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 18
---
# 方法 : WCF エンドポイントとメッセージ キュー アプリケーションを使用してメッセージを交換する
既存の MSMQ アプリケーションを [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] アプリケーションと統合できます。それには、メッセージ キュー (MSMQ) 統合バインディングを使用して MSMQ メッセージを [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] メッセージとの間で相互に変換できます。 これにより、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントから MSMQ の受信側アプリケーションを呼び出したり、MSMQ の送信元アプリケーションから [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスを呼び出したりできます。  
  
 このセクションで使用する方法について説明<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>間キューに置かれた通信の (1) [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] System.Messaging および (2) MSMQ アプリケーション クライアントを使用して作成された MSMQ アプリケーション サービスとクライアントと[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]サービスです。  
  
 MSMQ 受信側のアプリケーションを呼び出す方法を説明する完全なサンプルについては、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]クライアントを参照してください、 [Windows Communication Foundation メッセージ キューが](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)サンプルです。  
  
 呼び出す方法を説明する完全なサンプルについては、 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] MSMQ クライアントからサービスを参照してください、[メッセージ キューが Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)サンプルです。  
  
### <a name="to-create-a-wcf-service-that-receives-messages-from-a-msmq-client"></a>MSMQ クライアントからのメッセージを受信する WCF サービスを作成するには  
  
1.  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスのサービス コントラクトを定義するインターフェイスを、次のコード例に示すように定義します。このサービスは、MSMQ の送信元アプリケーションからキューに置かれたメッセージを受信します。  
  
     [!code-csharp[S_MsmqToWcf#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#1)]
     [!code-vb[S_MsmqToWcf#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#1)]  
  
2.  インターフェイスを実装し、適用、 <xref:System.ServiceModel.ServiceBehaviorAttribute>クラスに属性の次のコード例に示すようにします。  
  
     [!code-csharp[S_MsmqToWcf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#2)]
     [!code-vb[S_MsmqToWcf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#2)]  
  
3.  指定する構成ファイルを作成、 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>します。  
  
  
  
4.  インスタンスを作成、 <xref:System.ServiceModel.ServiceHost>構成のバインディングを使用するオブジェクト。  
  
  
  
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
 [方法: キューの WCF エンドポイントとメッセージを交換](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)   
 [Windows Communication Foundation メッセージ キュー](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)   
 [メッセージ キュー (MSMQ) をインストールします。](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)   
 [Windows Communication Foundation へのメッセージ キュー](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)   
 [メッセージ キューを介したメッセージ セキュリティ](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)