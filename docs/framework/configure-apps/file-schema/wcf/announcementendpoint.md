---
title: "&lt;announcementEndpoint&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 034b7c69-a770-4502-8cef-38007bbcd025
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# &lt;announcementEndpoint&gt;
この構成要素は、固定アナウンス コントラクトが設定されている標準エンドポイントを定義します。  サービスは、サービスが開いたとき、または閉じたときにオンラインおよびオフラインのアナウンス メッセージを送信することによって、その可用性をアナウンスすることもできます。  [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] サービスは、[\<serviceDiscovery\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) 要素でアナウンス エンドポイントを指定し、AnnouncementClient を使用してアナウンスを実行します。  他のサービスからのアナウンスをリッスンしようとするクライアントは、実際に、[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] サービスとして動作します。このため、[\<services\>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md) セクションに、このクライアントのアナウンス エンドポイントを構成する必要があります。  
  
## 構文  
  
```  
  
<system.serviceModel>  
    <standardEndpoints>  
       <announcementEndpoint>   
          <standardEndpoint  
                  discoveryVersion=”WSDiscovery11/WSDiscoveryApril2005”  
                  maxAnnouncementDelay=”Timespan”   
                  name="String" />   
       </announcementEndpoint>          
    </standardEndpoints>  
</system.serviceModel>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|discoveryVersion|WS\-Discovery プロトコルの 2 つのバージョンのうち、1 つを指定する文字列。  有効値は WSDiscovery11 と WSDiscoveryApril2005 です。  この値は、<xref:System.ServiceModel.Discovery.Configuration.DiscoveryVersion> 型です。|  
|maxAnnouncementDelay|Discovery プロトコルが Hello メッセージを送信するまでの待機時間の最大値を指定する Timespan 値。  メッセージは送信前に 0 からこの属性値の間のランダムな時間だけ待機します。  この属性はランダムな短い待機時間を設定するために使用されるもので、ネットワークが機能しなくなり、すべてのサービスが同時にオンラインに戻ったときにネットワーク ストームが発生することを防ぎます。|  
|name|標準エンドポイントの構成名を指定する文字列。  この名前は、サービス エンドポイントの `endpointConfiguration` 属性で使用され、標準エンドポイントと構成を関連付けます。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<standardEndpoints\>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|1 つ以上のプロパティ \(アドレス、バインディング、コントラクト\) が固定されている、あらかじめ定義されたエンドポイントである標準エンドポイントのコレクション。|  
  
## 使用例  
 http およびピア ネットワーク経由でアナウンス メッセージをリッスンするクライアントの例を次に示します。  
  
```  
  
<services>  
  <service name="ServiceAnnouncementListener">  
              <endpoint name="httpAnnouncementEndpoint"  
                        kind="announcementEndpoint"  
                        binding="basicHttpBinding"  
                        address="announcements" />  
              <endpoint name="peerNetAnnouncementEndpoint"  
                        kind="announcementEndpoint"  
                        binding="peerTcpBinding"  
                        address="net.p2p://discoveryMesh/multicast"  
                        bindingConfiguration="discoveryPeerTcpBindingConfig" />  
  ...  
  </service>  
</services>  
  
<standardEndpoints>  
  <announcementEndpoint>  
     <standardEndpoint name="httpAnnouncementEndpoint"                         
                       version="WSDiscoveryApril2005" />  
     <standardEndpoint name="peerNetAnnouncementEndpoint"                         
                       version="WSDiscoveryApril2005" />  
   </announcementEndpoint>  
</standardEndpoints>  
  
```  
  
## 参照  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>