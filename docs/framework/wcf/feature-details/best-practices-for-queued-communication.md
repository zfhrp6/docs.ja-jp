---
title: "キューに置かれた通信のベスト プラクティス | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ベスト プラクティス [WCF], キューに置かれた通信"
  - "キュー [WCF], ベスト プラクティス"
ms.assetid: 446a6383-cae3-4338-b193-a33c14a49948
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# キューに置かれた通信のベスト プラクティス
ここでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] のキューに置かれた通信で推奨されるベスト プラクティスについて説明します。以下の各セクションでは、シナリオの観点から推奨されるベスト プラクティスについて説明します。  
  
## キューに置かれたベストエフォート方式の高速メッセージング  
 キューに置かれたメッセージングによってもたらされる分離と、ベストエフォート保証による高パフォーマンスの高速メッセージングを必要とするシナリオでは、非トランザクション キューを使用し、<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> プロパティを `false` に設定します。  
  
 また、<xref:System.ServiceModel.MsmqBindingBase.Durable%2A> プロパティを `false` に設定して、ディスク書き込みの負荷がかからないようにすることもできます。  
  
 セキュリティは、パフォーマンスに影響を及ぼします。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][パフォーマンスに関する考慮事項](../../../../docs/framework/wcf/feature-details/performance-considerations.md).  
  
## キューに置かれた信頼性のあるエンド ツー エンドのメッセージング  
 以下のセクションでは、エンド ツー エンドで信頼できるメッセージングが必要なシナリオで推奨されるベスト プラクティスについて説明します。  
  
### 基本的で信頼できる転送  
 エンド ツー エンドの信頼性を実現するには、<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> プロパティを `true` に設定して、確実に転送できるようにします。<xref:System.ServiceModel.MsmqBindingBase.Durable%2A> プロパティは、要件に応じて `true` に設定することも、`false` に設定することもできます \(既定値は `true` です\)。通常、エンド ツー エンドの信頼性の一環として、<xref:System.ServiceModel.MsmqBindingBase.Durable%2A> プロパティは `true` に設定されています。これはパフォーマンス コストに影響しますが、これによりメッセージが永続的になるため、キュー マネージャーがクラッシュした場合でもメッセージが失われなくなります。  
  
### トランザクションの使用  
 エンド ツー エンドの信頼性を確保するには、トランザクションを使用する必要があります。`ExactlyOnce` の保証によって保証されるのは、メッセージがターゲット キューに配信されることだけです。メッセージを確実に受信するには、トランザクションを使用します。トランザクションを使用しないと、サービスがクラッシュした場合に、配信中であるが、実際にはアプリケーションに配信されるメッセージは失われます。  
  
### 配信不能キューの使用  
 配信不能キューを使用すると、メッセージがターゲット キューに配信されなかった場合に、必ず通知されます。システム指定の配信不能キューまたはカスタムの配信不能キューを使用できます。アプリケーションごとに専用の配信不能キューに配信不能メッセージを送信できるため、一般にカスタムの配信不能キューを使用することをお勧めします。カスタムの配信不能キューを使用しない場合は、システムで実行されているすべてのアプリケーションで発生するすべての配信不能メッセージが 1 つのキューに配信されます。この場合、各アプリケーションは配信不能キュー全体を検索して、それぞれのアプリケーションに関連する配信不能メッセージを見つける必要があります。MSMQ 3.0 を使用する場合など、カスタムの配信不能キューを使用できないこともあります。  
  
 エンド ツー エンドの信頼性が必要な通信では、配信不能キューを無効にすることはお勧めしません。  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [配信不能キューを使用したメッセージ転送エラー処理](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md).  
  
### 有害メッセージ処理の使用  
 有害メッセージ処理は、メッセージ処理のエラーから回復する機能を提供します。  
  
 有害メッセージ処理機能を使用する場合は、<xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> プロパティが適切な値に設定されていることを確認します。このプロパティを <xref:System.ServiceModel.ReceiveErrorHandling> に設定すると、データが失われることになります。一方、<xref:System.ServiceModel.ReceiveErrorHandling> に設定すると、有害メッセージが検出されたときにサービス ホストでエラーが発生します。MSMQ 3.0 を使用する場合、データの損失を防ぎ、有害メッセージを取り除くための最適なオプションは <xref:System.ServiceModel.ReceiveErrorHandling> です。MSMQ 4.0 を使用する場合は、<xref:System.ServiceModel.ReceiveErrorHandling> が推奨されます。<xref:System.ServiceModel.ReceiveErrorHandling> に設定すると有害メッセージがキューから取り除かれるため、サービスは新しいメッセージの処理を続行できます。有害メッセージ サービスは、取り除かれた有害メッセージを別個に処理できます。  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [有害メッセージ処理](../../../../docs/framework/wcf/feature-details/poison-message-handling.md).  
  
## 高スループットの実現  
 単一のエンドポイントで高スループットを実現するには、以下を使用します。  
  
-   トランザクション バッチ。トランザクション バッチでは、1 回のトランザクションで多くのメッセージを読み取ることができます。これにより、トランザクションのコミットが最適化され、全体的なパフォーマンスが向上します。バッチ処理の難点は、バッチ内の 1 つのメッセージでエラーが発生した場合に、バッチ全体をロールバックし、再び安全にバッチ処理できるようになるまで、メッセージを 1 つずつ処理する必要があることです。ほとんどの場合、有害メッセージはまれであるため、特にトランザクションに他のリソース マネージャーが参加している場合は、バッチ処理がシステム パフォーマンスを向上させる方法として推奨されます。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][トランザクションに含まれるメッセージのバッチ処理](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md).  
  
-   同時実行。同時実行によりスループットが向上します。ただし、同時実行は共有リソースの競合に影響します。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][同時実行](../../../../docs/framework/wcf/samples/concurrency.md).  
  
-   調整。最適なパフォーマンスを実現するために、ディスパッチャー パイプラインのメッセージの数を調整します。この調整を行う方法の例については、「[調整](../../../../docs/framework/wcf/samples/throttling.md)」を参照してください。  
  
 バッチ処理を使用する場合は、同時実行と調整は同時バッチに変換されることに気をつけてください。  
  
 スループットと可用性を高めるには、キューから読み取る [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスのファームを使用します。この場合、ファームのすべてのサービスが同じエンドポイントで同じコントラクトを公開している必要があります。ファームを使用すると、多数のサービスがすべて同じキューから読み取ることができるため、この方法はメッセージの生成率が高いアプリケーションで最も効果を発揮します。  
  
 ファームを使用する場合、MSMQ 3.0 ではリモート トランザクション読み取りがサポートされていないので注意してください。MSMQ 4.0 は、リモート トランザクション読み取りをサポートしています。  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]、「[トランザクションに含まれるメッセージのバッチ処理](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md)」および「[Windows Vista、Windows Server 2003、および Windows XP におけるキュー機能の相違点](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)」を参照してください。  
  
## 作業単位のセマンティクスによるキュー処理  
 キューにある一連のメッセージが関連している可能性があるため、これらのメッセージの順序付けが重要となるシナリオがあります。このようなシナリオでは、関連するメッセージのグループを 1 つの単位としてまとめて処理します。つまり、すべてのメッセージが正常に処理されるか、どのメッセージも処理されないかのいずれかになります。このような動作を実装するには、キューでセッションを使用します。  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [セッションでキューに置かれたメッセージのグループ化](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md).  
  
## 要求\/応答メッセージの関連付け  
 通常、キューは一方向ですが、シナリオによっては、受信した応答を以前に送信した要求に関連付けることが必要になる場合があります。このような関連付けが必要な場合、関連付け情報を含む独自の SOAP メッセージ ヘッダーをメッセージに追加することをお勧めします。通常、送信側がこのヘッダーをメッセージに添付すると、受信側は、このメッセージを処理して応答キューにある新しいメッセージで応答するときに、関連付け情報を含む送信側のメッセージ ヘッダーを添付します。これにより、送信側は要求メッセージを使用して応答メッセージを識別できます。  
  
## 非 WCF アプリケーションとの統合  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスまたはクライアントを非 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスまたはクライアントと統合するときには、`MsmqIntegrationBinding` を使用します。非 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションには、System.Messaging、COM\+、[!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]、または C\+\+ を使用して作成された MSMQ アプリケーションなどがあります。  
  
 `MsmqIntegrationBinding` を使用するときは、以下の点に注意してください。  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] メッセージの本文は、MSMQ メッセージの本文と同じではありません。キューに置かれたバインディングを使用して [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] メッセージを送信する場合は、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] メッセージの本文が MSMQ メッセージの内部に配置されます。MSMQ インフラストラクチャは、この追加情報を認識しません。認識するのは、MSMQ メッセージだけです。  
  
-   `MsmqIntegrationBinding` では、よく使用されるシリアル化型をサポートしています。ジェネリック メッセージである <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> の本文の型は、シリアル化型に基づいてさまざまな型パラメーターを受け取ります。たとえば、<xref:System.ServiceModel.MsmqIntegration.MsmqMessageSerializationFormat> には `MsmqMessage\<byte[]>` が必要であり、<xref:System.ServiceModel.MsmqIntegration.MsmqMessageSerializationFormat> には `MsmqMessage<Stream>` が必要です。  
  
-   XML シリアル化では、[\<behavior\>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) 要素の `KnownTypes` 属性を使用して既知の型を指定できます。この型は、後で XML メッセージを逆シリアル化する方法を確認する際に使用されます。  
  
## 参照  
 [WCF でのキュー](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)   
 [方法 : WCF エンドポイントを使用してキューに置かれたメッセージを交換する](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)   
 [方法 : WCF エンドポイントとメッセージ キュー アプリケーションを使用してメッセージを交換する](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)   
 [セッションでキューに置かれたメッセージのグループ化](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md)   
 [トランザクションに含まれるメッセージのバッチ処理](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md)   
 [配信不能キューを使用したメッセージ転送エラー処理](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)   
 [有害メッセージ処理](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)   
 [Windows Vista、Windows Server 2003、および Windows XP におけるキュー機能の相違点](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)   
 [トランスポート セキュリティを使用したメッセージのセキュリティ保護](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)   
 [メッセージ セキュリティを使用したメッセージのセキュリティ保護](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md)   
 [キューに置かれたメッセージングのトラブルシューティング](../../../../docs/framework/wcf/feature-details/troubleshooting-queued-messaging.md)