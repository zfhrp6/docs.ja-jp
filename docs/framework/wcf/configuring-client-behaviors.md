---
title: "クライアントの動作の構成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: df5b32fa-e73b-4e8e-b66f-357c748e0173
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6f16f32128c7223fa600802ae593d36286847dc8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="configuring-client-behaviors"></a>クライアントの動作の構成
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] は 2 とおりの方法で動作を構成します。1 つは動作の構成を参照する方法で、これはクライアント アプリケーションの構成ファイルの `<behavior>` セクションで定義されます。もう 1 つは、呼び出し元アプリケーションでプログラムによって動作を構成する方法です。 このトピックでは、両方の方法について説明します。  
  
 構成ファイルを使用する場合、動作の構成には、構成設定の名前付きコレクションがあります。 各動作の構成には、一意の名前を指定する必要があります。 この文字列をエンドポイントの構成の `behaviorConfiguration` 属性で使用し、エンドポイントと動作を関連付けます。  
  
## <a name="example"></a>例  
 `myBehavior` という動作を定義する構成コードを次に示します。 クライアント エンドポイントは、この動作を `behaviorConfiguration` 属性で参照します。  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name="myBehavior">  
                    <clientVia />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
        <bindings>  
            <basicHttpBinding>  
                <binding name="myBinding" maxReceivedMessageSize="10000" />  
            </basicHttpBinding>  
        </bindings>  
        <client>  
            <endpoint address="myAddress" binding="basicHttpBinding" bindingConfiguration="myBinding" behaviorConfiguration="myBehavior" contract="myContract" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="using-behaviors-programmatically"></a>プログラムによる動作の使用  
 クライアントを開く前に、`Behaviors` クライアント オブジェクトまたはクライアント チャネル ファクトリ オブジェクト上の適切な [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] プロパティを見つけることで、動作をプログラムによって構成または挿入することもできます。  
  
## <a name="example"></a>例  
 次のコード例は、チャネル オブジェクトの作成前に、<xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> プロパティから返される <xref:System.ServiceModel.Description.ServiceEndpoint> 上の <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> プロパティにアクセスすることで、プログラムでクライアント動作が挿入される方法を示します。  
  
 [!code-csharp[ChannelFactoryBehaviors#10](../../../samples/snippets/csharp/VS_Snippets_CFX/channelfactorybehaviors/cs/client.cs#10)]
 [!code-vb[ChannelFactoryBehaviors#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelfactorybehaviors/vb/client.vb#10)]  
  
## <a name="see-also"></a>関連項目  
 [\<ビヘイビアー >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)
