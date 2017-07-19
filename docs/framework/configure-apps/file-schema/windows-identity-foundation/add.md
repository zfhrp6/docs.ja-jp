---
title: "&lt;add&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
caps.latest.revision: 7
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 7
---
# &lt;add&gt;
指定されたセキュリティ トークン ハンドラーをトークン ハンドラー コレクションに追加します。  
  
## 構文  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type=xs:string>  
        <optionalConfigurationElement>  
        </optionalConfigurationElement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|Description|  
|--------|-----------------|  
|type|追加すると、トークン ハンドラーの CLR 型名。  指定する方法の詳細については、 `type`属性は、 [Custom Type References](http://msdn.microsoft.com/ja-jp/7286d2e3-c63d-49fd-abdc-ce2705f22c24)。|  
  
### 子要素  
  
|要素|Description|  
|--------|-----------------|  
|[\<samlSecurityTokenRequirement\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|構成を提供、 <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>クラスは、 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>クラス、または派生クラスのこれらのクラスのいずれか。|  
|[\<sessionTokenRequirement\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessiontokenrequirement.md)|構成を提供、 <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>クラスまたは派生クラス。|  
|[\<userNameSecurityTokenHandlerRequirement\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/usernamesecuritytokenhandlerrequirement.md)|構成を提供、 <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>クラスまたは派生クラス。|  
|[\<x509SecurityTokenHandlerRequirement\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/x509securitytokenhandlerrequirement.md)|オプションの構成を提供、 <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>クラスまたは派生クラス。|  
  
### 親要素  
  
|要素|Description|  
|--------|-----------------|  
|[\<securityTokenHandlers\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|エンドポイントには登録されているセキュリティ トークン ハンドラーのコレクションを指定します。|  
  
## 解説  
 `<add>`要素は、トークン ハンドラーの設定を指定します。 単一の子要素を取ることができます。  これかどうか、ハンドラー クラスを通じて参照に依存している、 `type`属性の`<add>`要素はこの機能のサポートを提供します。  この機能を提供するトークン ハンドラー クラスを受け取るコンス トラクターを公開する必要があります、 <xref:System.Xml.XmlElement>オブジェクト。  
  
```  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 この機能が組み込まれているセキュリティ トークン ハンドラー クラスのいくつかを。  These classes are <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.  
  
> [!IMPORTANT]
>  トークン ハンドラーのコレクションは、指定された型の 1 つのハンドラーを含めることができます。  派生するハンドラーを追加する場合は、たとえば、つまり、 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>クラス、コレクションには、まず削除する必要があります、 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>、です、コレクションから既定で存在します。  使用できます、 [\<削除\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md)要素は、コレクションの使用を 1 つのハンドラーを削除するには、 [\<clear\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md)要素は、コレクションからすべてのイベント ハンドラーを削除します。  
  
 ハンドラーで指定した設定をオーバーライドで、トークン ハンドラーのコレクションで指定された同等の設定に[\<securityTokenHandlerConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)要素とは、サービス レベルで指定されている、 [\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)要素。  
  
## 使用例  
 次の XML の使用を示しています、 `<add>`と`<remove>`カスタム セッション トークン ハンドラーが既定のセッション トークン ハンドラーを置換する要素。  XML から取得されます、 `ClaimsAwareWebFarm`サンプル。  
  
```  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```