---
title: "&lt;persistenceProvider&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# &lt;persistenceProvider&gt;
使用する永続化プロバイダーの実装の型と、永続化操作に使用するタイムアウトを指定します。  
  
## 構文  
  
```  
  
<persistenceProvider persistenceOperationTimeout="TimeSpan"  
   type="String" />  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|persistenceOperationTimeout|永続化動作に使用するタイムアウトを指定する <xref:System.TimeSpan> 値。  既定値は “00:00:30” です。|  
|型|使用する永続化プロバイダー ファクトリの型を指定する文字列。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<behavior\>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|動作の要素を指定します。|  
  
## 解説  
 この要素は、WCF サービスの状態をシリアル化するために使用される永続化プロバイダーを指定します。  HTTP ヘッダーに状態情報を渡す `wsHttpContextBinding` と一緒に使用する必要があります。  
  
## 参照  
 <xref:System.ServiceModel.Configuration.PersistenceProviderElement>   
 <xref:System.ServiceModel.Persistence.PersistenceProvider>