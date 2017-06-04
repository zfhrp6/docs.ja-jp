---
title: "相関関係の概要 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: edcc0315-5d26-44d6-a36d-ea554c418e9f
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# 相関関係の概要
相関関係とは、ワークフロー サービス メッセージを互いに関連付ける、最初の要求への応答などのアプリケーションのインスタンス状態と関連付ける、または特定の注文 ID を注文処理ワークフローの永続化された状態に関連付けるためのしくみです。  ここでは、相関関係の概要について説明します。  このセクションの他のトピックでは、相関関係の各種類についての追加情報を提供します。  
  
## 相関関係の種類  
 相関関係には、プロトコル ベースとコンテンツ ベースがあります。  プロトコル ベースの相関関係では、メッセージ間のマッピングを提供するためのメッセージ配信インフラストラクチャで提供されるデータが使用されます。  プロトコル ベースの相関関係を使用して関連付けられたメッセージは、メモリ内の <xref:System.ServiceModel.Channels.RequestContext> などのオブジェクトを使用して、またはトランスポート プロトコルで提供されるトークンによって、互いに関連付けられます。  コンテンツ ベースの相関関係では、メッセージが、アプリケーションで指定されたデータを使用して関連付けられます。  コンテンツ ベースの相関関係を使用して関連付けられたメッセージは、アプリケーションが定義する顧客番号などのメッセージ内のデータによって互いに関連付けられます。  
  
 相関関係に参加するアクティビティは、<xref:System.ServiceModel.Activities.CorrelationHandle> を使用してメッセージング アクティビティを互いに結び付けます。  たとえば、サービスの呼び出しに使用される <xref:System.ServiceModel.Activities.Send> と、それに続く、サービスからのコールバックの受信に使用される <xref:System.ServiceModel.Activities.Receive> は、同じ <xref:System.ServiceModel.Activities.CorrelationHandle> を共有します。  この基本的なパターンは、相関関係がコンテンツ ベースであっても、プロトコル ベースであっても使用されます。  関連付けハンドルは、各アクティビティに明示的に設定する、またはアクティビティを <xref:System.ServiceModel.Activities.CorrelationScope> アクティビティに格納することができます。  <xref:System.ServiceModel.Activities.CorrelationScope> に格納されたアクティビティには、<xref:System.ServiceModel.Activities.CorrelationScope> が管理する関連付けハンドルがあり、<xref:System.ServiceModel.Activities.CorrelationHandle> を明示的に設定する必要がありません。  <xref:System.ServiceModel.Activities.CorrelationScope> スコープでは、要求\/応答の相関関係と、もう 1 つの種類の相関関係のための <xref:System.ServiceModel.Activities.CorrelationHandle> 管理が提供されます。  <xref:System.ServiceModel.Activities.WorkflowServiceHost> を使用してホストされるワークフロー サービスには、<xref:System.ServiceModel.Activities.CorrelationScope> アクティビティと同じ既定の関連付け管理があります。  多くのシナリオで、この既定の関連付け管理は、<xref:System.ServiceModel.Activities.CorrelationScope> 内のメッセージング アクティビティ、またはワークフロー サービスが <xref:System.ServiceModel.Activities.CorrelationHandle> セットを要求しないことを意味します。ただし、2 つの <xref:System.ServiceModel.Activities.Receive> アクティビティが並行している、または 2 つの <xref:System.ServiceModel.Activities.Send> アクティビティに 2 つの <xref:System.ServiceModel.Activities.Receive> アクティビティが続くなど、複数のメッセージング アクティビティが並行または重複している場合を除きます。  既定の相関関係の詳細情報は、このセクションの中のそれぞれの種類の相関関係を説明するトピックに記述されています。  メッセージング アクティビティ[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[メッセージング アクティビティ](../../../../docs/framework/wcf/feature-details/messaging-activities.md)」および「[方法: メッセージング アクティビティを使用してワークフロー サービスを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)」を参照してください。  
  
## プロトコル ベースの相関関係  
 プロトコル ベースの相関関係では、メッセージを相互に関連付け、該当するインスタンスと関連付けるために、トランスポート機構が使用されます。  システムで提供される一部のプロトコル相関関係には、要求\/応答の相関関係とコンテキスト ベースの相関関係が含まれます。  要求\/応答の相関関係を使用して、メッセージング アクティビティの 1 つのペアが関連付けられ、<xref:System.ServiceModel.Activities.ReceiveReply> と <xref:System.ServiceModel.Activities.Send> のペアや、<xref:System.ServiceModel.Activities.SendReply> と <xref:System.ServiceModel.Activities.Receive> のペアなどの双方向の操作が形成されます。  また、[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ワークフロー デザイナーには、このパターンに迅速に実装できるアクティビティ テンプレートのセットが用意されています。  コンテキスト ベースの相関関係は、「[.NET コンテキスト交換プロトコルの仕様](http://go.microsoft.com/fwlink/?LinkID=166059)」で説明されているコンテキスト交換メカニズムに基づきます。  コンテキスト ベースの相関関係を使用するには、<xref:System.ServiceModel.BasicHttpContextBinding>、<xref:System.ServiceModel.WSHttpContextBinding>、または <xref:System.ServiceModel.NetTcpContextBinding> などのコンテキスト ベースのバインディングがエンドポイントで使用される必要があります。  
  
 プロトコルの相関関係[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[コンテキスト交換](../../../../docs/framework/wcf/feature-details/context-exchange-correlation.md)」、「[永続的な二重](../../../../docs/framework/wcf/feature-details/durable-duplex-correlation.md)」、および「[要求\/応答](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md)」を参照してください。  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ワークフロー デザイナーのアクティビティ テンプレートの使用方法[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[メッセージング アクティビティ](../../../../docs/framework/wcf/feature-details/messaging-activities.md)」を参照してください。  サンプル コードについては、「[永続的な二重 &#91;WF サンプル&#93;](../../../../docs/framework/windows-workflow-foundation/samples/durable-duplex.md)」および「[NetContextExchangeCorrelation](http://msdn.microsoft.com/ja-jp/93c74a1a-b9e2-46c6-95c0-c9b0e9472caf)」のサンプルを参照してください。  
  
## コンテンツ ベースの相関関係  
 コンテンツ ベースの相関関係では、メッセージ内の一部の情報を特定のインスタンスとの関連付けに使用します。  プロトコル ベースの相関関係と異なり、コンテンツ ベースの相関関係では、各関連メッセージ内のこの情報がある場所に、アプリケーションの作成者が明示的に記述されている必要があります。  コンテンツ ベースの相関関係を使用するアクティビティでは、<xref:System.ServiceModel.MessageQuerySet> を使用して、このメッセージ データを指定します。  コンテンツ ベースの相関関係は、<xref:System.ServiceModel.BasicHttpContextBinding> などのコンテキスト バインディングの 1 つを使用しないサービスと通信する場合に便利です。  コンテンツ ベースの相関関係[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[コンテンツ ベース](../../../../docs/framework/wcf/feature-details/content-based-correlation.md)」を参照してください。  サンプル コードについては、「[コンテンツ ベースの相関関係](../../../../docs/framework/windows-workflow-foundation/samples/content-based-correlation.md)」および「[相関電卓](../../../../docs/framework/windows-workflow-foundation/samples/correlated-calculator.md)」のサンプルを参照してください。  
  
## 参照  
 [コンテンツ ベースの相関関係](../../../../docs/framework/windows-workflow-foundation/samples/content-based-correlation.md)   
 [相関電卓](../../../../docs/framework/windows-workflow-foundation/samples/correlated-calculator.md)   
 [永続的な二重 &#91;WF サンプル&#93;](../../../../docs/framework/windows-workflow-foundation/samples/durable-duplex.md)   
 [NetContextExchangeCorrelation](http://msdn.microsoft.com/ja-jp/93c74a1a-b9e2-46c6-95c0-c9b0e9472caf)