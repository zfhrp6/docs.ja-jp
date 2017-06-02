---
title: "チャネルの開発 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0513af9f-a0c2-457b-9a50-5b6bfee48513
caps.latest.revision: 17
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 17
---
# チャネルの開発
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] アプリケーション レイヤーで使用できるプロトコル チャネルやトランスポート チャネルを開発するには、いくつかの手順が必要です。このトピックでは、これらの手順について説明し、詳細情報の参照先となる特定のトピックを示します。チャネル モデルと、このトピックで説明するそのさまざまな種類について理解するには、「[チャネル モデルの概要](../../../../docs/framework/wcf/extending/channel-model-overview.md)」を参照してください。トランスポート チャネルの完全なサンプルについては、「[トランスポート: UDP](../../../../docs/framework/wcf/samples/transport-udp.md)」を参照してください。  
  
## チャネル開発タスクの一覧  
 ユーザー定義チャネルを作成する手順は、次のとおりです。すべてのチャネルで、次の手順が必要です。  
  
1.  <xref:System.ServiceModel.Channels.IChannelFactory> と <xref:System.ServiceModel.Channels.IChannelListener> で、チャネルのメッセージ交換パターン \(<xref:System.ServiceModel.Channels.IOutputChannel>、<xref:System.ServiceModel.Channels.IInputChannel>、<xref:System.ServiceModel.Channels.IDuplexChannel>、<xref:System.ServiceModel.Channels.IRequestChannel>、または <xref:System.ServiceModel.Channels.IReplyChannel>\) のうちのどれをサポートするか、また、選択したパターンでこれらのインターフェイスのセッションの多いバリエーションをサポートするかどうかを決定します。詳細については、「[メッセージ交換パターンの選択](../../../../docs/framework/wcf/extending/choosing-a-message-exchange-pattern.md)」を参照してください。  
  
2.  選択したメッセージ交換パターンをサポートするチャネル ファクトリおよびリスナー \(<xref:System.ServiceModel.Channels.IChannelFactory> および <xref:System.ServiceModel.Channels.IChannelListener>\) を作成します。ファクトリの開発の詳細については、「[クライアント : チャネル ファクトリとチャネル](../../../../docs/framework/wcf/extending/client-channel-factories-and-channels.md)」を参照してください。リスナーの開発の詳細については、「[サービス : チャネル リスナーとチャネル](../../../../docs/framework/wcf/extending/service-channel-listeners-and-channels.md)」を参照してください。  
  
3.  ネットワーク固有の例外が、<xref:System.ServiceModel.CommunicationException> の適切な派生クラスまたは <xref:System.TimeoutException?displayProperty=fullName> に標準化されていることを確認します。詳細については、「[例外とエラーの処理](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)」を参照してください。  
  
4.  アプリケーション レイヤーから使用できるようにするには、カスタム チャネルを追加する <xref:System.ServiceModel.Channels.BindingElement> をチャネル スタックに追加します。詳細については、「[BindingElement の作成](../../../../docs/framework/wcf/extending/creating-a-bindingelement.md)」を参照してください。  
  
 アプリケーション レイヤーでより完全なサポートを実現するには、次の追加手順が必要です。  
  
1.  バインド要素拡張セクションを追加して、新しいバインド要素を構成システムに公開します。詳細については、「[構成とメタデータのサポート](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md)」を参照してください。  
  
2.  他のエンドポイントに機能を伝達するメタデータ拡張を追加します。詳細については、「[構成とメタデータのサポート](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md)」を参照してください。  
  
3.  適切に定義されたプロファイルに従って、バインド要素のスタックを事前構成するバインディングを追加します。詳細については、「[ユーザー定義バインディングの作成](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)」を参照してください。  
  
4.  構成システムにバインディングを開示する、バインディング セクションおよびバインディング構成要素を追加します。詳細については、「[構成とメタデータのサポート](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md)」を参照してください。  
  
## 参照  
 [バインディングの拡張](../../../../docs/framework/wcf/extending/extending-bindings.md)