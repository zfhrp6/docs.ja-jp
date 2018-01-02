---
title: '&lt;serviceTokenResolver&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: cd981c8e48f003060c74787fdd2f29557c07901d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltservicetokenresolvergt"></a>&lt;serviceTokenResolver&gt;
トークン ハンドラーはコレクション内のハンドラーによって使用されるサービスのトークン リゾルバーを登録します。 サービスのトークン リゾルバーを使用して、入力方向のトークンとメッセージの暗号化トークンを解決します。  
  
 \<system.identityModel >  
\<identityConfiguration >  
\<securityTokenHandlers >  
\<securityTokenHandlerConfiguration >  
\<serviceTokenResolver >  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <serviceTokenResolver type=xs:string>  
        </serviceTokenResolver>  
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
|型|サービスのトークン リゾルバーの種類を指定します。 いずれか、<xref:System.IdentityModel.Selectors.SecurityTokenResolver>型または型から派生した、<xref:System.IdentityModel.Selectors.SecurityTokenResolver>クラスです。 指定する方法について、`type`属性 [カスタム型の参照] を参照してください。 必須。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|トークン ハンドラーのセキュリティのコレクションの構成を提供します。|  
  
## <a name="remarks"></a>コメント  
 入力方向のトークンとメッセージの暗号化トークンを解決するのには、サービスのトークン リゾルバーを使用できます。 着信トークン暗号化解除に使用されるキーの取得に使用されます。 指定する必要があります、`type`属性。 指定された型には、いずれかを指定できる<xref:System.IdentityModel.Selectors.SecurityTokenResolver>やカスタム型から派生した、<xref:System.IdentityModel.Selectors.SecurityTokenResolver>クラスです。  
  
 いくつかのトークン ハンドラーを使用すると、構成でサービスのトークン リゾルバーの設定を指定できます。 セキュリティ トークン ハンドラーのコレクションで指定された個々 のトークン ハンドラーの設定をオーバーライドします。  
  
> [!NOTE]
>  指定する、`<serviceTokenResolver>`要素の子要素として、 [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)要素は推奨されていませんもは旧バージョンとの互換性のため、引き続きサポートします。 上の設定、`<securityTokenHandlerConfiguration>`要素をオーバーライドで、`<identityConfiguration>`要素。  
  
## <a name="example"></a>例  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
