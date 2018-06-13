---
title: 配信不能キューを使用したメッセージ転送エラー処理
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9e891c6a-d960-45ea-904f-1a00e202d61a
ms.openlocfilehash: b70b7a7849ba0927c8ee4a4903aefc27bfa9d0c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33504082"
---
# <a name="using-dead-letter-queues-to-handle-message-transfer-failures"></a>配信不能キューを使用したメッセージ転送エラー処理
キューに置かれたメッセージは、配信に失敗する可能性があります。 配信に失敗したメッセージは、配信不能キューに記録されます。 配信の失敗は、ネットワーク エラー、キューが削除されている、キューがいっぱいになっている、認証エラー、配信が時間どおりに行われなかったなど、さまざまな理由で生じる可能性があります。  
  
 キューに置かれたメッセージは、受信側のアプリケーションでタイムリーに読み取られないと、長時間キューに残ることがあります。 時間依存のメッセージでは、このような動作が適切でない場合があります。 時間依存のメッセージでは、メッセージをキューに格納しておくことができる期間を示す TTL (Time to Live) プロパティが、キューに置かれたバインディングに設定されおり、この期間を超えると、メッセージの有効期限が切れます。 期限切れのメッセージは、配信不能キューと呼ばれる特別なキューに送信されます。 また、キューのクォータの超過、認証エラーなどの理由で、メッセージが配信不能キューに置かれる場合もあります。  
  
 一般に、アプリケーションには、配信不能キューのメッセージとエラーの理由を読み取るための補正ロジックが記述されています。 補正ロジックはエラーの原因に依存します。 たとえば、認証エラーの場合は、メッセージに添付された証明書を修正し、メッセージを再送信できます。 また、ターゲット キューのクォータに達したために配信が失敗した場合は、クォータの問題が解決されていることを期待して配信を再試行できます。  
  
 ほとんどのキュー システムには、そのシステムから配信できなかったすべてのメッセージを格納するための、システム全体の配信不能キューがあります。 メッセージ キュー (MSMQ) には、システム全体の配信不能キューが 2 種類用意されています。1 つはトランザクション キューへの配信に失敗したメッセージを格納するトランザクション システム全体の配信不能キューで、もう 1 つは非トランザクション キューへの配信に失敗したメッセージを格納する非トランザクション システム全体の配信不能キューです。 2 つのクライアントが 2 つの異なるサービスにメッセージを送信して、WCF で異なるキューが送信する同じ MSMQ サービスを共有するため場合、は、システム配信不能キューにメッセージが混在することはできます。 これは、必ずしも最適であるとは言えません。 場合によっては (たとえば、セキュリティ上の理由で)、一方のクライアントが、もう一方のクライアントのメッセージを配信不能キューから読み取ることができないようにする必要があるからです。 また、共有された配信不能キューでは、クライアントがキューを参照して、送信したメッセージを検索する必要もありますが、配信不能キューに置かれているメッセージの数によっては、これは極めて大きな負荷になる可能性があります。 そのため、WCF で`NetMsmqBinding`、`MsmqIntegrationBinding,`および MSMQ に[!INCLUDE[wv](../../../../includes/wv-md.md)](アプリケーション固有の配信不能キューとも呼ばれます)、カスタム配信不能キューを提供します。  
  
 カスタム配信不能キューでは、同じ MSMQ サービスを共有してメッセージを送信するクライアントをそれぞれ分離できます。  
  
 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]と[!INCLUDE[wxp](../../../../includes/wxp-md.md)]、Windows Communication Foundation (WCF) では、すべてのキューに置かれたクライアント アプリケーションのシステム全体の配信不能キューを提供します。 [!INCLUDE[wv](../../../../includes/wv-md.md)]WCF では、各キューに置かれたクライアント アプリケーションの配信不能キューが用意されています。  
  
## <a name="specifying-use-of-the-dead-letter-queue"></a>配信不能キューの使用の指定  
 配信不能キューは、送信元アプリケーションのキュー マネージャーに存在します。 ここには、有効期限が切れたメッセージと転送または配信に失敗したメッセージが格納されます。  
  
 バインディングには、次の配信不能キュー プロパティがあります。  
  
-   <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A>  
  
-   <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A>  
  
## <a name="reading-messages-from-the-dead-letter-queue"></a>配信不能キューからのメッセージの読み取り  
 配信不能キューからメッセージを読み取るアプリケーションは、WCF サービスを次の小さな相違点を除いて、アプリケーション キューから読み取ると同様です。  
  
-   トランザクション システムの配信不能キューからメッセージを読み取るには、URI (Uniform Resource Identifier) を net.msmq://localhost/system$;DeadXact という形式にする必要があります。  
  
-   非トランザクション システムの配信不能キューからメッセージを読み取る場合、URI は、net.msmq://localhost/system$;DeadLetter という形式にする必要があります。  
  
-   カスタム配信不能キューからメッセージの読み取り、URI でなければなりませんフォーム: net.msmq://localhost/private/\<*カスタム dlq 名*> 場所*カスタム dlq 名*カスタムの名前を指定します配信不能キュー。  
  
 キューのアドレス方法の詳細については、次を参照してください。[サービス エンドポイントとキューのアドレス指定](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md)です。  
  
 受信側で WCF スタックでは、メッセージのアドレスと、サービスがリッスンしているアドレスと一致します。 アドレスが一致する場合、メッセージはディスパッチされますが、一致しない場合はディスパッチされません。 これにより、配信不能キューから読み取るときに問題が生じる可能性があります。一般に、配信不能キュー内のメッセージは該当サービスにアドレス指定され、配信不能キュー サービスにアドレス指定されないからです。 そのため、配信不能キューから読み取るサービスは、`ServiceBehavior` アドレス フィルターをインストールし、受信者とは無関係にキュー内のすべてのメッセージを一致させるようスタックに指示する必要があります。 具体的には、`ServiceBehavior` パラメーターを持つ <xref:System.ServiceModel.AddressFilterMode.Any> を、配信不能キューからメッセージを読み取るサービスに追加する必要があります。  
  
## <a name="poison-message-handling-from-the-dead-letter-queue"></a>配信不能キューの有害メッセージの処理  
 配信不能キューでは、条件付きで有害メッセージを処理できます。 システム キューからサブキューを作成できないため、システム配信不能キューから読み取るときは、`ReceiveErrorHandling` を `Move` に設定できません。 カスタム配信不能キューから読み取る場合は、サブキューを使用できるので、`Move` が有害メッセージに対する有効な処置であることに注意してください。  
  
 `ReceiveErrorHandling` を `Reject` に設定しているときにカスタム配信不能キューから読み取った場合、有害メッセージはシステム配信不能キューに置かれます。 システム配信不能キューから読み取ると、有害メッセージは破棄 (削除) されます。 MSMQ のシステム配信不能キューから拒否すると、メッセージは破棄 (削除) されます。  
  
## <a name="example"></a>例  
 次の例は、配信不能キューを作成する方法と、配信不能キューを使用して期限切れのメッセージを処理する方法を示しています。 例は例では、に基づいて[する方法: WCF エンドポイントとのキューに置かれたメッセージを交換](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)です。 この例では、アプリケーションごとの配信不能キューを使用する発注書処理サービスにクライアント コードを書き込む方法を示します。 また、配信不能キューのメッセージを処理する方法も示します。  
  
 以下は、アプリケーションごとの配信不能キューを指定するクライアントのコードです。  
  
 [!code-csharp[S_DeadLetter#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_deadletter/cs/client.cs#1)]
 [!code-vb[S_DeadLetter#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_deadletter/vb/client.vb#1)]  
  
 以下は、クライアント構成ファイルのコードです。  
  
  
  
 以下は、配信不能キューのメッセージを処理するサービスのコードです。  
  
 [!code-csharp[S_DeadLetter#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_deadletter/cs/dlservice.cs#3)]
 [!code-vb[S_DeadLetter#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_deadletter/vb/dlservice.vb#3)]  
  
 以下は、配信不能キュー サービス構成ファイルのコードです。  
  
  
  
## <a name="see-also"></a>関連項目  
 [キューの概要](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 [方法 : WCF エンドポイントを使用してキューに置かれたメッセージを交換する](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 [有害メッセージ処理](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)
