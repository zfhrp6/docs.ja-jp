---
title: "&lt;udpAnnoucementEndpoint&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5b3fa9c5-f372-4df9-a9d6-1e426063b721
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# &lt;udpAnnoucementEndpoint&gt;
この構成要素は、UDP バインディングを使用してアナウンス メッセージを送信するためにサービスが使用する標準エンドポイントを定義します。  これには固定コントラクトがあり、2 つの探索のバージョンをサポートします。  また、WS\-Discovery の仕様 \(WS\-Discovery April 2005 または WS\-Discovery V1.1\) に規定された固定 UDP バインディングと既定のアドレスも備えています。  アナウンス メッセージの送受信に使用するマルチキャスト アドレスを指定できます。  
  
## 構文  
  
```  
  
<system.serviceModel>  
    <standardEndpoints>  
       <announcementEndpoint>   
          <standardEndpoint  
                  discoveryVersion=”WSDiscovery11/WSDiscoveryApril2005”  
                  maxAnnouncementDelay=”Timespan”   
                  multicastAddress=”Uri”  
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
|multicastAddress|探索メッセージの送受信に使用するマルチキャスト アドレスを指定する URI。  既定値は、プロトコル仕様に準じたマルチキャスト アドレスです。|  
|name|標準エンドポイントの構成名を指定する文字列。  この名前は、サービス エンドポイントの `endpointConfiguration` 属性で使用され、標準エンドポイントと構成を関連付けます。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<udpTransportSettings\>](../../../../../docs/framework/configure-apps/file-schema/wcf/udptransportsettings.md)|UDP エンドポイントの UDP トランスポートを構成できる設定のコレクション。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<standardEndpoints\>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|1 つ以上のプロパティ \(アドレス、バインディング、コントラクト\) が固定されている、あらかじめ定義されたエンドポイントである標準エンドポイントのコレクション。|  
  
## 使用例  
 既定のマルチキャスト アドレスを使用した UDP マルチキャスト トランスポート経由、および指定されたマルチキャスト アドレスを使用した UDP マルチキャスト トランスポート経由でアナウンスをリッスンするクライアントの例を次に示します。  
  
```  
  
<services>  
  <service name="ServiceAnnouncementListener">  
      <endpoint name="udpAnnouncementEndpointStandard"  
                kind="udpAnnouncementEndpoint"  
                bindingConfiguration="..." />  
      <endpoint name="udpAnnouncementEndpoint2"  
                kind="udpAnnouncementEndpoint"  
                endpointConfiguration="AnnouncementConfiguration3702"  
                bindingConfiguration="..." />  
...  
  </service>  
</services>  
<standardEndpoints>  
  <udpAnnouncementEndpoint>  
     <standardEndpoint name="AnnouncementConfiguration2"   
          version="WSDiscoveryApril2005"   
          multicastAddress="soap.udp://239.255.255.250:3703"/>          
  </udpAnnouncementEndpoint>  
</standardEndpoints>  
  
```  
  
## 参照  
 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>