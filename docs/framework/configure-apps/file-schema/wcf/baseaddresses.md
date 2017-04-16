---
title: "&lt;baseAddresses&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# &lt;baseAddresses&gt;
自己ホスト環境でのサービス ホストのベース アドレスである `baseAddress` 要素のコレクションを表します。  ベース アドレスが存在すると、そのベース アドレスに関連したアドレスを使用してエンドポイントを構成できます。  
  
## 構文  
  
```  
  
<baseAddresses>  
   <add baseAddress="string" />  
</baseAddresses>  
```  
  
## 型  
 `Type`  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
 なし。  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<add\>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md)|サービス ホストによって使用されるベース アドレスを指定する構成要素。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<host\>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|サービス ホストの設定を指定する構成要素です。|  
  
## 参照  
 <xref:System.ServiceModel.Configuration.HostElement>   
 <xref:System.ServiceModel.ServiceHost>   
 <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>   
 [ホスト](../../../../../docs/framework/wcf/feature-details/hosting.md)