---
title: "&lt;tokenReplayDetection&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ac3f588e-5f75-4275-b969-2d492ecc3b47
caps.latest.revision: 6
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 5
---
# &lt;tokenReplayDetection&gt;
トークン リプレイ検出を有効にし、トークンの有効期限を指定します。  
  
## 構文  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <tokenReplayDetection enabled=xs:boolean expirationPeriod=TimeSpan>  
    </tokenReplayDetection>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## 型  
 <xref:System.IdentityModel.Configuration.TokenReplayDetectionElement>  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|Description|  
|--------|-----------------|  
|enabled|トークン リプレイ検出が有効かどうかを指定する値; 「true」トークン リプレイ検出を有効にします。|  
|expirationPeriod|<xref:System.TimeSpan> 項目がキャッシュから切らされ、削除されたと見なされる前に時間の最大サイズを指定します。  <xref:System.TimeSpan> 値を指定する方法の詳細については、 " " を参照してください。 [Timespan Values](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md#BKMK_TimespanValues)|  
  
### 子要素  
 なし  
  
### 親要素  
  
|要素|Description|  
|--------|-----------------|  
|[\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|サービス レベルの ID の設定を指定します。|  
|[\<securityTokenHandlerConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|セキュリティ トークン ハンドラーの収集の構成を提供します。|  
  
## 解説  
 `<tokenReplayDetection>` の要素は `<identityConfiguration>` 要素の下のまたは `<securityTokenHandlerConfiguration>` 要素の下のセキュリティ トークン ハンドラー コレクション レベル サービス レベルで指定できます。  サービスで指定されたトークン ハンドラー コレクションの設定によってオーバーライドされます。  
  
 トークン再生のキャッシュの種類は、要素で [\<tokenReplayCache\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) 指定されます。