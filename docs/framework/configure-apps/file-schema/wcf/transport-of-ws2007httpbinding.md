---
title: "&lt;ws2007HttpBinding&gt; の &lt;transport&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc60e72ae810578edb71b73b39e756a951b1f425
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="lttransportgt-of-ltws2007httpbindinggt"></a>&lt;ws2007HttpBinding&gt; の &lt;transport&gt;
HTTP トランスポートの認証設定を定義します。  
  
 \<system.serviceModel >  
\<バインド >  
\<ws2007HttpBinding >  
\<バインド >  
\<セキュリティ >  
\<トランスポート >  
  
## <a name="syntax"></a>構文  
  
```  
transport clientCredentialType =   
       "Basic/Certificate/Digest/None/Ntlm/Windows"  
       proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
       realm="string"   
```  
  
## <a name="type"></a>型  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`clientCredentialType`|サービスに対するクライアントの認証に使用される資格情報を指定します。 この属性は <xref:System.ServiceModel.HttpClientCredentialType> 型です。|  
|`proxyCredentialType`|ドメイン プロキシに対するクライアントの認証に使用される資格情報を指定します。 この属性は <xref:System.ServiceModel.HttpProxyCredentialType> 型です。|  
|`realm`|ダイジェスト認証または基本認証の認証レルム。 既定値は空の文字列です。<br /><br /> 認証レルムでは、少なくとも、認証を実行するホストの名前を指定します。 アクセス権のあるユーザーのコレクションも指定できます。 ユーザーは、認証レルムを照会して、複数のユーザー名とパスワードの候補のうち、どれを使用できるかを確認できます。|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType 属性  
  
|値|説明|  
|-----------|-----------------|  
|なし|セキュリティを無効にします。|  
|Basic|基本認証を使用します。|  
|Digest|ダイジェスト認証を使用します。|  
|Ntlm|Windows ドメインのフォールバックとして NTLM 認証を使用します。|  
|Windows|統合 Windows 認証を使用します。|  
|証明書|X.509 証明書を使用して、クライアントを認証します。|  
  
## <a name="proxycredentialtype-attribute"></a>proxyCredentialType 属性  
  
|値|説明|  
|-----------|-----------------|  
|なし|セキュリティを無効にします。|  
|Basic|基本認証を使用します。|  
|Digest|ダイジェスト認証を使用します。|  
|Ntlm|Windows ドメインのフォールバックとして NTLM を使用します。|  
|Windows|統合 Windows 認証を使用します。|  
|証明書|X.509 証明書を使用して、クライアントを認証します。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<セキュリティ >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-ws2007httpbinding.md)|セキュリティ機能を表す、 [ \<ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md)要素。|  
  
## <a name="see-also"></a>参照  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>  
 [サービスおよびクライアントのセキュリティ保護](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [バインディング](../../../../../docs/framework/wcf/bindings.md)  
 [システムが提供するバインディングの構成](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<バインド >](../../../../../docs/framework/misc/binding.md)
