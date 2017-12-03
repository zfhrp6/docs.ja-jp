---
title: "メタデータ エンドポイントを公開する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 29cd8a60-dfb7-460c-bf5a-c2b31b782671
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 64032fbc675e30e9f01a5db4d56ecc36574e08de
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="publishing-metadata-endpoints"></a><span data-ttu-id="1caff-102">メタデータ エンドポイントを公開する</span><span class="sxs-lookup"><span data-stu-id="1caff-102">Publishing Metadata Endpoints</span></span>
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]<span data-ttu-id="1caff-103"> サービスは 1 つ以上のメタデータ エンドポイントを公開することにより、メタデータを公開します。</span><span class="sxs-lookup"><span data-stu-id="1caff-103"> services publish metadata by publishing one or more metadata endpoints.</span></span> <span data-ttu-id="1caff-104">サービス メタデータを公開すると、そのメタデータで WS-MetadataExchange (MEX) や HTTP/GET 要求などの標準化プロトコルを使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="1caff-104">Publishing service metadata makes the metadata available using standardized protocols, such as WS-MetadataExchange (MEX) and HTTP/GET requests.</span></span> <span data-ttu-id="1caff-105">メタデータのエンドポイントは、アドレス、バインディング、およびコントラクトを持つ他のサービス エンドポイントに似ており、構成またはコードを使用してサービス ホストに追加できます。</span><span class="sxs-lookup"><span data-stu-id="1caff-105">Metadata endpoints are similar to other service endpoints in that they have an address, a binding, and a contract, and they can be added to a service host through configuration or in code.</span></span> <span data-ttu-id="1caff-106">メタデータ エンドポイントの公開を有効にするには、<xref:System.ServiceModel.Description.ServiceMetadataBehavior> サービス動作をサービスに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1caff-106">To enable publishing metadata endpoints, you must add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> service behavior to the service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1caff-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="1caff-107">In This Section</span></span>  
 [<span data-ttu-id="1caff-108">方法: 構成ファイルを使用して、サービスのメタデータを公開</span><span class="sxs-lookup"><span data-stu-id="1caff-108">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 <span data-ttu-id="1caff-109">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスを構成してメタデータを公開し、`?wsdl` クエリ文字列を使用した WS-MetadataExchange または HTTP/GET 要求によりメタデータをクライアントが取得できるようにする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1caff-109">Demonstrates how to configure a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service to publish metadata so that clients can retrieve the metadata using a WS-MetadataExchange or an HTTP/GET request using the `?wsdl` query string.</span></span>  
  
 [<span data-ttu-id="1caff-110">方法: コードを使用して、サービスのメタデータを公開</span><span class="sxs-lookup"><span data-stu-id="1caff-110">How to: Publish Metadata for a Service Using Code</span></span>](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 <span data-ttu-id="1caff-111">コードを使用して [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスのメタデータの公開を有効にして、クライアントが `?wsdl` クエリ文字列を使用した WS-MetadataExchange または HTTP/GET 要求によりメタデータを取得できるようにする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1caff-111">Demonstrates how to enable metadata publishing for a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service in code so that clients can retrieve the metadata using a WS-MetadataExchange or an HTTP/GET request using the `?wsdl` query string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1caff-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="1caff-112">See Also</span></span>  
 [<span data-ttu-id="1caff-113">メタデータの公開</span><span class="sxs-lookup"><span data-stu-id="1caff-113">Publishing Metadata</span></span>](../../../docs/framework/wcf/feature-details/publishing-metadata.md)
