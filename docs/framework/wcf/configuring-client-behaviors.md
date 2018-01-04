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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ee79900b52ae0fa58e8fb9a5cbbf50f5a882c295
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-client-behaviors"></a><span data-ttu-id="6e725-102">クライアントの動作の構成</span><span class="sxs-lookup"><span data-stu-id="6e725-102">Configuring Client Behaviors</span></span>
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]<span data-ttu-id="6e725-103"> は 2 とおりの方法で動作を構成します。1 つは動作の構成を参照する方法で、これはクライアント アプリケーションの構成ファイルの `<behavior>` セクションで定義されます。もう 1 つは、呼び出し元アプリケーションでプログラムによって動作を構成する方法です。</span><span class="sxs-lookup"><span data-stu-id="6e725-103"> configures behaviors in two ways: either by referring to behavior configurations -- which are defined in the `<behavior>` section of a client application configuration file – or programmatically in the calling application.</span></span> <span data-ttu-id="6e725-104">このトピックでは、両方の方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6e725-104">This topic describes both approaches.</span></span>  
  
 <span data-ttu-id="6e725-105">構成ファイルを使用する場合、動作の構成には、構成設定の名前付きコレクションがあります。</span><span class="sxs-lookup"><span data-stu-id="6e725-105">When using a configuration file, behavior configuration is a named collection of configuration settings.</span></span> <span data-ttu-id="6e725-106">各動作の構成には、一意の名前を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6e725-106">The name of each behavior configuration must be unique.</span></span> <span data-ttu-id="6e725-107">この文字列をエンドポイントの構成の `behaviorConfiguration` 属性で使用し、エンドポイントと動作を関連付けます。</span><span class="sxs-lookup"><span data-stu-id="6e725-107">This string is used in the `behaviorConfiguration` attribute of an endpoint configuration to link the endpoint to the behavior.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e725-108">例</span><span class="sxs-lookup"><span data-stu-id="6e725-108">Example</span></span>  
 <span data-ttu-id="6e725-109">`myBehavior` という動作を定義する構成コードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="6e725-109">The following configuration code defines a behavior called `myBehavior`.</span></span> <span data-ttu-id="6e725-110">クライアント エンドポイントは、この動作を `behaviorConfiguration` 属性で参照します。</span><span class="sxs-lookup"><span data-stu-id="6e725-110">The client endpoint references this behavior in the `behaviorConfiguration` attribute.</span></span>  
  
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
  
## <a name="using-behaviors-programmatically"></a><span data-ttu-id="6e725-111">プログラムによる動作の使用</span><span class="sxs-lookup"><span data-stu-id="6e725-111">Using Behaviors Programmatically</span></span>  
 <span data-ttu-id="6e725-112">クライアントを開く前に、`Behaviors` クライアント オブジェクトまたはクライアント チャネル ファクトリ オブジェクト上の適切な [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] プロパティを見つけることで、動作をプログラムによって構成または挿入することもできます。</span><span class="sxs-lookup"><span data-stu-id="6e725-112">You can also configure or insert behaviors programmatically by locating the appropriate `Behaviors` property on the [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] client object or on the client channel factory object prior to opening the client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e725-113">例</span><span class="sxs-lookup"><span data-stu-id="6e725-113">Example</span></span>  
 <span data-ttu-id="6e725-114">次のコード例は、チャネル オブジェクトの作成前に、<xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> プロパティから返される <xref:System.ServiceModel.Description.ServiceEndpoint> 上の <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> プロパティにアクセスすることで、プログラムでクライアント動作が挿入される方法を示します。</span><span class="sxs-lookup"><span data-stu-id="6e725-114">The following code example shows how to programmatically insert a behavior by accessing the <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> property on the <xref:System.ServiceModel.Description.ServiceEndpoint> returned from the <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> property prior to the creation of the channel object.</span></span>  
  
 [!code-csharp[ChannelFactoryBehaviors#10](../../../samples/snippets/csharp/VS_Snippets_CFX/channelfactorybehaviors/cs/client.cs#10)]
 [!code-vb[ChannelFactoryBehaviors#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelfactorybehaviors/vb/client.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="6e725-115">参照</span><span class="sxs-lookup"><span data-stu-id="6e725-115">See Also</span></span>  
 [<span data-ttu-id="6e725-116">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="6e725-116">\<behaviors></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)
