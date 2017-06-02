---
title: "&lt;serviceBehavior&gt; の &lt;routing&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d8f9c844-4629-4a45-9599-856dc8f01794
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# &lt;serviceBehavior&gt; の &lt;routing&gt;
ルーティング構成の動的な変更を可能にするルーティング サービスへの実行時アクセスを提供します。  
  
## 構文  
  
```  
  
<behaviors>  
  <serviceBehaviors>  
    <behavior name=String">  
      <routing filterTable=”String”  
         routeOnHeadersOnly="Boolean"  
         SoapProcessingEnabled=”Boolean” />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|filterTable|ルーティング サービスによって評価されるフィルターを含むルーティング テーブルの名前を指定する文字列。  この値は、[\<filterTables\>](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) セクションにある [\<filterTable\>](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertable.md) 要素の `name` 属性の値と一致する必要があります。|  
|routeOnHeaderOnly|フィルターがメッセージの本文とヘッダーの両方を調べるか、ヘッダーのみを調べるかを指定するブール値。  既定値は、`true` です。|  
|soapProcessingEnabled|SOAP 処理を実行するかどうかを指定するブール値。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<behavior\>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|動作の要素を指定します。|  
  
## 解説  
 サービスの動作構成に追加すると、この構成要素により、サービスのルーティングが有効になります。  この要素には、サービスで使用される実際のルーティング テーブルを指定できます。  
  
 この構成セクションを使用すると、配置パターンの変更時にルーティング設定を変更できます。  実行時には、新しいルーティング設定を使用した独自のルーティング拡張を登録できます。ルーティング サービスは \(開始時に適用されていた規則に関係なく\) 更新済みの構成情報を使用して新たなメッセージとセッションにサービスを提供します。ただし、インフライトのメッセージやセッションには以前の規則が適用されます。このようにして、実行時において、セッション セーフでリサイクルの程度を抑えた状態でのルーティング サービスの再構成が可能となります。  
  
## 参照  
 <xref:System.ServiceModel.Routing.RoutingExtenstion>   
 <xref:System.ServiceModel.Routing.Configuration.RoutingExtenstionElement>