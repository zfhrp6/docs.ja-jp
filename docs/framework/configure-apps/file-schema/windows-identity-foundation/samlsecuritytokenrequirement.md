---
title: "&lt;samlSecurityTokenRequirement&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
caps.latest.revision: 4
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 4
---
# &lt;samlSecurityTokenRequirement&gt;
これらのクラスのいずれかの <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> クラス、<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> クラス、または派生クラスにコンフィギュレーションを提供します。  <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> クラスで表される。  
  
## 構文  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement   
            issuerCertificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
            issuerCertificateRevocationMode="NoCheck||Offline||Online"  
            issuerCertificateTrustedStoreLocation="CurrentLocation||LocalMachine"  
            issuerCertificateValidator="Namespace.Class Assembly"  
            mapToWindows=xs:boolean  
          <nameClaimType value=xs:string />  
          <roleClaimType value=xs:string />  
        </samlSecurityTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|mapToWindows|たとえば、ハンドラーが Windows アカウントに入力された UPN の要求の使用によって検証のトークンをマップするかどうかを指定します。  既定値は「false」です。|  
|issuerCertificateRevocationMode|X.509 証明書に使用する破棄の方法を指定する <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> の値。  既定値は「オンライン」です。|  
|issuerCertificateValidationMode|X.509 証明書に使用する検証の方法を指定する <xref:System.ServiceModel.Security.X509CertificateValidationMode> の値。  既定値は、「」PeerOrChainTrust です。|  
|issuerCertificateTrustedStoreLocation|X.509 証明書の店舗を指定する <xref:System.Security.Cryptography.X509Certificates.StoreLocation> の値。  既定値は、「」LocalMachine です。|  
|issuerCertificateValidator|<xref:System.IdentityModel.Selectors.X509CertificateValidator>取得元の注文タイプ。  `issuerCertificateValidationMode` の属性をカスタム「」の場合、この型のインスタンスはフィールドの証明書の検証に使用されます。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<nameClaimType\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/nameclaimtype.md)|<xref:System.Security.Principal.IIdentity.Name%2A> のプロパティを指定する要求タイプを設定します。|  
|[\<roleClaimType\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/roleclaimtype.md)|たとえば、ハンドラーの <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> 方法によって返された <xref:System.Security.Claims.ClaimsIdentity> のオブジェクト コレクションの要求ロールのタイプを定義する要求タイプを指定します。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<add\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|たとえば、ハンドラーのグループに指定セキュリティのトークン ハンドラーを追加します。|  
  
## 解説  
 オブジェクト モデル \(<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> クラスが `<samlSecurityTokenRequirement>` の要素を表され、<xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> または <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>の `SamlSecurityTokenRequirement` のプロパティをコンフィギュレーションします。  
  
## 使用例  
  
```  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement issuerCertificateValidationMode="PeerOrChainTrust"  
                                  issuerCertificateRevocationMode="Online"  
                                  issuerCertificateTrustedStoreLocation="LocalMachine"  
                                  mapToWindows="false">  
  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```