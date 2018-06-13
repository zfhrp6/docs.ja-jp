---
title: '方法: Probe 要求の探索バージョンを特定する'
ms.date: 03/30/2017
ms.assetid: b3c4e2e2-2957-4074-ae6a-776a5ca84278
ms.openlocfilehash: 8ac9804b0fe46ca5fbe580d713ec82a2f9bb0128
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489782"
---
# <a name="how-todetermine-the-discovery-version-of-a-probe-request"></a><span data-ttu-id="e7cc1-102">方法: Probe 要求の探索バージョンを特定する</span><span class="sxs-lookup"><span data-stu-id="e7cc1-102">How to:Determine the Discovery Version of a Probe Request</span></span>
<span data-ttu-id="e7cc1-103">探索プロキシでは、異なる探索バージョンを使用する複数の探索エンドポイントを公開する場合があります。</span><span class="sxs-lookup"><span data-stu-id="e7cc1-103">A discovery proxy may expose multiple discovery endpoints using different discovery versions.</span></span> <span data-ttu-id="e7cc1-104">プロキシでは、UDP マルチキャスト Probe 要求を受け取った場合、マルチキャスト抑制メッセージで応答する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e7cc1-104">When a UDP multicast Probe request arrives at the proxy the proxy should respond with a multicast suppression message.</span></span> <span data-ttu-id="e7cc1-105">これを行うには、要求の探索バージョンを特定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e7cc1-105">In order to do this it would have to know the discovery version of the request.</span></span>  
  
### <a name="to-determine-the-discovery-version-of-a-probe-request"></a><span data-ttu-id="e7cc1-106">Probe 要求の探索バージョンを特定するには</span><span class="sxs-lookup"><span data-stu-id="e7cc1-106">To Determine the Discovery Version of a Probe Request</span></span>  
  
1.  <span data-ttu-id="e7cc1-107">次のコードに示すように、Probe 要求に応答するメソッド (<xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A> など) で静的 <xref:System.ServiceModel.OperationContext.Current%2A> プロパティを使用して <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension> を検索します。</span><span class="sxs-lookup"><span data-stu-id="e7cc1-107">In the method that responds to a Probe request (for example <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A>) use the static <xref:System.ServiceModel.OperationContext.Current%2A> property to search for a <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension> as shown in the following code.</span></span>  
  
    ```  
    DiscoveryOperationContextExtension doce = OperationContext.Current.Extensions.Find<DiscoveryOperationContextExtension>();  
    // Access the discovery version from the DiscoveryOperationContextExtension  
    doce.DiscoveryVersion;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e7cc1-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="e7cc1-108">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion%2A>  
 [<span data-ttu-id="e7cc1-109">探索プロキシの実装</span><span class="sxs-lookup"><span data-stu-id="e7cc1-109">Implementing a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md)  
 [<span data-ttu-id="e7cc1-110">探索プロキシのサンプル</span><span class="sxs-lookup"><span data-stu-id="e7cc1-110">Discovery Proxy Sample</span></span>](../../../../docs/framework/wcf/samples/discovery-proxy-sample.md)
