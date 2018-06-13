---
title: '&lt;standardEndpoints&gt;'
ms.date: 03/30/2017
ms.assetid: d62153d7-a6e6-462a-a784-cca61e9c2ba1
ms.openlocfilehash: 689ed041304d5ae84218dde2575d7bbd0440490d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33353183"
---
# <a name="ltstandardendpointsgt"></a>&lt;standardEndpoints&gt;
この構成セクションでは、再使用可能な構成済みのエンドポイントである標準エンドポイントのコレクションを定義できます。 標準エンドポイントは、固定値に設定されたアドレス、バインディング、およびコントラクトの 1 つ以上の属性を持ちます。 たとえば、探索エンドポイントでは、コントラクトが固定されています。 標準エンドポイントを使用して、カスタム バインドの定義と同様に新しいプロパティを指定して、サービス エンドポイントを拡張することもできます。  
  
 \<system.ServiceModel >  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.serviceModel>  
    <standardEndpoints>  
    </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<announcementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md)|固定アナウンス コントラクトが含まれた標準エンドポイントを定義します。 サービスは、サービスが開いたとき、または閉じたときにオンラインおよびオフラインのアナウンス メッセージを送信することによって、その可用性をアナウンスすることもできます。 Windows Communication Foundation (WCF) サービスでアナウンス エンドポイントを指定する、 [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md)要素と使用をお知らせを実行する AnnouncementClient です。 他のサービスからのアナウンスをリッスンするように元のクライアントが、WCF サービスとして動作して実際にはそのクライアントのアナウンス エンドポイントを構成する必要があるため、 [ \<services >](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md)セクションです。|  
|[\<discoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md)|固定探索コントラクトが含まれた標準エンドポイントを定義します。 サービスの構成に追加すると、この要素により、探索メッセージをリッスンする場所が指定されます。 クライアントの構成に追加すると、この要素により、探索クエリの送信先となる場所が指定されます。|  
|[\<dynamicEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/dynamicendpoint.md)|この構成要素は、アプリケーションが、実行時に動的にエンドポイント アドレスを検索するクライアント プログラムとして機能するための情報を格納する標準エンドポイントを定義します。|  
|[\<mexEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/mexendpoint.md)|固定 IMetadataExchange コントラクトが含まれた標準エンドポイントを定義します。 IMetadataExchange はすべてのメタデータ交換エンドポイントでコントラクトとして指定されるため、独自のエンドポイントを定義せずにこの標準エンドポイントを使用できます。|  
|[\<udpAnnoucementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/udpannoucementendpoint.md)|サービスが UDP バインディングでアナウンス メッセージを送信するために使用する標準エンドポイントを定義します。 これには固定コントラクトがあり、2 つの探索のバージョンをサポートします。 また、WS-Discovery の仕様 (WS-Discovery April 2005 または WS-Discovery V1.1) に規定された固定 UDP バインディングと既定のアドレスも備えています。 アナウンス メッセージの送受信に使用するマルチキャスト アドレスを指定できます。|  
|[\<udpDiscoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/udpdiscoveryendpoint.md)|UDP マルチキャスト バインディングを使用した探索操作用に事前に構成される標準エンドポイントを定義します。 このエンドポイントには固定コントラクトがあり、WS-Discovery プロトコルの 2 つのバージョンをサポートします。 また、WS-Discovery の仕様 (WS-Discovery April 2005 または WS-Discovery V1.1) に規定された固定 UDP バインディングと既定のアドレスも備えています。|  
|[\<webHttpEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpendpoint.md)|固定の標準エンドポイントを定義[ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)自動的にバインディングを追加、 [ \<webHttp >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md)動作します。 このエンドポイントは、REST サービスを作成する場合に使用します。|  
|[\<webScriptEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/webscriptendpoint.md)|固定の標準エンドポイントを定義[ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)自動的にバインディングを追加、 [ \<enableWebScript >](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md)動作します。 このエンドポイントは、ASP.NET AJAX アプリケーションから呼び出されるサービスを作成する場合に使用します。|  
|[\<workflowControlEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/workflowcontrolendpoint.md)|ワークフロー インスタンスの実行の制御 (作成、実行、保留、終了など) に使用する標準エンドポイントを定義します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|\<system.ServiceModel >|すべての WCF 構成要素のルート要素です。|  
  
## <a name="see-also"></a>関連項目  
 [標準エンドポイント](../../../../../docs/framework/wcf/feature-details/standard-endpoints.md)
