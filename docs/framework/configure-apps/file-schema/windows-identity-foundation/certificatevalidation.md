---
title: "&lt;certificateValidation&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
caps.latest.revision: 4
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 4
---
# &lt;certificateValidation&gt;
証明書を検証するためにトークン ハンドラーが使用する設定を制御します。  これらの設定は固有のハンドラーが独自の検証コントロールで構成されている場合はオーバーライドされます。  
  
## 構文  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <certificateValidation  
      certificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
      revocationMode="NoCheck||Offline||Online"  
      trustedStoreLocation="CurrentLocation||LocalMachine" >  
    </certificateValidation>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|Description|  
|--------|-----------------|  
|certificateValidationMode|X.509 証明書に使用する有効性認証モードを指定する <xref:System.ServiceModel.Security.X509CertificateValidationMode> 値。  既定値は 「PeerOrChainTrust」です。  カスタム検証を指定するには、このカスタム属性を 「」に設定し、要素を使用して検証コントロールを [\<certificateValidator\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md) 指定します。  省略可能です。|  
|revocationMode|X.509 証明書に使用する失効モードを指定する <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> 値。  既定値は 「オンライン」です。  省略可能です。|  
|trustedStoreLocation|X.509 証明書ストアを指定する <xref:System.Security.Cryptography.X509Certificates.StoreLocation> 値。  既定値は 「LocalMachine」です。  省略可能です。|  
  
### 子要素  
  
|要素|Description|  
|--------|-----------------|  
|[\<certificateValidator\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md)|証明書検証するためのカスタム型を指定します。  この型は、要素の `certificateValidationMode` のカスタム [\<certificateValidation\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) 属性を 「」に設定されている場合のみ使用できます。|  
  
### 親要素  
  
|要素|Description|  
|--------|-----------------|  
|[\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|サービス レベルの ID の設定を指定します。|  
|[\<securityTokenHandlerConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|セキュリティ トークン ハンドラーの収集の構成を提供します。|  
  
## 解説  
 `<certificateValidation>` の要素は `<identityConfiguration>` 要素の下のまたは `<securityTokenHandlerConfiguration>` 要素の下のセキュリティ トークン ハンドラー コレクション レベル サービス レベルで指定できます。  サービスで指定されたトークン ハンドラー コレクションの設定によってオーバーライドされます。  一部のトークン ハンドラーは構成で証明書検証設定を指定できるようにします。  個別のトークン ハンドラーの設定はサービス レベルでセキュリティ トークン ハンドラー コレクションで指定されたオーバーライドします。  
  
## 使用例  
  
```  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```