---
title: '&lt;Audienceuri&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 3ce884c19d205df4727dcce96ffdf34144ff1dd6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ltaudienceurisgt"></a>&lt;Audienceuri&gt;
証明書利用者 (RP) の許容可能な識別子 Uri のセットを指定します。 許可されている対象 Uri のいずれかのスコープがない限り、トークンは承認されません。  
  
 \<system.identityModel >  
\<identityConfiguration >  
\<securityTokenHandlers >  
\<securityTokenHandlerConfiguration >  
\<Audienceuri >  
  
## <a name="syntax"></a>構文  
  
```xml  
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
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|モード|<xref:System.IdentityModel.Selectors.AudienceUriMode>着信トークンに対象者制限を適用するかどうかを指定する値。 使用可能な値は、「常に」、"Never"、"BearerKeyOnly"です。 既定値は、「常に」です。 省略可能です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|`<add value=xs:string>`|指定された URI を追加、 `value` Audienceuri コレクションに属性します。 `value` 属性は必須です。 URI は、大文字小文字を区別します。|  
|`<clear>`|Audienceuri コレクションをクリアします。 すべての識別子は、コレクションから削除されます。|  
|`<remove value=xs:string>`|指定された URI の削除、 `value` Audienceuri コレクションから属性。 `value` 属性は必須です。 URI は、大文字小文字を区別します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|トークン ハンドラーのセキュリティのコレクションの構成を提供します。|  
  
## <a name="remarks"></a>コメント  
 既定では、コレクションが空です。使用して`<add>`、 `<clear>`、および`<remove>`要素のコレクションを変更します。 <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>および<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>許可対象ユーザーの URI の制限事項のいずれかを構成する対象ユーザー URI のコレクション内の値をオブジェクト<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement>オブジェクト。  
  
 `<audienceUris>`要素として表されます、<xref:System.IdentityModel.Configuration.AudienceUriElementCollection>クラスです。 によって表されるコレクションに追加された個々 の URI、<xref:System.IdentityModel.Configuration.AudienceUriElement>クラスです。  
  
> [!NOTE]
>  使用、`<audienceUris>`要素の子要素として、 [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)要素は推奨されていませんもは旧バージョンとの互換性のため、引き続きサポートします。 上の設定、`<securityTokenHandlerConfiguration>`要素をオーバーライドで、`<identityConfiguration>`要素。  
  
## <a name="example"></a>例  
 次の XML では、アプリケーションの許容される対象ユーザー Uri を構成する方法を示します。 この例では、1 つの URI を構成します。 この URI のスコープのトークンが受け入れられます、他のすべてのユーザーは拒否されます。  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
