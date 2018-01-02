---
title: "&lt;キャッシュ&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: b9dfa7b2f0952f3f9e224ad51fd4d9c0c263ce04
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltcachesgt"></a>&lt;キャッシュ&gt;
セッション トークンやトークン リプレイ検出のために使用されるキャッシュに登録します。  
  
 \<system.identityModel >  
\<identityConfiguration >  
\<キャッシュ >  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<sessionSecurityTokenCache >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md)|サービスまたはセキュリティ トークン ハンドラーはコレクションのセッション トークンのキャッシュに登録します。|  
|[\<tokenReplayCache >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md)|トークン リプレイ キャッシュ サービスまたはセキュリティ トークン ハンドラー コレクションに登録します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|サービス レベルの id 設定を指定します。|  
|[\<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|トークン ハンドラーのセキュリティのコレクションの構成を提供します。|  
  
## <a name="remarks"></a>コメント  
 A`<caches>`下にあるサービス レベルで要素を指定することができます、`<identityConfiguration>`要素またはセキュリティ トークン ハンドラーのコレクション レベルの下で、`<securityTokenHandlerConfiguration>`要素。 サービスに指定されたトークン ハンドラーはコレクションの設定をオーバーライドします。  
  
 `<caches>`要素として表されます、<xref:System.IdentityModel.Configuration.IdentityModelCachesElement>クラスです。 構成済みのキャッシュがによって表される、<xref:System.IdentityModel.Configuration.IdentityModelCaches>クラスです。  
  
## <a name="example"></a>例  
 次の XML は、セッション セキュリティ トークンを保持するためのカスタム キャッシュの構成を示します (<xref:System.IdentityModel.Tokens.SessionSecurityToken>)。 構成がから取得した、`ClaimsAwareWebFarm`サンプルです。  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
