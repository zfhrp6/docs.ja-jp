---
title: "システム標準のバインディング | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "バインディング [WCF], システム標準"
ms.assetid: 2c243746-45ce-4588-995e-c17126a579a6
caps.latest.revision: 60
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 60
---
# システム標準のバインディング
バインディングにより、エンドポイントとの通信で使用する通信メカニズムが指定され、エンドポイントへの接続方法が示されます。バインディングには次の要素が含まれます。  
  
-   プロトコル スタックは、エンドポイントに送信されるメッセージで使用するセキュリティ、信頼性、およびコンテキスト フローの設定を決定します。  
  
-   トランスポートは、エンドポイントにメッセージを送信するときに使用する基礎トランスポート プロトコル \(TCP または HTTP など\) を決定します。  
  
-   エンコードは、エンドポイントに送信されるメッセージに使用するネットワーク エンコード \(text\/XML、バイナリ、MTOM \(Message Transmission Optimization Mechanism\) など\) を決定します。  
  
 ここでは、システム指定の [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] バインディングをすべて示します。このバインディングがいずれもアプリケーションの条件に適合しない場合は、カスタム バインディングを作成できます。カスタム バインディングの作成[!INCLUDE[crabout](../../../includes/crabout-md.md)]、「[カスタム バインディング](../../../docs/framework/wcf/extending/custom-bindings.md)」を参照してください。  
  
 WS\-Federation プロトコルをサポートする、セキュリティで保護された相互操作可能なバインディングを使用すると、フェデレーションに属す組織のユーザーを効率的に認証および承認できます。  
  
> [!IMPORTANT]
>  常にセキュリティを備えたバインディングを選択します。既定では、[\<basicHttpBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) 要素以外のバインディングでセキュリティが有効になっています。セキュリティで保護されたバインディングを選択しない場合、またはセキュリティを無効にする場合は、セキュリティで保護されたデータ センターや隔離されたネットワークにデータを保存するなど、他の方法でデータを保護してください。  
  
> [!IMPORTANT]
>  他の方法によってデータをセキュリティ保護している場合を除き、セキュリティをサポートしないバインディングやセキュリティが無効になっているバインディングでは、双方向コントラクトを使用しないでください。  
  
## システム指定のバインディング  
 次のバインディングは [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] に付属します。  
  
|バインディング|構成要素|説明|  
|-------------|----------|--------|  
|<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)|ASP.NET Web サービス \(ASMX\) ベースのサービスなど、WS\-Basic Profile に適合する Web サービスとの通信に適したバインディング。このバインディングはトランスポートとして HTTP を、既定のメッセージ エンコーディングとして text\/XML を使用します。|  
|<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|二重のサービス コントラクト以外に適した、セキュリティで保護された相互操作可能なバインディング。|  
|<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)|双方向サービス コントラクト、または SOAP 中継局を介しての通信に適した、セキュリティで保護された相互操作可能なバインディング。|  
|<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|フェデレーションに属す組織のユーザーを効率的に認証および承認できる WS\-Federation プロトコルをサポートする、セキュリティで保護された相互操作可能なバインディング。|  
|<xref:System.ServiceModel.NetHttpBinding>|\<netHttpBinding\>|HTTP や WebSocket のサービスを使用するために設計され、既定でバイナリ エンコーディングを使用するバインディング。|  
|<xref:System.ServiceModel.NetHttpsBinding>|\<netHttpsBinding\>|HTTP や WebSocket のサービスを使用するために設計され、既定でバイナリ エンコーディングを使用するセキュリティで保護されたバインディング。|  
|<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)|[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] アプリケーション間での複数コンピューターの通信に適した、セキュリティで保護された最適バインディング。|  
|<xref:System.ServiceModel.NetNamedPipeBinding>|[\<netNamedPipeBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md)|[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] アプリケーション間でのコンピューター通信に適した、セキュリティで保護された信頼できる最適バインディング。|  
|<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] アプリケーション間での複数コンピューターの通信に適した、キューに置かれたバインディング。|  
|<xref:System.ServiceModel.NetPeerTcpBinding>|[\<netPeerTcpBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md)|セキュリティで保護された、複数のコンピューター通信を可能にするバインディング。|  
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|[\<msmqIntegrationBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)|[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] アプリケーションとメッセージ キュー \(MSMQ: Message Queuing\) アプリケーション間のコンピューター間通信に適したバインディング。|  
|<xref:System.ServiceModel.BasicHttpContextBinding>|[\<basicHttpContextBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/basichttpcontextbinding.md)|WS\-Basic Profile に適合する Web サービスとの通信に適したバインディング。このバインディングでは、HTTP クッキーを使用してコンテキストを交換できるようになります。|  
|<xref:System.ServiceModel.NetTcpContextBinding>|[\<netTcpContextBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/nettcpcontextbinding.md)|[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] アプリケーション間での複数コンピューターの通信に適した、セキュリティで保護された最適バインディング。このバインディングでは、SOAP ヘッダーを使用してコンテキストを交換できるようになります。|  
|<xref:System.ServiceModel.WebHttpBinding>|[\<webHttpBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)|SOAP メッセージではなく、HTTP 要求を介して公開される [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Web サービスのエンドポイントを構成するために使用されるバインディング。|  
|<xref:System.ServiceModel.WSHttpContextBinding>|[\<wsHttpContextBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/wshttpcontextbinding.md)|非双方向サービス コントラクトに適した、セキュリティで保護された相互操作可能なバインディング。このバインディングでは、SOAP ヘッダーを使用してコンテキストを交換できるようになります。|  
|<xref:System.ServiceModel.Channels.UdpBinding>|\<udpBinding\>|単純なメッセージを複数のクライアントに同時に送信するために使用されるバインディング。|  
  
 各システム指定のバインディングの機能を次の表に示します。各バインディングをこの表の列に示します。機能とその説明は 2 番目の表の行に示します。次の表に、使用されるバインディングの省略形のキーを示します。バインディングを選択するには、必要な行の機能がすべて含まれる列を調べます。  
  
|バインディング|相互運用性|セキュリティ \(既定\)|セッション<br /><br /> \(既定\)|トランザクション|双方向|エンコード \(かっこ内は既定値\)|ストリーム<br /><br /> \(かっこ内は既定値\)|  
|-------------|-----------|-------------------|----------------------|--------------|---------|------------------------|----------------------------|  
|<xref:System.ServiceModel.BasicHttpBinding>|Basic Profile 1.1|\(なし\)、トランスポート、メッセージ、混在|\(なし\)|\(なし\)|n\/a|テキスト、\(MTOM\)|○<br /><br /> \(buffered\)|  
|<xref:System.ServiceModel.WSHttpBinding>|WS|トランスポート、\(メッセージ\)、混在|\(なし\)、信頼できるセッション、セキュリティ保護されたセッション|\(なし\)、あり|適用なし|\(テキスト\)、MTOM|×|  
|<xref:System.ServiceModel.WSDualHttpBinding>|WS|\(メッセージ\)、なし|\(信頼できるセッション\)、セキュリティ保護されたセッション|\(なし\)、あり|○|\(テキスト\)、MTOM|×|  
|<xref:System.ServiceModel.WSFederationHttpBinding>|WS\-Federation|\(メッセージ\)、混在、なし|\(なし\)、信頼できるセッション、セキュリティ保護されたセッション|\(なし\)、あり|×|\(テキスト\)、MTOM|×|  
|<xref:System.ServiceModel.NetHttpBinding>|.NET|\(なし\)、トランスポート、メッセージ、TransportWithMessageCredential、TransportCredentialOnly|下記のメモを参照|なし|下記のメモを参照|\(バイナリ\)、テキスト、MTOM|○ \(buffered\)|  
|T:System.ServiceModel.NetHttpsBinding|.NET|\(トランスポート\)、TransportWithMessageCredential|下記のメモを参照|なし|下記のメモを参照|\(バイナリ\)、テキスト、MTOM|○ \(buffered\)|  
|<xref:System.ServiceModel.NetTcpBinding>|.NET|\(トランスポート\)、メッセージ、なし、混在|\(トランスポート\)、信頼できるセッション、セキュリティ保護されたセッション|\(なし\)、あり|○|Binary|○<br /><br /> \(buffered\)|  
|<xref:System.ServiceModel.NetNamedPipeBinding>|.NET|\(トランスポート\)、なし|なし、\(トランスポート\)|\(なし\)、あり|○|Binary|○<br /><br /> \(buffered\)|  
|<xref:System.ServiceModel.NetMsmqBinding>|.NET|メッセージ、\(トランスポート\)、なし|\(なし\)、トランスポート|なし、\(あり\)|×|Binary|×|  
|<xref:System.ServiceModel.NetPeerTcpBinding>|Peer|\(トランスポート\)|\(なし\)|\(なし\)|○||×|  
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|MSMQ|\(トランスポート\)|\(なし\)|なし、\(あり\)|適用なし|適用なし|×|  
|<xref:System.ServiceModel.BasicHttpContextBinding>|Basic Profile 1.1|\(なし\)、トランスポート、メッセージ、混在|\(なし\)|\(なし\)|n\/a|テキスト、\(MTOM\)|○<br /><br /> \(buffered\)|  
|<xref:System.ServiceModel.NetTcpContextBinding>|.NET|\(トランスポート\)、メッセージ、なし、混在|\(トランスポート\)、信頼できるセッション、セキュリティ保護されたセッション|\(なし\)、あり|○|Binary|○<br /><br /> \(buffered\)|  
|<xref:System.ServiceModel.WSHttpContextBinding>|WS|トランスポート、\(メッセージ\)、混在|\(なし\)、信頼できるセッション、セキュリティ保護されたセッション|\(なし\)、あり|適用なし|テキスト、\(MTOM\)|×|  
|<xref:System.ServiceModel.Channels.UdpBinding>|.NET **Note:**  相互運用性は、このバインディングが実装する標準の UDP 上の SOAP 仕様を実装することによって実現できます。|\(なし\)|\(なし\)|\(なし\)|適用なし|\(テキスト\)|×|  
  
> [!IMPORTANT]
>  <xref:System.ServiceModel.NetHttpBinding> は、HTTP や WebSocket のサービスを使用するために設計されたバインディングで、既定でバイナリ エンコーディングを使用します。<xref:System.ServiceModel.NetHttpBinding> は、要求\/応答コントラクトまたは双方向コントラクトで使用されるかどうかを検出し、一致する動作を変更します。要求\/応答用の HTTP と双方向用の Websocket を使用します。この動作は、<xref:System.ServiceModel.NetHttpBinding.WebSocketTransportUsage%2A> バインディング構成を使用してオーバーライドできます。Allowed: 既定値で、上で説明したように動作します。NotAllowed: Websocket の使用を抑止します。この設定を使用した双方向コントラクトを使用しようとすると、例外が発生します。Required: 要求\/応答コントラクトでも Websocket が使用されるようにします。NetHttpBinding は、HTTP モードと WebSocket モードの両方で信頼できるセッションをサポートします。WebSocket モードでは、セッションはトランスポートによって提供されます。  
  
 次の表では、前の表に示された機能について説明します。  
  
|機能|説明|  
|--------|--------|  
|相互運用性の種類|バインディングによる相互操作を可能にするプロトコルまたはテクノロジに名前を付けます。|  
|セキュリティ|チャネルをセキュリティで保護する方法を指定します。<br /><br /> -   なし : SOAP のメッセージはセキュリティで保護されず、クライアントは認証されません。<br />-   トランスポート : セキュリティ要件はトランスポート層で満たされます。<br />-   メッセージ : セキュリティ要件はメッセージ層で満たされます。<br />-   混在 : メッセージ形式でクレームに含まれ、整合性と機密性の要件がトランスポート層で満たされます。|  
|セッション|このバインディングでセッション コントラクトをサポートするかどうかを指定します。|  
|トランザクション|トランザクションが有効かどうかを指定します。|  
|双方向|双方向コントラクトがサポートされているかどうかを指定します。この機能はバインディングでセッションをサポートする必要があることに注意してください。|  
|エンコード|メッセージのネットワーク上での形式を指定します。次の値を使用できます。<br /><br /> -   テキスト : UTF\-8 など<br />-   Binary<br />-   MTOM: SOAP エンベロープのコンテキストの中でバイナリ XML 要素を効率的にエンコードするためのメソッドです。|  
|ストリーム|受信メッセージおよび送信メッセージに対してストリーミングをサポートするかどうかを指定します。バインディングで `TransferMode` プロパティを使用して値を設定します。次の値を使用できます。<br /><br /> -   <xref:System.ServiceModel.TransferMode>: 要求メッセージと応答メッセージを共にバッファリングします。<br />-   <xref:System.ServiceModel.TransferMode>: 要求メッセージと応答メッセージを共にストリーミングします。<br />-   <xref:System.ServiceModel.TransferMode>: 要求メッセージをストリーミングし、応答メッセージをバッファリングします。<br />-   <xref:System.ServiceModel.TransferMode>: 要求メッセージをバッファリングし、応答メッセージをストリーミングします。|  
  
## 参照  
 [エンドポイントの作成の概要](../../../docs/framework/wcf/endpoint-creation-overview.md)   
 [サービスとクライアントを構成するためのバインディングの使用](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)   
 [基本的な WCF プログラミング](../../../docs/framework/wcf/basic-wcf-programming.md)