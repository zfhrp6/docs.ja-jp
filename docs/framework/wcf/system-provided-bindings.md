---
title: "システム標準のバインディング"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- bindings [WCF], system-provided
ms.assetid: 2c243746-45ce-4588-995e-c17126a579a6
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c5f8df31e31c9617fe7bcd92789671d220382a82
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="system-provided-bindings"></a>システム標準のバインディング
バインディングにより、エンドポイントとの通信で使用する通信メカニズムが指定され、エンドポイントへの接続方法が示されます。 バインディングには次の要素が含まれます。  
  
-   プロトコル スタックは、エンドポイントに送信されるメッセージで使用するセキュリティ、信頼性、およびコンテキスト フローの設定を決定します。  
  
-   トランスポートは、エンドポイントにメッセージを送信するときに使用する基礎トランスポート プロトコル (TCP または HTTP など) を決定します。  
  
-   エンコードは、エンドポイントに送信されるメッセージに使用するネットワーク エンコード (text/XML、バイナリ、MTOM (Message Transmission Optimization Mechanism) など) を決定します。  
  
 ここでは、システム指定の [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] バインディングをすべて示します。 このバインディングがいずれもアプリケーションの条件に適合しない場合は、カスタム バインドを作成できます。 [!INCLUDE[crabout](../../../includes/crabout-md.md)]カスタム バインディングを作成するを参照してください[カスタム バインド](../../../docs/framework/wcf/extending/custom-bindings.md)です。  
  
 WS-Federation プロトコルをサポートする、セキュリティで保護された相互操作可能なバインディングを使用すると、フェデレーションに属す組織のユーザーを効率的に認証および承認できます。  
  
> [!IMPORTANT]
>  常にセキュリティを備えたバインディングを選択します。 既定では、すべてのバインドを除く、 [ \<basicHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)要素が有効になっているセキュリティ保護されています。 セキュリティで保護されたバインディングを選択しない場合、またはセキュリティを無効にする場合は、セキュリティで保護されたデータ センターや隔離されたネットワークにデータを保存するなど、他の方法でデータを保護してください。  
  
> [!IMPORTANT]
>  他の方法によってデータをセキュリティ保護している場合を除き、セキュリティをサポートしないバインディングやセキュリティが無効になっているバインディングでは、双方向コントラクトを使用しないでください。  
  
## <a name="system-provided-bindings"></a>システム標準のバインディング  
 次のバインディングは [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] に付属します。  
  
|バインド|構成要素|説明|  
|-------------|---------------------------|-----------------|  
|<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)|ASP.NET Web サービス (ASMX) ベースのサービスなど、WS-Basic Profile に適合する Web サービスとの通信に適したバインディング。 このバインディングはトランスポートとして HTTP を、既定のメッセージ エンコーディングとして text/XML を使用します。|  
|<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|二重のサービス コントラクト以外に適した、セキュリティで保護された相互操作可能なバインディング。|  
|<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)|二重のサービス コントラクト、または SOAP 中継局を介しての通信に適した、セキュリティで保護された相互操作可能なバインディング。|  
|<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|フェデレーションに属す組織のユーザーを効率的に認証および承認できる WS-Federation プロトコルをサポートする、セキュリティで保護された相互操作可能なバインディング。|  
|<xref:System.ServiceModel.NetHttpBinding>|\<netHttpBinding >|HTTP や WebSocket のサービスを使用するように設計され、既定ではバイナリ エンコードを使用するバインディング。|  
|<xref:System.ServiceModel.NetHttpsBinding>|\<netHttpsBinding >|HTTP や WebSocket のサービスを使用するように設計され、既定ではバイナリ エンコードを使用するセキュリティで保護されたバインディング。|  
|<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)|[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] アプリケーション間での複数コンピューターの通信に適した、セキュリティで保護された最適バインディング。|  
|<xref:System.ServiceModel.NetNamedPipeBinding>|[\<netNamedPipeBinding >](../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md)|[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] アプリケーション間でのコンピューター通信に適した、セキュリティで保護された信頼できる最適バインディング。|  
|<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding >](../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] アプリケーション間での複数コンピューターの通信に適した、キューに置かれたバインディング。|  
|<xref:System.ServiceModel.NetPeerTcpBinding>|[\<netPeerTcpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md)|セキュリティで保護された、複数のコンピューター通信を可能にするバインディング。|  
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|[\<msmqIntegrationBinding >](../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)|[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] アプリケーションとメッセージ キュー (MSMQ: Message Queuing) アプリケーション間のコンピューター間通信に適したバインディング。|  
|<xref:System.ServiceModel.BasicHttpContextBinding>|[\<basicHttpContextBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpcontextbinding.md)|WS-Basic Profile に適合する Web サービスとの通信に適したバインディング。このバインディングでは、HTTP クッキーを使用してコンテキストを交換できるようになります。|  
|<xref:System.ServiceModel.NetTcpContextBinding>|[\<netTcpContextBinding >](../../../docs/framework/configure-apps/file-schema/wcf/nettcpcontextbinding.md)|[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] アプリケーション間での複数コンピューターの通信に適した、セキュリティで保護された最適バインディング。このバインディングでは、SOAP ヘッダーを使用してコンテキストを交換できるようになります。|  
|<xref:System.ServiceModel.WebHttpBinding>|[\<webHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)|SOAP メッセージではなく、HTTP 要求を介して公開される [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Web サービスのエンドポイントを構成するために使用されるバインディング。|  
|<xref:System.ServiceModel.WSHttpContextBinding>|[\<wsHttpContextBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpcontextbinding.md)|セキュリティで保護されたと |<xref:System.ServiceModel.UdpBinding>|\<udpBinding >|単純なメッセージを複数のクライアントに同時に送信するために使用されるバインディング。|  
  
 各システム指定のバインディングの機能を次の表に示します。 各バインディングをこの表の列に示します。機能とその説明は 2 番目の表の行に示します。 次の表に、使用されるバインディングの省略形のキーを示します。 バインディングを選択するには、必要な行の機能がすべて含まれる列を調べます。  
  
|バインド|相互運用性|セキュリティ (既定)|セッション<br /><br /> (既定)|トランザクション|二重|エンコード (かっこ内は既定値)|ストリーム<br /><br /> (既定)|  
|-------------|----------------------|--------------------------|-----------------------------|------------------|------------|--------------------------|-------------------------------|  
|<xref:System.ServiceModel.BasicHttpBinding>|Basic Profile 1.1|(なし)、トランスポート、メッセージ、混在|(なし)|(なし)|N/A|テキスト、(MTOM)|[はい]<br /><br /> (buffered)|  
|<xref:System.ServiceModel.WSHttpBinding>|WS|トランスポート、(メッセージ)、混在|(なし)、信頼できるセッション、セキュリティ保護されたセッション|(なし)、あり|N/A|(テキスト)、MTOM|×|  
|<xref:System.ServiceModel.WSDualHttpBinding>|WS|(メッセージ)、なし|(信頼できるセッション)、セキュリティ保護されたセッション|(なし)、あり|[はい]|(テキスト)、MTOM|×|  
|<xref:System.ServiceModel.WSFederationHttpBinding>|WS-Federation|(メッセージ)、混在、なし|(なし)、信頼できるセッション、セキュリティ保護されたセッション|(なし)、あり|×|(テキスト)、MTOM|×|  
|<xref:System.ServiceModel.NetHttpBinding>|.NET|(なし)、トランスポート、メッセージ、TransportWithMessageCredential、TransportCredentialOnly|下記のメモを参照|なし|下記のメモを参照|(バイナリ)、テキスト、MTOM|〇 (バッファリング)|  
|<xref:System.ServiceModel.NetHttpsBinding>|.NET|(トランスポート)、TransportWithMessageCredential|下記のメモを参照|なし|下記のメモを参照|(バイナリ)、テキスト、MTOM|〇 (バッファリング)|  
|<xref:System.ServiceModel.NetTcpBinding>|.NET|(トランスポート)、メッセージ、なし、混在|(トランスポート)、信頼できるセッション、セキュリティ保護されたセッション|(なし)、あり|[はい]|2 項|[はい]<br /><br /> (buffered)|  
|<xref:System.ServiceModel.NetNamedPipeBinding>|.NET|(トランスポート)、なし|なし、(トランスポート)|(なし)、あり|[はい]|2 項|[はい]<br /><br /> (buffered)|  
|<xref:System.ServiceModel.NetMsmqBinding>|.NET|メッセージ、(トランスポート)、なし|(なし)、トランスポート|なし、(あり)|×|2 項|×|  
|<xref:System.ServiceModel.NetPeerTcpBinding>|Peer|(トランスポート)|(なし)|(なし)|[はい]||×|  
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|MSMQ|(トランスポート)|(なし)|なし、(あり)|N/A|N/A|×|  
|<xref:System.ServiceModel.BasicHttpContextBinding>|Basic Profile 1.1|(なし)、トランスポート、メッセージ、混在|(なし)|(なし)|N/A|テキスト、(MTOM)|[はい]<br /><br /> (buffered)|  
|<xref:System.ServiceModel.NetTcpContextBinding>|.NET|(トランスポート)、メッセージ、なし、混在|(トランスポート)、信頼できるセッション、セキュリティ保護されたセッション|(なし)、あり|[はい]|2 項|[はい]<br /><br /> (buffered)|  
|<xref:System.ServiceModel.WSHttpContextBinding>|WS|トランスポート、(メッセージ)、混在|(なし)、信頼できるセッション、セキュリティ保護されたセッション|(なし)、あり|N/A|テキスト、(MTOM)|×|  
|<xref:System.ServiceModel.UdpBinding>|.NET**注:**相互運用性は、このバインディングを実装する標準の over UDP の SOAP 仕様を実装することによって実現できます。|(なし)|(なし)|(なし)|N/A|(テキスト)|×|  
  
> [!IMPORTANT]
>  <xref:System.ServiceModel.NetHttpBinding> は、HTTP や WebSocket のサービスを使用するために設計されたバインドで、既定ではバイナリ エンコードを使用します。 <xref:System.ServiceModel.NetHttpBinding> は、要求-応答コントラクトと双方向コントラクトのどちらで使用されているかを検出し、一致するように動作を変更します。要求-応答には HTTP、双方向には WebSocket を使用します。 使用してこの動作をオーバーライドすることができます、 <!--zz <xref:System.ServiceModel.NetHttpBinding.WebSocketTransportUsage%2A>--> `System.ServiceModel.NetHttpBinding.WebSocketTransportUsage`バインディング: - 許可されているこの既定値は、前述のように動作します。NotAllowed - この Websocket が使用されないようにします。 この設定で二重のコントラクトを使用しようとして、例外が発生します。必要な - Websocket が要求/応答コントラクトに対しても使用されるようにします。 NetHttpBinding では、HTTP モードと WebSocket モードの両方で信頼できるセッションをサポートしています。 WebSocket モードでは、セッションがトランスポートによって提供されます。  
  
 次の表では、前の表に示された機能について説明します。  
  
|機能|説明|  
|-------------|-----------------|  
|相互運用性の種類|バインディングによる相互操作を可能にするプロトコルまたはテクノロジに名前を付けます。|  
|セキュリティ|チャネルをセキュリティで保護する方法を指定します。<br /><br /> -なし:、SOAP メッセージ セキュリティ保護されていないと、クライアントが認証されていません。<br />トランスポート: セキュリティ要件はトランスポート層で満たされます。<br />-メッセージ: セキュリティ要件はメッセージ層で満たされます。<br />混合: 要求が実行されます。 メッセージです。整合性と機密性の要件はトランスポート層で満たされます。|  
|セッション|このバインディングでセッション コントラクトをサポートするかどうかを指定します。|  
|トランザクション|トランザクションが有効かどうかを指定します。|  
|二重|二重のコントラクトがサポートされているかどうかを指定します。 この機能はバインディングでセッションをサポートする必要があることに注意してください。|  
|エンコード|メッセージのネットワーク上での形式を指定します。 次の値を使用できます。<br /><br /> テキスト。 たとえば utf-8 です。<br />-バイナリ<br />メッセージ転送の最適化メカニズム (MTOM): SOAP エンベロープのコンテキスト内でのバイナリの XML 要素を効率的にエンコードするためのメソッドです。|  
|ストリーム|受信メッセージおよび送信メッセージに対してストリーミングをサポートするかどうかを指定します。 バインディングで `TransferMode` プロパティを使用して値を設定します。 次の値を使用できます。<br /><br /> -   <xref:System.ServiceModel.TransferMode.Buffered>: 要求メッセージと応答メッセージを共にバッファリングします。<br />-   <xref:System.ServiceModel.TransferMode.Streamed>: 要求メッセージと応答メッセージを共にストリーミングします。<br />-   <xref:System.ServiceModel.TransferMode.StreamedRequest>: 要求メッセージをストリーミングし、応答メッセージをバッファーします。<br />-   <xref:System.ServiceModel.TransferMode.StreamedResponse>: 要求メッセージをバッファーし、応答メッセージをストリーミングします。|  
  
## <a name="see-also"></a>参照  
 [エンドポイントの作成の概要](../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [サービスとクライアントを構成するためのバインディングの使用](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [基本的な WCF プログラミング](../../../docs/framework/wcf/basic-wcf-programming.md)
