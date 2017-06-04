---
title: "&lt;serviceAuthenticationManager&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# &lt;serviceAuthenticationManager&gt;
サービス レベルで転送、メッセージ、または送信元の有効性を確立するワークフロー構成要素を提供します。  
  
## 構文  
  
```  
  
<behaviors>  
  <serviceBehaviors>  
    <behavior name=String">  
      <serviceAuthenticationManager serviceAuthenticationManagerType =”String”/>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|serviceAuthenticationManagerType|現在の動作の認証ポリシーの種類を指定する文字列。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<behavior\>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|動作の要素を指定します。|  
  
## 参照  
 <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>