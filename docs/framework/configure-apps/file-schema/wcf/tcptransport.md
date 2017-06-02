---
title: "&lt;tcpTransport&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 8fcd18c1-9958-42e7-b442-7903f7bdb563
caps.latest.revision: 18
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# &lt;tcpTransport&gt;
カスタム バインディングのメッセージを転送するためにチャネルで使用できる TCP トランスポートを定義します。  
  
## 構文  
  
```  
  
<tcpTransport   
    listenBacklog="Integer"  
        portSharingEnabled="Boolean"  
    teredoEnabled="Boolean"  
    transferMode=”Buffered/Streamed”  
        <connectionPoolSettings  
          groupName=”String”  
        idleTimeout"TimeSpan"  
        leaseTimeout="TimeSpan"  
        maxOutboundConnectionsPerEndpopint=”Integer” />  
/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|channelInitializationTimeout|接続が切断されるまでのチャネルの初期化ステータスの最大時間 \(秒単位\)。  このクォータは、.Net メッセージ フレーム プロトコルを使用して TCP 接続が接続を認証するのに必要な時間を含みます。  クライアントは、サーバーが認証を実行するための十分な情報を得る前に初期データを送信する必要があります。  既定値は 30 秒です。|  
|listenBacklog|Web サービスの保留可能なキュー内の接続要求の最大数。  `connectionLeaseTimeout` 属性は、クライアントが接続されるのを待つ時間を制限します。この時間が経過すると接続の例外をスローします。  これは、Web サービスに対して保留可能なキュー内の接続要求の最大数を制御するソケット レベルのプロパティです。  したがって、ListenBacklog が低すぎる場合、サーバーが既存のキュー内の接続の一部を確認するまで WCF は要求を受け入れを停止し、新しい接続を破棄します。既定値は 16 x Sql プロセッサの数です。|  
|portSharingEnabled|TCP ポート共有をこの接続で有効にする場合に指定するブール値。  これが `false` の場合、各バインディングは独自の排他ポートを使用します。  既定値は、`false` です。<br /><br /> この設定は、サービスのみに関連します。  クライアントには影響はありません。<br /><br /> この設定を使用するには、\[スタートアップの種類\] を \[手動\] または \[自動\] に変更して、Windows Communication Foundation \(WCF\) の TCP ポート共有サービスを有効にする必要があります。|  
|teredoEnabled|Teredo \(ファイアウォールの内側にあるクライアントをアドレス指定するためのテクノロジ\) が有効であるかどうかを指定するブール値。  既定値は、`false` です。<br /><br /> このプロパティは、基になる TCP ソケットで Tredo を有効にします。  詳細については、「[Teredo の概要](http://go.microsoft.com/fwlink/?LinkId=95339)」を参照してください。<br /><br /> このプロパティは [!INCLUDE[wxpsp2](../../../../../includes/wxpsp2-md.md)] および [!INCLUDE[ws2003](../../../../../includes/ws2003-md.md)] にのみ適用できます。  [!INCLUDE[wv](../../../../../includes/wv-md.md)] には、Teredo 用のコンピューター全体の構成オプションがあるので、Vista を実行する場合は、このプロパティは無視されます。  Teredo の場合、クライアント コンピューターおよびサービス コンピューターの両方に Microsoft IPv6 スタックをインストールし、Teredo 用に正しく設定する必要があります。  Teredo の構成の詳細については、「[Teredo の概要](http://go.microsoft.com/fwlink/?LinkId=95339)」を参照してください。  詳細については、「[Windows Server 2003 Technology Centers](http://go.microsoft.com/fwlink/?LinkId=49888)」を参照してください。|  
  
### 子要素  
 なし  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<binding\>](../../../../../docs/framework/misc/binding.md)|カスタム バインドのすべてのバインド機能を定義します。|  
  
## 解説  
 このトランスポートは、"net.tcp:\/\/hostname:port\/path" の形式の URI を使用します。  他の URI コンポーネントは省略可能です。  
  
 `tcpTransport` 要素は、TCP トランスポート プロトコルを実装するカスタム バインディングを作成する場合の開始点となります。  このトランスポートは、WCF 間の通信用に最適化されています。  
  
## 参照  
 <xref:System.ServiceModel.Configuration.TcpTransportElement>   
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>   
 <xref:System.ServiceModel.Channels.TransportBindingElement>   
 <xref:System.ServiceModel.Channels.CustomBinding>   
 [トランスポート](../../../../../docs/framework/wcf/feature-details/transports.md)   
 [トランスポートの選択](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)   
 [バインディング](../../../../../docs/framework/wcf/bindings.md)   
 [バインディングの拡張](../../../../../docs/framework/wcf/extending/extending-bindings.md)   
 [カスタム バインディング](../../../../../docs/framework/wcf/extending/custom-bindings.md)   
 [\<customBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)