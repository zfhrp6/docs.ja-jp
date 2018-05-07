---
title: '&lt;ws2007HttpBinding&gt; の &lt;transport&gt;'
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: 3be9d4e64e63b32156cb64257f5bed8230cee3aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="lttransportgt-of-ltws2007httpbindinggt"></a>&lt;ws2007HttpBinding&gt; の &lt;transport&gt;
HTTP トランスポートの認証設定を定義します。  
  
 \<system.serviceModel>  
\<bindings>  
\<ws2007HttpBinding >  
\<binding>  
\<セキュリティ >  
\<transport>  
  
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
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-ws2007httpbinding.md)|セキュリティ機能を表す、 [ \<ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md)要素。|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>  
 [サービスおよびクライアントのセキュリティ保護](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [バインディング](../../../../../docs/framework/wcf/bindings.md)  
 [システムが提供するバインディングの構成](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<binding>](../../../../../docs/framework/misc/binding.md)
