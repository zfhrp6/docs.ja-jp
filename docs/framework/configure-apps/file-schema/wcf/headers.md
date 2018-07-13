---
title: '&lt;header&gt;'
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: 7683b07093719cda6b210a4174d47e5785d4644d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747152"
---
# <a name="ltheadersgt"></a>&lt;header&gt;
エンドポイントは、基本となる URI だけでなく、1 つ以上の SOAP ヘッダーによってアドレス指定することもできます。 これが役に立つのは、エンドポイントのクライアントに中継局を指す SOAP ヘッダーを含める必要がある、SOAP 中継局のシナリオの場合です。 この構成要素を使用して、カスタムのアドレス ヘッダーを定義できます。 エンドポイント ヘッダー コレクション内のエントリは、ユーザー定義の XML 要素です。 各要素は、正しい形式の XML である必要があります。  
  
 \<system.ServiceModel >  
\<client>  
\<endpoint>  
  
## <a name="syntax"></a>構文  
  
```xml  
<headers>  
    <Region xmlns="Uri">"String"</Region>  
        <Member xmlns="Uri">"String"</Member>  
</headers>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|Region||  
|メンバー||  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<endpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|さまざまなタイプのエンドポイントを設定します。|  
  
## <a name="remarks"></a>コメント  
 オプション ヘッダーは、エンドポイントの識別または対話のために、より詳細なアドレス指定情報を提供します。 たとえば、ヘッダーを使用して、受信メッセージの処理方法や、エンドポイントからの応答メッセージの送信先を指定できるほか、複数のサービス インスタンスが使用できる場合に、特定ユーザーからの受信メッセージの処理に使用するインスタンスを指定できます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Headers%2A>  
 <xref:System.ServiceModel.Channels.AddressHeaderCollection>  
 [エンドポイント : アドレス、バインディング、およびコントラクト](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
