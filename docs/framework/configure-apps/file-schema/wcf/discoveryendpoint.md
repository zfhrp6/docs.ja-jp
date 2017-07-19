---
title: "&lt;discoveryEndpoint&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fae2f48b-a635-4e4b-859d-a1432ac37e1c
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# &lt;discoveryEndpoint&gt;
この構成要素は、固定探索コントラクトが含まれた標準エンドポイントを定義します。  サービスの構成に追加すると、この要素により、探索メッセージをリッスンする場所が指定されます。  クライアントの構成に追加すると、この要素により、探索クエリの送信先となる場所が指定されます。  
  
## 構文  
  
```  
  
<system.serviceModel>  
    <standardEndpoints>  
       <discoveryEndpoint>   
          <standardEndpoint  
                  discoveryMode=”Adhoc/Managed”  
                  discoveryVersion=”WSDiscovery11/WSDiscoveryApril2005”  
                  maxResponseDelay=”Timespan”   
                  name="String" />  
       </discoveryEndpoint>          
    </standardEndpoints>  
</system.serviceModel>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|discoveryMode|探索プロトコルのモードを示す文字列。  有効値は "Adhoc" と "Managed" です。  マネージ モードでは、プロトコルは Discoverable サービスのリポジトリとして機能する Discovery Proxy に依存します。  アドホック モードでは、プロトコルは UDP マルチキャスト メカニズムを使用して利用可能なサービスを探索する必要があります。  この値は、<xref:System.Servicemodel.Discovery.DiscoveryMode> 型です。|  
|discoveryVersion|WS\-Discovery プロトコルの 2 つのバージョンのうち、1 つを指定する文字列。  有効値は WSDiscovery11 と WSDiscoveryApril2005 です。  この値は、<xref:System.Servicemodel.Discovery.DiscoveryVersion> 型です。|  
|maxResponseDelay|Discovery プロトコルが Probe Match や Resolve Match などのメッセージを送信するまでの待機時間の最大値を指定する Timespan 値。<br /><br /> すべての ProbeMatch が同時に送信されると、ネットワーク ストームが発生することがあります。  これを防ぐために、各 ProbeMatch はランダムな時間だけ待機して送信されます。  ランダムな待機時間は、0 からこの属性に設定された値の範囲内で設定されます。  この属性を 0 に設定すると、ProbeMatch メッセージは待機せずに短いループで送信されます。  それ以外の場合は、ProbeMatch メッセージはランダムな時間だけ待機して送信されます。すべての ProbeMatch メッセージの送信にかかる合計時間が maxResponseDelay を超えることはありません。  この値はサービスのみに関連するもので、クライアントが使用するものではありません。|  
|`name`|標準エンドポイントの構成名を指定する文字列。  この名前は、サービス エンドポイントの `endpointConfiguration` 属性で使用され、標準エンドポイントと構成を関連付けます。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<standardEndpoints\>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|1 つ以上のプロパティ \(アドレス、バインディング、コントラクト\) が固定されている、あらかじめ定義されたエンドポイントである標準エンドポイントのコレクション。|  
  
## 使用例  
 ピア ネットワーク マルチキャスト トランスポート経由で探索メッセージをリッスンするサービスの例を次に示します。  この例では、明示的に WS\-Discovery April 2005 バージョンを指定します。  
  
 標準エンドポイントの構成はサービスごとに定義します。サービス間で共有することはできません。  別のサービスで同じ探索エンドポイントを使用するには、該当のサービスのセクションに同じ構成を追加する必要があります。  
  
```  
  
<services>  
    <service name="CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
             <endpoint binding="basicHttpBinding"   
                address="calculator" contract="ICalculatorService" />  
             <endpoint name="peerNetDiscovery"  
                binding="peerTcpBinding"  
                address="net.p2p://discoveryMesh/multicast"  
                kind="discoveryEndpoint"  
                endpointConfiguration="peerTcpDiscoveryEndpointConfiguration"  
                bindingConfiguration="discoveryPeerTcpBindingConfig" />      
   </service>  
</services>  
<standardEndpoints>  
  <discoveryEndpoint>  
     <standardEndpoint name="peerTcpDiscoveryEndpointConfiguration "                         
                       version="WSDiscoveryApril2005" />  
   </discoveryEndpoint>  
</standardEndpoints>  
  
```  
  
## 参照  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>