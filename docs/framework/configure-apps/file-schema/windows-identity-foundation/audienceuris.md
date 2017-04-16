---
title: "&lt;audienceUris&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
caps.latest.revision: 8
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 8
---
# &lt;audienceUris&gt;
依存元の相手 \(RP\) の許容可能な識別子は Uri のセットを指定します。  トークンが許可されている対象ユーザーの Uri のいずれかのスコープでない限り許可されません。  
  
## 構文  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <audienceUris mode=xs:string>  
          <add value=xs:string />  
          <clear />  
          <remove value=xs:string />  
        </audienceUris>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|Description|  
|--------|-----------------|  
|mode|<xref:System.IdentityModel.Selectors.AudienceUriMode> 、対象者の制限が、受信したトークンに適用かどうかを示す値。  使用可能な値は、「は、」"Never"、および"BearerKeyOnly"です。  既定値は「常に」です。  省略可能です。|  
  
### 子要素  
  
|要素|Description|  
|--------|-----------------|  
|`<add value=xs:string>`|指定した URI を追加、 `value`属性、audienceUris コレクションに。  `value` 属性は必須です。  URI は、大文字小文字を区別です。|  
|`<clear>`|AudienceUris のコレクションを消去します。  すべての識別子は、コレクションから削除されます。|  
|`<remove value=xs:string>`|指定した URI を削除、 `value` audienceUris コレクションから属性をします。  `value` 属性は必須です。  URI は、大文字小文字を区別です。|  
  
### 親要素  
  
|要素|Description|  
|--------|-----------------|  
|[\<securityTokenHandlerConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|構成コレクションのセキュリティ トークン ハンドラーを提供します。|  
  
## 解説  
 既定では、コレクションは空です。 使用`<add>`、 `<clear>`、および`<remove>`要素は、コレクションを変更します。  <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler><xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>オブジェクトの値を構成するのには、対象の URI のコレクションでは、URI の制限で視聴者を許可されて使用<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement>オブジェクト。  
  
 `<audienceUris>`要素で表される、 <xref:System.IdentityModel.Configuration.AudienceUriElementCollection>クラス。  コレクションに追加する個々 の URI が表され、 <xref:System.IdentityModel.Configuration.AudienceUriElement>クラス。  
  
> [!NOTE]
>  使用、 `<audienceUris>`要素の子要素として、 [\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)要素は推奨されていませんが、旧バージョンとの互換性のためのサポートもします。  設定で、 `<securityTokenHandlerConfiguration>`要素無効もに、 `<identityConfiguration>`要素。  
  
## 使用例  
 次の XML は、アプリケーションを適切な対象ユーザー Uri を構成する方法を示しています。  次の使用例は、単一の URI を設定します。  この URI のスコープのトークンを受け入れられます、他のユーザーはすべて拒否されます。  
  
```  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```