---
title: "&lt;キャッシュ&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
caps.latest.revision: 7
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 7
---
# &lt;キャッシュ&gt;
セッション トークンをトークンのリプレイ検出を使用して、キャッシュを登録します。  
  
## 構文  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
 なし  
  
### 子要素  
  
|要素|Description|  
|--------|-----------------|  
|[\<sessionSecurityTokenCache\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md)|セッション トークンをキャッシュ サービスとセキュリティ トークン ハンドラーのコレクションを登録します。|  
|[\<tokenReplayCache\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md)|サービスまたはセキュリティ トークン ハンドラーのコレクションを再生のトークン キャッシュを登録します。|  
  
### 親要素  
  
|要素|Description|  
|--------|-----------------|  
|[\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|サービス ・ レベルの id の設定を指定します。|  
|[\<securityTokenHandlerConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|構成コレクションのセキュリティ トークン ハンドラーを提供します。|  
  
## 解説  
 A `<caches>`要素は、サービス ・ レベルで指定できます、 `<identityConfiguration>`要素またはセキュリティ トークン ハンドラー コレクションのレベルの下に、 `<securityTokenHandlerConfiguration>`要素。  サービスで指定されているコレクションをトークン ハンドラーの設定をオーバーライドします。  
  
 `<caches>`要素で表される、 <xref:System.IdentityModel.Configuration.IdentityModelCachesElement>クラス。  構成済みキャッシュによって表される、 <xref:System.IdentityModel.Configuration.IdentityModelCaches>クラス。  
  
## 使用例  
 次の XML は、セッションのセキュリティ トークンを保持して、カスタム キャッシュの構成を示しています \(<xref:System.IdentityModel.Tokens.SessionSecurityToken>\)。  構成から取得されます、 `ClaimsAwareWebFarm`サンプル。  
  
```  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```