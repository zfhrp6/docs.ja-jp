---
title: "双方向サービス"
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
ms.assetid: 396b875a-d203-4ebe-a3a1-6a330d962e95
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a5c7cb9d963e56c6a6e06421afdb14427440643c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="duplex-services"></a>双方向サービス
双方向サービス コントラクトは、両方のエンドポイントが互いに独立してメッセージを送信できるメッセージ交換パターンです。 双方向サービスでは、クライアントのエンドポイントにメッセージを返信できるため、イベントのような動作を実現できます。 双方向通信は、クライアントがサービスに接続し、サービスからクライアントにメッセージを返信できるチャネルがサービスに提供されると発生します。 双方向サービスにおけるイベントのような動作は、セッション内でのみ機能することに注意してください。  
  
 双方向コントラクトを作成するには、インターフェイスのペアを作成します。 最初のインターフェイスは、クライアントから呼び出すことのできる操作を記述したサービス コントラクト インターフェイスです。 そのサービス コントラクトを指定する必要があります、*コールバック コントラクト*で、<xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType>プロパティです。 このコールバック コントラクトが、サービスがクライアント エンドポイントで呼び出すことのできる操作を定義するインターフェイスになります。 双方向コントラクトではセッションは必要ありませんが、システム指定の二重バインディングではセッションを利用します。  
  
 双方向コントラクトの例を次に示します。  
  
 [!code-csharp[c_DuplexServices#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#0)]
 [!code-vb[c_DuplexServices#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#0)]  
  
 `CalculatorService` クラスは、プライマリ `ICalculatorDuplex` インターフェイスを実装します。 このサービスは <xref:System.ServiceModel.InstanceContextMode.PerSession> インスタンス モードを使用して、各セッションの結果を保持します。 `Callback` というプライベート プロパティを使用して、クライアントへのコールバック チャネルにアクセスします。 次のサンプル コードに示すように、サービスはこのコールバックを使用し、コールバック インターフェイスを介してメッセージをクライアントに返信します。  
  
 [!code-csharp[c_DuplexServices#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#1)]
 [!code-vb[c_DuplexServices#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#1)]  
  
 クライアントは、サービスからのメッセージを受信するために、双方向コントラクトのコールバック インターフェイスを実装するクラスを提供する必要があります。 次のサンプル コードに、`CallbackHandler` インターフェイスを実装する `ICalculatorDuplexCallback` クラスを示します。  
  
 [!code-csharp[c_DuplexServices#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#2)]
 [!code-vb[c_DuplexServices#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#2)]  
  
 双方向コントラクト用に生成された [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントには、構築時に <xref:System.ServiceModel.InstanceContext> クラスを提供する必要があります。 この <xref:System.ServiceModel.InstanceContext> クラスが、コールバック インターフェイスを実装するオブジェクトのサイトとして使用され、サービスから返信されるメッセージを処理します。 <xref:System.ServiceModel.InstanceContext> クラスは、`CallbackHandler` クラスのインスタンスを使用して構築されます。 このオブジェクトは、コールバック インターフェイスでサービスからクライアントに送信されるメッセージを処理します。  
  
 [!code-csharp[c_DuplexServices#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#3)]
 [!code-vb[c_DuplexServices#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#3)]  
  
 サービスの構成は、セッション通信と双方向通信の両方をサポートするバインディングを提供するように設定する必要があります。 `wsDualHttpBinding` 要素はセッション通信をサポートし、どちらの方向にも HTTP 接続が 1 つ用意される双方向 HTTP 接続を提供して双方向通信を実現します。  
  
 クライアントで、サーバーがクライアントへの接続に使用するアドレスを構成する必要があります。次のサンプル構成を参照してください。  
  
  
  
> [!NOTE]
>  非双方向クライアントがセキュリティで保護されたメッセージ交換を使用して認証に失敗した場合、通常、<xref:System.ServiceModel.Security.MessageSecurityException> がスローされます。 ただし、セキュリティで保護されたメッセージ交換を使用する双方向クライアントが認証に失敗した場合、クライアントは代わりに <xref:System.TimeoutException> を受信します。  
  
 `WSHttpBinding` 要素を使用するクライアントとサービスを作成しても、クライアントのコールバック エンドポイントが含まれていない場合は、次のエラーが発生します。  
  
```  
HTTP could not register URL  
htp://+:80/Temporary_Listen_Addresses/<guid> because TCP port 80 is being used by another application.  
```  
  
 次のサンプル コードは、コードでクライアントのエンドポイント アドレスを指定する方法を示しています。  
  
```  
WSDualHttpBinding binding = new WSDualHttpBinding();  
EndpointAddress endptadr = new EndpointAddress("http://localhost:12000/DuplexTestUsingCode/Server");  
binding.ClientBaseAddress = new Uri("http://localhost:8000/DuplexTestUsingCode/Client/");  
```  
  
 次のサンプル コードは、構成でクライアントのエンドポイント アドレスを指定する方法を示しています。  
  
```xml  
<client>  
    <endpoint name ="ServerEndpoint"   
          address="http://localhost:12000/DuplexTestUsingConfig/Server"  
          bindingConfiguration="WSDualHttpBinding_IDuplexTest"   
            binding="wsDualHttpBinding"  
           contract="IDuplexTest" />  
</client>  
<bindings>  
    <wsDualHttpBinding>  
        <binding name="WSDualHttpBinding_IDuplexTest"    
          clientBaseAddress="http://localhost:8000/myClient/" >  
            <security mode="None"/>  
         </binding>  
    </wsDualHttpBinding>  
</bindings>  
```  
  
> [!WARNING]
>  双方向モデルでは、サービスまたはクライアントによってチャネルがいつ閉じられたかが自動的に検出されません。 このため、サービスが突然終了した場合、既定ではクライアントには通知されず、クライアントが突然終了した場合も、サービスには通知されません。 クライアントとサービスは、独自のプロトコルを実装して、互いに通知するように選択できます。  
  
## <a name="see-also"></a>関連項目  
 [双方向](../../../../docs/framework/wcf/samples/duplex.md)  
 [クライアントのランタイム動作の指定](../../../../docs/framework/wcf/specifying-client-run-time-behavior.md)  
 [方法: チャネル ファクトリを作成、しを使用して作成するチャネルの管理](../../../../docs/framework/wcf/feature-details/how-to-create-a-channel-factory-and-use-it-to-create-and-manage-channels.md)
