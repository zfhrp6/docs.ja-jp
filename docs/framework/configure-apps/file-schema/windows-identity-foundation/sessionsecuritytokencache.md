---
title: "&lt;sessionSecurityTokenCache&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
caps.latest.revision: 8
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 7
---
# &lt;sessionSecurityTokenCache&gt;
セッション トークンをキャッシュ サービスとセキュリティ トークン ハンドラーのコレクションを登録します。  
  
## 構文  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
      <sessionSecurityTokenCache type=xs:string>  
      </sessionSecurityTokenCache>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|Description|  
|--------|-----------------|  
|type|派生した型は<xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>クラス。  ユーザー設定を指定する方法の詳細については`type`を参照してください[Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md#BKMK_CustomTypeReferences)。|  
  
### 子要素  
 なし  
  
### 親要素  
  
|要素|Description|  
|--------|-----------------|  
|[\<キャッシュ\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|サービス、セキュリティ トークン ハンドラーのコレクションを使用して、キャッシュを登録します。|  
  
## 使用例  
 次の XML は、セッションのセキュリティ トークンを保持して、カスタム キャッシュの構成を示しています \(<xref:System.IdentityModel.Tokens.SessionSecurityToken>\)。  構成から取得されます、 `ClaimsAwareWebFarm`サンプル。  このサンプルの詳細についてを参照してください[WIF コード サンプル インデックス](../../../../../docs/framework/security/wif-code-sample-index.md)。  
  
```  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## 参照  
 <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>