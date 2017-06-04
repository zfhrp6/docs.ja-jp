---
title: "&lt;findCriteria&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5454cd19-6bf5-4ba8-94d1-f58d10dc1917
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# &lt;findCriteria&gt;
探索サービスの検索にクライアント アプリケーションによって使用される基準を提供する構成要素。  基準は、\(探しているサービスを指定する\) 検索条件と \(検索をどのくらい続けるかを指定する\) 検索終了条件にグループ化できます。  
  
## 構文  
  
```  
  
<system.serviceModel>  
    <standardEndpoints>  
       <dynamicEndpoint>   
          <standardEndpoint>  
             <discoveryClientSettings discoveryEndpoint=”String” >  
               <findCriteria duration=”TimeSpan”  
                  maxResults=”Integer”   
                  scopeMatchBy=”Uri” >  
                  <contractTypeNames>  
                     <add name="String" namespace="String" />  
                  <contractTypeNames>  
                  <extensions />  
                  <scopes>  
                    <add scope="URI"/>  
                  </scopes>  
               </findCriteria>  
             </discoveryClientSettings>  
          <standardEndpoint>  
       </dynamicEndpoint>          
    </standardEndpoints>  
</system.serviceModel>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|duration|ネットワーク上でサービスからの応答を待機する最長時間を指定する Timespan 値。  既定の時間は 20 秒です。|  
|maxResults|ネットワークまたはインターネット上で待機する、サービスから応答の最大数を指定する整数。  `duration` 属性に指定した時間が経過する前に応答の最大数に達した場合、検索操作は終了します。|  
|scopeMatchBy|Probe メッセージのスコープをエンドポイントのスコープと一致させるときに使用する、一致のアルゴリズムを指定する URI。<br /><br /> サポートされているスコープ一致規則は 5 つあります。  スコープ一致規則を指定しなかった場合は、`ScopeMatchByPrefix` が使用されます。  詳細については、「<xref:System.ServiceModel.Discovery.FindCriteria>」を参照してください。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<contractTypeNames\>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|ワークフロー サービス コントラクト型の名前を格納する構成要素のコレクション。|  
|\<findCriteria\> の \<extensions\>|拡張を提供する XML 要素オブジェクトのコレクション。|  
|[\<scopes\>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|特定のサービスを特定する検索操作の実行中に使用される絶対 URI を格納するオブジェクトのコレクション。<br /><br /> 特定のサービスが見つかった場合、サービス URI とスコープ URI が一致します。複雑な一致を処理するスコープ規則が使用されることもあります。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<standardEndpoints\>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|サービス探索プロセスにクライアントとして参加するためにアプリケーションが必要とする設定を格納します。|  
  
## 参照  
 <xref:System.ServiceModel.Discovery.FindCriteria>   
 <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>