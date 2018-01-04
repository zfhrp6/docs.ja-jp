---
title: "方法 : WCF エンドポイントを使用してキューに置かれたメッセージを交換する"
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
ms.assetid: 938e7825-f63a-4c3d-b603-63772fabfdb3
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 975c5ea5d5b3ab81d37b713e84f273e4c2c1c0b5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-exchange-queued-messages-with-wcf-endpoints"></a>方法 : WCF エンドポイントを使用してキューに置かれたメッセージを交換する
キューを使用すると、通信中にサービスを使用できない場合でも、クライアントと [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービス間で信頼できるメッセージングを使用できます。 以下の手順は、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスの実装時に、標準のキューに置かれたバインディングを使用してクライアントとサービス間で永続的な通信を確保する方法を示しています。  
  
 ここでは、<xref:System.ServiceModel.NetMsmqBinding> を使用して [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントと [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービス間でキューによる通信を行う方法について説明します。  
  
### <a name="to-use-queuing-in-a-wcf-service"></a>WCF サービスでキューを使用するには  
  
1.  <xref:System.ServiceModel.ServiceContractAttribute> でマークされたインターフェイスを使用して、サービス コントラクトを定義します。 サービス コントラクトの一部であるインターフェイスの動作を <xref:System.ServiceModel.OperationContractAttribute> でマークし、メソッドに対して応答が返されないため、一方向と指定します。 サービス コントラクトおよびその操作の定義の例を次のコードに示します。  
  
     [!code-csharp[S_Msmq_Transacted#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#1)]
     [!code-vb[S_Msmq_Transacted#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#1)]  
  
2.  サービス コントラクトがユーザー定義型を渡す場合は、その型のデータ コントラクトを定義する必要があります。 次のコードは、2 つのデータ コントラクト (`PurchaseOrder` および `PurchaseOrderLineItem`) を示します。 これらの 2 つの型は、サービスに送信されるデータを定義します  (このデータ コントラクトを定義するクラスによって多数のメソッドが定義されることに注意してください)。 これらのメソッドは、データ コントラクトの一部とは見なされません。 `DataMember` 属性で宣言されているメンバーだけがデータ コントラクトに含まれます。  
  
     [!code-csharp[S_Msmq_Transacted#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#2)]
     [!code-vb[S_Msmq_Transacted#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#2)]  
  
3.  インターフェイスで定義したサービス コントラクトのメソッドをクラスに実装します。  
  
     [!code-csharp[S_Msmq_Transacted#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#3)]
     [!code-vb[S_Msmq_Transacted#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#3)]  
  
     <xref:System.ServiceModel.OperationBehaviorAttribute> メソッド上の `SubmitPurchaseOrder` に注意してください。 これは、トランザクション内でこの操作を呼び出す必要があること、およびメソッドが完了したときにトランザクションが自動的に完了することを指定します。  
  
4.  <xref:System.Messaging> を使用してトランザクション キューを作成します。 代わりに、MSMQ (Microsoft Message Queuing) Microsoft 管理コンソール (MMC: Microsoft Management Console) を使用してキューを作成することもできます。 その場合は、トランザクション キューを作成してください。  
  
     [!code-csharp[S_Msmq_Transacted#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#4)]
     [!code-vb[S_Msmq_Transacted#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#4)]  
  
5.  サービス アドレスを指定し、標準の <xref:System.ServiceModel.Description.ServiceEndpoint> バインディングを使用する <xref:System.ServiceModel.NetMsmqBinding> を構成で定義します。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]使用して[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]構成を参照してください[Windows Communication Foundation アプリケーションを構成する](http://msdn.microsoft.com/en-us/13cb368e-88d4-4c61-8eed-2af0361c6d7a)です。  
  
  
  
6.  `OrderProcessing` を使用して、キューからメッセージを読み取って処理する <xref:System.ServiceModel.ServiceHost> サービスのホストを作成します。 サービス ホストを開いてサービスを使用できるようにします。 任意のキーを押してサービスを終了するようユーザーに伝えるメッセージを表示します。 `ReadLine` を呼び出して、キーが押されるまで待機してサービスを終了します。  
  
     [!code-csharp[S_Msmq_Transacted#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#6)]
     [!code-vb[S_Msmq_Transacted#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#6)]  
  
### <a name="to-create-a-client-for-the-queued-service"></a>キューに置かれたサービスのクライアントを作成するには  
  
1.  次の例は、ホスト アプリケーションを実行し、Svcutil.exe ツールを使用して [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントを作成する方法を示します。  
  
    ```  
    svcutil http://localhost:8000/ServiceModelSamples/service  
    ```  
  
2.  次の例に示すように、アドレスを指定し、標準の <xref:System.ServiceModel.Description.ServiceEndpoint> バインディングを使用する <xref:System.ServiceModel.NetMsmqBinding> を構成で定義します。  
  
  
  
3.  次の例に示すように、トランザクション キューに書き込むトランザクション スコープを作成し、`SubmitPurchaseOrder` 操作を呼び出して、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントを閉じます。  
  
     [!code-csharp[S_Msmq_Transacted#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#8)]
     [!code-vb[S_Msmq_Transacted#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#8)]  
  
## <a name="example"></a>例  
 次の例は、この例に含まれるサービス コード、ホスト アプリケーション、App.config ファイル、およびクライアント コードを示します。  
  
 [!code-csharp[S_Msmq_Transacted#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#9)]
 [!code-vb[S_Msmq_Transacted#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#9)]  
  
 [!code-csharp[S_Msmq_Transacted#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#10)]
 [!code-vb[S_Msmq_Transacted#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#10)]  
  
  
  
 [!code-csharp[S_Msmq_Transacted#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#12)]
 [!code-vb[S_Msmq_Transacted#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#12)]  
  
  
  
## <a name="see-also"></a>参照  
 <xref:System.ServiceModel.NetMsmqBinding>  
 [トランザクション MSMQ バインディング](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)  
 [WCF でのキュー](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [方法 : WCF エンドポイントとメッセージ キュー アプリケーションを使用してメッセージを交換する](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 [Windows Communication Foundation でのメッセージ キュー](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)  
 [メッセージ キュー (MSMQ) のインストール](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)  
 [メッセージ キュー統合バインディングのサンプル](http://msdn.microsoft.com/en-us/997d11cb-f2c5-4ba0-9209-92843d4d0e1a)  
 [Windows Communication Foundation へのメッセージ キュー](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)  
 [メッセージ キューを介したメッセージ セキュリティ](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
