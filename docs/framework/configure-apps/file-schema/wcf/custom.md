---
title: "&lt;custom&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# &lt;custom&gt;
ユーザー設定のピア リゾルバー サービスの設定を指定します。  
  
## 構文  
  
```  
  
<custom address="Uri"  
   resolverType="String">  
      <headers/>  
   <identity/>  
</peerResolver>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|`address`|カスタム ピア リゾルバー サービスをホストするピア ノードのエンドポイント アドレスを指定する URI。|  
|`resolverType`|カスタム ピア リゾルバー サービスの種類を指定する文字列。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<identity\>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|この要素を使用して構成されたカスタム ピア リゾルバーの ID を指定します。  この要素は <xref:System.ServiceModel.Configuration.IdentityElement> 型です。|  
|[\<headers\>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|カスタム ピア リゾルバーによって処理される SOAP メッセージに使用するアドレス ヘッダーのコレクション。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<resolver\>](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|ピア メッシュ ID を解決してメッシュに参加する複数ノードを表すピア ノード アドレスのセットを取得するために使用されるピア リゾルバー。|  
  
## 解説  
 この要素は、サービスをホストするピアのエンドポイント アドレスや特定のバインディング設定など、カスタム ピア リゾルバー サービスの基本設定を定義します。  カスタム リゾルバーを作成する方法の詳細については、「[Adding a Custom Resolver to a PeerChannel Application](http://msdn.microsoft.com/ja-jp/12aa3787-2962-439c-ad27-46523c8b0419)」を参照してください。  
  
## 参照  
 <xref:System.Servicemodel.PeerResolvers.CustomPeerResolverService>   
 <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>   
 <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>   
 <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>   
 [ピア リゾルバー](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)   
 [Adding a Custom Resolver to a PeerChannel Application](http://msdn.microsoft.com/ja-jp/12aa3787-2962-439c-ad27-46523c8b0419)