---
title: "&lt;extensions&gt; セクション | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# &lt;extensions&gt; セクション
この構成セクションには、拡張のコレクションが含まれています。この拡張のコレクションによってユーザーは、ユーザー定義のバインディング、動作、およびその他の拡張機能を作成できます。  
  
 \<system.ServiceModel\>  
  
## 構文  
  
```  
  
<system.serviceModel>  
    <extensions>  
      <bindingExtensions>  
      </bindingExtensions>  
      <behaviorExtensions>  
      </behaviorExtensions>  
      <bindingElementExtensions>  
      </bindingElementExtensions>  
      <endpointExtensions>  
      </endpointExtensions>  
    </extensions>  
</system.serviceModel>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
 なし。  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<behaviorExtensions\>](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviorextensions.md)|このセクションには、動作拡張を指定する子要素が含まれています。この動作拡張により、ユーザーはサービスまたはエンドポイントの動作をカスタマイズできます。|  
|[\<bindingElementExtensions\>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingelementextensions.md)|このセクションは、コンピューターまたはアプリケーションの構成ファイルからカスタム バインディング要素を使用できます。|  
|[\<bindingExtensions\>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingextensions.md)|このセクションには、バインディング拡張を指定する子要素が含まれています。このバインディング拡張によって、ユーザーはバインディングをカスタマイズできます。|  
|[\<endpointExtensions\>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointextensions.md)|このセクションには、標準エンドポイントを登録する子要素が含まれています。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|system.ServiceModel|すべての WCF 構成要素のルート要素です。|