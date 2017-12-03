---
title: '&lt;endpointDiscovery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6cca48cec486cfdbb9bca2eba48847c25c35abe9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltendpointdiscoverygt"></a>&lt;endpointDiscovery&gt;
エンドポイントのさまざまな探索設定を指定します (探索可能性、スコープ、メタデータに対するカスタム拡張など)。  
  
\<システムです。ServiceModel >  
\<ビヘイビアー >  
\<endpointBehaviors >  
\<動作 >  
\<endpointDiscovery >  
  
## <a name="syntax"></a>構文  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enabled="Boolean">
        <scopes>
          <add scope="URI"/>
        </scopes>
        <extensions />
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|enabled|探索可能性をこのエンドポイントで有効にするかどうかを指定するブール値。 既定値は、`false` です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<スコープ >](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|エンドポイントのスコープ URI のコレクション。 複数の URI を 1 つのエンドポイントに関連付けることができます。|  
|[\<拡張機能 >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) [の\<endpointDiscovery >]|エンドポイントで発行されるカスタム メタデータを指定できる、XML 要素のコレクション。|  
|\<種類 >|検索するインターフェイスのコレクション。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<動作 >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|動作の要素を指定します。|  
|||  
  
## <a name="remarks"></a>コメント  
 エンドポイントの動作構成に追加し、`enabled` 属性を `true` に設定すると、この構成要素の探索可能性が有効になります。 さらに、使用することができます、 [\<スコープ >](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)子要素のカスタム スコープ Uri、クエリ中にサービス エンドポイントのフィルター処理に使用できるを指定するだけでなく[\<拡張子 >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md)子要素のカスタム メタデータ (EPR、ContractTypeName、必要のある、スコープおよび ListenURI) は、標準の探索可能メタデータと共に発行する必要がありますを指定します。  
  
 この構成要素が依存、 [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md)探索可能性のサービス レベルの制御を提供する要素。 場合、この要素の設定は無視されます、つまり[ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md)は構成に存在しません。  
  
## <a name="example"></a>例  
 次の構成例では、フィルターのスコープと、エンドポイントで発行される拡張メタデータを指定しています。  
  
```xml  
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
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
