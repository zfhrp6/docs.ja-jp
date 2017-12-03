---
title: '&lt;httpTransport&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8b30c065-b32a-4fa3-8eb4-5537a9c6b897
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3097f5352a8f92397b80f0c20e0cc2206e1e3fee
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="lthttptransportgt"></a>&lt;httpTransport&gt;
カスタム バインドの SOAP メッセージを送信する HTTP トランスポートを指定します。  
  
 \<system.serviceModel >  
\<バインド >  
\<customBinding >  
\<バインド >  
\<httpTransport >  
  
## <a name="syntax"></a>構文  
  
```xml  
<httpTransport  
    allowCookies=Boolean"  
    authenticationScheme="Digest/Negotiate/Ntlm/Basic/Anonymous"  
    bypassProxyOnLocal=Boolean"  
    hostnameComparisonMode="StrongWildcard/Exact/WeakWildcard"  
    keepAliveEnabled="Boolean"  
    maxBufferSize="Integer"  
    proxyAddress="Uri"  
    proxyAuthenticationScheme="None/Digest/Negotiate/Ntlm/Basic/Anonymous"  
IntegratedWindowsAuthentication: Specifies Windows authentication"  
    realm="String"  
    transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"  
        unsafeConnectionNtlmAuthentication="Boolean"  
        useDefaultWebProxy="Boolean" />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|allowCookies|クライアントがクッキーを受け入れて、それらを今後の要求に反映させるかどうかを指定するブール値です。 既定値は、`false` です。<br /><br /> この属性はクッキーを使用する ASMX Web サービスと対話する場合に使用できます。 この方法で、サーバーから返されるクッキーを、それ以降のサービスに対するすべてのクライアント要求に自動的にコピーできます。|  
|authenticationScheme|HTTP リスナーにより処理されているクライアント要求の認証に使用するプロトコルを指定します。 以下の値が有効です。<br /><br /> -Digest: ダイジェスト認証を指定します。<br />-Negotiate: クライアントとネゴシエートし認証方式を決定します。 クライアントとサーバーの両方が Kerberos をサポートする場合は、この方式が使用されます。それ以外の場合は NTLM が使用されます。<br />-Ntlm: NTLM 認証を指定します。<br />-基本: は、基本認証を指定します。<br />-Anonymous: 匿名認証を指定します。<br /><br /> 既定は Anonymous です。 この属性は <xref:System.Net.AuthenticationSchemes> 型です。 この属性は 1 回だけ設定できます。|  
|bypassProxyOnLocal|ローカル アドレスでプロキシ サーバーをバイパスするかどうかを示すブール値。 既定値は、`false` です。<br /><br /> ローカル アドレスは、ローカル LAN またはイントラネット上にあるアドレスです。<br /><br /> [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] は、サービス アドレスが http://localhost で始まる場合は常にプロキシを無視します。<br /><br /> クライアントが同じマシン上のサービスと対話するときにプロキシを経由させる場合は、localhost ではなくホスト名を使用する必要があります。|  
|hostnameComparisonMode|URI の解析に使用する HTTP ホスト名比較モードを指定します。 有効な値は次のとおりです。<br /><br /> -StrongWildcard: (「+」)、指定されたスキーム、ポートと相対 URI のコンテキストですべてのホスト名に一致します。<br />厳密: ワイルドカードは使用できません。<br />-WeakWildcard: ("*") または厳密なワイルドカードのメカニズムにより、指定されたスキーム、ポートと対応していない明示的に相対の UIR のコンテキストですべての可能なホスト名と一致します。<br /><br /> 既定値は StrongWildcard です。 この属性は `System.ServiceModel.HostnameComparisonMode` 型です。|  
|keepAliveEnabled|インターネット リソースへの永続的な接続を行うかどうかを示すブール値。|  
|maxBufferSize|バッファーの最大サイズを指定する正の整数です。 既定値は 524288 です|  
|proxyAddress|HTTP プロキシのアドレスを指定する URI。 `useSystemWebProxy` が `true` の場合、この設定を `null` にする必要があります。 既定値は、`null` です。|  
|proxyAuthenticationScheme|HTTP プロキシにより処理されているクライアント要求の認証に使用するプロトコルを指定します。 以下の値が有効です。<br /><br /> -None: 認証は実行されません。<br />-Digest: ダイジェスト認証を指定します。<br />-Negotiate: クライアントとネゴシエートし認証方式を決定します。 クライアントとサーバーの両方が Kerberos をサポートする場合は、この方式が使用されます。それ以外の場合は NTLM が使用されます。<br />-Ntlm: NTLM 認証を指定します。<br />-基本: は、基本認証を指定します。<br />-Anonymous: 匿名認証を指定します。<br />-IntegratedWindowsAuthentication: Windows 認証を指定します。<br /><br /> 既定は Anonymous です。 この属性は <xref:System.Net.AuthenticationSchemes> 型です。|  
|realm|プロキシおよびサーバーで使用するレルムを指定する文字列です。 既定値は空の文字列です。<br /><br /> サーバーは、レルムを使用して、保護されたリソースをパーティションに分割します。 パーティションごとに、独自の認証方式と承認データベースの両方、またはそのいずれかを指定できます。 レルムは、基本認証およびダイジェスト認証だけに使用されます。 クライアントが正常に認証されると、その認証は特定のレルムのすべてのリソースに対して有効となります。 レルムの詳細については、http://www.ietf.org の RFC 2617 を参照してください。|  
|transferMode|メッセージが要求や応答をバッファーするか、ストリーミングするかを指定します。 以下の値が有効です。<br /><br /> -Buffered: 要求および応答メッセージをバッファーします。<br />ストリーミングを使用: 要求および応答メッセージをストリーミングします。<br />-StreamedRequest: 要求メッセージをストリーミングし、応答メッセージをバッファーします。<br />-StreamedResponse: 要求メッセージをバッファーし、応答メッセージをストリーミングします。<br /><br /> 既定値はバッファーです。 この属性は <xref:System.ServiceModel.TransferMode> 型です。|  
|unsafeConnectionNtlmAuthentication|サーバー上で安全ではない接続共有を有効にするかどうかを指定するブール値です。 既定値は、`false` です。 有効な場合、NTLM 認証は、TCP 接続ごとに 1 回実行されます。|  
|useDefaultWebProxy|ユーザー固有の設定ではなく、コンピューター全体のプロキシ設定を使用するかどうかを指定するブール値です。 既定値は、`true` です。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<バインド >](../../../../../docs/framework/misc/binding.md)|カスタム バインドのすべてのバインド機能を定義します。|  
  
## <a name="remarks"></a>コメント  
 `httpTransport` 要素は、HTTP トランスポート プロトコルを実装するカスタム バインディングを作成する場合の開始点となります。 HTTP は、相互運用性のために使用される主要なトランスポートです。 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] は、他の非 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] Web サービス スタックとの相互運用性を保証するために、このトランスポートをサポートします。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Configuration.HttpTransportElement>  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [トランスポート](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [トランスポートの選択](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [バインディング](../../../../../docs/framework/wcf/bindings.md)  
 [バインディングの拡張](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [カスタム バインド](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
