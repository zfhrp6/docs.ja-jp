---
title: '&lt;findCriteria&gt;'
ms.date: 03/30/2017
ms.assetid: 5454cd19-6bf5-4ba8-94d1-f58d10dc1917
ms.openlocfilehash: fc9cd3b87d0f47ae0f16b5c5bfcaa4a1167bae9f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32748647"
---
# <a name="ltfindcriteriagt"></a>&lt;findCriteria&gt;
探索サービスの検索にクライアント アプリケーションによって使用される基準を提供する構成要素。 条件は、(探しているサービスの種類を指定する) 検索条件にグループ化できるし、検索終了条件 (期間、検索する必要があります)。  
  
 \<system.ServiceModel >  
\<standardEndpoints >  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <dynamicEndpoint>
      <standardEndpoint>
        <discoveryClientSettings discoveryEndpoint="String">
          <findCriteria duration="TimeSpan" maxResults="Integer" scopeMatchBy="Uri">
            <contractTypeNames>
              <add name="String" namespace="String" />
            <contractTypeNames>
            <extensions />
            <scopes>
              <add scope="URI" />
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      </standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|duration|ネットワーク上でサービスからの応答を待機する最長時間を指定する Timespan 値。 既定の時間は 20 秒です。|  
|maxResults|ネットワークまたはインターネット上で待機する、サービスから応答の最大数を指定する整数。 `duration` 属性に指定した時間が経過する前に応答の最大数に達した場合、検索操作は終了します。|  
|scopeMatchBy|Probe メッセージのスコープをエンドポイントのスコープと一致させるときに使用する、一致のアルゴリズムを指定する URI。<br /><br /> サポートされているスコープ一致規則は 5 つあります。 スコープ一致規則を指定しなかった場合は、`ScopeMatchByPrefix` が使用されます。 詳細については、「<xref:System.ServiceModel.Discovery.FindCriteria>」を参照してください。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<contractTypeNames >](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|ワークフロー サービス コントラクト型の名前を格納する構成要素のコレクション。|  
|\<拡張機能 > の\<findCriteria >|拡張を提供する XML 要素オブジェクトのコレクション。|  
|[\<スコープ >](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|特定のサービスを特定する検索操作の実行中に使用される絶対 URI を格納するオブジェクトのコレクション。<br /><br /> 特定のサービスが見つかった場合、サービス URI とスコープ URI が一致します。複雑な一致を処理するスコープ規則が使用されることもあります。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<standardEndpoints >](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|サービス探索プロセスにクライアントとして参加するためにアプリケーションが必要とする設定を格納します。|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Discovery.FindCriteria>  
 <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
