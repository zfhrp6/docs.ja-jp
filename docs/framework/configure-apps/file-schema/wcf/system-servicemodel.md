---
title: '&lt;system.serviceModel&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.ServiceModel
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel
helpviewer_keywords:
- <system.serviceModel> element
- system.serviceModel element
ms.assetid: 78519531-ad7a-40d3-b3e7-42f1103d8854
ms.openlocfilehash: ef3af4663462ff2bb93622e128e58a3ac039dcf5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33353212"
---
# <a name="ltsystemservicemodelgt"></a>&lt;system.serviceModel&gt;
この構成セクションには、すべての Windows Communication Foundation (WCF) ServiceModel 構成要素が含まれています。  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.serviceModel>  
  <behaviors>  
  </behaviors>  
  <bindings>  
  </bindings>  
  <client>  
  </client>  
  <comContracts>  
  </comContracts>  
  <commonBehaviors>  
  </commonBehaviors>  
  <diagnostics>  
  </diagnostics>  
  <extensions>  
  </extensions>
  <protocolMapping>
  </protocolMapping>
  <routing>
  </routing>  
  <serviceHostingEnvironment>  
  </serviceHostingEnvironment>  
  <services>  
  </services>
  <standardEndpoints>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<behaviors>](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)|このセクションは、`endpointBehaviors` と`serviceBehaviors` という 2 つの子コレクションを定義します。  各コレクションは、エンドポイントとサービスによって使用されるそれぞれの動作要素を定義します。 各動作要素は、その一意の `name` 属性で識別されます。|  
|[\<bindings>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|このセクションには、標準バインディングおよびカスタム バインドのコレクションが保持されます。 各エントリは、その一意の `name` により識別されます。 サービスは、`name` を使用してバインディングをリンクすることにより、バインディングを使用します。|  
|[\<クライアント >](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|このセクションは、クライアントがサービスの接続に使用するエンドポイントの一覧を含みます。|  
|[\<comContracts>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)|このセクションは、WCF と COM 相互運用が有効な COM コントラクトを定義します。|  
|[\<commonBehaviors >](../../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md)|このセクションは、machine.config ファイルでだけ定義できます。 このセクションは、`endpointBehaviors` と`serviceBehaviors` という 2 つの子コレクションを定義します。  各コレクションは、すべての WCF エンドポイントと、コンピューター上のサービスによって使用されるそれぞれの動作要素を定義します。  両方で、動作が定義されている場合`<commonBehaviors>`と`<behaviors>`セクションではの動作、\<動作 > セクションが優先します。|  
|[\<拡張機能 >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions-section.md)|このセクションには、拡張のコレクションが含まれています。これにより、ユーザー定義のバインディング、動作、およびその他の拡張機能を作成できるようになります。|  
|[\<診断 >](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|このセクションには、WCF の診断機能の設定が含まれます。 ユーザーはトレース、パフォーマンス カウンター、および WMI プロバイダーを有効または無効にしたり、カスタム メッセージ フィルターを追加したりできます。|  
|[\<protocolMapping >](../../../../../docs/framework/configure-apps/file-schema/wcf/protocolmapping.md)|このセクションでは、トランスポート プロトコル スキーム (など、http、net.tcp、net.pipe など) と WCF バインディング間の既定のプロトコル マッピングのセットを定義します。|  
|[\<ルーティング >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|このセクションでは、Windows Communication Foundation (WCF) の種類を決定するルーティング フィルターのセットを定義<xref:System.ServiceModel.Dispatcher.MessageFilter>受信メッセージの評価とルーティング テーブルをメッセージを送信するときにターゲット エンドポイントを定義するときに使用される、フィルターに一致します。|  
|[\<ServiceHostingEnvironment >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|このセクションは、環境をホストするサービスがインスタンス化する特定のトランスポートの型を定義します。 このセクションが空の場合は、既定の型が使用されます。|  
|[\<services>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md)|このセクションには、サービスのコレクションが含まれています。 アセンブリで定義された各サービスの場合、この要素は、サービスの設定を指定する `service` 要素を含みます。|  
|[\<standardEndpoints >](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|このセクションは、再使用可能な構成済みのエンドポイントである標準エンドポイントのコレクションを定義します。 標準エンドポイントは、固定値に設定されたアドレス、バインディング、およびコントラクトの 1 つ以上の属性を持ちます。 たとえば、探索エンドポイントでは、コントラクトが固定されています。 標準エンドポイントを使用して、カスタム バインドの定義と同様に新しいプロパティを指定して、サービス エンドポイントを拡張することもできます。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|\<configuration>|.NET 構成ファイルのすべての構成要素のルート要素。|  
  
## <a name="remarks"></a>コメント  
 WCF では、他の製品の構成セクションに要素を追加しません。  
  
 WCF サービスが定義されている、`services`構成ファイルのセクションです。 アセンブリには、任意の数のサービスを含めることができます。 各サービスには、独自の `service` 設定セクションがあります。 セクションとその内容は、サービス コントラクト、動作、および特定のサービスのエンドポイントを定義します。  
  
 サービスの `name` 属性だけが必須項目です。  既定では、サービスの名前は、サービスの実装に使用される、基になる CLR 型を示します。ただし、<xref:System.ServiceModel.ServiceContractAttribute> の ConfigurationName プロパティを変更して、CLR 型要件をオーバーライドすることもできます。  
  
 `behaviorConfiguration` 属性は省略できます。 サービスが使用するサービス動作を識別します。 この属性で指定された動作は、同じ構成ファイルの範囲内に定義されたサービス動作にリンクしている必要があります。  
  
 各サービスでは、`endpoint` 要素で定義された 1 つまたは複数のエンドポイントが公開されます。 各エンドポイントには、独自のアドレスおよびバインディングがあります。 構成ファイル内で使用されるすべてのバインディングは、そのファイルのスコープ内で定義される必要があります。  
  
 バインディングは、`name` 属性と `bindingConfiguration` 属性の組み合わせによってエンドポイントにリンクされます。 `binding` 属性は、バインディングが定義されているセクションで定義します。 `bindingConfiguration` 属性は、バインディング セクション内で使用される構成済みバインディングを定義します。 バインディング セクションでは、複数の構成済みバインディングを定義できます。  
  
## <a name="example"></a>例  
 これは、WCF 構成ファイルの例です。  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
    <system.serviceModel>  
        <behaviors>  
           <!-- List of Behaviors -->  
        </behaviors>  
        <client>  
           <!-- List of Endpoints -->  
        </client>  
        <diagnostics wmiProviderEnabled="false" performanceCountersEnabled="false" tracingEnabled="false">  
        </diagnostics>  
        <serviceHostingEnvironment>  
           <!-- List of entries -->  
        </serviceHostingEnvironment>  
        <comContracts>  
           <!-- List of COM+ Contracts -->  
        </comContracts>          
        <services>  
           <!-- List of Services -->  
        </services>  
        <bindings>  
           <!-- List of Bindings -->  
        </bindings>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Configuration.ServiceModelSectionGroup>
