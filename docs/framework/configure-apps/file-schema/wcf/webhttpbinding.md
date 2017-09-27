---
title: '&lt;webHttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 84179d77-825d-44b9-895a-ab08e7aa044d
caps.latest.revision: 13
author: Erikre
ms.author: erikre
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 76883fd9702e475bd6afd9629fb4702ca42395d4
ms.openlocfilehash: 61eaf6ba83b94724555ca3fee53e3a4d538ee11a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/25/2017

---
# <a name="ltwebhttpbindinggt"></a>&lt;webHttpBinding&gt;
SOAP メッセージに代わって HTTP 要求に応答する [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Web サービスのエンドポイントを構成するために使用するバインディング要素を定義します。  
  
\<システムです。ServiceModel >  
\<バインド >  
\<webHttpBinding >  
  
## <a name="syntax"></a>構文  
  
```xml  
<webHttpBinding>  
  <binding   
    allowCookies="Boolean"  
    bypassProxyOnLocal="Boolean"  
    closeTimeout="TimeSpan"  
    hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
    maxBufferPoolSize="integer"  
    maxBufferSize="integer"  
    maxReceivedMessageSize="Integer"  
    name="string"  
    openTimeout="TimeSpan"   
    proxyAddress="URI"  
    receiveTimeout="TimeSpan"  
    sendTimeout="TimeSpan"  
    transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"  
    useDefaultWebProxy="Boolean" 
    writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding">  
  <security mode="None/Transport/TransportCredentialOnly">  
    <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
               proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
               realm="string" />  
  </security>  
  <readerQuotas maxArrayLength="Integer" 
                maxBytesPerRead="Integer" 
                maxDepth="Integer" 
                maxNameTableCharCount="Integer" 
                maxStringContentLength="Integer" />  
  </binding>  
</webHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|allowCookies|クライアントがクッキーを受け入れて、それらを今後の要求に反映させるかどうかを指定するブール値です。 既定値は false です。<br /><br /> クッキーを使用する ASMX Web サービスと対話する場合にこのプロパティを使用できます。 この方法で、サーバーから返されるクッキーを、それ以降のサービスに対するすべてのクライアント要求に自動的にコピーできます。|  
|bypassProxyOnLocal|ローカル アドレスでプロキシ サーバーをバイパスするかどうかを示すブール値。 既定値は、`false` です。|  
|closeTimeout|クローズ操作が完了するまでの期間を指定する <xref:System.TimeSpan> 値。 この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。 既定値は 00:01:00 です。|  
|hostnameComparisonMode|URI の解析に使用する HTTP ホスト名比較モードを指定します。 この属性は <xref:System.ServiceModel.HostNameComparisonMode> 型で、URI が一致したときにサービスへのアクセスにホスト名を使用するかどうかを指定します。 既定値は <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> で、一致しているホスト名を無視します。|  
|maxBufferPoolSize|このバインディングに使用するバッファー プール サイズの上限を指定する整数。 既定は 524,288 バイト (512 * 1024) です。 Windows Communication Foundation (WCF) では、多くの部分でバッファーを使用します。 使用するたびに毎回バッファーを作成および破壊すると負荷が高くなります。バッファーのガベージ コレクションも同様です。 バッファー プールを使用すると、バッファーをプールから取得して使用し、作業が終わったらプールに戻すことができます。 これで、バッファーの作成と破棄のオーバーヘッドを回避できます。|  
|maxBufferSize|チャネルからメッセージを受け取るメッセージ バッファーのマネージャーが使用するために割り当てられる最大メモリ量を指定する整数。 既定値は 524,288 (0x80000) バイトです。|  
|maxReceivedMessageSize|このバインディングで構成されるチャネルで受信可能な最大メッセージ サイズ (ヘッダーを含む) をバイト単位で指定する正の整数。 この制限を超えるメッセージの送信者はエラーを受信します。 メッセージは受信者によって破棄され、トレース ログにこのイベントのエントリが作成されます。 既定値は 65536 です。 **注:**だけでこの値を大きく ASP.NET 互換モードで十分ではありません。 値を大きく必要がありますも`httpRuntime`(を参照してください[httpRuntime Element (ASP.NET Settings Schema)](http://msdn.microsoft.com/en-us/e9b81350-8aaf-47cc-9843-5f7d0c59f369))。|  
|name|バインディングの構成名を格納する文字列です。 この値は、バインディングの ID として使用されるため、一意にする必要があります。 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 以降では、バインディングおよび動作に名前を付ける必要はありません。 既定の構成と無名のバインディングおよび動作の詳細については、次を参照してください。[簡略化された構成](../../../../../docs/framework/wcf/simplified-configuration.md)と[WCF サービスの構成を簡略化](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)です。|  
|openTimeout|実行中の操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。 この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。 既定値は 00:01:00 です。|  
|proxyAddress|HTTP プロキシのアドレスを指定する URI。 `useSystemWebProxy` が `true` の場合、この設定を `null` にする必要があります。 既定値は、`null` です。|  
|receiveTimeout|受信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。 この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。 既定値は 00:01:00 です。|  
|sendTimeout|送信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。 この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。 既定値は 00:01:00 です。|  
|transferMode|バインディングで構成されたサービスがメッセージ転送のストリーム モードまたはバッファー モード (あるいは両方のモード) を使用するかどうかを示す <xref:System.ServiceModel.TransferMode> 値。 既定値は、`Buffered` です。|  
|useDefaultWebProxy|システムの自動設定 HTTP プロキシを使用するかどうかを指定するブール値。 既定値は、`true` です。|  
|writeEncoding|メッセージ テキストに使用される文字エンコーディングを指定します。 以下の値が有効です。<br /><br /> UnicodeFffeTextEncoding: Unicode BigEndian エンコーディング。<br /><br /> Utf16TextEncoding: 16 ビットのエンコーディング。<br /><br /> Utf8TextEncoding: 8 ビットのエンコーディング。<br /><br /> 既定値は Utf8TextEncoding です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<ある readerQuotas >](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|このバインディングを使用して構成されるエンドポイントにより処理可能な、POX メッセージの複雑さに対する制約を定義します。 この要素は <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> 型です。|  
|[\<セキュリティ >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-webhttpbinding.md)|バインディングのセキュリティ設定を定義します。 この要素は <xref:System.ServiceModel.Configuration.WebHttpSecurityElement> 型です。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<バインド >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|この要素には、標準バインディングおよびカスタム バインディングのコレクションが保持されます。|  
  
## <a name="remarks"></a>コメント  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] Web プログラミング モデルを使用すると、開発者は、SOAP ベースのメッセージングに代わって "Plain Old XML" (POX) スタイルのメッセージングを使用する HTTP 要求を通じて [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] Web サービスを公開できます。 を HTTP 要求を使用するサービスと通信するクライアントとサービスのエンドポイントを構成する必要があります、 [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)を持つ、 \<WebHttpBehavior > が付属しています。  
  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] の配信および ASP.AJAX 統合のサポートは、Web プログラミング モデル上に構築されます。 モデルの詳細については、次を参照してください。 [WCF Web HTTP プログラミング モデル](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.WebHttpBinding>   
 <xref:System.ServiceModel.Configuration.WebHttpBindingElement>   
 [WCF Web HTTP プログラミング モデル](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)   
 [バインド](../../../../../docs/framework/wcf/bindings.md)   
 [システム指定のバインディングを構成します。](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<バインド >](../../../../../docs/framework/misc/binding.md)

