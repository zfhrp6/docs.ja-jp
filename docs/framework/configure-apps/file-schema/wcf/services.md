---
title: "&lt;services&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# &lt;services&gt;
サービスは、設定ファイルの `services` セクションで定義されます。  各サービスには、独自の `service` 設定セクションがあります。  
  
 \<system.ServiceModel\>  
  
## 構文  
  
```  
  
<system.serviceModel>  
        <services>  
        <service>  
        </service>  
        </services>  
</system.serviceModel>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
 なし  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<service\>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|サービス コントラクト、動作、および特定のサービスのエンドポイントを定義します。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<system.serviceModel\>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|すべての Windows Communication Foundation \(WCF\) 構成要素のルート要素です。|  
  
## 参照  
 <xref:System.ServiceModel.Configuration.ServicesSection>