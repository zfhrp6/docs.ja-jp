---
title: "&lt;endpointDiscovery&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# &lt;endpointDiscovery&gt;
エンドポイントのさまざまな探索設定を指定します \(探索可能性、スコープ、メタデータに対するカスタム拡張など\)。  
  
## 構文  
  
```  
  
<behaviors>  
  <endpointBehaviors>  
    <behavior name="String">  
      <endpointDiscovery enabled="Boolean">  
        <scopes>  
          <add scope="URI"/>  
        </scopes>  
        <extensions>  
        </extensions>  
      </endpointDiscovery>  
    </behavior>  
  </endpointBehaviors>  
</behaviors>  
  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|enabled|探索可能性をこのエンドポイントで有効にするかどうかを指定するブール値。  既定値は、`false` です。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<scopes\>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|エンドポイントのスコープ URI のコレクション。  複数の URI を 1 つのエンドポイントに関連付けることができます。|  
|[\<extensions\>](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) \[\<endpointDiscovery\>\]|エンドポイントで発行されるカスタム メタデータを指定できる、XML 要素のコレクション。|  
|\<types\>|検索するインターフェイスのコレクション。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<behavior\>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|動作の要素を指定します。|  
|||  
  
## 解説  
 エンドポイントの動作構成に追加し、`enabled` 属性を `true` に設定すると、この構成要素の探索可能性が有効になります。  [\<scopes\>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)[\<extensions\>](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) 子要素を使用して、標準の探索可能なメタデータと共に発行する必要のあるカスタム メタデータを指定することも可能です \(EPR、ContractTypeName、BindingName、Scope、ListenURI\)。  
  
 この構成要素は、探索可能性のサービス レベルでの制御を提供する [\<serviceDiscovery\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) 要素に依存します。  これは、構成に [\<serviceDiscovery\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) が指定されていない場合、この要素の設定が無視されることを意味します。  
  
## 使用例  
 次の構成例では、フィルターのスコープと、エンドポイントで発行される拡張メタデータを指定しています。  
  
```  
  
<services>  
  <service name="CalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
     <endpoint binding="basicHttpBinding"  
              address="calculator"  
              contract="ICalculatorService"  
              behaviorConfiguration="calculatorEndpointBehavior" />  
  </service>  
</services>  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceDiscovery />  
    </behavior>  
  </serviceBehaviors>  
  <endpointBehaviors>  
    <behavior name="calculatorEndpointBehavior">  
      <endpointDiscovery enabled="true">  
        <scopes>  
          <add scope="http://contoso/test1"/>  
          <add scope="http://contoso/test2"/>  
        </scopes>  
        <extensions>  
          <e:Publisher xmlns:e="http://example.org">  
            <e:Name>The Example Organization</e:Name>  
            <e:Address>One Example Way, ExampleTown, EX 12345</e:Address>  
            <e:Contact>support@example.org</e:Contact>  
          </e:Publisher>  
          <AnotherCustomMetadata>Custom Metadata</AnotherCustomMetadata>  
        </extensions>  
      </endpointDiscovery>  
    </behavior>  
  </endpointBehaviors>  
</behaviors>  
  
```  
  
## 参照  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>