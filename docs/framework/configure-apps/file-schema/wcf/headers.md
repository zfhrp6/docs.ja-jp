---
title: "&lt;ヘッダー&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5d5e0a56055df588e9e42c4e1855c352c3f0d1b2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltheadersgt"></a>&lt;ヘッダー&gt;
エンドポイントは、基本となる URI だけでなく、1 つ以上の SOAP ヘッダーによってアドレス指定することもできます。 これが役に立つのは、エンドポイントのクライアントに中継局を指す SOAP ヘッダーを含める必要がある、SOAP 中継局のシナリオの場合です。 この構成要素を使用して、カスタムのアドレス ヘッダーを定義できます。 エンドポイント ヘッダー コレクション内のエントリは、ユーザー定義の XML 要素です。 各要素は、正しい形式の XML である必要があります。  
  
 \<システムです。ServiceModel >  
\<クライアント >  
\<エンドポイント >  
  
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
|[\<エンドポイント >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|さまざまなタイプのエンドポイントを設定します。|  
  
## <a name="remarks"></a>コメント  
 オプション ヘッダーは、エンドポイントの識別または対話のために、より詳細なアドレス指定情報を提供します。 たとえば、ヘッダーを使用して、受信メッセージの処理方法や、エンドポイントからの応答メッセージの送信先を指定できるほか、複数のサービス インスタンスが使用できる場合に、特定ユーザーからの受信メッセージの処理に使用するインスタンスを指定できます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Headers%2A>  
 <xref:System.ServiceModel.Channels.AddressHeaderCollection>  
 [エンドポイント: アドレス、バインディング、およびコントラクト](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
