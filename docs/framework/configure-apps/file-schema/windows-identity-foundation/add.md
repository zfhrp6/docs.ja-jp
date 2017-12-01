---
title: '&lt;add&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: cc1907d5f6117307ebadd04641c9eddc48e77cec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ltaddgt"></a>&lt;add&gt;
トークン ハンドラー コレクションに指定されたセキュリティ トークン ハンドラーを追加します。  
  
 \<system.identityModel >  
\<identityConfiguration >  
\<securityTokenHandlers >  
\<add>  
  
## <a name="syntax"></a>構文  
  
```xml  
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
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|型|追加するトークン ハンドラーの CLR 型名。 指定する方法について、`type`属性は、「[カスタム型の参照](http://msdn.microsoft.com/en-us/7286d2e3-c63d-49fd-abdc-ce2705f22c24)です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|構成を提供、<xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>クラス、<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>クラス、またはこれらのクラスのいずれかの派生クラス。|  
|[\<sessionTokenRequirement >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessiontokenrequirement.md)|構成を提供、<xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>クラスまたは派生クラス。|  
|[\<userNameSecurityTokenHandlerRequirement >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/usernamesecuritytokenhandlerrequirement.md)|構成を提供、<xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>クラスまたは派生クラス。|  
|[\<x509SecurityTokenHandlerRequirement >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/x509securitytokenhandlerrequirement.md)|省略可能な構成を提供、<xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>クラスまたは派生クラス。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<securityTokenHandlers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|エンドポイントに登録されているセキュリティ トークン ハンドラーのコレクションを指定します。|  
  
## <a name="remarks"></a>コメント  
 `<add>`要素は、トークン ハンドラーの構成を指定する 1 つの子要素を受け取ることができます。 これはを通じてハンドラー クラスを参照するかどうかに依存する、`type`の属性、`<add>`要素は、この機能のサポートを提供します。 この機能を提供するトークン ハンドラー クラスを受け取るコンス トラクターを公開する必要があります、<xref:System.Xml.XmlElement>オブジェクト。  
  
```  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 この機能を提供、組み込みのセキュリティ トークン ハンドラーのクラスのいくつかの操作を行います。 これらのクラスは<xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>、 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>、 <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>、 <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>、および<xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>です。  
  
> [!IMPORTANT]
>  トークン ハンドラー コレクションには、特定の型の 1 つのハンドラーのみを含めることができます。 つまり、たとえば、派生元のハンドラーを追加する場合、<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>クラス、コレクションを削除する必要あります、<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>は既定では、コレクションから存在します。 使用することができます、 [\<削除 >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md)コレクションまたは使用から 1 つのハンドラーを削除する要素、 [\<オフ >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md)コレクションからすべてのイベント ハンドラーを削除する要素。  
  
 ハンドラーに指定された設定がの下にトークン ハンドラー コレクションに指定した同等の設定を上書き、 [ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)要素とその下にあるサービス レベルで指定されています。[ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)要素。  
  
## <a name="example"></a>例  
 次の XML の使用方法を示します、`<add>`と`<remove>`に既定のセッション トークン ハンドラーをカスタム セッション トークン ハンドラーに置き換える要素。 XML を取得、`ClaimsAwareWebFarm`サンプルです。  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
