---
title: "&lt;ws2007HttpBinding&gt; の &lt;transport&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# &lt;ws2007HttpBinding&gt; の &lt;transport&gt;
HTTP トランスポートの認証設定を定義します。  
  
## 構文  
  
```  
  
transport clientCredentialType =   
       "Basic/Certificate/Digest/None/Ntlm/Windows"  
       proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
       realm="string"   
```  
  
## 型  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|`clientCredentialType`|サービスに対するクライアントの認証に使用される資格情報を指定します。  この属性は <xref:System.ServiceModel.HttpClientCredentialType> 型です。|  
|`proxyCredentialType`|ドメイン プロキシに対するクライアントの認証に使用される資格情報を指定します。  この属性は <xref:System.ServiceModel.HttpProxyCredentialType> 型です。|  
|`realm`|ダイジェスト認証または基本認証の認証レルム。  既定値は空の文字列です。<br /><br /> 認証レルムでは、少なくとも、認証を実行するホストの名前を指定します。  アクセス権のあるユーザーのコレクションも指定できます。  ユーザーは、認証レルムを照会して、複数のユーザー名とパスワードの候補のうち、どれを使用できるかを確認できます。|  
  
## clientCredentialType 属性  
  
|値|説明|  
|-------|--------|  
|なし|セキュリティを無効にします。|  
|Basic|基本認証を使用します。|  
|Digest|ダイジェスト認証を使用します。|  
|Ntlm|Windows ドメインのフォールバックとして NTLM 認証を使用します。|  
|Windows|統合 Windows 認証を使用します。|  
|証明書|X.509 証明書を使用して、クライアントを認証します。|  
  
## proxyCredentialType 属性  
  
|値|説明|  
|-------|--------|  
|なし|セキュリティを無効にします。|  
|Basic|基本認証を使用します。|  
|Digest|ダイジェスト認証を使用します。|  
|Ntlm|Windows ドメインのフォールバックとして NTLM を使用します。|  
|Windows|統合 Windows 認証を使用します。|  
|証明書|X.509 証明書を使用して、クライアントを認証します。|  
  
### 子要素  
 なし  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<security\>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-ws2007httpbinding.md)|[\<ws2007HttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) 要素のセキュリティ機能を表します。|  
  
## 参照  
 <xref:System.ServiceModel.HttpTransportSecurity>   
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>   
 <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>   
 <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>   
 [サービスおよびクライアントのセキュリティ保護](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [バインディング](../../../../../docs/framework/wcf/bindings.md)   
 [システムが提供するバインディングの構成](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/ja-jp/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<binding\>](../../../../../docs/framework/misc/binding.md)