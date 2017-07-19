---
title: "&lt;securityTokenHandlers&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
caps.latest.revision: 5
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 5
---
# &lt;securityTokenHandlers&gt;
エンドポイントには登録されているセキュリティ トークン ハンドラーのコレクションを指定します。  
  
## 構文  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|Description|  
|--------|-----------------|  
|name|トークン ハンドラーのコレクションの名前を指定します。  フレームワークによって認識される唯一の値は、"ActAs"と"OnBehalfOf"です。  トークン ハンドラーのコレクションにこれらの名前のいずれかに指定されている場合は、それぞれトークンの ActAs または OnBehalfOf を処理すると、コレクションが使用されます。|  
  
### 子要素  
  
|要素|Description|  
|--------|-----------------|  
|[\<add\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|セキュリティ トークン ハンドラーは、トークン ハンドラー コレクションに追加します。|  
|[\<clear\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md)|すべてのセキュリティ トークン ハンドラー、トークン ハンドラーのコレクションを消去します。|  
|[\<削除\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md)|セキュリティ トークン ハンドラーは、トークン ハンドラー コレクションから削除します。|  
|[\<securityTokenHandlerConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|構成、トークン ハンドラーのコレクションを提供します。|  
  
### 親要素  
  
|要素|Description|  
|--------|-----------------|  
|[\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|サービス ・ レベルの id の設定を指定します。|  
  
## 解説  
 サービスの構成では、セキュリティ トークン ハンドラーの 1 つ以上の名前付きコレクションを指定できます。  使用してコレクションの名前を指定することができます、 `name`属性。  フレームワークの処理のみの名前は"ActAs"と"OnBehalfOf"です。  ハンドラーがコレクションに存在する場合は、セキュリティ トークン サービス \(STS\) の代わりに、既定のハンドラーを処理するとき使用されます`ActAs`と`OnBehalfOf`トークン。  
  
 既定では、コレクションの次のハンドラーの種類を設定します。 <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>、 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>、 <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>、 <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>、 <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>、 <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>、および<xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>。  使用してそのコレクションを変更することができます、 `<add>`、 `<remove>`、および`<clear>`の要素。  のみ、単一のハンドラーは特定の型のコレクション内に存在することを確認する必要があります。  ハンドラーから派生させる場合は、たとえば、 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>は、クラス ハンドラーまたは、 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>両方が、単一のコレクションに構成可能性があります。  
  
 使用して、 `<securityTokenHandlerConfiguration>`コレクション内で、ハンドラーの構成設定を指定する要素。  この要素で指定された設定をオーバーライドするを通じてサービスに指定された、 [\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)要素。  （いくつかの組み込みのハンドラーの種類を含む） いくつかのハンドラーは、子要素の追加の構成をサポートできる、 `<add>`要素。  ハンドラーで指定した設定は、コレクションまたはサービスで指定された同等の設定をオーバーライドします。