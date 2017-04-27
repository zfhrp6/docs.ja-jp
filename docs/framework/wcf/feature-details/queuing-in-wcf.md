---
title: "WCF でのキュー | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e98d76ba-1acf-42cd-b137-0f8214661112
caps.latest.revision: 21
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 19
---
# WCF でのキュー
ここでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] でキュー通信を使用する方法について説明します。  
  
## WCF トランスポート バインディングとしてのキュー  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、交換する内容をコントラクトによって指定します。  コントラクトは、ビジネスによって異なるまたはアプリケーション固有のメッセージ交換です。  メッセージ交換に使用する機構 \(または "方法"\) は、バインディングで指定します。  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のバインディングは、メッセージ交換の詳細をカプセル化します。  バインディングは、そのバインディングが表すトランスポートまたはプロトコルのさまざまな部分をユーザーが制御するための構成調整情報を公開します。  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のキューは、他のトランスポート バインディングと同様に扱われます。これは、多くのキュー アプリケーションにとって大きな利点となります。  現在、多くのキュー アプリケーションは、他のリモート プロシージャ コール \(RPC\) スタイルの分散アプリケーションとは異なる方法で記述されており、これが原因でフォローと管理が難しくなっています。  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、分散アプリケーションを記述するスタイルはほとんど同じなので、フォローと管理が簡単です。  さらに、交換の機構をビジネス ロジックから切り離すことによって、アプリケーション固有のコードに影響を与えることなく、簡単にトランスポートを構成したり、そのトランスポートに変更を加えたりできます。  次の図は、MSMQ をトランスポートとして使用する WCF サービスとクライアントの構造を示しています。  
  
 ![キューに置かれたアプリケーションの図](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "Distributed\-Queue\-Figure")  
  
 上の図からわかるように、クライアントとサービスは、アプリケーションのセマンティクス、つまりコントラクトと実装だけを定義する必要があります。  サービスは、優先設定を使用してキューに置かれたバインディングを構成します。  クライアントは、[ServiceModel メタデータ ユーティリティ ツール \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) を使用して、サービスに対する [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントを生成し、サービスへのメッセージ送信に使用するバインディングを記述した構成ファイルを生成します。  したがって、キューに置かれたメッセージを送信するとき、クライアントは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントをインスタンス化し、そのクライアントに対する操作を呼び出します。  これによって、メッセージは転送キューに送信され、次にターゲット キューに転送されます。  キュー通信の複雑さはすべて、メッセージを送受信するアプリケーションからは見えません。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のキューに置かれたバインディングには、次の注意事項があります。  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] で既定のキューに置かれたバインディングは、キューを使用した双方向通信をサポートしないので、すべてのサービス操作は一方向である必要があります。  双方向通信のサンプル \(「[双方向通信](../../../../docs/framework/wcf/samples/two-way-communication.md)」\) では、2 つの一方向コントラクトを使用して、キューを使用した双方向通信を実装する方法について説明しています。  
  
-   メタデータ交換を使用する [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントを生成するには、サービスに追加の HTTP エンドポイントが必要です。これによって、エンドポイントを直接照会して [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントを生成したり、キュー通信を適切に構成するためにバインディング情報を取得したりできるようになります。  
  
-   キューに置かれたバインディングに応じて、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の外側で別の構成が必要になります。  たとえば、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に付属の <xref:System.ServiceModel.NetMsmqBinding> クラスでは、バインディングを構成する以外に、メッセージ キュー \(MSMQ\) を最小限構成することが必要です。  
  
 後のセクションでは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に付属する、MSMQ に基づいた特定のキューに置かれたバインディングについて説明します。  
  
### MSMQ  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のキューに置かれたトランスポートでは、そのキュー通信に MSMQ を使用します。  
  
 MSMQ は Windows のオプション コンポーネントとして付属し、NT サービスの 1 つとして実行されます。  MSMQ サービスは、転送するメッセージを転送キューから取り込み、配信するメッセージをターゲット キューから取り込みます。  MSMQ キュー マネージャーは信頼できるメッセージ転送プロトコルを実装して、送信中にメッセージが失われないようにします。  このプロトコルは、ネイティブまたは SOAP リライアブル メッセージ プロトコル \(SRMP\) などの SOAP ベースのプロトコルです。  
  
 MSMQ では、キューをトランザクションまたは非トランザクションとして設定できます。  トランザクション キューの場合、トランザクションによるメッセージの取り込みと配信が可能です。メッセージは、キューに永続的に格納されます。  トランザクション キューに送信されたメッセージは、正確に 1 回だけ、順序どおりに転送されます。  非トランザクション キューを使用すると、揮発性メッセージと非揮発性メッセージの両方を送信できます。  非トランザクション キューに送信されたメッセージには、信頼できる転送保証がありません。したがって、メッセージが失われる可能性があります。  
  
 MSMQ キューも、Active Directory ディレクトリ サービスに登録された Windows ID を使用してセキュリティで保護できます。  MSMQ をインストールするとき、Active Directory 統合をインストールできます。Active Directory 統合では、コンピューターを Windows ドメイン ネットワークに含める必要があります。  
  
 MSMQ [!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[Message Queuing \(MSMQ\)](http://msdn.microsoft.com/ja-jp/ff917e87-05d5-478f-9430-0f560675ece1)」を参照してください。  
  
### NetMsmqBinding  
 [\<netMsmqBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md) <!-- TODO: review token in CAPS to fix the content [!INCLUDE[indigo2 は、]()] [!INCLUDE[indigo2 に用意されているキューに置かれたバインディングで、2 つの]()]  -->  エンドポイントが MSMQ を使用して通信するために使用します。  したがって、このバインディングは、MSMQ 固有のプロパティを公開します。  ただし、すべての MSMQ 機能とプロパティが `NetMsmqBinding` で公開されるわけではありません。  コンパクトな `NetMsmqBinding` は、大部分のユーザーが満足できる最適な機能セットを考慮して設計されています。  
  
 `NetMsmqBinding` は、これまでに説明した基本的なキューの概念をバインディングのプロパティという形で明確に示しています。  このプロパティは、メッセージの転送方法と配信方法を MSMQ に伝達します。  プロパティのカテゴリの詳細については、後のセクションを参照してください。  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]、特定のプロパティについて詳しく説明している概念に関するトピックを参照してください。  
  
#### ExactlyOnce プロパティと Durable プロパティ  
 `ExactlyOnce` プロパティと `Durable` プロパティは、キュー間のメッセージの転送方法を制御します。  
  
-   `ExactlyOnce`: `true` \(既定\) に設定した場合、キューに置かれたチャネルによって、メッセージが重複しないようにすることができます \(メッセージが配信される場合\)。  また、メッセージが失われないようにすることもできます。  メッセージを配信できない場合、またはメッセージを配信する前にメッセージの有効期間 \(TTL: Time To Live\) が切れた場合、失敗したメッセージが配信エラー理由と共に配信不能キューに記録されます。  `false` に設定した場合、キューに置かれたチャネルにより、メッセージの転送が試行されます。  この場合、必要に応じて配信不能キューを選択できます。  
  
-   `Durable:` `true` \(既定\) に設定した場合、キューに置かれたチャネルによって、MSMQ がメッセージをディスクに永続的に格納することが保証されます。  したがって、MSMQ サービスを停止して再起動した場合、ディスク上のメッセージがターゲット キューに転送されるか、サービスに配信されます。  `false` に設定した場合、メッセージは揮発性ストアに格納され、MSMQ サービスを停止して再起動すると、メッセージは失われます。  
  
 `ExactlyOnce` の信頼できる転送を実現するために、MSMQ ではトランザクション キューを使用する必要があります。  また、MSMQ では、トランザクションがトランザクション キューから読み取られる必要があります。  このため、`NetMsmqBinding` を使用する場合、`ExactlyOnce` を `true` に設定したときは、メッセージの送受信にトランザクションが必要なことに注意してください。  同様に、ベスト エフォート保証を使用する場合 \(`ExactlyOnce` が `false` の場合など\) および揮発性メッセージングを行う場合、MSMQ で非トランザクション キューを使用する必要があります。  このため、`ExactlyOnce` を `false` に設定するか、または Durable を `false` に設定した場合、トランザクションを使用して送受信できません。  
  
> [!NOTE]
>  正しいキュー \(トランザクションまたは非トランザクション\) がバインディングの設定に基づいて作成されるようにしてください。  `ExactlyOnce` が `true` の場合はトランザクション キューを使用し、false の場合は非トランザクション キューを使用します。  
  
#### 配信不能キューのプロパティ  
 配信不能キューは、配信に失敗したメッセージを格納するために使用されます。  ユーザーは、配信不能キューからメッセージを読み取る補正ロジックを記述できます。  
  
 多くのキュー システムは、システム全体の配信不能キューを提供します。  MSMQ は、非トランザクション キューへの配信が失敗したメッセージに対してシステム全体の非トランザクション配信不能キューを提供し、トランザクション キューへの配信が失敗したメッセージに対してシステム全体のトランザクション配信不能キューを提供します。  
  
 異なるターゲット キューにメッセージを送信する複数のクライアントによって MSMQ サービスが共有される場合、クライアントが送信したすべてのメッセージが同じ配信不能キューに集まります。  これが適さない状況もあります。  分離を向上するために、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] と [!INCLUDE[wv](../../../../includes/wv-md.md)] の MSMQ には、ユーザーが配信に失敗したメッセージを格納するために指定できるカスタム配信不能キュー \(またはアプリケーション固有の配信不能キュー\) が用意されています。  したがって、異なるクライアントが同じ配信不能キューを共有することがありません。  
  
 バインディングには、2 つの該当するプロパティがあります。  
  
-   `DeadLetterQueue`: このプロパティは、配信不能キューが要求されるかどうかを示す列挙体です。  この列挙体では、配信不能キューが要求される場合、そのキューの種類も指定します。  値は、`None`、`System`、および `Custom` です。  [!INCLUDE[crabout](../../../../includes/crabout-md.md)] これらのプロパティの解釈については、「[配信不能キューを使用したメッセージ転送エラー処理](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)」を参照してください。  
  
-   `CustomDeadLetterQueue`: このプロパティは、アプリケーション固有の配信不能キューの URI \(Uniform Resource Identifier\) アドレスです。  `DeadLetterQueue`.`Custom` を選択した場合、このプロパティは必須です。  
  
#### 有害メッセージ処理プロパティ  
 サービスがトランザクションでターゲット キューからメッセージを読み取るとき、サービスはさまざまな原因でメッセージの処理に失敗する可能性があります。  失敗したメッセージは、再度読み取るためにキューに戻されます。  繰り返し失敗するメッセージを処理するために、有害メッセージ処理プロパティをバインディングで構成できます。  `ReceiveRetryCount`、`MaxRetryCycles`、`RetryCycleDelay`、および `ReceiveErrorHandling` という 4 つのプロパティがあります。  これらのプロパティ[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[有害メッセージ処理](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)」を参照してください。  
  
#### セキュリティ プロパティ  
 MSMQ では、キューのアクセス制御リスト \(ACL\)、認証されたメッセージの送信など、独自のセキュリティ モデルを公開します。  `NetMsmqBinding` は、このセキュリティ プロパティをそのトランスポート セキュリティ設定の一部として公開します。  トランスポート セキュリティのバインディングには、`MsmqAuthenticationMode` プロパティおよび `MsmqProtectionLevel` プロパティという 2 つのプロパティがあります。  このプロパティの設定は、MSMQ の構成方法によって異なります。  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [トランスポート セキュリティを使用したメッセージのセキュリティ保護](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md).  
  
 トランスポート セキュリティに加えて、実際の SOAP メッセージはメッセージ セキュリティでも保護できます。  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [メッセージ セキュリティを使用したメッセージのセキュリティ保護](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md).  
  
 また、`MsmqTransportSecurity` は、2 つのプロパティ `MsmqEncryptionAlgorithm` と `MsmqHashAlgorithm` を公開します。  このプロパティは、キュー間の転送でメッセージを暗号化するために、または署名をハッシュするために選択できる異なるアルゴリズムの列挙体です。  
  
#### その他のプロパティ  
 上記のプロパティに加えて、次の MSMQ 固有のプロパティがバインディングで公開されます。  
  
-   `UseSourceJournal`: ソース ジャーナリングが有効かどうかを示すプロパティです。  ソース ジャーナリングとは、転送キューから正常に送信されたメッセージを追跡する MSMQ の機能です。  
  
-   `UseMsmqTracing`: MSMQ トレースが有効かどうかを示すプロパティです。  MSMQ トレースでは、MSMQ キュー マネージャーをホストしているコンピューターでメッセージが送受信されるたびに、レポート メッセージをレポート キューに送信します。  
  
-   `QueueTransferProtocol`: キュー間のメッセージ転送に使用するプロトコルの列挙体です。  MSMQ では、ネイティブのキュー間転送プロトコルおよび SOAP リライアブル メッセージ プロトコル \(SRMP\) と呼ばれる SOAP ベースのプロトコルを実装しています。  SRMP は、キュー間の転送に HTTP トランスポートを使用している場合に使用します。  SRMP Secure は、キュー間の転送に HTTPS を使用している場合に使用します。  
  
-   `UseActiveDirectory`: キューのアドレス解決に Active Directory を使用する必要があるかどうかを示すブール値です。  既定ではオフになっています。  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [サービス エンドポイントとキューのアドレス指定](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md).  
  
### MsmqIntegrationBinding  
 `MsmqIntegrationBinding` は、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] エンドポイントが、C、C\+\+、COM、または System.Messaging API を使用して作成された既存の MSMQ アプリケーションと通信する場合に使用されます。  
  
 このバインディングのプロパティは、`NetMsmqBinding` のプロパティと同じです。  ただし、次のような違いがあります。  
  
-   `MsmqIntegrationBinding` の操作コントラクトは、型パラメーターが本文型である型 <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> の 1 つのパラメーターしか指定することができません。  
  
-   ほとんどの MSMQ ネイティブ メッセージ プロパティは、使用するために <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> で公開されます。  
  
-   メッセージ本文のシリアル化と逆シリアル化のために、XML、ActiveX などのシリアライザーが用意されています。  
  
### サンプル コード  
 MSMQ を使用する WCF サービスを書き込む方法の手順については、次のトピックを参照してください。  
  
-   [方法 : WCF エンドポイントとメッセージ キュー アプリケーションを使用してメッセージを交換する](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
  
-   [方法 : WCF エンドポイントを使用してキューに置かれたメッセージを交換する](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
  
 WCF での MSMQ の使用を示す完全なコード サンプルについては、次のトピックを参照してください。  
  
-   [トランザクション MSMQ バインディング](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)  
  
-   [揮発性キューによる通信](../../../../docs/framework/wcf/samples/volatile-queued-communication.md)  
  
-   [配信不能キュー](../../../../docs/framework/wcf/samples/dead-letter-queues.md)  
  
-   [セッションとキュー](../../../../docs/framework/wcf/samples/sessions-and-queues.md)  
  
-   [双方向通信](../../../../docs/framework/wcf/samples/two-way-communication.md)  
  
-   [トランザクション バッチ](../../../../docs/framework/wcf/samples/transacted-batching.md)  
  
-   [SRMP](../../../../docs/framework/wcf/samples/srmp.md)  
  
-   [メッセージ キューを介したメッセージ セキュリティ](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)  
  
## 参照  
 [サービス エンドポイントとキューのアドレス指定](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md)   
 [キューに置かれたアプリケーションの Web ホスト](../../../../docs/framework/wcf/feature-details/web-hosting-a-queued-application.md)