---
title: '&lt;netPeerTcpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: netPeerBinding element
ms.assetid: 2dd77ada-a176-47c7-a740-900b279f1aad
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2d20faaee94363a1f54cf398d72955f376087b36
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltnetpeertcpbindinggt"></a>&lt;netPeerTcpBinding&gt;
ピア チャネル固有の TCP メッセージングのバインディングを定義します。  
  
 \<システムです。ServiceModel >  
\<バインド >  
\<netPeerTcpBinding >  
  
## <a name="syntax"></a>構文  
  
```xml  
<netPeerBinding>  
    <binding name="string"  
         closeTimeout="TimeSpan"  
         openTimeout="TimeSpan"   
         receiveTimeout="TimeSpan"  
         sendTimeout="TimeSpan"  
         listenIPAddress="String"  
          maxBufferPoolSize="integer"  
         maxReceiveMessageSize="Integer"   
         port="Integer"  
         <security mode="None/Transport/Message/TransportWithMessageCredential">  
            <transport credentialType="Certificate/Password" />  
        </security>  
    </binding>  
</netPeerBinding>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|closeTimeout|クローズ操作が完了するまでの期間を指定する <xref:System.TimeSpan> 値。 この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。 既定値は 00:01:00 です。|  
|listenIPAddress|ピア ノードが TCP メッセージをリッスンする IP アドレスを指定する文字列です。 既定値は、`null` です。|  
|maxBufferPoolSize|このバインディングに使用するバッファー プール サイズの上限を指定する整数。 既定は 524,288 バイト (512 * 1024) です。 Windows Communication Foundation (WCF) では、多くの部分でバッファーを使用します。 使用するたびに毎回バッファーを作成および破壊すると負荷が高くなります。バッファーのガベージ コレクションも同様です。 バッファー プールを使用すると、バッファーをプールから取得して使用し、作業が終わったらプールに戻すことができます。 これで、バッファーの作成と破棄のオーバーヘッドを回避できます。|  
|maxReceivedMessageSize|このバインディングで構成されるチャネルで受信可能な最大メッセージ サイズ (ヘッダーを含む) をバイト単位で指定する正の整数。 この制限を超えるメッセージの送信者が、SOAP エラーを受信します。 メッセージは受信者によって破棄され、トレース ログにこのイベントのエントリが作成されます。 既定値は 65536 です。|  
|name|バインディングの構成名を格納する文字列です。 この値は、バインディングの ID として使用されるため、一意にする必要があります。 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 以降では、バインディングおよび動作に名前を付ける必要はありません。 既定の構成と無名のバインディングおよび動作の詳細については、次を参照してください。[簡略化された構成](../../../../../docs/framework/wcf/simplified-configuration.md)と[WCF サービスの構成を簡略化](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)です。|  
|openTimeout|実行中の操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。 この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。 既定値は 00:01:00 です。|  
|ポート|このバインディングがピア チャネルの TCP メッセージを処理するネットワーク インターフェイス ポートを指定する整数です。 この値の有効値の範囲は <xref:System.Net.IPEndPoint.MinPort> ～ <xref:System.Net.IPEndPoint.MaxPort> です。 既定値は 0 です。|  
|receiveTimeout|受信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。 この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。 既定値は 00:10:00 です。|  
|sendTimeout|送信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。 この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。 既定値は 00:01:00 です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<ある readerQuotas >](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|このバインドを使用して設定されるエンドポイントにより処理可能な、SOAP メッセージの複雑さに対する制約を定義します。 この要素は <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> 型です。|  
|[\<競合回避モジュール >](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|ピア メッシュ ID を解決してピア メッシュ内のノードのエンドポイント ID アドレスを取得するために、このバインディングによって使用されるピア リゾルバーを指定します。|  
|[\<セキュリティ >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|メッセージのセキュリティ設定を定義します。 この要素は <xref:System.ServiceModel.Configuration.PeerSecurityElement> 型です。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<バインド >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|この要素には、標準バインディングおよびカスタム バインディングのコレクションが保持されます。|  
  
## <a name="remarks"></a>コメント  
 このバインディングは、TCP を介したピア トランスポートを使用するピア ツー ピア アプリケーションまたはマルチパーティ アプリケーションの作成をサポートします。 各ピア ノードは、この種類のバイディングを使用して定義された複数のピア チャネルをホストできます。  
  
## <a name="example"></a>例  
 次の例では、ピア チャネルを使用してマルチパーティ通信を実現する、NetPeerTcpBinding バインディングを使用する方法を示します。 このバインディングの使用の詳細なシナリオでは、次を参照してください。 [Net ピア TCP](http://msdn.microsoft.com/en-us/31f4db66-edb2-40a6-b92a-14098e92acae)です。  
  
```xml  
<configuration>  
<system.ServiceModel>  
<bindings>  
<netPeerBinding>  
    <binding   
         closeTimeout="00:00:10"  
         openTimeout="00:00:20"   
         receiveTimeout="00:00:30"  
         sendTimeout="00:00:40"  
         maxBufferSize="1001"  
         maxConnections="123"   
         maxReceiveMessageSize="1000">  
        <reliableSession ordered="false"  
            inactivityTimeout="00:02:00"  
            enabled="true" />  
        <security mode="TransportWithMessageCredential">  
            <message clientCredentialType="CardSpace" />  
        </security>  
    </binding>  
</netPeerBinding>  
</bindings>  
</system.ServiceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>参照  
 <xref:System.ServiceModel.NetPeerTcpBinding>  
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement>  
 [バインディング](../../../../../docs/framework/wcf/bindings.md)  
 [システムが提供するバインディングの構成](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<バインド >](../../../../../docs/framework/misc/binding.md)  
 [Net ピア TCP](http://msdn.microsoft.com/en-us/31f4db66-edb2-40a6-b92a-14098e92acae)  
 [ピアツーピア ネットワーク](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
