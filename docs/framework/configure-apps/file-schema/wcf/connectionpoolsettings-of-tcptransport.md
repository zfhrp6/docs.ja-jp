---
title: "&lt;tcpTransport&gt; の &lt;connectionPoolSettings&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2fbc3aa7-fcc9-4193-99a3-85d31d60d3f7
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f0e9c4d34caa16f41e874b7a3880325a6585c230
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltconnectionpoolsettingsgt-of-lttcptransportgt"></a>&lt;tcpTransport&gt; の &lt;connectionPoolSettings&gt;
TCP トランスポートの追加の接続プール設定を指定します。  
  
 \<system.serviceModel >  
\<バインド >  
\<customBinding >  
\<バインド >  
\<tcpTransport >  
\<connectionPoolSettings >  
  
## <a name="syntax"></a>構文  
  
```xml  
<connectionPoolSettings  
    groupName="String"  
    idleTimeout"TimeSpan"  
        leaseTimeout="TimeSpan"  
    maxOutboundConnectionsPerEndpopint="Integer" />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`groupName`|送信チャネルに使用される接続プールの名前を定義する文字列です。 ストリーム配信モードでは、接続が共有されません。したがって、接続プールは無効です。 既定は、"default" 文字列です。 この値を変更して、特定のクライアントの接続を、個別のグループに分離できます。|  
|`idleTimeout`|接続が切断されるまでの最大アイドル時間を指定する正の <xref:System.TimeSpan>。 既定値は 00:02:00 です。|  
|`leaseTimeout`|アクティブな接続が終了されるまでの時間を指定する <xref:System.TimeSpan>。 既定値は 00:05:00 です。<br /><br /> 接続は、接続キャッシュに返された後、アクティブに転送中ではないときに終了します。 TCP トランスポートによって使用される接続キャッシュは、各エンドポイントの必要に応じて、`maxOutboundConnectionsPerEndpoint.` で設定されているキャッシュ制限内で新しい接続を作成します。|  
|`maxOutboundConnectionsPerEndpoint`|そのサービスによって開始されるリモート エンドポイントへの接続の最大数を指定する正の整数。 制限を超えた接続は、制限内に空きができるまでキューに置かれます。 `idleTimeout` は、例外がスローされるまでに接続をキューに入れたままにする期間を制限します。 既定値は 10 です。<br /><br /> この属性は、クライアントから特定のサービス エンドポイントへの接続で、同時にアクティブできる接続数を制限します。 この値よりも多くのアクティブなクライアント接続がある場合、サービスは、クライアントに応答しないように見える可能性があります。 この場合は、この値を調整して、予想される特定のエンドポイントへの同時クライアント接続の最大数より大きくする必要があります。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<namedPipeTransport >](../../../../../docs/framework/configure-apps/file-schema/wcf/namedpipetransport.md)|チャネルで名前付きパイプを使用してメッセージを転送するトランスポートを定義します。|  
  
## <a name="see-also"></a>参照  
 <xref:System.ServiceModel.Configuration.TcpConnectionPoolSettingsElement>  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement.ConnectionPoolSettings%2A>  
 <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [トランスポート](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [トランスポートの選択](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [バインディング](../../../../../docs/framework/wcf/bindings.md)  
 [バインディングの拡張](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [カスタム バインディング](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
