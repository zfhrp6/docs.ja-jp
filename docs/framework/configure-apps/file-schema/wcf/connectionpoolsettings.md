---
title: "&lt;connectionPoolSettings&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6fa7fa65-2c6e-4eab-b8cf-7690112c0be5
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# &lt;connectionPoolSettings&gt;
名前付きパイプ バインディングの追加の接続プール設定を指定します。  
  
## 構文  
  
```  
  
<connectionPoolSettings  
        groupName=”String”  
    idleTimeout"TimeSpan"  
    maxOutboundConnectionsPerEndpopint=”Integer” />  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|`groupName`|送信チャネルに使用される接続プールの名前を定義する文字列です。  ストリーム配信モードでは、接続が共有されません。したがって、接続プールは無効です。  既定は、"default" 文字列です。  この値を変更して、特定のクライアントの接続を、個別のグループに分離できます。|  
|`idleTimeout`|接続が切断されるまでの最大アイドル時間を指定する正の <xref:System.TimeSpan>。  既定値は 00:02:00 です。|  
|`maxOutboundConnectionsPerEndpoint`|そのサービスによって開始されるリモート エンドポイントへの接続の最大数を指定する正の整数。  制限を超えた接続は、制限内に空きができるまでキューに置かれます。  `idleTimeout` は、例外がスローされるまでに接続をキューに入れたままにする期間を制限します。  既定値は 10 です。<br /><br /> この属性は、クライアントから特定のサービス エンドポイントへの接続で、同時にアクティブできる接続数を制限します。  この値よりも多くのアクティブなクライアント接続がある場合、サービスは、クライアントに応答しないように見える可能性があります。  この場合は、この値を調整して、予想される特定のエンドポイントへの同時クライアント接続の最大数より大きくする必要があります。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<namedPipeTransport\>](../../../../../docs/framework/configure-apps/file-schema/wcf/namedpipetransport.md)|チャネルで名前付きパイプを使用してメッセージを転送するトランスポートを定義します。|  
  
## 参照  
 <xref:System.ServiceModel.Configuration.NamedPipeConnectionPoolSettingsElement>   
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement.ConnectionPoolSettings%2A>   
 <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>   
 <xref:System.ServiceModel.Channels.TransportBindingElement>   
 <xref:System.ServiceModel.Channels.CustomBinding>   
 [トランスポート](../../../../../docs/framework/wcf/feature-details/transports.md)   
 [トランスポートの選択](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)   
 [バインディング](../../../../../docs/framework/wcf/bindings.md)   
 [バインディングの拡張](../../../../../docs/framework/wcf/extending/extending-bindings.md)   
 [カスタム バインディング](../../../../../docs/framework/wcf/extending/custom-bindings.md)   
 [\<customBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)