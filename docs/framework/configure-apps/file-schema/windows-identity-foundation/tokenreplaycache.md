---
title: "&lt;tokenReplayCache&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
caps.latest.revision: 8
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 7
---
# &lt;tokenReplayCache&gt;
サービスまたはセキュリティ トークン ハンドラーのコレクションを再生のトークン キャッシュを登録します。  
  
## 構文  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
      <tokenReplayCache type=xs:string>  
      </tokenReplayCache>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|Description|  
|--------|-----------------|  
|type|派生した型は<xref:System.IdentityModel.Tokens.TokenReplayCache>クラス。  ユーザー設定を指定する方法の詳細については`type`を参照してください[Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md#BKMK_CustomTypeReferences)。|  
  
### 子要素  
 なし  
  
### 親要素  
  
|要素|Description|  
|--------|-----------------|  
|[\<キャッシュ\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|サービス、セキュリティ トークン ハンドラーのコレクションを使用して、キャッシュを登録します。|  
  
## 解説  
 トークンの再実行キャッシュを使用すると、再生されたトークンを検出します。  トークンのリプレイ検出を有効にして、 [\<tokenReplayDetection\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)要素は、また、最大有効期間トークンを指定します。  
  
## 使用例  
 次の XML は、再生されたトークンを検出するためには、カスタムのキャッシュの構成を示しています。  
  
```  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## 参照  
 <xref:System.IdentityModel.Tokens.TokenReplayCache>   
 [\<tokenReplayDetection\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)