---
title: "&lt;clientVia&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# &lt;clientVia&gt;
トランスポート チャネルの作成対象となる URI を指定します。  詳細については、「<xref:System.ServiceModel.Description.ClientViaBehavior>」を参照してください。  
  
## 構文  
  
```  
  
<clientVia viaUri="String"/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|`viaUri`|メッセージの経路を示す URI を指定する文字列。|  
  
### 子要素  
 なし  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<behavior\>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|エンドポイントの動作を指定します。|  
  
## 参照  
 <xref:System.ServiceModel.Configuration.ClientViaElement>   
 <xref:System.ServiceModel.Description.ClientViaBehavior>