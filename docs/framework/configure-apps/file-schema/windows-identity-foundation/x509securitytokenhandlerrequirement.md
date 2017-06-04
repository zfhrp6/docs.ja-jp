---
title: "&lt;x509SecurityTokenHandlerRequirement&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
caps.latest.revision: 3
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 3
---
# &lt;x509SecurityTokenHandlerRequirement&gt;
<xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> クラスまたは派生クラスに必要なコンフィギュレーションを提供します。  
  
## 構文  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
        <x509SecurityTokenHandlerRequirement>  
          mapToWindows=xs:boolean  
          certificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
          certificateValidator="Namespace.Class, Assembly"  
          revocationMode="NoCheck||Offline||Online"  
          trustedStoreLocation="CurrentUser||LocalMachine"  
        </x509SecurityTokenHandlerRequirement>  
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
|certificateValidationMode|X.509 証明書に使用する検証の方法を指定する <xref:System.ServiceModel.Security.X509CertificateValidationMode> の値。  既定値は、「」PeerOrChainTrust です。|  
|mapToWindows|たとえば、ハンドラーが Windows アカウントに入力された UPN の要求の使用によって検証のトークンをマップするかどうかを指定します。  既定値は「false」です。|  
|revocationMode|X.509 証明書に使用する破棄の方法を指定する <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> の値。  既定値は「オンライン」です。|  
|trustedStoreLocation|X.509 証明書の店舗を指定する <xref:System.Security.Cryptography.X509Certificates.StoreLocation> の値。  既定値は、「」LocalMachine です。|  
|certificateValidator|<xref:System.IdentityModel.Selectors.X509CertificateValidator>取得元の注文タイプ。  `certificateValidationMode` の属性をカスタム「」の場合、この型のインスタンスはフィールドの証明書の検証に使用されます。|  
  
### 子要素  
 なし  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<add\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|たとえば、ハンドラーのグループに指定セキュリティのトークン ハンドラーを追加します。|  
  
## 使用例  
  
```  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"   
                                         certificateValidationMode="PeerOrChainTrust"   
                                         revocationMode="Online"   
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```